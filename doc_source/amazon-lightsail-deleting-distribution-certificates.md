# Deleting SSL/TLS certificates for your Amazon Lightsail distribution<a name="amazon-lightsail-deleting-distribution-certificates"></a>

 *Last updated: July 23, 2020* 

You can delete Amazon Lightsail SSL/TLS certificates that you're no longer using on your distributions\. For example, your certificate might be expired and you've already attached an updated certificate that's validated\. For more information about certificates, see [SSL/TLS certificates in Amazon Lightsail](understanding-tls-ssl-certificates-in-lightsail-https.md)\. For more information about distributions, see [Content delivery network distributions in Amazon Lightsail](amazon-lightsail-content-delivery-network-distributions.md)\.

Deleting an SSL/TLS certificate is final and can't be undone\. You have a quota of certificates you can create over a 365\-day period\. For more information, see [Lightsail service quotas](https://docs.aws.amazon.com/general/latest/gr/lightsail.html#limits_lightsail) in the *AWS General Reference*\.

## Delete an SSL/TLS certificate for your distribution<a name="deleting-distribution-certificate"></a>

Complete the following procedure to delete an SSL/TLS certificate for your distribution\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Networking** tab\.

1. Choose the name of the distribution from which you want to delete the SSL/TLS certificate\. If the certificate is not currently in use, then you can choose any distribution because all of your certificates are listed in every distribution\.

1. Choose the **Custom domains** tab on your distribution's management page\.

1. In the **Certificates** section of the page, choose the ellipsis icon \(⋮\) for the certificate that you want to delete, and choose **Delete**\.

   The **Delete** option is unavailable if the certificate you want to delete is in use\. To delete certificates that are in use, you need to first change the custom domains of the distribution that is using the certificate, or disable custom domains on the distribution that is using the certificate\. For more information, see [Changing custom domains for your Amazon Lightsail distribution](amazon-lightsail-changing-distribution-custom-domains.md) and [Enabling custom domains for your Amazon Lightsail distributions](amazon-lightsail-disabling-distribution-custom-domains.md#amazon-lightsail-disabling-distribution-custom-domains.title)\.

1. Choose **Yes, delete** to confirm the deletion\.

## Additional information<a name="delete-distribution-certificates-additional-information"></a>

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
+ [Viewing SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-viewing-distribution-certificates.md)
+ [Deleting SSL/TLS certificates for your Amazon Lightsail distribution](#amazon-lightsail-deleting-distribution-certificates)