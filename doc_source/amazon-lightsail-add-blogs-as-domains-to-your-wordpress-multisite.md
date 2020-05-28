# Add blogs as domains to your WordPress Multisite instance in Amazon Lightsail<a name="amazon-lightsail-add-blogs-as-domains-to-your-wordpress-multisite"></a>

 *Last updated: January 13, 2020* 

A WordPress Multisite instance in Amazon Lightsail is designed to use multiple domains, or subdomains, for each blog site that you create within that instance\. In this guide, we’ll show you how to add a blog site using a different domain than your main blog’s primary domain on your WordPress Multisite instance\. For example, if your main blog’s primary domain is `example.com`, you can create new blog sites that use the `another-example.com` and `third-example.com` domains on the same instance\.

**Note**  
You can also add sites using subdomains to your WordPress Multisite instance\. For more information, see [Add blogs as subdomains to your WordPress Multisite instance in Amazon Lightsail](amazon-lightsail-add-blogs-as-subdomains-to-your-wordpress-multisite.md)\.

## Prerequisites<a name="add-blogs-as-domains-to-your-wordpress-multisite-prerequisites"></a>

Complete the following prerequisites in the order shown:
+ Create a WordPress Multisite instance in Lightsail\. For more information, see [Create an Amazon Lightsail instance](how-to-create-amazon-lightsail-instance-virtual-private-server-vps.md)\.
+ Create a static IP and attach it to your WordPress Multisite instance in Lightsail\. For more information, see [Create a static IP and attach it to an instance in Amazon Lightsail](lightsail-create-static-ip.md)\.
+ Add your domain to Lightsail by creating a DNS zone, then point it to the static IP that you attached to your WordPress Multisite instance\. For more information, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)\.
+ Define the primary domain for your WordPress Multisite instance in Lightsail\. For more information, see [Define the primary domain for your WordPress Multisite instance in Amazon Lightsail](amazon-lightsail-define-the-primary-domain-for-your-wordpress-multisite.md)\.

## Activate the WordPress MU Domain Mapping plugin<a name="activate-the-wordpress-mu-domain-mapping-plugin"></a>

In this step you will activate the WordPress MU Domain Mapping plugin that is preinstalled on your WordPress Multisite instance\. This plugin enables you to easily add multiple domains to your instance, and redirect them to the correct blog site on your WordPress Multisite instance\.

1. Sign in to the administration dashboard of your WordPress Multisite instance\.
**Note**  
For more information, see [Getting the application user name and password for your 'Certified by Bitnami' instance in Amazon Lightsail](log-in-to-your-bitnami-application-running-on-amazon-lightsail.md)\.

1. Choose **My Sites**, then **Network Admin**, and **Plugins** in the top navigation pane\.  
![\[Plugins menu on the WordPress administration dashboard.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/wp-multisite-add-blogs-as-domains-plugins-menu.png)

1. Choose **Network Activate** listed under the WordPress MU Domain Mapping plugin\.  
![\[WordPress MU domain mapping.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/wp-multisite-add-blogs-as-domains-wordpress-mu-domain-mapping.png)

1. After the WordPress MU Domain Mapping plugin is active, choose **Settings**, then **Domain Mapping** in the left navigation pane\.

1. In the Domain Mapping Configuration page, choose the **Permanent redirect** checkbox\. Leave all other options as they are\.  
![\[WordPress domain mapping options.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/wp-multisite-add-blogs-as-domains-domain-options.png)

1. Choose **Save**\.

   You’ve now enabled the use of domains with your WordPress Multisite instance\. Continue to the next step, to add a new blog site as a domain\.

## Add a blog as a domain to your WordPress Multisite instance<a name="add-a-blog-as-a-domain-to-your-wordpress-multisite-instance"></a>

Complete these steps to create a blog site on your WordPress Multisite instance that uses a domain which is different than your main blog’s primary domain\.

1. In the administration dashboard of your WordPress Multisite instance, choose **My Sites**, then **Network Admin**, and **Sites**\.  
![\[Sites menu in the WordPress administration dashboard.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/wp-multisite-add-blogs-as-domains-sites-menu.png)

1. Choose **Add New** to add a new blog site\.

1. Enter a site address, which is the domain that will be used for the new blog site\. For example, if your new blog site will use `example-blog.com` as the domain, then enter use `example-blog` into the text box\. Ignore the primary domain suffix displayed on the page\.  
![\[Ignore the domain suffix in the WordPress administration dashboard.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/wp-multisite-add-blogs-as-domains-ignore-domain-suffix.png)

1. Enter a site title, select a site language, and enter an admin email\.

1. Choose **Add Site**\.

1. Choose **My Sites**, then **Network Admin**, and **Sites** in the top navigation pane\. The newly created blog site should be listed\.

1. Hover your cursor over the newly created blog site, and make note of the site ID number shown in the URL pop up at the bottom of the browser window\. You will need the site ID in the next set of steps\.  
![\[WordPress site ID.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/wp-multisite-add-blogs-as-domains-site-id.png)

1. Choose **Settings**, then **Domain** in the left navigation pane\.

1. Enter the site ID acquired earlier in this guide into the **Site ID** text box, and enter the domain for the new blog site into the **Domain** text box\.  
![\[Adding a new domain in WordPress.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/wp-multisite-add-blogs-as-domains-new-domain.png)

1. Choose **Save**\.

1. Choose **My Sites**, then **Network Admin**, and **Sites** in the top navigation pane\. The new blog site’s domain should be listed under the Mapping column as shown in the following screenshot:  
![\[Sites list in the WordPress administration dashboard.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/wp-multisite-add-blogs-as-domains-sites-list.png)

   At this point, the new blog site has been created in your WordPress Multisite instance, but the domain is not yet configured to route to the new blog site\. Continue to the next step to add an address record \(A record\) to your domain’s DNS zone\.

## Add an address record \(A record\) to your domain’s DNS zone<a name="add-address-record-to-your-domains-dns-zone"></a>

Complete these steps to point the domain for your new blog site to your WordPress Multisite instance\. You must perform these steps for every blog site that you create on your WordPress Multisite instance\.

For demonstration purposes, we’ll use the Lightsail DNS zone\. However, the steps may be similar for other DNS zones typically hosted by domain registrars\.

**Important**  
You can create a maximum of three DNS zones in the Lightsail console\. If you need more DNS zones, we recommend using Amazon Route 53 to manage your domain’s DNS records\. For more information, see [Making Amazon Route 53 the DNS Service for an Existing Domain](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/MigratingDNS.html)\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Networking** tab\.

1. Under the **DNS zones** section of the page, choose the DNS zone for your new blog site’s domain\.

1. In the DNS zone editor, choose **Add record**\.  
![\[The DNS zone editor in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/wp-multisite-add-blogs-as-domains-dns-zone.png)

1. Choose **A record** in the record type drop\-down menu\.

1. In the **Subdomain** text box, enter an “at” \(@\) symbol to create a record for the root of the domain\.

1. In the **Resolves to** text box, choose the static IP address attached to your WordPress Multisite instance\.  
![\[Adding an address record to the DNS zone in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/wp-multisite-add-blogs-as-domains-a-record.png)

1. Choose the Save icon\.

   After the change propagates through the internet’s DNS, the domain will redirect to the new blog site on your WordPress Multisite instance\.

## Update the site address to access the administration dashboard for your new blog site<a name="update-the-site-address-to-access-the-administration-dashboard"></a>

Although you are able to access the new blog using the domain name, you’re not able to access the blog’s administration dashboard\. This is because WordPress still considers the new site to be a subdomain of the primary domain and tries to access it using an invalid URL, such as `example-blog.example.com` instead of `example-blog.com`\. To resolve this, edit the blog’s site address in the network administration dashboard as follows:

1. Sign in to the administration dashboard of your WordPress Multisite instance\.

1. Choose **My Sites**, then **Network Admin**, and **Sites** in the top navigation pane\.

1. Choose the new blog site from the list of sites\.  
![\[Sites list in the WordPress administration dashboard.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/wp-multisite-add-blogs-as-domains-sites.png)

1. In the **Site Address \(URL\)** text box, enter the correct domain for the blog site  
![\[Site address URL in the WordPress administration dashboard.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/wp-multisite-add-blogs-as-domains-site-address-url.png)

1. Choose **Save Changes**\.  
![\[WordPress domains.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/wp-multisite-add-blogs-as-domains-choose-dashboard.png)

   The site URL is updated to reflect the correct domain name\. When you choose Dashboard, displayed under the URL, you should be redirected to the administration dashboard for your new blog site\.