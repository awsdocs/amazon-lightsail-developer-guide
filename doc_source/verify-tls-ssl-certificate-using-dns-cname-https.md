# Verify an SSL/TLS certificate in Amazon Lightsail<a name="verify-tls-ssl-certificate-using-dns-cname-https"></a>

*Last updated: January 18, 2019*

After you create your Lightsail load balancer and create a certificate, you need to verify that you control all the domains and subdomains where you want to have encrypted \(HTTPS\) traffic\.

**Note**  
For more information about Lightsail load balancers, see [Lightsail load balancers](understanding-lightsail-load-balancers.md)\.

**Contents**
+ [Step 1: Create a Lightsail DNS zone for your domain](#verify-ssl-tls-create-dns-zone)
+ [Step 2: Add records to your domain's DNS zone](#verify-ssl-tls-create-dns-records)
+ [Next step](#verify-ssl-tls-next-step)

## Step 1: Create a Lightsail DNS zone for your domain<a name="verify-ssl-tls-create-dns-zone"></a>

If you haven't done so already, create a Lightsail DNS zone for your domain\. For more information, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md) 

## Step 2: Add records to your domain's DNS zone<a name="verify-ssl-tls-create-dns-records"></a>

The certificate that you created in the Lightsail load balancer provides a set of canonical name \(CNAME\) records\. You add these records to your domain's DNS zone to validate that you own or control that domain\. In the following steps, we'll show you how to get the CNAME records and add them to your domain's DNS zone in the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Networking** tab\.

1. Choose the load balancer that you want to manage\.

1. Choose the **Inbound traffic** tab\.

1. Scroll to the **Certificates** section of the page, then highlight all of the CNAME records displayed on the page, including the records for alternate domains and subdomains\.

   Press **Ctrl\+C** if you’re using Windows, or **Cmd\+C** if you’re using Mac, to copy them to your clipboard\.  
![\[Certificate pending validation with domains and subdomains.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/example.certificate-validation-with-subdomains.png)

1. Open a text editor, such as Notepad if you're using Windows, or TextEdit if you're using Mac\. In the text file, press **Ctrl\+V** if you’re using Windows, or **Cmd\+V** if you’re using Mac, to paste the values into the text file\.

   Leave this text file open; you will need these CNAME values when adding the records to your domain's DNS zone later in this guide\.  
![\[Text file with certificate CNAME records.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ssl-tls-cname-records-text-file.png)

1. Choose **Home** on the top navigation bar of the Lightsail console\.

1. Choose **Networking** on the Lightsail home page\.

1. Choose the DNS zone for the domain that will use the certificates\.

1. Choose **Add record** to add the first CNAME record\.

1. Choose **CNAME** for the record type\.

1. Toggle to the text file that contains the CNAME records for your certificates\.

   Copy the **Name** of the CNAME record\. For example, `_1bfb0b9ef15a50f9041e559d2c67b760.example.com`\.

1. Toggle to the DNS Zone management page and paste the **Name** into the **Subdomain** field\.
**Important**  
Adding a CNAME record that contains the domain name \(such as `.example.com`\) will result in duplication of the domain name \(such as `.example.com.example.com`\)\. To avoid duplication, edit the entry so that only the part of the CNAME that you need is added\. This would be `_1bfb0b9ef15a50f9041e559d2c67b760`\.

1. Copy the **Value** of the CNAME record\. For example, `_c9a0c385eda13283350e35f297469a13.hkvuiqjoua.acm-validations.aws`\.

1. Toggle to the DNS Zone management page and paste the **Value** into the **Maps to** field\.

1. Choose the **Save** icon to add the record\.

1. If you have alternate subdomains, choose **Add record** to add another record\.
**Note**  
 To learn more about alternate domains or subdomains, see [Add alternate domains and subdomains to your SSL/TLS certificate in Amazon Lightsail](add-alternate-domain-names-to-tls-ssl-certificate-https.md)\.

1. Repeat steps 11 \- 16 to add the CNAME record\(s\) for the alternate subdomains\.

   You can also [add an alias \(A\) record to point to your load balancer](add-alias-record-for-lightsail-load-balancer.md) while you're on the DNS zone management page\.

   When finished, your DNS zone should look like the following screenshot\.  
![\[CNAMES in Lightsail ready to be submitted for validation.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/dns-validation-cname-with-alternate-names.png)

   After some time, your domain is verified and you will see the following message on the **Inbound traffic** tab of the load balancer management page\.  
![\[Successful validation of domain.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/example-com-verified-and-ready-to-use.png)

## Next step<a name="verify-ssl-tls-next-step"></a>

Once your domain is verified, you are ready to [attach a validated SSL/TLS certificate to your Lightsail load balancer](attach-validated-certificate-to-load-balancer.md)\.