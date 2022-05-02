# Disabling custom domains for your Amazon Lightsail distributions<a name="amazon-lightsail-disabling-distribution-custom-domains"></a>

 *Last updated: July 23, 2020* 

Disable custom domains for your Amazon Lightsail distribution to stop using your registered domain names with your distribution\. After you disable custom domains, your distribution accepts traffic only for the default domain that is associated with your distribution when you first create it \(e\.g\., `123456abcdef.cloudfront.net`\), and traffic for the previously associated custom domains will see a 403 error\.

For more information about distributions, see [Content delivery network distributions in Amazon Lightsail](amazon-lightsail-content-delivery-network-distributions.md)\.

## Disable custom domains for your distribution<a name="disable-distribution-custom-domains"></a>

Complete the following procedure to disable custom domains for your distribution\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Networking** tab\.

1. Choose the name of the distribution for which want to disable custom domains\.

1. Choose the **Custom domains** tab on your distribution's management page\.

1. Under the **Use your custom domains with HTTPS** section of the page, use the toggle to disable custom domains for your distribution\.

1. At the prompt, choose **Yes, disable** to confirm that you want to disable custom domains for your distribution\.

   Your request to disable custom domains is submitted, and the status of your distribution is changed to **In progress**\. After a while, the status of your distribution changes to **Enabled**\.

After you disable custom domains, your distribution accepts traffic only for the default domain that is associated with your distribution when you first create it \(e\.g\., `123456abcdef.cloudfront.net`\), and traffic for the previously associated custom domains will see a 403 error\. You should update the DNS records of the domains so that traffic for those domains is directed to another resource\.

## Additional information<a name="disabling-distribution-custom-domains-additional-information"></a>

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
+ [Changing custom domains for your Amazon Lightsail distribution](amazon-lightsail-changing-distribution-custom-domains.md)
+ [Disabling custom domains for your Amazon Lightsail distributions](#amazon-lightsail-disabling-distribution-custom-domains)
+ [Viewing distribution metrics in Amazon Lightsail](amazon-lightsail-viewing-distribution-health-metrics.md)
+ [Deleting your Amazon Lightsail distribution](amazon-lightsail-deleting-distribution.md)
+ [SSL/TLS certificates in Amazon Lightsail](understanding-tls-ssl-certificates-in-lightsail-https.md)
+ [Creating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-create-a-distribution-certificate.md)
+ [Validating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-validating-a-distribution-certificate.md)
+ [Viewing SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-viewing-distribution-certificates.md)
+ [Deleting SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-deleting-distribution-certificates.md)