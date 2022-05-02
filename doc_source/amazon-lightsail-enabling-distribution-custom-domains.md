# Enabling custom domains for your Amazon Lightsail distributions<a name="amazon-lightsail-enabling-distribution-custom-domains"></a>

 *Last updated: July 23, 2020* 

Enable custom domains for your Amazon Lightsail distribution to use your registered domain names with your distribution\. Before you enable custom domains, your distribution accepts traffic only for the default domain that is associated with your distribution when you first create it \(e\.g\., `123456abcdef.cloudfront.net`\)\. When you enable custom domains, you must choose the Lightsail SSL/TLS certificate that you created for the domains that you want to use with your distribution\. After you enable custom domains, your distribution accepts traffic for all of the domains that are associated with the certificate that you chose\.

**Important**  
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

1. Under the **Use your custom domains with HTTPS** section of the page, use the toggle to enable custom domains with HTTPS for your distribution\.

1. To enable custom domains, choose the SSL/TLS certificate that you want to use with your distribution\.

   The domain names that are specified on the certificate are the domain names that are added to your distribution\.

1. Choose **Save**\.

   Your request to enable custom domains is submitted, and the status of your distribution is changed to **In progress**\. After a while, the status of your distribution changes to **Enabled**\.

After you enable custom domains for your distribution, you should update the DNS records of the domains so that traffic for those domains is directed to your distribution\. You do this by creating alias records that point to the default domain name of your distribution \(e\.g\., `123456abcdef.cloudfront.net`\)\. For more information, see [Pointing your domains to your Amazon Lightsail distributions](amazon-lightsail-point-domain-to-distribution.md)\.

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