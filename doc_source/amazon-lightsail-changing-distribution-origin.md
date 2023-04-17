# Changing the origin of your Amazon Lightsail distribution<a name="amazon-lightsail-changing-distribution-origin"></a>

 *Last updated: November 30, 2022* 

In this guide, we show you how to change the origin of your Amazon Lightsail distribution after you create it\. An origin is the definitive source of content for your distribution\. When you create your distribution, you choose the Lightsail instance, Lightsail bucket, or Lightsail load balancer \(with one or more instances attached to it\) that hosts the content of your website or web application\. For more information, see [Content delivery network distributions in Amazon Lightsail](amazon-lightsail-content-delivery-network-distributions.md)\.

You can change the origin at any time after you create your distribution\. When you change the origin, your distribution immediately begins replicating the change to the edge locations\. Your distribution will continue to forward requests to the previous origin in a given edge location until the distribution is updated to the new origin in that edge location\.

Changing the origin does not require your distribution to repopulate edge caches with content from your new origin\. As long as the user requests in your website or web application have not changed, your distribution continues to serve content that is already in an edge cache until the cache lifespan for your content expires\.

## Origin protocol policy<a name="changing-distribution-origin-protocol-policy"></a>

The origin protocol policy is the protocol policy that your distribution uses when pulling content from your origin\. After you choose an origin for your distribution, you should determine if your distribution should use Hypertext Transfer Protocol \(HTTP\) or Hypertext Transfer Protocol Secure \(HTTPS\) when pulling content from your origin\. If your origin is not configured for HTTPS, then you must use HTTP\.

You can choose one of the following origin protocol policies for your distribution:
+ **HTTP Only** \- Your distribution uses only HTTP to access the origin\. This is the default setting\.
+ **HTTPS Only** \- Your distribution uses only HTTPS to access the origin\.

The steps to edit your origin protocol policy are included in the following [Change your distribution's origin](#changing-distribution-origin) section of this guide\.

## Change your distribution's origin<a name="changing-distribution-origin"></a>

Complete the following procedure to change your distribution's origin\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Networking** tab\.

1. Choose the name of the distribution for which you want to change the origin\.

1. Choose the **Details** tab on your distribution's management page, and scroll to the **Choose your origin** section of the page\.

   The **Select your origin** section of the page displays your distribution's current origin\.

1. Choose **Change origin**\.

1. Choose the AWS Region in which your origin resource was created\.

   Distributions are global resources\. They can reference an origin in any AWS Region, and distribute its content globally\.

1. Choose your origin\. An origin can be an instance, bucket, or a load balancer \(with one or more instances attached to it\)\.

1. Choose **Save** to update your distribution with your new origin\.

   After you choose an origin for your distribution, you should determine if your distribution should use Hypertext Transfer Protocol \(HTTP\) or Hypertext Transfer Protocol Secure \(HTTPS\) when pulling content from your origin\.

1. \(Optional\) To change your origin protocol policy, choose the pencil icon displayed next to the current origin protocol policy that your distribution uses\. For more information, see [Origin protocol policy](#changing-distribution-origin-protocol-policy)\.

   This option is listed in the **Choose your origin** section of the page, under the origin resource you selected for your distribution\.
**Note**  
When you select a Lightsail bucket as the origin of your distribution, the **Origin protocol policy** defaults to **HTTPS only**\. You cannot change the origin protocol policy when a bucket is the origin of your distribution\.  
![\[Origin protocol policy\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/origin-protocol-policy.png)

1. Choose **HTTP only** or **HTTPS only**, then choose **Save** to save the origin protocol policy\.

When you save changes to your distribution's configuration, your distribution starts to propagate the changes to all edge locations\. Until your configuration is updated in an edge location, your distribution continues to serve your content from that location based on the previous configuration\. After your configuration is updated in an edge location, your distribution immediately starts to serve your content from that location based on the new configuration\.

Your changes don't propagate to every edge location instantaneously\. When propagation is complete, the status of your distribution changes from **InProgress** to **Enabled**\. While your distribution is propagating your changes, we can't determine whether a given edge location is serving your content based on the previous configuration or the new configuration\.

## Additional information<a name="changing-distribution-origin-additional-information"></a>

Here are some articles to help you manage distributions in Lightsail:
+ [Content delivery network distributions in Amazon Lightsail](amazon-lightsail-content-delivery-network-distributions.md)
+ [Creating Amazon Lightsail distributions](amazon-lightsail-creating-content-delivery-network-distribution.md)
+ [Understanding request and response behaviors of an Amazon Lightsail distribution](amazon-lightsail-distribution-request-and-response.md)
+ [Configuring your WordPress instance to work with your Amazon Lightsail distribution](amazon-lightsail-editing-wp-config-for-distribution.md)
+ [Testing your Amazon Lightsail distribution](amazon-lightsail-testing-distribution.md)
+ [Changing the origin of your Amazon Lightsail distribution](#amazon-lightsail-changing-distribution-origin)
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
+ [Deleting SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-deleting-distribution-certificates.md)