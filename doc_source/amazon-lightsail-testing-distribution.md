# Testing your Amazon Lightsail distribution<a name="amazon-lightsail-testing-distribution"></a>

 *Last updated: July 23, 2020* 

In this guide, we show you how to test that your Amazon Lightsail distribution is caching and serving content from your origin\. You should perform this test after you add your registered domain name to your distribution\. For more information about distributions, see [Content delivery network distributions in Amazon Lightsail](amazon-lightsail-content-delivery-network-distributions.md)\.

## Test your distribution<a name="testing-distributions"></a>

Complete the following procedure to test your distribution\. We use the Chrome web browser in this procedure; other browsers may use similar steps\.

1. Open the Chrome web browser\.

1. Open the **Chrome Menu** in the upper\-right\-hand corner of the browser window and select **More Tools** > **Developer Tools**\.

   You can also use the shortcut Option \+ ⌘ \+ J \(on macOS\), or Shift \+ CTRL \+ J \(on Windows/Linux\)\.

1. In the developer tools pane, choose the **Network** tab\.

1. Browse to the domain of your distribution \(e\.g\., `https://www.example.com`\)\.

   The **Network** tab of the Chrome developer tools should will populate with a list of objects from your website\. 

1. Choose a static object, such as an image file \(\.jpg, \.png, \.gif\)\.

1. In the **Header** panel that appears, you should see that the `via` and `x-cache` headers both mention CloudFront\. This confirms that your distribution is caching and serving content from your origin\. your   
![\[Distribution test result\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/distribution-test-result.png)

## Additional information<a name="testing-distribution-additional-information"></a>

Here are some articles to help you manage distributions in Lightsail:
+ [Content delivery network distributions in Amazon Lightsail](amazon-lightsail-content-delivery-network-distributions.md)
+ [Creating Amazon Lightsail distributions](amazon-lightsail-creating-content-delivery-network-distribution.md)
+ [Understanding request and response behaviors of an Amazon Lightsail distribution](amazon-lightsail-distribution-request-and-response.md)
+ [Configuring your WordPress instance to work with your Amazon Lightsail distribution](amazon-lightsail-editing-wp-config-for-distribution.md)
+ [Testing your Amazon Lightsail distribution](#amazon-lightsail-testing-distribution)
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
+ [SSL/TLS certificates in Lightsail](understanding-tls-ssl-certificates-in-lightsail-https.md)
+ [Creating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-create-a-distribution-certificate.md)
+ [Validating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-validating-a-distribution-certificate.md)
+ [Viewing SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-viewing-distribution-certificates.md)
+ [Deleting SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-deleting-distribution-certificates.md)