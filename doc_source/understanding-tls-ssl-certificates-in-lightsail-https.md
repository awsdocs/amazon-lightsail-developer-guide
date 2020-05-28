# SSL/TLS certificates in Lightsail<a name="understanding-tls-ssl-certificates-in-lightsail-https"></a>

**Note**  
Lightsail uses SSL/TLS certificates to handle encrypted web traffic \(HTTPS requests\)\. You can create certificates, verify domain ownership, and then attach the validated certificates to your Lightsail load balancer\.

 *Last updated: November 29, 2017* 

When you create a Lightsail load balancer, port 80 is open for handling regular \(unencrypted\) web traffic by default\. You must create a Transport Layer Security \(TLS\) certificate to enable HTTPS \(encrypted\) traffic\. TLS is just an updated, more secure version of Secure Socket Layer \(SSL\)\. Throughout the documentation and the Lightsail console, you'll see us refer to it as **SSL/TLS**\.

You can create up to two SSL/TLS certificates per Lightsail load balancer\. Only one certificate can be active at a time\. If you delete a valid, in\-use certificate from your load balancer, you will no longer be able to handle encrypted \(HTTPS\) traffic with your load balancer until you attach another valid certificate\.

## Why use HTTPS?<a name="why-use-https"></a>

First and foremost is security\. HTTPS offers an extra layer of security because it uses TLS to move data\. HTTPS encryption is confidential between the web server and the client's browser, because they are the only two entities who can decrypt the traffic\. HTTPS connections are also more secure because the data a client exchanges with the server can't be modified by another party\.

Aside from security benefits mentioned above, there are other reasons to use HTTPS in addition to HTTP\. For example, in 2014 Google began ranking secure websites higher in search results\. In other words, a site that uses HTTPS ranks closer to the top of search results compared to a site that only uses HTTP \(all other things being equal\)\.

 [Learn more about HTTPS as a ranking signal](https://webmasters.googleblog.com/2014/08/https-as-ranking-signal.html) 

## Get started<a name="https-get-started"></a>

To enable HTTPS, you must follow these steps in order\.

![\[HTTPS process overview\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/create-https-load-balancer-process-summary.png)

You can get started with HTTPS by following these links\.
+  [Create a Lightsail load balancer and attach instances to it](create-lightsail-load-balancer-and-attach-lightsail-instances.md) 
+  [Create an SSL/TLS certificate](create-tls-ssl-certificate-and-attach-to-lightsail-load-balancer-https.md) 
+  [Verify domain ownership](verify-tls-ssl-certificate-using-dns-cname-https.md) 
+  [Attach your validated certificate to enable HTTPS](attach-validated-certificate-to-load-balancer.md) 