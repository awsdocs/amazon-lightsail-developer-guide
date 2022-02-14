# Add the default domain of a distribution to a Lightsail container service<a name="amazon-lightsail-adding-distribution-default-domain-to-container-service"></a>

 *Last updated: January 25, 2022* 

You can choose an Amazon Lightsail container service as the origin of a content delivery network \(CDN\) distribution\. The distribution then caches and serves the website or web application hosted on your container service\. If you're using a Lightsail distribution with your Lightsail container service, Lightsail automatically adds the default domain name of your distribution as a custom domain on your container service\. This enables traffic to be routed between your distribution and your container service\. However, you *must* perform the steps outlined in this guide to manually add the default domain name of your distribution to your container service under the following circumstances:
+ If something goes wrong and your distribution's default domain name is not automatically added to your container service\.
+ If you're using a distribution other than a Lightsail distribution with your container service\.

You can manually add the default domain name of your distribution to your container service only by using the AWS Command Line Interface \(AWS CLI\)\. For more information about container services, see [Container services in Amazon Lightsail](amazon-lightsail-container-services.md)\. For more information about distributions, see [Object storage in Amazon Lightsail](buckets-in-amazon-lightsail.md)\.

## Adding the default domain of a distribution to a container service<a name="adding-distribution-default-domain-to-container-service"></a>

Complete the following procedure to add the default domain of a distribution to a container service in Lightsail using the AWS Command Line Interface \(AWS CLI\)\. You do this by using the `update-container-service` command\. For more information, see [update\-container\-service](https://docs.aws.amazon.com/cli/latest/reference/lightsail/update-container-service.html) in the *AWS CLI Command Reference*\.

**Note**  
You must install the AWS CLI and configure it for Lightsail before continuing with this procedure\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a Command Prompt or Terminal window\.

1. Enter one of the following commands to add the default domain of a distribution to a container service\.
**Note**  
If you added a custom domain to your container service, then you will need to specify both your custom domain and the default domain of your distribution\.

   **No custom domain is configured on the container service:**

   ```
   aws lightsail update-container-service --service-name ContainerServiceName --public-domain-names '{"_": ["DistributionDefaultDomain"]}'
   ```

   **One or more custom domains are configured on the container service:**

   ```
   aws lightsail update-container-service --service-name ContainerServiceName --public-domain-names '{"CertificateName": ["ExistingCustomDomain"],"_": ["DistributionDefaultDomain"]}'
   ```

   In the command, replace the following example text with your own:
   + *ContainerServiceName* \- The name of the Lightsail container service that was specified as the origin of the distribution\.
   + *DistributionDefaultDomain* \- The default domain of the distribution that is using the container service as the origin\. For example, `example123.cloudfront.net`\.
   + *CertificateName*" \- The name of the Lightsail certificate of the custom domains that are currently attached to the container service, if any\. If there are no custom domains attached to the container service, then use the command labeled as **No custom domain is configured on the container service**\.
   + *DistributionDefaultDomain* \- The custom domain currently attached to the container service\.

   Examples:
   + **No custom domain is configured on the container service:**

     ```
     aws lightsail update-container-service --service-name ContainerServiceName --public-domain-names '{"_": ["example123.cloudfront.net"]}'
     ```
   + **One or more custom domains are configured on the container service:**

     ```
     aws lightsail update-container-service --service-name ContainerServiceName --public-domain-names '{"example-com": ["example.com"],"_": ["example123.cloudfront.net"]}'
     ```