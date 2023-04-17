# SSL/TLS certificates in Lightsail<a name="understanding-tls-ssl-certificates-in-lightsail-https"></a>

**Note**  
Amazon Lightsail uses SSL/TLS certificates to validate custom \(registered\) domains that you can use with Lightsail load balancers, content delivery network \(CDN\) distributions, and container services\. After a validated certificate is attached to one of those Lightsail resources, the traffic that is routed to that resource through the domain is encrypted using Hypertext Transfer Protocol Secure \(HTTPS\)\.

 *Last updated: November 1, 2022* 

You can create Transport Layer Security \(TLS\) certificates in Amazon Lightsail to enable encrypted web traffic for custom \(registered\) domains that you want to use with your Lightsail load balancers content delivery network distributions, and container services\. TLS is an updated, more secure version of Secure Socket Layer \(SSL\)\. Throughout the Lightsail documentation and console, you'll see us refer to it as **SSL/TLS**\.

**Note**  
The Lightsail certificates that you can attach to load balancers, CDN distributions, and container services are issued by the AWS Certificate Manager \(ACM\) service\. Starting October 11, 2022, any public certificate obtained through Lightsail for your load balancers, CDN distributions, and container services will be issued from one of the multiple intermediate certificate authorities \(ICAs\) or subordinate CAs that ACM manages\. For more information, see [Amazon introduces dynamic intermediate certificate authorities](https://aws.amazon.com/blogs/security/amazon-introduces-dynamic-intermediate-certificate-authorities/) in the *AWS Security Blog*\.

## Why use HTTPS?<a name="why-use-https"></a>

First and foremost is security\. HTTPS offers an extra layer of security because it uses TLS to move data\. HTTPS encryption is confidential between the web server and the client's browser, because they are the only two entities who can decrypt the traffic\. HTTPS connections are also more secure because the data a client exchanges with the server can't be modified by another party\.

Aside from security benefits mentioned above, there are other reasons to use HTTPS in addition to HTTP\. For example, in 2014 Google began ranking secure websites higher in search results\. In other words, a site that uses HTTPS ranks closer to the top of search results compared to a site that only uses HTTP \(all other things being equal\)\.

 [Learn more about HTTPS as a ranking signal](https://webmasters.googleblog.com/2014/08/https-as-ranking-signal.html) 

## Process overview<a name="cert-process"></a>

The process to use a Lightsail certificate is simple\. It involves the following steps:

1. Create your Lightsail resource that can use a Lightsail certificate, such as a load balancer, CDN distribution, or container service\.

1. Create a certificate for your domain using Lightsail\.

1. Validate the certificate by adding a canonical name \(CNAME\) record to the DNS of your domain

1. Attach the validated certificate to your Lightsail resource\.

1. Modify the DNS of your domain to route traffic to your Lightsail resource\.

![\[HTTPS process overview\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/create-certificate-process-summary.png)

After the certificate is attached to the resource, the traffic that is routed to that resource through the domain is encrypted using HTTPS\.

## Using SSL/TLS certificates with your Lightsail distribution and container service<a name="using-ssl-tls-with-distribution"></a>

HTTPS is required on Lightsail distributions and container services\. When you create either of those resources, HTTPS is enabled by default for the resource's default domain \(e\.g\., `https://123456abcdef.cloudfront.net/` for a distribution or `https://container-service-1.123456abcdef.us-west-2.cs.amazonlightsail.com/` for a container service\)\. If you want to use your registered domain name \(e\.g\., `example.com`\) with your distribution or container service, you must create a Lightsail SSL/TLS certificate, validate it with your domain name, and enable custom domains on your resource\. Enabling custom domains on your distribution or container service also attaches your domain's validated certificate to your resource\.

You can get started with enabling custom domains and HTTPS on your distribution by following these links\.
+ [Creating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-create-a-distribution-certificate.md)
+ [Validating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-validating-a-distribution-certificate.md)
+ [Viewing SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-viewing-distribution-certificates.md)
+ [Enabling custom domains for your Amazon Lightsail distributions](amazon-lightsail-enabling-distribution-custom-domains.md)
+ [Pointing your domains to your Amazon Lightsail distributions](amazon-lightsail-point-domain-to-distribution.md)

For more information about distributions, see [Content delivery network distributions in Amazon Lightsail](amazon-lightsail-content-delivery-network-distributions.md)\.

You can get started with enabling custom domains and HTTPS on your container service by following these links\.
+ [Creating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-creating-container-services-certificates.md)
+ [Validating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-validating-container-services-certificates.md)
+ [Enabling and managing custom domains for your Amazon Lightsail container services](amazon-lightsail-enabling-container-services-custom-domains.md)

For more information about container services, see [Container services in Amazon Lightsail](amazon-lightsail-container-services.md)\.

## Using SSL/TLS certificates with your Lightsail load balancer<a name="using-ssl-tls-with-load-balancer"></a>

When you create a Lightsail load balancer, port 80 is open by default to handling regular HTTP traffic\. To enable HTTPS traffic over port 443, you must create an SSL/TLS certificate, validate it with your domain name, and attach it to your load balancer\.

You can create up to two SSL/TLS certificates per load balancer\. Only one certificate can be in use at a time per load balancer\. If you delete a valid, in\-use certificate from your load balancer, your load balancer is no longer be able to handle HTTPS traffic for the specified domain until you attach another valid certificate\.

You can get started with enabling HTTPS on your load balancer by following these links\.
+  [Create a Lightsail load balancer and attach instances to it](create-lightsail-load-balancer-and-attach-lightsail-instances.md) 
+  [Create an SSL/TLS certificate](create-tls-ssl-certificate-and-attach-to-lightsail-load-balancer-https.md) 
+  [Verify domain ownership](verify-tls-ssl-certificate-using-dns-cname-https.md) 
+  [Attach your validated certificate to enable HTTPS](attach-validated-certificate-to-load-balancer.md) 

For more information about load balancers, see [Amazon Lightsail load balancers](understanding-lightsail-load-balancers.md)\.