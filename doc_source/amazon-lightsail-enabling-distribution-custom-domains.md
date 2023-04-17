# Enabling custom domains for your Amazon Lightsail distributions<a name="amazon-lightsail-enabling-distribution-custom-domains"></a>

 *Last updated: December 29, 2022* 

Enable custom domains for your Amazon Lightsail distribution to use your registered domain names with your distribution\. Before you enable custom domains, your distribution accepts traffic only for the default domain that is associated with your distribution when you first create it \(e\.g\., `123456abcdef.cloudfront.net`\)\. When you enable custom domains, you must choose the Lightsail SSL/TLS certificate that you created for the domains that you want to use with your distribution\. After you enable custom domains, your distribution accepts traffic for all of the domains that are associated with the certificate that you chose\.

**Important**  
Only one certificate can be in use at a time per distribution\. If you disable custom domains on your distribution, your distribution is no longer able to handle HTTPS traffic for your registered domain until you enable custom domains again\.  
The domain names associated with the SSL/TLS certificate cannot be in use by another distribution across all Amazon Web Services \(AWS\) accounts, including distributions on the Amazon CloudFront service\. You will be able to create the certificate for the domains, but you will not be able to use it with your distribution\.

For more information about distributions, see [Content delivery network distributions in Amazon Lightsail](amazon-lightsail-content-delivery-network-distributions.md)\.

## Prerequisites<a name="enable-distribution-custom-domains-prerequisite"></a>

Before you get started, you need to create a Lightsail distribution\. For more information, see [Creating Amazon Lightsail distributions](amazon-lightsail-creating-content-delivery-network-distribution.md)\.

You also should have created and validated an SSL/TLS certificate for your distribution\. For more information, see [Creating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-create-a-distribution-certificate.md) and [Validating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-validating-a-distribution-certificate.md)\.

## Enable custom domains for your distribution<a name="enable-distribution-custom-domains"></a>

Complete the following procedure to enable custom domains for your distribution\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Networking** tab\.

1. Choose the name of the distribution for which want to enable custom domains\.

1. Choose the **Custom domains** tab on your distribution's management page\.

1. Choose **Attach certificate**\.

   If you have no certificates, then you must first create and validate an SSL/TLS certificate for your domains, before you can attach it to your distribution\. For more information, see [Creating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-create-a-distribution-certificate.md)\.

1. In the dropdown menu that appears, select a valid certificate for the domain\(s\) that you want to use with your distribution\.

1. Verify the certificate information is correct, then choose **Attach**\.

1. The distribution's **Status** will change to **Updating**\. After the status changes to **Enabled**, the certificate's domain will appear in the **Custom domains** section\. 

1. Choose **Add domain assignment** to point the domain to your distribution\.

1. Verify the certificate and DNS information are correct, then choose **Add assignment**\. After a few moments, traffic for the domain that you selected will begin to be accepted by your distribution\.

## Additional information<a name="enabling-distribution-custom-domains-additional-information"></a>

Here are some articles to help you manage distributions in Lightsail:
+ [Content delivery network distributions in Amazon Lightsail](amazon-lightsail-content-delivery-network-distributions.md)
+ [Creating Amazon Lightsail distributions](amazon-lightsail-creating-content-delivery-network-distribution.md)
+ [Understanding request and response behaviors of an Amazon Lightsail distribution](amazon-lightsail-distribution-request-and-response.md)
+ [Configuring your WordPress instance to work with your Amazon Lightsail distribution](amazon-lightsail-editing-wp-config-for-distribution.md)
+ [Testing your Amazon Lightsail distribution](amazon-lightsail-testing-distribution.md)
+ [Changing the origin of your Amazon Lightsail distribution](amazon-lightsail-changing-distribution-origin.md)
+ [Changing the caching behavior of your Amazon Lightsail distribution](amazon-lightsail-changing-default-cache-behavior.md)
+ [Resetting the cache of your Amazon Lightsail distribution](amazon-lightsail-resetting-distribution-cache.md)
+ [Changing the plan of your Amazon Lightsail distribution](amazon-lighstail-changing-distribution-plan.md)
+ [Enabling custom domains for your Amazon Lightsail distributions](#amazon-lightsail-enabling-distribution-custom-domains)
+ [Pointing your domains to your Amazon Lightsail distributions](amazon-lightsail-point-domain-to-distribution.md)
+ [Changing custom domains for your Amazon Lightsail distribution](amazon-lightsail-changing-distribution-custom-domains.md)
+ [Disabling custom domains for your Amazon Lightsail distributions](amazon-lightsail-disabling-distribution-custom-domains.md)
+ [Viewing distribution metrics in Amazon Lightsail](amazon-lightsail-viewing-distribution-health-metrics.md)
+ [Deleting your Amazon Lightsail distribution](amazon-lightsail-deleting-distribution.md)
+ [SSL/TLS certificates in Amazon Lightsail](understanding-tls-ssl-certificates-in-lightsail-https.md)
+ [Creating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-create-a-distribution-certificate.md)
+ [Validating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-validating-a-distribution-certificate.md)
+ [Viewing SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-viewing-distribution-certificates.md)
+ [Deleting SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-deleting-distribution-certificates.md)