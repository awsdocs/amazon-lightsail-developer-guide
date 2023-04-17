# Changing custom domains for your Amazon Lightsail distribution<a name="amazon-lightsail-changing-distribution-custom-domains"></a>

 *Last updated: November 1, 2022* 

You can change the custom domains used by your Amazon Lightsail distribution to another domain or set of domains\. To do so, you must first create a new SSL/TLS certificate for the domains that you want to use with your distribution\. For more information, see [Creating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-create-a-distribution-certificate.md)\. After the new certificate is validated, you swap the old certificate for the new one, thereby changing the custom domains for your distribution\.

For more information about distributions, see [Creating Amazon Lightsail distributions](amazon-lightsail-creating-content-delivery-network-distribution.md)\.

## Changing custom domains for your distribution<a name="changing-distribution-custom-domains"></a>

Complete the following procedure to change the custom domains for your distribution\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Networking** tab\.

1. Choose the name of the distribution for which you want to change the custom domains\.

1. Choose the **Custom domains** tab on your distribution's management page\.

1. Detach the SSL/TLS certificate that is currently attached to the distribution\.

   The status of the distribution will change to **In progress**\.

1. After the distribution's status changes back to **Enabled**, choose **Attach certificate**\.

1. In the dropdown menu that appears, select a valid certificate for the domain\(s\) that you want to use with your distribution\.

1. Verify the certificate information is correct, then choose **Attach**\.

1. Add a domain assignment to the DNS of your domain to point the domain to your distribution\.

   The distribution's **Status** will change to **Updating**\. After the status changes to **Ready**, the certificate's domain will appear in the **Custom domains** section\. Choose **Add domain assignment** to point the domain to your distribution\.

1. Choose **Add assignment**\. After a few moments, traffic for the domain that you selected will begin to be accepted by your distribution\.

1. Choose **Save**\.

## Additional information<a name="changing-distribution-custom-domain-additional-information"></a>

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
+ [Enabling custom domains for your Amazon Lightsail distributions](amazon-lightsail-enabling-distribution-custom-domains.md)
+ [Pointing your domains to your Amazon Lightsail distributions](amazon-lightsail-point-domain-to-distribution.md)
+ [Changing custom domains for your Amazon Lightsail distribution](#amazon-lightsail-changing-distribution-custom-domains)
+ [Disabling custom domains for your Amazon Lightsail distributions](amazon-lightsail-disabling-distribution-custom-domains.md)
+ [Viewing distribution metrics in Amazon Lightsail](amazon-lightsail-viewing-distribution-health-metrics.md)
+ [Deleting your Amazon Lightsail distribution](amazon-lightsail-deleting-distribution.md)
+ [SSL/TLS certificates in Amazon Lightsail](understanding-tls-ssl-certificates-in-lightsail-https.md)
+ [Creating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-create-a-distribution-certificate.md)
+ [Validating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-validating-a-distribution-certificate.md)
+ [Viewing SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-viewing-distribution-certificates.md)
+ [Deleting SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-deleting-distribution-certificates.md)