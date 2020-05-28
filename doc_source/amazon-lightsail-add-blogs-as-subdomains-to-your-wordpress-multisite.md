# Add blogs as subdomains to your WordPress Multisite instance in Amazon Lightsail<a name="amazon-lightsail-add-blogs-as-subdomains-to-your-wordpress-multisite"></a>

 *Last updated: November 18, 2018* 

A WordPress Multisite instance in Amazon Lightsail is designed to use multiple domains, or subdomains, for each blog site that you create within that instance\. In this guide, we’ll show you how to add a blog site as a subdomain of your WordPress Multisite instance\. For example, if your main blog’s primary domain is `example.com`, you can create new blog sites that use the `earth.example.com` and `moon.example.com` subdomains on the same instance\.

**Note**  
You can also add sites using domains to your WordPress Multisite instance\. For more information, see [Add blogs as domains to your WordPress Multisite instance in Amazon Lightsail](amazon-lightsail-add-blogs-as-domains-to-your-wordpress-multisite.md)\.

## Prerequisites<a name="add-blogs-as-subdomains-to-your-wordpress-multisite-prerequisites"></a>

Complete the following prerequisites in the order shown:
+ Create a WordPress Multisite instance in Lightsail\. For more information, see [Create an Amazon Lightsail instance](how-to-create-amazon-lightsail-instance-virtual-private-server-vps.md)\.
+ Create a static IP and attach it to your WordPress Multisite instance in Lightsail\. For more information, see [Create a static IP and attach it to an instance in Amazon Lightsail](lightsail-create-static-ip.md)\.
+ Add your domain to Lightsail by creating a DNS zone, then point it to the static IP that you attached to your WordPress Multisite instance\. For more information, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)\.
+ Define the primary domain for your WordPress Multisite instance in Lightsail\. For more information, see [Define the primary domain for your WordPress Multisite instance in Amazon Lightsail](amazon-lightsail-define-the-primary-domain-for-your-wordpress-multisite.md)\.

## Add a blog as a subdomain to your WordPress Multisite instance<a name="add-a-blog-as-a-subdomain"></a>

Complete these steps to create new blogs on your WordPress Multisite instance that use a subdomain of your main blog’s primary domain\.

1. Sign in to the administration dashboard of your WordPress Multisite instance\.
**Note**  
For more information, see [Getting the application user name and password for your 'Certified by Bitnami' instance in Amazon Lightsail](log-in-to-your-bitnami-application-running-on-amazon-lightsail.md)\.

1. Choose **My Sites**, then **Network Admin**, and **Sites** in the top navigation pane\.  
![\[Sites menu in the WordPress administration dashboard.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/wp-multisite-add-blogs-as-subdomains-sites-menu.png)

1. Choose **Add New** to add a new blog site\.

1. Enter a site address, which is the subdomain that will be used for the new blog site\.  
![\[Add new site in the WordPress administration dashboard.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/wp-multisite-add-blogs-as-subdomains-add-new-site.png)

1. Enter a site title, select a site language, and enter an admin email\.

1. Choose **Add Site**\.

   At this point, the new blog site has been created in your WordPress Multisite instance, but the subdomain is not yet configured to route to the new blog site\. Continue to the next step to add an address record \(A record\) to your domain’s DNS zone\.  
![\[Sites list in the WordPress administartion dashboard.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/wp-multisite-add-blogs-as-subdomains-sites-list.png)

## Add an address record \(A record\) to your domain’s DNS zone<a name="add-an-address-record-to-your-domains-dns-zone"></a>

Complete these steps to point the subdomain for your new blog site to your WordPress Multisite instance\. You must perform these steps for every blog site that you create on your WordPress Multisite instance\.

For demonstration purposes, we’ll use the Lightsail DNS zone\. However, the steps may be similar for other DNS zones typically hosted by domain registrars\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Networking** tab\.

1. Under the **DNS zones** section of the page, choose the DNS zone for the domain that you defined as the primary domain for your WordPress Multisite instance\.

1. In the DNS zone editor, choose **Add record**\.  
![\[DNS zone editor in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/wp-multisite-add-blogs-as-subdomains-dns-zone.png)

1. Choose **A record** in the record type drop\-down menu\.

1. In the **Subdomain** text box, enter the subdomain specified as the site address when creating the new blog site on your WordPress Multisite instance\.

1. In the **Resolves to** text box, choose the static IP address attached to your WordPress Multisite instance\.  
![\[Adding an address record to the DNS zone in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/wp-multisite-add-blogs-as-subdomains-a-record.png)

1. Choose the Save icon\.

   That is all you need to do\. After the change propagates through the internet’s DNS, the domain will redirect to the new blog site on your WordPress Multisite instance\.