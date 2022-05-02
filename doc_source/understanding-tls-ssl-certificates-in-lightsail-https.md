# SSL/TLS certificates in Amazon Lightsail<a name="understanding-tls-ssl-certificates-in-lightsail-https"></a>

**Note**  
Amazon Lightsail uses SSL/TLS certificates to handle encrypted web traffic \(HTTPS requests\)\. You can create certificates, verify domain ownership, and then attach the validated certificates to a Lightsail load balancer or distribution\.

 *Last updated: July 23, 2020* 

You can create Transport Layer Security \(TLS\) certificates in Amazon Lightsail to enable encrypted web traffic, also known as Hypertext Transfer Protocol Secure \(HTTPS\), to Lightsail load balancers and distributions\. TLS is an updated, more secure version of Secure Socket Layer \(SSL\)\. Throughout the Lightsail documentation and console, you'll see us refer to it as **SSL/TLS**\.

## Why use HTTPS?<a name="why-use-https"></a>

First and foremost is security\. HTTPS offers an extra layer of security because it uses TLS to move data\. HTTPS encryption is confidential between the web server and the client's browser, because they are the only two entities who can decrypt the traffic\. HTTPS connections are also more secure because the data a client exchanges with the server can't be modified by another party\.

Aside from security benefits mentioned above, there are other reasons to use HTTPS in addition to HTTP\. For example, in 2014 Google began ranking secure websites higher in search results\. In other words, a site that uses HTTPS ranks closer to the top of search results compared to a site that only uses HTTP \(all other things being equal\)\.

 [Learn more about HTTPS as a ranking signal](https://webmasters.googleblog.com/2014/08/https-as-ranking-signal.html) 

## Using SSL/TLS certificates with your Lightsail distribution<a name="using-ssl-tls-with-distribution"></a>

HTTPS is required on Lightsail distributions\. When you create a distribution, HTTPS is enabled by default for your distribution's default domain \(e\.g\., `123456abcdef.cloudfront.net`\)\. If you want to use your registered domain name \(e\.g\., `example.com`\) with your distribution, you must create an SSL/TLS certificate, validate it with your domain name, and enable custom domains on your distribution\. Enabling custom domains on your distribution also attaches your domain's validated certificate to your distribution\.

Only one certificate can be in use at a time per distribution\. If you disable custom domains on your distribution, your distribution is no longer able to handle HTTPS traffic until you enable custom domains again\.

**Important**  
The domain names that you specify when creating an SSL/TLS certificate for your distribution cannot exist in another SSL/TLS certificate across all Amazon Web Services \(AWS\) accounts, including certificates issued by AWS Certificate Manager\.

You can get started with enabling custom domains and HTTPS on your distribution by following these links\.
+ [Creating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-create-a-distribution-certificate.md)
+ [Validating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-validating-a-distribution-certificate.md)
+ [Viewing SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-viewing-distribution-certificates.md)
+ [Enabling custom domains for your Amazon Lightsail distributions](amazon-lightsail-enabling-distribution-custom-domains.md)
+ [Pointing your domains to your Amazon Lightsail distributions](amazon-lightsail-point-domain-to-distribution.md)

For more information about distributions, see [Content delivery network distributions in Amazon Lightsail](amazon-lightsail-content-delivery-network-distributions.md)\.

## Using SSL/TLS certificates with your Lightsail load balancer<a name="using-ssl-tls-with-load-balancer"></a>

When you create a Lightsail load balancer, port 80 is open by default to handling regular HTTP traffic\. To enable HTTPS traffic over port 443, you must create an SSL/TLS certificate, validate it with your domain name, and attach it to your load balancer\.

You can create up to two SSL/TLS certificates per load balancer\. Only one certificate can be in use at a time per load balancer\. If you delete a valid, in\-use certificate from your load balancer, your load balancer is no longer be able to handle HTTPS traffic until you attach another valid certificate\.

To enable HTTPS on your load balancer, you must follow these steps in order\.

![\[HTTPS process overview\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/create-https-load-balancer-process-summary.png)

You can get started with enabling HTTPS on your load balancer by following these links\.
+  [Create a Lightsail load balancer and attach instances to it](create-lightsail-load-balancer-and-attach-lightsail-instances.md) 
+  [Create an SSL/TLS certificate](create-tls-ssl-certificate-and-attach-to-lightsail-load-balancer-https.md) 
+  [Verify domain ownership](verify-tls-ssl-certificate-using-dns-cname-https.md) 
+  [Attach your validated certificate to enable HTTPS](attach-validated-certificate-to-load-balancer.md) 

For more information about load balancers, see [Amazon Lightsail load balancers](understanding-lightsail-load-balancers.md)\.