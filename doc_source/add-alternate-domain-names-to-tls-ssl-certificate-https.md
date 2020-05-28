# Add alternate domains and subdomains to your SSL/TLS certificate in Amazon Lightsail<a name="add-alternate-domain-names-to-tls-ssl-certificate-https"></a>

 *Last updated: November 29, 2017* 

When you create your SSL/TLS certificate for your Lightsail load balancer, you can add alternate domains and subdomains to it\. These alternate names help ensure that all traffic to your load balancer is encrypted\.

When you specify a primary domain, you can use a fully qualified domain name such as `www.example.com` or an apex domain name such as `example.com`\.

The total number of domains and subdomains must not exceed 10, so you can add up to 9 alternate domains and subdomains to your certificate\. You might want to add entries similar to the following list\.
+ example\.com
+ example\.net
+ blog\.example\.com
+ myexamples\.com

## To create a certificate with alternate domains and subdomains<a name="create-certificate-with-alternate-domains-and-subdomains"></a>

1. If you don't have one yet, [create a Lightsail load balancer](create-lightsail-load-balancer-and-attach-lightsail-instances.md)\.

1. On the Lightsail home page, choose the **Networking** tab\.

1. Choose your Lightsail load balancer to manage it\.

1. Choose **Inbound traffic**\.

1. Choose **Create certificate**\.

1. Enter your primary domain \(e\.g\., `www.example.com`\)\.

1. Enter a name for your certificate or accept the default\.

   Resource names:
   + Must be unique within each AWS Region in your Lightsail account\.
   + Must contain 2 to 255 characters\.
   + Must start and end with an alphanumeric character or number\.
   + Can include alphanumeric characters, numbers, periods, dashes, and underscores\.

1. Enter your domains and subdomains in the list\. Choose the plus icon to add a new line\.  
![\[Create domains and subdomains for your SSL/TLS certificate\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/animated-gif-create-domain-and-subdomains-ssl-tls-certificate.gif)

1. Choose **Create**\.

   Once created, you have 72 hours to verify that you own your domain\.

## Next steps<a name="add-alternate-domain-names-next-steps"></a>
+  [Verify domain ownership using DNS](verify-tls-ssl-certificate-using-dns-cname-https.md) 

  Once verified, you can select your validated certificate to associate it with your Lightsail load balancer\.
+  [Enable session persistence](update-settings-for-lightsail-load-balancer-health-check-path-https-session-stickiness-persistence-cookie-duration.md) 