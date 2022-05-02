# Configuring your WordPress instance to work with your Amazon Lightsail distribution<a name="amazon-lightsail-editing-wp-config-for-distribution"></a>

 *Last updated: February 23, 2022* 

In this guide, we show you how to configure your WordPress instance to work with your Amazon Lightsail distribution\. To configure your WordPress instance to work with your distribution, determine if: 
+ **Your WordPress website uses Hypertext Transfer Protocol \(HTTP\) only** \- If your website uses HTTP only, and is not configured to use HTTPS, then you must follow the instructions in the [Configure your WordPress instance to work with your distribution using SSL/TLS termination](#configuring-non-https-wordpress-for-distribution) section of this guide\.
+ **Your WordPress website uses Hypertext Transfer Protocol Secure \(HTTPS\)** \- If your website is configured to use HTTPS, then you must follow the instructions in the [Configure your WordPress instance to work with your distribution using end\-to\-end encryption](#configuring-https-wordpress-for-distribution) section of this guide\. If you want to configure your WordPress website to use HTTPS, then see [Tutorial: Using Let’s Encrypt SSL certificates with your WordPress instance in Amazon Lightsail](amazon-lightsail-using-lets-encrypt-certificates-with-wordpress.md)\.

For more information about distributions, see [Content delivery network distributions in Amazon Lightsail](amazon-lightsail-content-delivery-network-distributions.md)\.

## Configure your WordPress instance to work with your distribution using SSL/TLS termination<a name="configuring-non-https-wordpress-for-distribution"></a>

All Lightsail distributions have HTTPS enabled by default for their default domain \(e\.g\., `123456abcdef.cloudfront.net`\)\. When you configure a WordPress instance that doesn't use HTTPS as the origin of your distribution, you can configure your distribution to terminate SSL/TLS and forward all content requests to your instance using an unencrypted connection\. The connection between your website visitors and your distribution is encrypted \(using HTTPS\), and the connection between your distribution and your instance is un\-encrypted \(using HTTP only\)\. This configuration is known as SSL/TLS termination\. To enable this configuration, you must configure your distribution's origin protocol policy to **HTTP only**, which is the default configuration\. For more information, see [Origin protocol policy](https://lightsail.aws.amazon.com/ls/docs/en_us/articles/amazon-lightsail-changing-distribution-origin#changing-distribution-origin-protocol-policy)\. You must also edit the WordPress configuration file \(`wp-config.php`\) in your instance to account for the TLS termination behavior from your distribution\. If you don't make the required edits to the `wp-config.php` file in your instance, your website visitors might see an error or your website content might not be formatted correctly\.

Complete the following procedure to edit the `wp-config.php` file in your WordPress instance for it to work with your distribution\.

**Note**  
We recommend that you create a snapshot of your WordPress instance before getting started with this procedure\. The snapshot can be used as a backup from which you can create another instance in case something goes wrong\. For more information, see [Creating a snapshot of your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md)\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the browser\-based SSH client icon that is displayed next to your WordPress instance\.

1. After you're connected to your instance, enter the following command to create a backup of the `wp-config.php` file\. If something goes wrong, you can restore the file using the backup\.

   ```
   sudo cp /opt/bitnami/wordpress/wp-config.php /opt/bitnami/wordpress/wp-config.php.backup
   ```

1. Enter the following command to open the `wp-config.php` file using Vim\.

   ```
   sudo vim /opt/bitnami/wordpress/wp-config.php
   ```

1. Press `I` to enter insert mode in Vim\.

1. Delete the following lines of code in the file\.

   ```
   define('WP_SITEURL', 'http://' . $_SERVER['HTTP_HOST'] . '/');
   define('WP_HOME', 'http://' . $_SERVER['HTTP_HOST'] . '/');
   ```

1. Add the following lines of code to the file, where you previously deleted the code\.

   ```
   define('WP_SITEURL', 'https://' . $_SERVER['HTTP_HOST'] . '/');
   define('WP_HOME', 'https://' . $_SERVER['HTTP_HOST'] . '/');
   if (isset($_SERVER['HTTP_CLOUDFRONT_FORWARDED_PROTO'])
   && $_SERVER['HTTP_CLOUDFRONT_FORWARDED_PROTO'] === 'https') {
   $_SERVER['HTTPS'] = 'on';
   }
   ```

1. Press the **Esc** key to exit insert mode in Vim, then type `:wq!` and press **Enter** to save your edits \(write\) and quit Vim\.

1. Enter the following command to restart the Apache service on your instance\.

   ```
   sudo /opt/bitnami/ctlscript.sh restart apache
   ```

1. Wait a few moments for your the Apache service to restart, then test that your distribution is caching your content\. For more information, see [Testing your Amazon Lightsail distribution](amazon-lightsail-testing-distribution.md)\.

1. If something went wrong, re\-connect to your instance using the browser\-based SSH client\. Run the following command to restore the `wp-config.php` file using the backup you created earlier in this guide\.

   ```
   sudo cp /opt/bitnami/wordpress/wp-config.php.backup /opt/bitnami/wordpress/wp-config.php
   ```

## Configure your WordPress instance to work with your distribution using end\-to\-end encryption<a name="configuring-https-wordpress-for-distribution"></a>

All Lightsail distributions have HTTPS enabled by default for their default domain \(e\.g\., `123456abcdef.cloudfront.net`\)\. When you configure a WordPress instance that uses HTTPS as the origin of your distribution, you can configure your distribution to forward all content requests to your instance using an encrypted connection\. The connection between your website visitors and your distribution is encrypted \(using HTTPS\), and so is the connection between your distribution and your instance\. This configuration is known as end\-to\-end encryption\. To enable this configuration, you must configure your distribution's origin protocol policy to **HTTPS only**\. For more information, see [Origin protocol policy](https://lightsail.aws.amazon.com/ls/docs/en_us/articles/amazon-lightsail-changing-distribution-origin#changing-distribution-origin-protocol-policy)\. If you don't configure your distribution's origin policy to **HTTPS only**, your website visitors will see an error\.

## Additional information about distributions<a name="distributions-editing-wp-config-additional-information"></a>

Here are some articles to help you manage distributions in Lightsail:
+ [Content delivery network distributions in Amazon Lightsail](amazon-lightsail-content-delivery-network-distributions.md)
+ [Creating Amazon Lightsail distributions](amazon-lightsail-creating-content-delivery-network-distribution.md)
+ [Understanding request and response behaviors of an Amazon Lightsail distribution](amazon-lightsail-distribution-request-and-response.md)
+ [Configuring your WordPress instance to work with your Amazon Lightsail distribution](#amazon-lightsail-editing-wp-config-for-distribution)
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
+ [Validating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-validating-a-distribution-certificate.md)
+ [Viewing SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-viewing-distribution-certificates.md)
+ [Deleting SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-deleting-distribution-certificates.md)