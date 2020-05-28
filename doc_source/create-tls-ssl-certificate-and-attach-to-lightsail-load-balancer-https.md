# Create an SSL/TLS certificate for your Lightsail load balancer<a name="create-tls-ssl-certificate-and-attach-to-lightsail-load-balancer-https"></a>

 *Last updated: August 20, 2018* 

After you create a Lightsail load balancer, you can attach a Transport Layer Security \(TLS\) certificate to enable HTTPS\. The SSL/TLS certificate lets your load balancer handle encrypted web traffic so that you can provide a more secure experience for your users\. To learn more, see [SSL/TLS certificates in Lightsail](understanding-tls-ssl-certificates-in-lightsail-https.md)\.

## Prerequisites<a name="create-ssl-tls-certificate-prerequisites"></a>

Before you get started, you will need the following\.
+ A Lightsail load balancer\. To learn more, see [Create a Lightsail load balancer](create-lightsail-load-balancer-and-attach-lightsail-instances.md)\.

## Create the certificate request<a name="create-ssl-tls-certificate"></a>

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose **Networking**\.

1. Choose the name of the load balancer for which you want to configure an SSL/TLS certificate\.

1. Choose the **Inbound traffic** tab\.

1. Choose **Create certificate**\.

1. Type your domain name \(e\.g\., `example.com`\) where it asks for **primary domain**\.

1. If needed, change the **certificate name**\.

   Resource names:
   + Must be unique within each AWS Region in your Lightsail account\.
   + Must contain 2 to 255 characters\.
   + Must start and end with an alphanumeric character or number\.
   + Can include alphanumeric characters, numbers, periods, dashes, and underscores\.

1. Optionally, you can add alternate domains and subdomains\.

   For more information, see [Add alternate domains and subdomains to your SSL/TLS certificate](add-alternate-domain-names-to-tls-ssl-certificate-https.md)

1. Choose **Create**\.

   Lightsail begins the validation process\. You have 72 hours to verify that you own your domain\.

   After you create your certificate, you see the certificate along with the domain name and all your alternate domains and subdomains\. You need to create a DNS record for each domain and subdomain\.  
![\[Certificate pending validation with domains and subdomains\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-certificate-validation.png)

## Next step<a name="create-ssl-tls-certificate-next-steps"></a>
+  [Verify that you own your domain](verify-tls-ssl-certificate-using-dns-cname-https.md) 