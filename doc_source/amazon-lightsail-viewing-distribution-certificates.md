# Viewing SSL/TLS certificates for your Amazon Lightsail distribution<a name="amazon-lightsail-viewing-distribution-certificates"></a>

 *Last updated: July 23, 2020* 

You can view the Amazon Lightsail SSL/TLS certificates that you created for your Lightsail distributions\. You do this by accessing the management page of any distribution in the Lightsail console\.

For more information about SSL/TLS certificates, see [SSL/TLS certificates in Amazon Lightsail](understanding-tls-ssl-certificates-in-lightsail-https.md)\.

## Prerequisites<a name="view-distribution-certificates-prerequisite"></a>

Before you get started, you need to create a Lightsail distribution\. For more information, see [Creating Amazon Lightsail distributions](amazon-lightsail-creating-content-delivery-network-distribution.md) and [Content delivery network distributions in Amazon Lightsail](amazon-lightsail-content-delivery-network-distributions.md)\.

You also should have created an SSL/TLS certificate for your distribution\. For more information, see [Creating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-create-a-distribution-certificate.md)\.

## View your distribution SSL/TLS certificates<a name="view-distribution-certificates"></a>

Complete the following procedure to view your distribution SSL/TLS certificates\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Networking** tab\.

1. Choose the name of a distribution\.

   You can view all of your certificates regardless of the distribution you choose\.

1. Choose the **Custom domains** tab on your distribution's management page\.

1. Scroll down to the **Certificates** section of the page\.

   All of your distribution certificates are listed under the **Certificates** section of the page\. Choose **Show details** to view your certificate's important dates, encryption details, identification, and validation records\. Your certificates are valid for 13 months from the date you created them, after which time Lightsail attempts to automatically revalidate them\. Don't delete the CNAME records that you added to your domain because they are required when your certificate is re\-validated on the **Valid until** date listed\.

   After you have a valid SSL/TLS certificate to use with your distribution, you should enable custom domains so that you can use the domain names of the certificate on your distribution\. For more information, see [Enabling custom domains for your Amazon Lightsail distributions](amazon-lightsail-enabling-distribution-custom-domains.md)\.

## Additional information<a name="viewing-distribution-certificates-additional-information"></a>

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
+ [Disabling custom domains for your Amazon Lightsail distributions](amazon-lightsail-disabling-distribution-custom-domains.md)
+ [Viewing distribution metrics in Amazon Lightsail](amazon-lightsail-viewing-distribution-health-metrics.md)
+ [Deleting your Amazon Lightsail distribution](amazon-lightsail-deleting-distribution.md)
+ [SSL/TLS certificates in Amazon Lightsail](understanding-tls-ssl-certificates-in-lightsail-https.md)
+ [Creating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-create-a-distribution-certificate.md)
+ [Validating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-validating-a-distribution-certificate.md)
+ [Viewing SSL/TLS certificates for your Amazon Lightsail distribution](#amazon-lightsail-viewing-distribution-certificates)
+ [Deleting SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-deleting-distribution-certificates.md)