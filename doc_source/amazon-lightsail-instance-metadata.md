# Instance metadata and user data in Amazon Lightsail<a name="amazon-lightsail-instance-metadata"></a>

 *Last updated: September 23, 2022* 

*Instance metadata* is data about your instance that you can use to configure or manage the running instance\. Instance metadata is divided into categories, for example, hostname, events, and security groups\. You can also use instance metadata to access user data that you specified when launching your instance\. For example, you can specify parameters for configuring your instance, or include a simple script\. Instances can also include dynamic data, such as an instance identity document that is generated when the instance is launched\.

**Important**  
Although you can only access instance metadata and user data from within the instance itself, the data is not protected by authentication or cryptographic methods\. Anyone who has direct access to the instance, and potentially any software running on the instance, can view its metadata\. Therefore, you should not store sensitive data, such as passwords or long\-lived encryption keys, as user data\.

## Use the Instance Metadata Service<a name="amazon-lightsail-use-imds"></a>

You can access instance metadata from a running instance in Lightsail by using one of the following methods:
+ Instance Metadata Service Version 1 \(IMDSv1\) – a request/response method
+ Instance Metadata Service Version 2 \(IMDSv2\) – a session\-oriented method
**Important**  
Not all instance blueprints in Lightsail support IMDSv2\. Use the `MetadataNoToken` instance metric to track the number of calls to the instance metadata service that are using IMDSv1\. For more information, see [Viewing instance metrics in Amazon Lightsail](amazon-lightsail-viewing-instance-health-metrics.md)\.

For more information about using IMDS, see [Use the Instance Metadata Service with an Amazon Lightsail instance](amazon-lightsail-configuring-instance-metadata-service.md)\.

## Additional IMDS documentation<a name="amazon-lightsail-imds-documentation"></a>

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