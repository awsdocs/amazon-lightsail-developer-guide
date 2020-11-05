# Enabling HTTPS on your WordPress instance in Amazon Lightsail<a name="amazon-lightsail-enabling-https-on-wordpress"></a>

 *Last updated: October 1, 2020* 

Enabling Hypertext Transfer Protocol Secure \(HTTPS\) for your WordPress website assures visitors that your website is secure; that it's sending and receiving encrypted data\. A non\-secure website has an address that starts with `http`, such as `http://example.com`, while a secure website has an address that starts with `https`, such as `https://example.com`\. Even if your website is primarily informational, it's still recommended that you enable HTTPS\. This is because most web browsers will notify website visitors that your website is not secure if HTTPS is not enabled, and your website will rank lower in search engine results\.

This guide shows you how to use the Bitnami HTTPS configuration tool \(`bncert`\) to enable HTTPS on your *Certified by Bitnami* WordPress instance on Amazon Lightsail\. It lets you request certificates only for the domains and subdomains that you specify when making your request\. Alternately, you can use the Certbot tool, which lets you request a certificate for domains and a wildcard certificate for subdomains\. A wildcard certificate works for *any* subdomains of a domain, which is beneficial if you don't know which subdomains you will use to direct traffic to your instance\. However, Certbot does not automatically renew your certificate like the `bncert` tool\. If you use Certbot, you have to manually renew your certificates every 90 days\. For more information about using Certbot to enable HTTPS, see [Tutorial: Using Let’s Encrypt SSL certificates with your WordPress instance in Amazon Lightsail](amazon-lightsail-using-lets-encrypt-certificates-with-wordpress.md)\.

**Contents**
+ [Step 1: Learn about the process](#https-process-wordpress)
+ [Step 2: Complete the prerequisites](#https-prerequisites-wordpress)
+ [Step 3: Connect to your instance](#https-wordpress-connect-to-instance)
+ [Step 4: Confirm the bncert tool is installed on your instance](#https-wordpress-bncert-install)
+ [Step 5: Enable HTTPS on your WordPress instance](#https-wordpress-enable)
+ [Step 6: Test that your website is using HTTPS](#test-https-on-your-website)

## Step 1: Learn about the process<a name="https-process-wordpress"></a>

**Note**  
In this section, you get a high\-level overview of the process\. The specific steps to perform this process are included in the subsequent steps of this guide\.

To enable HTTPS for your WordPress website, connect to your Lightsail instance using SSH, and use the `bncert` tool to request an SSL/TLS certificate from the [Let's Encrypt](https://letsencrypt.org/about/) certificate authority\. When you request the certificate, you specify your website's primary domain \(`example.com`\) and alternate domains \(`www.example.com`, `blog.example.com`, etc\.\), if any\. Let's Encrypt validates that you own the domains either by asking you to create TXT records in the DNS of your domains, or by verifying that those domains are already directing traffic to the public IP address of the instance from which you make the request\.

After your certificate is validated, you can configure your WordPress website to automatically redirect visitors from HTTP to HTTPS \(`http://example.com` redirects to `https://example.com`\) so that visitors are forced to use the encrypted connection\. You can also configure your website to automatically redirect the `www` subdomain to the apex of your domain \(`https://www.example.com` redirects to `https://example.com`\) or vice versa \(`https://example.com` redirects to `https://www.example.com`\)\. These redirections are also configured using the `bncert` tool\.

Let's Encrypt requires that you renew your certificate every 90 days to maintain HTTPS on your website\. The `bncert` tool automatically renews your certificates for you, so that you can spend more time focusing on your website\.

**Limitations of the bncert tool**

The `bncert` tool has the following limitations:
+ It's not preinstalled on all *Certified by Bitnami* WordPress instances when they're created\. WordPress instances that were created on Lightsail a while back will require that you manually install the `bncert` tool\. Step 4 of this guide shows you how to confirm that the tool is installed on your instance, and how to install it if it's not\.
+ It lets you request certificates only for the domains and subdomains that you specify when making your request\. This is different than the Certbot tool, which lets you request a certificate for domains and a wildcard certificate for subdomains\. A wildcard certificate works for *any* subdomains of a domain, which is beneficial if you don't know which subdomains you will use to direct traffic to your instance\. However, Certbot does not automatically renew your certificate like the `bncert` tool\. If you use Certbot, you have to manually renew your certificates every 90 days\. For more information about using Certbot to enable HTTPS, see [Tutorial: Using Let’s Encrypt SSL certificates with your WordPress instance in Amazon Lightsail](amazon-lightsail-using-lets-encrypt-certificates-with-wordpress.md)\.

## Step 2: Complete the prerequisites<a name="https-prerequisites-wordpress"></a>

Complete the following prerequisites if you haven’t already done so:
+ Create a WordPress instance in Lightsail, and configure your website on your instance\. For more information, see [Get started with Linux/Unix\-based instances in Amazon Lightsail](getting-started-with-amazon-lightsail.md)\.
+ Attach a static IP to your instance\. Your instance's public IP address changes if you stop and start your instance\. A static IP does not change if you stop and start your instance\. For more information, see [Create a static IP and attach it to an instance in Amazon Lightsail](lightsail-create-static-ip.md)\.
+ Create a snapshot of your WordPress instance after you're done configuring it, or enable automatic snapshots\. The snapshot can be used as a backup from which you can create another instance in case something goes wrong with your original instance\. For more information, see [Creating a snapshot of your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md) or [Enabling or disabling automatic snapshots for instances or disks in Amazon Lightsail](amazon-lightsail-configuring-automatic-snapshots.md)\.
+ Add DNS records to the DNS of your domain that directs traffic for the apex of your domain \(`example.com`\) and for its `www` subdomain \(`www.example.com`\) to the public IP address of your WordPress instance in Lightsail\. You can complete these actions at your domain's current DNS hosting provider\. Or if you transferred management of your domain's DNS to Lightsail, you can complete these actions using a DNS zone in Lightsail\. To learn more, see [DNS in Amazon Lightsail](understanding-dns-in-amazon-lightsail.md)\.
**Important**  
Add DNS records to the DNS of all domains that you want use with your WordPress website\. All of those domains should be routing traffic to the public IP address of your WordPress website\. The `bncert` tool will issue certificates only for domains that are currently directing traffic to the public IP address of your WordPress instance\.

## Step 3: Connect to your instance<a name="https-wordpress-connect-to-instance"></a>

Complete the following steps to connect to your instance using the browser\-based SSH client in the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the SSH quick connect icon for your WordPress instance\.  
![\[SSH quick connect on the Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a825044edce3b3cf14c8cdbea7367d2e/images/amazon-lightsail-wordpress-ssh-quick-connect.png)

   The browser\-based SSH client terminal window opens\. You are successfully connected to your instance via SSH if you see the Bitnami logo as shown in the following example\.  
![\[Browser-based SSH client terminal window in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a825044edce3b3cf14c8cdbea7367d2e/images/amazon-lightsail-ssh-session-bncert.png)

## Step 4: Confirm the bncert tool is installed on your instance<a name="https-wordpress-bncert-install"></a>

Complete the following steps to ensure the Bitnami HTTPS configuration tool \(`bncert`\) is installed on your instance\. It's not preinstalled on all *Certified by Bitnami* WordPress instances when they're created\. WordPress instances that were created on Lightsail a while back will require that you manually install the `bncert` tool\. This procedure includes the steps to install the tool if it's is not installed\.

1. Enter the following command to run the `bncert` tool\.

   ```
   sudo /opt/bitnami/bncert-tool
   ```
   + If you see `command not found` in the response as shown in the following example, then the `bncert` tool is not installed on your instance\. Continue to the next step in this procedure to install the `bncert` tool on your instance\.
**Important**  
The `bncert` tool can only be used on WordPress instances that are *Certified by Bitnami*\. Alternately, you can use the Certbot tool to enable HTTPS on your WordPress instance\. For more information, see [Tutorial: Using Let’s Encrypt SSL certificates with your WordPress instance in Amazon Lightsail](amazon-lightsail-using-lets-encrypt-certificates-with-wordpress.md)\.  
![\[Message confirming the bncert tool is not installed\]](https://d9yljz1nd5001.cloudfront.net/en_us/a825044edce3b3cf14c8cdbea7367d2e/images/run-bncert-tool-fail.png)
   + If you see `Welcome to the Bitnami HTTPS configuration tool` in the response as shown in the following example, then the `bncert` tool is installed on your instance\. Continue to the [Step 5: Enable HTTPS on your WordPress instance](#https-wordpress-enable) section of this guide\.  
![\[Message confirming the bncert tool is installed\]](https://d9yljz1nd5001.cloudfront.net/en_us/a825044edce3b3cf14c8cdbea7367d2e/images/run-bncert-tool-success.png)

1. Enter the following command to download the `bncert` run file to your instance\.

   ```
   wget -O bncert-linux-x64.run https://downloads.bitnami.com/files/bncert/latest/bncert-linux-x64.run
   ```

1. Enter the following command to create a directory for the `bncert` run file on your instance\.

   ```
   sudo mkdir /opt/bitnami/bncert
   ```

1. Enter the following command to move the downloaded `bncert` run file to the new directory you created\.

   ```
   sudo mv bncert-linux-x64.run /opt/bitnami/bncert/
   ```

1. Enter the following command to make the `bncert` run a file that can be executed as a program\.

   ```
   sudo chmod +x /opt/bitnami/bncert/bncert-linux-x64.run
   ```

1. Enter the following command to create a symbolic link that runs the `bncert` tool when you enter the `sudo /opt/bitnami/bncert-tool` command\.

   ```
   sudo ln -s /opt/bitnami/bncert/bncert-linux-x64.run /opt/bitnami/bncert-tool
   ```

   You are now done installing the `bncert` tool on your instance\. Continue to the [Step 5: Enable HTTPS on your WordPress instance](#https-wordpress-enable) section of this guide\.

## Step 5: Enable HTTPS on your WordPress instance<a name="https-wordpress-enable"></a>

Complete the following procedure to enable HTTPs on your WordPress instance after you have confirmed that the `bncert` tool is installed on your instance\.

1. Enter the following command to run the `bncert` tool\.

   ```
   sudo /opt/bitnami/bncert-tool
   ```

   You should see a message similar to the following example\.  
![\[Running the bncert tool\]](https://d9yljz1nd5001.cloudfront.net/en_us/a825044edce3b3cf14c8cdbea7367d2e/images/run-bncert-tool-success.png)

   If the `bncert` tool has been installed on your instance for a while, then you might see a message indicating that an updated version of the tool is available\. Choose to download it as shown in the following example, and then enter the `sudo /opt/bitnami/bncert-tool` command to run the `bncert` tool again\.  
![\[Message indicating a new version of the bncert tool is available\]](https://d9yljz1nd5001.cloudfront.net/en_us/a825044edce3b3cf14c8cdbea7367d2e/images/bncert-update-required.png)

1. Enter your primary domain name and alternate domain names separated by a space as shown in the following example\.

   If your domain is not configured to route traffic to the public IP address of your instance, the `bncert` tool will ask you to make that configuration before continuing\. Your domain must be routing traffic to the public IP address of the instance from which you are using the `bncert` tool to enable HTTPS on the instance\. This confirms that you own the domain, and serves as the validation for your certificate\.  
![\[Entering the primary and alternate domain names\]](https://d9yljz1nd5001.cloudfront.net/en_us/a825044edce3b3cf14c8cdbea7367d2e/images/bncert-domain-names.png)

1. The `bncert` tool will ask you how you want your website's redirection to be configured\. These are the options available: 
   + **Enable HTTP to HTTPS redirection** \- Specifies whether users who browse to the HTTP version of your website \(i\.e\., `http:/example.com`\) are automatically redirected to the HTTPS version \(i\.e\., `https://example.com`\)\. We recommend enabling this option because it forces all visitors to use the encrypted connection\. Type `Y` and press **Enter** to enable it\.
   + **Enable non\-www to www redirection** \- Specifies whether users who browse to the apex of your domain \(i\.e\., `https://example.com`\) are automatically redirected to your domain's `www` subdomain \(i\.e\., `https://www.example.com`\)\. We recommend enabling this option\. However, you may want to disable it and enable the alternate option \(enable `www` to non\-`www` redirection\) if you have specified the apex of your domain as your preferred website address in search engine tools like Google's webmaster tools, or if your apex points directly to your IP and your `www` subdomain references your apex via a CNAME record\. Type `Y` and press **Enter** to enable it\.
   + **Enable www to non\-www redirection** \- Specifies whether users who browse to your domain's `www` subdomain \(i\.e\., `https://www.example.com`\) are automatically redirected to the apex of your domain \(i\.e\., `https://example.com`\)\. We recommend disabling this, if you enabled non\-`www` redirection to `www`\. Type `N` and press **Enter** to disable it\.

   Your selections should look like the following example\.  
![\[Website redirection options\]](https://d9yljz1nd5001.cloudfront.net/en_us/a825044edce3b3cf14c8cdbea7367d2e/images/bncert-enable-disable-redirection.png)

1. The changes that are going to be made are listed\. Type `Y` and press **Enter** to confirm and continue\.  
![\[Confirming the changes\]](https://d9yljz1nd5001.cloudfront.net/en_us/a825044edce3b3cf14c8cdbea7367d2e/images/bncert-confirm-changes.png)

1. Enter your email address to associate with your Let's Encrypt certificate and press **Enter**\.  
![\[Associating your email address with your Let's Encrypt certificate\]](https://d9yljz1nd5001.cloudfront.net/en_us/a825044edce3b3cf14c8cdbea7367d2e/images/bncert-email-address.png)

1. Review the Let's Encrypt Subscriber Agreement\. Type `Y` and press **Enter** to accept the agreement and continue\.  
![\[Review the Let's Encrypt subscriber agreement\]](https://d9yljz1nd5001.cloudfront.net/en_us/a825044edce3b3cf14c8cdbea7367d2e/images/bncert-lets-ecrypt-agreement.png)

   The actions are performed to enable HTTPS on your instance, including requesting the certificate and configuring the redirections you specified\.  
![\[Actions being performed\]](https://d9yljz1nd5001.cloudfront.net/en_us/a825044edce3b3cf14c8cdbea7367d2e/images/bncert-performing-actions.png)

   Your certificate is successfully issued and validated, and the redirections are successfully configured on your instance if you see a message similar to the following example\.  
![\[Actions successfully completed\]](https://d9yljz1nd5001.cloudfront.net/en_us/a825044edce3b3cf14c8cdbea7367d2e/images/bncert-success-conf.png)

   The `bncert` tool will perform an automatic renewal of your certificate every 80 days before it expires\. Repeat the above steps if you wish to use additional domains and subdomains with your instance, and you want to enable HTTPS for those domains\.

   You are now done enabling HTTPS on your WordPress instance\. Continue to the [Step 6: Test that your website is using HTTPS](#test-https-on-your-website) section of this guide\.

## Step 6: Test that your website is using HTTPS<a name="test-https-on-your-website"></a>

After you enable HTTPS on your WordPress instance, you should confirm that your website is using HTTPS by browsing to all of the domains that you specified when using the `bncert` tool\. When you visit each domain, you should see that they use a secure connection as shown in the following example\.

**Note**  
You might have to refresh, and clear your browser's cache to see the change\.

![\[Secured website confirmation\]](https://d9yljz1nd5001.cloudfront.net/en_us/a825044edce3b3cf14c8cdbea7367d2e/images/bncert-secured-website.png)

You might also notice that the non\-`www` address redirects to the `www` subdomain of your domain, or vice versa depending on the option you selected when running the `bncert` tool\.