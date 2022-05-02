# Validating SSL/TLS certificates for your Amazon Lightsail distribution<a name="amazon-lightsail-validating-a-distribution-certificate"></a>

 *Last updated: July 23, 2020* 

You must validate an Amazon Lightsail SSL/TLS certificate after you created it and before you can use it with your Lightsail distribution\. When you validate a certificate, you verify that you control all the domain names that you specified for the certificate when you created it\. You do this by adding canonical name \(CNAME\) records to the DNS zone of each of the domains specified on the certificate\. The records that you need to add are listed in the Lightsail console\.

In this guide, we provide you with the procedure to validate your certificate using a Lightsail DNS zone\. The procedure to validate your certificate using a different DNS hosting provider, like Domain\.com or GoDaddy, may be similar\. For more information about Lightsail DNS zones, see [DNS in Amazon Lightsail](understanding-dns-in-amazon-lightsail.md)\.

For more information about SSL/TLS certificates, see [SSL/TLS certificates in Amazon Lightsail](understanding-tls-ssl-certificates-in-lightsail-https.md)\.

**Contents**
+ [Prerequisite](#validate-distribution-certificate-prerequisite)
+ [Get the CNAME record values to validate your certificate](#get-distribution-certificate-cname-records)
+ [Add the CNAME records to your domain's DNS zone](#add-distribution-certificate-cname-records)
+ [Viewing the status of your distribution certificate](#viewing-distribution-certificate-status)
+ [Additional information](#validating-distribution-certificates-additional-information)

## Prerequisite<a name="validate-distribution-certificate-prerequisite"></a>

Before you get started, you need to create an SSL/TLS certificate for your distribution\. For more information, see [Creating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-create-a-distribution-certificate.md)\.

## Get the CNAME record values to validate your certificate<a name="get-distribution-certificate-cname-records"></a>

Complete the following procedure to get the CNAME records that you must add to your domains to validate the certificate\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Networking** tab\.

1. Choose the name of the distribution for which want to get the CNAME record values of a certificate\.  
![\[Networking tab of the Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/lightsail-home-page-networking.png)

1. Choose the **Custom domains** tab on your distribution's management page\.  
![\[Custom domains tab of a Lightsail distribution.\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/lightsail-distribution-custom-domains-tab.png)

1. Scroll down to the **Certificates** section of the page\.

   All of your distribution certificates are listed under the **Certificates** section of the page, including certificates with a **Pending validation** status\.  
![\[SSL/TLS certificates section of a Lightsail distribution.\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/distribution-certificates-section.png)

1. Find the certificate that you want to validate, and make note of the **Name** and **Value** of the CNAME records that you must add for each domain listed\.  
![\[Records to validate domain ownership for a Lightsail SSL/TLS certificate.\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/lighstail-certificate-validation-records.png)

   You must add these records exactly as listed\. We recommend that you copy and paste these values into a text file that you can refer to later\. For more information, see the following [Add the CNAME records to your domain's DNS zone](#add-distribution-certificate-cname-records) section of this guide\.

## Add the CNAME records to your domain's DNS zone<a name="add-distribution-certificate-cname-records"></a>

Complete the following procedure to add CNAME records to your domain's DNS zone\.

1. On the Lightsail home page, choose the **Networking** tab\.

1. Under the **DNS zones** section of the page, choose the domain name to which you want to add the CNAME records to validate your certificate\.  
![\[Networking tab of the Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/lightsail-home-page-networking-dns-zone.png)

1. Choose **Add record** in the DNS zone management page\.  
![\[Add record to Lightsail DNS zone\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/lightsail-dns-zone-add-record.png)

1. Choose **CNAME** in the DNS record type drop\-down\.

1. In the **Subdomain** text box, enter the **Name** value of the CNAME record that you got from your certificate\.

   The Lightsail console pre\-populates the apex portion of your domain\. For example, if you want to add the `www.example.com` subdomain, then you only have to enter `www` into the text box, and Lightsail adds the `.example.com` portion for you when you save the record\.

1. In the **Maps to** text box, enter the **Value** portion of the CNAME record that you got from your certificate\.

1. Confirm that the values you entered are exactly as they were listed on the certificate that you want to validate\.  
![\[Add CNAME record to Lightsail DNS zone\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/lightsail-dns-zone-cname-record.png)

1. Choose the save icon to save the record to your DNS zone\.

   Repeat these steps to add additional CNAME records for domains on your certificate that need to be validated\. Allow time for changes to propagate through the internet's DNS\. After a few minutes, you should see if the status of your distribution certificate has changed to **Valid**\. For more information, see the following [Viewing the status of your distribution certificate](#viewing-distribution-certificate-status) section of this guide\.

## Viewing the status of your distribution certificate<a name="viewing-distribution-certificate-status"></a>

Complete the following procedure to view the status of your SSL/TLS certificate for your distribution\.

1. On the Lightsail home page, choose the **Networking** tab\.

1. Choose the name of the distribution for which you want to view a certificate's status\.  
![\[Networking tab of the Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/lightsail-home-page-networking.png)

1. Choose the **Custom domains** tab on your distribution's management page\.  
![\[Custom domains tab of a Lightsail distribution.\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/lightsail-distribution-custom-domains-tab.png)

1. Scroll down to the **Certificates** section of the page\.

   All of your distribution certificates are listed under the **Certificates** section of the page, including certificates with **Pending validation** and **Valid** statuses\.  
![\[Validated SSL/TLS certificate\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/lightsail-validated-certificate.png)

   A **Valid** status confirms that you successfully validated your certificate with the CNAME records that you added to your domains\. Choose **Show details** to view your certificate's important dates, encryption details, identification, and validation records\. Your certificates are valid for 13 months from the date on which you validated them, after which time Lightsail attempts to automatically re\-validate them\. Don't delete the CNAME records that you added to your domain because they are required when your certificate is re\-validated on the **Valid until** date listed\.

   After you validate your SSL/TLS certificate, you should enable custom domains for your distribution to use the domain names of your certificate on your distribution\. For more information, see [Enabling custom domains for your Amazon Lightsail distributions](amazon-lightsail-enabling-distribution-custom-domains.md)\.

## Additional information<a name="validating-distribution-certificates-additional-information"></a>

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
+ [Validating SSL/TLS certificates for your Amazon Lightsail distribution](#amazon-lightsail-validating-a-distribution-certificate)
+ [Viewing SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-viewing-distribution-certificates.md)
+ [Deleting SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-deleting-distribution-certificates.md)