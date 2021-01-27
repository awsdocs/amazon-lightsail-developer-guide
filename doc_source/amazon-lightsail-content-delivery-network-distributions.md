# Content delivery network distributions in Amazon Lightsail<a name="amazon-lightsail-content-delivery-network-distributions"></a>

**Note**  
An Amazon Lightsail content delivery network \(CDN\) distribution caches your website or web application content at worldwide locations\. When your user requests content that you're serving through a distribution, the request is routed to the nearest location in terms of latency\. Lightsail distributions are backed by the Amazon CloudFront global network, which serves content from servers in 84 cities across 24 countries\.

 *Last updated: July 23, 2020* 

A Lightsail distribution uses a globally distributed network of servers, also known as *edge locations*, to provide faster delivery of your content to your users\. To use a distribution, you first create and host your website or web application on a Lightsail instance, or multiple instances attached to a Lightsail load balancer\. You then create and configure a Lightsail distribution to pull, cache, and serve content from your instance or load balancer\. Your instance or load balancer, also known as your distribution's *origin*, is the definitive source of your content\.

When your user requests content by visiting your website, which is being served through a distribution, the request is routed to the nearest location in terms of latency\. Your distribution then performs one of the following actions:
+ If the content is already being cached in the edge location, your distribution immediately serves it to your user\.
+ If the content is not yet being cached in that edge location, your distribution retrieves it from the specified origin, caches it, and serves it to your user\.

Your content is cached in edge locations for the duration of the cache lifespan \(time to live\) that you specify for your distribution, so that other requests at the same location are immediately fulfilled\. Your cached content is cleared from the edge location when it reaches its cache lifespan\. Your distribution retrieves, caches, and serves content the next time a content request is routed to the edge location\.

In the following diagram:
+ 1 represents the origin of your distribution, such as a Lightsail instance that is hosting your website\.
+ 2 represents your distribution, or the edge locations that pull, cache, and serve content from your origin\.
+ 3 represents your users who are served content from the edge locations\.

![\[Lightsail distribution diagram\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/distribution-diagram.png)

**Note**  
This diagram is for illustration purpose only and doesn't show actual edge locations\. For more information about edge locations, see [Edge locations and IP address ranges](#edge-locations) later in this guide\.

This method of serving content is faster and more efficient than the traditional method of serving content from just one, central instance\. Your users access your content from locations that are nearby, as opposed to all of your users accessing the same central instance that may be far away\.

## Use cases<a name="distribution-use-cases"></a>

A Lightsail distribution speeds up the delivery of your content \(for example, website pages, images, style sheets, JavaScript, and so on\) to viewers *worldwide*\. By using a distribution, you can take advantage of the AWS backbone network and edge servers to give your viewers a fast, safe, and reliable experience when they visit your website\.

Using a distribution to cache and serve your content also reduces the load on your origin, because most requests are served by your distribution and not your instance or load balancer\.

A distribution allows you to take advantage of TLS termination, which reduces the load on your origin by offloading the cryptographic processing to your distribution\. You can use your registered domain name together with a Lightsail SSL/TLS certificate to enable Hypertext Transfer Protocol Secure \(HTTPS\) for your distribution\. Your users establish an encrypted HTTPS connection to your distribution, while your distribution pulls content from your origin using HTTP\.

## Configure your distribution<a name="configure-distribution"></a>

These are the general steps to follow to serve your website or web application using a Lightsail instance and a distribution\.

1. Create a Lightsail instance to host your content\. The instance serves as the origin of your distribution\. The origin stores the original, definitive version of your content\. For more information, see [Create an Amazon Lightsail instance](how-to-create-amazon-lightsail-instance-virtual-private-server-vps.md)\.

1. Attach a Lightsail static IP to your instance\. Your instance's default public IP address changes if you stop and start your instance, which will break the connection between your distribution and your origin instance\. A static IP does not change if you stop and start your instance\. For more information, see [Create a static IP and attach it to an instance in Amazon Lightsail](lightsail-create-static-ip.md)\.

1. Upload your content and files to your instance\. Your files, also known as *objects*, typically include web pages, images, and media files, but can be anything that can be served over HTTP\.

1. \(Optional\) Create a Lightsail load balancer if your website requires fault tolerance\. Then attach multiple copies of your instance to your load balancer\. You can configure your load balancer \(with one or more instances attached to it\) as the origin of your distribution, instead of configuring your instance as the origin\. For more information, see [Create a Lightsail load balancer and attach instances to it](create-lightsail-load-balancer-and-attach-lightsail-instances.md)\.

1. Create a Lightsail distribution, and configure your instance or load balancer as the origin\. At the same time, you specify details such as the cache lifespan of your content, and which elements of your website or web application are cached\. For more information, see [Creating Amazon Lightsail distribution](amazon-lightsail-creating-content-delivery-network-distribution.md)\.

1. \(Optional\) If your distribution's origin is a WordPress instance, you must edit the WordPress configuration file in your instance to make your WordPress website work with your distribution\. For more information, see [Configuring your WordPress instance to work with your Amazon Lightsail distribution](amazon-lightsail-editing-wp-config-for-distribution.md)\.

1. \(Optional\) Create a Lightsail DNS zone to manage your domain's DNS in the Lightsail console\. This allows you to easily map your domain to your Lightsail resources\. For more information, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)\. Alternately, you can continue hosting your domain's DNS where it's currently being hosted\.

1. Create a Lightsail SSL/TLS certificate for your domain to use it with your distribution\. Lightsail distributions require HTTPS, so you must request an SSL/TLS certificate for your domain before you can use it with your distribution\. For more information, see [Creating SSL/TLS certificates for your distribution in Amazon Lightsail](amazon-lightsail-create-a-distribution-certificate.md)\.

1. Enable custom domains for your distributions to use your registered domain names with your distributions\. Enabling custom domains requires that you specify the Lightsail SSL/TLS certificate that you created for your domains\. This adds your domains to your distribution and enables HTTPS\. For more information, see [Enabling custom domains for your Amazon Lightsail distributions](amazon-lightsail-enabling-distribution-custom-domains.md)\.

1. Add an alias record to your domain's DNS to begin routing traffic for your domain to your distribution\. After you add the alias record, users who visit your domain are routed through your distribution\. For more information, see [Pointing your domains to your Amazon Lightsail distributions](amazon-lightsail-point-domain-to-distribution.md)\.

1. Test that your distribution is caching your content\. For more information, see [Testing your Amazon Lightsail distribution](amazon-lightsail-testing-distribution.md)\.

## Edge locations and IP address ranges<a name="edge-locations"></a>

Lightsail distributions use the same edge servers and IP address ranges as Amazon CloudFront\. For a list of the locations of CloudFront edge servers, see the [Amazon CloudFront Product Details page](http://aws.amazon.com/cloudfront/details)\. For a list of the CloudFront IP ranges, see the [CloudFront global IP list](http://d7uri8nf7uskq.cloudfront.net/tools/list-cloudfront-ips)\.

## Additional information about distributions<a name="distributions-additional-information"></a>

Here are some articles to help you manage distributions in Lightsail:
+ [Content delivery network distributions in Amazon Lightsail](#amazon-lightsail-content-delivery-network-distributions)
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
+ [SSL/TLS certificates in Lightsail](understanding-tls-ssl-certificates-in-lightsail-https.md)
+ [Creating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-create-a-distribution-certificate.md)
+ [Validating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-validating-a-distribution-certificate.md)
+ [Viewing SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-viewing-distribution-certificates.md)
+ [Deleting SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-deleting-distribution-certificates.md)