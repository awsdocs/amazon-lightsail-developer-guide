# Define the primary domain for your WordPress Multisite instance in Amazon Lightsail<a name="amazon-lightsail-define-the-primary-domain-for-your-wordpress-multisite"></a>

 *Last updated: June 18, 2021* 

A WordPress Multisite instance in Amazon Lightsail is designed to use multiple domains, or subdomains, for each blog site that you create within that instance\. Because of this, you must define the primary domain to use for the main blog of your WordPress Multisite instance\.

## Prerequisites<a name="define-the-primary-domain-for-your-wordpress-multisite-prerequisites"></a>

Complete the following prerequisites in the order shown:

1. Create a WordPress Multisite instance in Lightsail\. For more information, see [Create an Amazon Lightsail instance](how-to-create-amazon-lightsail-instance-virtual-private-server-vps.md)\.

1. Create a static IP and attach it to your WordPress Multisite instance in Lightsail\. For more information, see [Create a static IP and attach it to an instance in Amazon Lightsail](lightsail-create-static-ip.md)\.
**Important**  
You must reboot your WordPress Multisite instance after you attach a static IP to it\. This will allow the instance to recognize the new static IP associated to it\.

1. Add your domain to Lightsail by creating a DNS zone, then point it to the static IP that you attached to your WordPress Multisite instance\. For more information, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)\.

1. Allow time for the DNS changes to propagate through the internet's DNS\. Then, you can continue to the [Define the primary domain for your WordPress Multisite instance>](#define-the-primary-domain-for-your-wordpress-multisite) section of this guide\.

## Define the primary domain for your WordPress Multisite instance<a name="define-the-primary-domain-for-your-wordpress-multisite"></a>

Complete these steps to ensure that your domain, such as `example.com`, redirects to the main blog of your WordPress Multisite instance\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the SSH quick connect icon for your WordPress Multisite instance\.  
![\[SSH quick connect on the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/wp-multisite-ssh-quick-connect.png)

1. Enter the following command to define the primary domain name for your WordPress Multisite instance\. Be sure to replace `<domain>` with the correct domain name for your WordPress Multisite\.

   ```
   sudo /opt/bitnami/configure_app_domain --domain <domain>
   ```

   Example:

   ```
   sudo /opt/bitnami/configure_app_domain --domain example.com
   ```
**Note**  
If this command fails, you might be using an older version of the WordPress Multisite instance\. Try running the following commands instead, and be sure to replace `<domain>` with the correct domain name for your WordPress Multisite\.  

   ```
   cd /opt/bitnami/apps/wordpress
   sudo ./bnconfig --machine_hostname <domain>
   ```
After running that command, enter the following command to keep the bnconfig tool from automatically running every time the server restarts\.  

   ```
   sudo mv bnconfig bnconfig.disabled
   ```

   At this point, browsing to the domain that you defined should redirect you to the main blog of your WordPress Multisite instance\.

## Next steps<a name="define-the-primary-domain-for-your-wordpress-multisite-next-steps"></a>

Complete the next steps after you have defined the primary domain for your WordPress Multisite instance:
+ [Add blogs as subdomains to your WordPress Multisite instance in Amazon Lightsail](amazon-lightsail-add-blogs-as-subdomains-to-your-wordpress-multisite.md)
+ [Add blogs as domains to your WordPress Multisite instance in Amazon Lightsail](amazon-lightsail-add-blogs-as-domains-to-your-wordpress-multisite.md)