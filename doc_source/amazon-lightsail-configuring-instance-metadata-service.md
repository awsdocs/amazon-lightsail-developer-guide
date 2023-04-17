# Use the Instance Metadata Service with an Amazon Lightsail instance<a name="amazon-lightsail-configuring-instance-metadata-service"></a>

 *Last updated: January 19, 2023* 

You can access instance metadata from a running instance by using one of the following methods:
+ Instance Metadata Service Version 1 \(IMDSv1\) – a request/response method
+ Instance Metadata Service Version 2 \(IMDSv2\) – a session\-oriented method
**Important**  
Not all instance blueprints in Lightsail support IMDSv2\. Use the `MetadataNoToken` instance metric to track the number of calls to the instance metadata service that are using IMDSv1\. For more information, see [Viewing instance metrics in Amazon Lightsail](amazon-lightsail-viewing-instance-health-metrics.md)\.

By default, you can use either IMDSv1 or IMDSv2, or both\. The instance metadata service distinguishes between IMDSv1 and IMDSv2 requests based on whether a `PUT` or `GET` header, which is unique to IMDSv2, is present in any given request\. For more information, see [Add defense in depth against open firewalls, reverse proxies, and SSRF vulnerabilities with enhancements to the EC2 Instance Metadata Service](https://aws.amazon.com/blogs/security/defense-in-depth-open-firewalls-reverse-proxies-ssrf-vulnerabilities-ec2-instance-metadata-service/)\.

You can configure the instance metadata service on each instance so that local code or users must use IMDSv2\. When you specify that IMDSv2 must be used, IMDSv1 no longer works\. For more information, see [Configure the instance metadata options](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/configuring-instance-metadata-options.html) in the *Amazon Elastic Compute Cloud User Guide for Linux Instances*\.

To retrieve instance metadata, see [Retrieve instance metadata](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/instancedata-data-retrieval.html) in the *Amazon Elastic Compute Cloud User Guide for Linux Instances*\.

**Note**  
The examples in this section use the IPv4 address of the instance metadata service: `169.254.169.254`\. If you are retrieving instance metadata for instances over the IPv6 address, make sure to enable and use the IPv6 address instead: `fd00:ec2::254`\. The IPv6 address of the instance metadata service is compatible with IMDSv2 commands\.

## How Instance Metadata Service Version 2 works<a name="instance-metadata-v2-how-it-works"></a>

IMDSv2 uses session\-oriented requests\. With session\-oriented requests, you create a session token that defines the session duration, which can be a minimum of one second and a maximum of six hours\. During the specified duration, you can use the same session token for subsequent requests\. After the specified duration expires, you must create a new session token to use for future requests\.

The following examples use Linux and PowerShell shell script and IMDSv2 to retrieve the top\-level instance metadata items\. These examples do the following: 
+ Create a session token lasting six hours \(21,600 seconds\) by using the `PUT` request
+ Store the session token header in a variable named `TOKEN` \(on Linux\) or `token` \(on Windows\)
+ Request the top\-level metadata items by using the token

Start by running the following commands:
+ **On Linux:**
  + First, generate a token with the following command\.

    ```
    [ec2-user ~]$ TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"`
    ```
  + Then, use the token to generate top\-level metadata items with the following command\.

    ```
    [ec2-user ~]$ curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/meta-data/
    ```
+ **On Windows:**
  + First, generate a token with the following command\.

    ```
    PS C:\> [string]$token = Invoke-RestMethod -Headers @{"X-aws-ec2-metadata-token-ttl-seconds" = "21600"} -Method PUT -Uri http://169.254.169.254/latest/api/token
    ```
  + Then, use the token to generate top\-level metadata items with the following command\.

    ```
    PS C:\> Invoke-RestMethod -Headers @{"X-aws-ec2-metadata-token" = $token} -Method GET -Uri http://169.254.169.254/latest/meta-data/
    ```

After you create a token, you can reuse it until it expires\. In the following examples, each command gets the ID of the blueprint \(Amazon Machine Image \(AMI\)\) that's used to launch the instance\. The token from the previous example is reused\. It is stored in `$TOKEN` \(on Linux\) or `$token` \(on Windows\)\.
+ **On Linux:**

  ```
  [ec2-user ~]$ curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/meta-data/ami-id
  ```
+ **On Windows:**

  ```
  PS C:\> Invoke-RestMethod -Headers @{"X-aws-ec2-metadata-token" = $token} `
  -Method GET -uri http://169.254.169.254/latest/meta-data/ami-id
  ```

When you use IMDSv2 to request instance metadata, the request must include the following:
+ **A `PUT` request** – Use a `PUT` request to initiate a session to the instance metadata service\. The `PUT` request returns a token that must be included in subsequent `GET` requests to the instance metadata service\. The token is required to access metadata when using IMDSv2\.
+ **The token** – Include the token in all `GET` requests to the instance metadata service\. When token usage is set to `required`, requests without a valid token or with an expired token receive a `401 - Unauthorized` HTTP error code\. For information about changing the token usage requirement, see [update\-instance\-metadata\-options](https://docs.aws.amazon.com/cli/latest/reference/lightsail/update-instance-metadata-options.html) in the *AWS CLI Command Reference*\.
  + The token is an instance\-specific key\. The token is not valid on other instances and will be rejected if you attempt to use it outside of the instance on which it was generated\.
  + The `PUT` request must include a header that specifies the time to live \(TTL\) for the token, in seconds\. The TTL can be specified to a maximum of six hours \(21,600 seconds\)\. The token represents a logical session\. The TTL specifies the length of time that the token is valid and, therefore, the duration of the session\.
  + After a token expires, to continue accessing instance metadata, you must create a new session using another `PUT` request\.
  + You can choose to reuse a token or create a new token with every request\. For a small number of requests, it might be easier to generate and immediately use a token each time you need to access the instance metadata service\. But for efficiency, you can specify a longer duration for the token and reuse it instead of writing a `PUT` request every time you need to request instance metadata\. There is no practical limit on the number of concurrent tokens, with each representing its own session\. IMDSv2 is, however, still constrained by normal instance metadata service connection and throttling limits\. For more information, see [Query throttling](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instancedata-data-retrieval.html#instancedata-throttling) in the *Amazon Elastic Compute Cloud User Guide for Linux Instances*\.

HTTP `GET` and `HEAD` methods are allowed in IMDSv2 instance metadata requests\. `PUT` requests are rejected if they contain an `X-Forwarded-For` header\.

By default, the response to `PUT` requests has a response hop limit \(time to live\) of `1` at the IP protocol level\. If you need a larger hop limit, you can adjust it by using the `update-instance-metadata-options` command\. For example, you might need a larger hop limit for backward compatibility with container services running on the instance\. For more information, see [update\-instance\-metadata\-options](https://docs.aws.amazon.com/cli/latest/reference/lightsail/update-instance-metadata-options.html) in the *AWS CLI Command Reference*\.

## Transition to using Instance Metadata Service Version 2<a name="instance-metadata-transition-to-version-2"></a>

Use of Instance Metadata Service Version 2 \(IMDSv2\) is optional\. Instance Metadata Service Version 1 \(IMDSv1\) will continue to be supported indefinitely\. If you choose to migrate to using IMDSv2, we recommend that you use the following tools and transition path\. 

**Tools for helping with the transition to IMDSv2**

If your software uses IMDSv1, use the following tools to help reconfigure your software to use IMDSv2\.
+ **AWS software:** The latest versions of the AWS SDKs and the AWS CLI support IMDSv2\. To use IMDSv2, make sure that your instances have the latest versions of the AWS SDKs and the AWS CLI\. For information about updating the AWS CLI, see [Installing, updating, and uninstalling the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html) in the *AWS Command Line Interface User Guide*\. All Amazon Linux 2 software packages support IMDSv2\.
+ **Instance metric**: IMDSv2 uses token\-backed sessions, while IMDSv1 does not\. The `MetadataNoToken` instance metric tracks the number of calls to the instance metadata service that are using IMDSv1\. By tracking this metric to zero, you can determine if and when all of your software has been upgraded to use IMDSv2\. For more information, see [Viewing instance metrics in Amazon Lightsail](amazon-lightsail-viewing-instance-health-metrics.md)\.
+ **Updates to Lightsail API operations and AWS CLI commands**: For existing instances, you can use the [update\-instance\-metadata\-options](https://docs.aws.amazon.com/cli/latest/reference/lightsail/update-instance-metadata-options.html) AWS CLI command \(or the [UpdateInstanceMetadataOptions](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UpdateInstanceMetadataOptions.html) API operation\) to require the use of IMDSv2\. The following command is an example\. Make sure you replace *InstanceName* with the name of your instance, and *RegionName* with the AWS Region your instance is in\.

  ```
  aws lightsail update-instance-metadata-options --region RegionName --instance-name InstanceName --http-tokens required
  ```

**Recommended path to requiring IMDSv2 access**

Using the preceding tools, we recommend that you follow this path for transitioning to IMDSv2:

### Step 1: At the start<a name="path-step-1"></a>

Update the AWS SDKs, the AWS CLI, and your software that uses role credentials on your instances to IMDSv2\-compatible versions\. For information about updating the AWS CLI, see [Upgrading to the latest version of the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-linux.html#install-linux-awscli-upgrade) in the *AWS Command Line Interface User Guide*\.

Then, change your software that directly accesses instance metadata \(in other words, that does not use an AWS SDK\) by using the IMDSv2 requests\. 

### Step 2: During the transition<a name="path-step-2"></a>

Track your transition progress by using the instance metric `MetadataNoToken`\. This metric shows the number of calls to the instance metadata service that are using IMDSv1 on your instances\. For more information, see [Viewing instance metrics in Amazon Lightsail](amazon-lightsail-viewing-instance-health-metrics.md)\.

### Step 3: When everything is ready on all instances<a name="path-step-3"></a>

Everything is ready on all instances when the instance metric `MetadataNoToken` records zero IMDSv1 usage\. At this stage, you can require IMDSv2 use through the [update\-instance\-metadata\-options](https://docs.aws.amazon.com/cli/latest/reference/lightsail/update-instance-metadata-options.html) command\. You can make these changes on running instances; you do not need to restart your instances\. 

Updating instance metadata options for existing instances is available only through the Lightsail API or the AWS CLI\. It is currently not available in the Lightsail console\. For more information, see [update\-instance\-metadata\-options](https://docs.aws.amazon.com/cli/latest/reference/lightsail/update-instance-metadata-options.html)\.

## Additional IMDS documentation<a name="amazon-lightsail-configuring-instance-metadata-service-imds-documentation"></a>

The following IMDS documentation is available in the *Amazon Elastic Compute Cloud User Guide for Linux Instances* and the *Amazon Elastic Compute Cloud User Guide for Windows Instances*:

**Note**  
In Amazon EC2, instance blueprints are referred to as Amazon Machine Images \(AMIs\)\.
+ For Linux instances:
  + [Configure the instance metadata options](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/configuring-instance-metadata-options.html)
  + [Retrieve instance metadata](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instancedata-data-retrieval.html)
  + [Work with instance user data](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instancedata-add-user-data.html)
  + [Retrieve dynamic data](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instancedata-dynamic-data-retrieval.html)
  + [Instance metadata categories](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instancedata-data-categories.html)
  + [Example: AMI launch index value](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMI-launch-index-examples.html)
  + [Instance identity documents](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-identity-documents.html)
+ For Windows instances:
  + [Configure the instance metadata options](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/configuring-instance-metadata-options.html)
  + [Retrieve instance metadata](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/instancedata-data-retrieval.html)
  + [Work with instance user data](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/instancedata-add-user-data.html)
  + [Retrieve dynamic data](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/instancedata-dynamic-data-retrieval.html)
  + [Instance metadata categories](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/instancedata-data-categories.html)
  + [Example: AMI launch index value](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/AMI-launch-index-examples.html)
  + [Instance identity documents](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/instance-identity-documents.html)