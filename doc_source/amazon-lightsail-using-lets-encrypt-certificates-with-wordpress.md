# Tutorial: Using Let’s Encrypt SSL certificates with your WordPress instance in Amazon Lightsail<a name="amazon-lightsail-using-lets-encrypt-certificates-with-wordpress"></a>

 *Last updated: June 7, 2019* 

Amazon Lightsail makes it easy to secure your websites and applications with SSL/TLS using Lightsail load balancers\. However, using a Lightsail load balancer might not generally be the right choice\. Perhaps your site doesn't need the scalability or fault tolerance load balancers provide, or maybe you're optimizing for cost\.

In the latter case, you might consider using Let's Encrypt to obtain a free SSL certificate\. If so, that's no problem\. You can integrate those certificates with Lightsail instances\. This tutorial shows you how to request a Let’s Encrypt wildcard certificate using Certbot, and integrate it with your WordPress instance using the Really Simple SSL plugin\.

**Note**  
To learn more about SSL/TLS certificates in Lightsail, see [SSL/TLS certificates in Lightsail](understanding-tls-ssl-certificates-in-lightsail-https.md)\.

**Contents**
+ [Step 1: Complete the prerequisites](#complete-the-prerequisites-lets-encrypt-wordpress)
+ [Step 2: Install Certbot on your Lightsail instance](#install-certbot-on-your-instance-wordpress)
+ [Step 3: Request a Let’s Encrypt SSL wildcard certificate](#request-a-lets-encrypt-certificate-wordpress)
+ [Step 4: Add TXT records to your domain’s DNS zone in Lightsail](#add-a-text-record-to-your-domains-dns-zone-lets-encrypt-wordpress)
+ [Step 5: Confirm that the TXT records have propagated](#confirm-the-text-records-have-propagated-lets-encrypt-wordpress)
+ [Step 6: Complete the Let’s Encrypt SSL certificate request](#complete-the-lets-encrypt-certificate-request-wordpress)
+ [Step 7: Create links to the Let’s Encrypt certificate files in the Apache server directory](#link-the-lets-encrypt-certificate-files-in-the-apache-directory-wordpress)
+ [Step 8: Integrate the SSL certificate with your WordPress site using the Really Simple SSL plugin](#integrate-certificates-with-wordpress-using-really-simple-ssl-plugin)
+ [Step 9: Renew the Let's Encrypt certificates every 90 days](#renew-a-lets-encrypt-certificate-wordpress)

## Step 1: Complete the prerequisites<a name="complete-the-prerequisites-lets-encrypt-wordpress"></a>

Complete the following prerequisites if you haven’t already done so:
+ Create a WordPress instance in Lightsail\. To learn more, see [Create an Amazon Lightsail instance](how-to-create-amazon-lightsail-instance-virtual-private-server-vps.md)\.
+ Register a domain name, and get administrative access to edit its DNS records\. To learn more, see [DNS in Amazon Lightsail](understanding-dns-in-amazon-lightsail.md)\.
**Note**  
We recommend that you manage your domain’s DNS records using a Lightsail DNS zone\. To learn more, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)\.
+ Use the browser\-based SSH terminal in the Lightsail console to perform the steps in this tutorial\. However, you can also use your own SSH client, such as PuTTY\. To learn more about configuring PuTTY, see [Download and set up PuTTY to connect using SSH in Amazon Lightsail](lightsail-how-to-set-up-putty-to-connect-using-ssh.md)\.

After you've completed the prerequisites, continue to the [next section](#install-certbot-on-your-instance-wordpress) of this tutorial\.

## Step 2: Install Certbot on your Lightsail instance<a name="install-certbot-on-your-instance-wordpress"></a>

Certbot is a client used to request a certificate from Let’s Encrypt and deploy it to a web server\. Let's Encrypt uses the ACME protocol to issue certificates, and Certbot is an ACME\-enabled client that interacts with Let's Encrypt\.

**To install Certbot on your Lightsail instance**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the SSH quick connect icon for the instance that you want to connect to\.  
![\[SSH quick connect on the Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wordpress-ssh-quick-connect.png)

1. After your Lightsail browser\-based SSH session is connected, enter the following command to update the packages on your instance:

   ```
   sudo apt-get update
   ```  
![\[Update the packages on your instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wordpress-ssh-lets-encrypt-update-packages.png)

1. Enter the following command to install the software properties package\. Certbot’s developers use a Personal Package Archive \(PPA\) to distribute Certbot\. The software properties package makes it more efficient to work with PPAs\.

   ```
   sudo apt-get install software-properties-common
   ```
**Note**  
If you encounter a `Could not get lock` error when running the `sudo apt-get install` command, please wait approximately 15 minutes and try again\. This error may be caused by a cron job that is using the Apt package management tool to install unattended upgrades\.

1. Enter the following command to add Certbot to the local apt repository:

   ```
   sudo apt-add-repository ppa:certbot/certbot -y
   ```

1. Enter the following command to update apt to include the new repository:

   ```
   sudo apt-get update -y
   ```

1. Enter the following command to install Certbot:

   ```
   sudo apt-get install certbot -y
   ```

   Certbot is now installed on your Lightsail instance\.

1. Keep the browser\-based SSH terminal window open—you return to it later in this tutorial\. Continue to the [next section](#request-a-lets-encrypt-certificate-wordpress) of this tutorial\.

## Step 3: Request a Let’s Encrypt SSL wildcard certificate<a name="request-a-lets-encrypt-certificate-wordpress"></a>

Begin the process of requesting a certificate from Let’s Encrypt\. Using Certbot, request a wildcard certificate, which lets you use a single certificate for a domain and its subdomains\. For example, a single wildcard certificate works for the `example.com` top\-level domain, and the `blog.example.com`, and `stuff.example.com` subdomains\.

**To request a Let’s Encrypt SSL wildcard certificate**

1. In the same browser\-based SSH terminal window used in [step 2](#install-certbot-on-your-instance-wordpress) of this tutorial, enter the following commands to set an environment variable for your domain\. You can now more efficiently copy and paste commands to obtain the certificate\. Be sure to replace `domain` with the name of your registered domain\.

   ```
   DOMAIN=domain
   ```

   ```
   WILDCARD=*.$DOMAIN
   ```

   Example:

   ```
   DOMAIN=example.com
   ```

   ```
   WILDCARD=*.$DOMAIN
   ```

1. Enter the following command to confirm the variables return the correct values:

   ```
   echo $DOMAIN && echo $WILDCARD
   ```

   You should see a result similar to the following:  
![\[Confirm the the domain environment variables.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ssh-lets-encrypt-confirm-variables.png)

1. Enter the following command to start Certbot in interactive mode\. This command tells Certbot to use a manual authorization method with DNS challenges to verify domain ownership\. It requests a wildcard certificate for your top\-level domain, as well as its subdomains\.

   ```
   sudo certbot -d $DOMAIN -d $WILDCARD --manual --preferred-challenges dns certonly
   ```

1. Enter your email address when prompted, because it’s used for renewal and security notices\.

1. Read the Let’s Encrypt terms of service\. When done, press A if you agree\. If you disagree, you cannot obtain a Let’s Encrypt certificate\.

1. Respond accordingly to the prompt to share your email address and to the warning about your IP address being logged\.

1. Let’s Encrypt now prompts you to verify that you own the domain specified\. You do this by adding TXT records to the DNS records for your domain\. A set of TXT record values are provided as shown in the following example:
**Note**  
Let's Encrypt may provide a single or multiple TXT records that you must use for verification\. In this example, we were provided with two TXT records to use for verification\.  
![\[TXT records for Let's Encrypt certificates.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ssh-lets-encrypt-text-records.png)

1. Keep the Lightsail browser\-based SSH session open—you return to it later in this tutorial\. Continue to the [next section](#add-a-text-record-to-your-domains-dns-zone-lets-encrypt-wordpress) of this tutorial\.

## Step 4: Add TXT records to your domain’s DNS zone in Lightsail<a name="add-a-text-record-to-your-domains-dns-zone-lets-encrypt-wordpress"></a>

Adding a TXT record to your domain’s DNS zone verifies that you own the domain\. For demonstration purposes, we use the Lightsail DNS zone\. However, the steps might be similar for other DNS zones typically hosted by domain registrars\.

**Note**  
To learn more about how to create a Lightsail DNS zone for your domain, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)\.

**To add TXT records to your domain’s DNS zone in Lightsail**

1. On the Lightsail home page, choose the **Networking** tab\.

1. Under the **DNS zones** section of the page, choose the DNS Zone for the domain that you specified in the Certbot certificate request\.

1. In the DNS zone editor, choose **Add record**\.  
![\[DNS zone editor in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-dns-zone-editor.png)

1. In the record type drop\-down menu, choose **TXT record**\.

1. Enter the values specified by the Let’s Encrypt certificate request into the **Subdomain** and **Responds with** fields as shown in the following screenshot\.  
![\[TXT records in the Lightsail DNS zone editor.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-dns-zone-editor-text-records.png)

1. Choose the Save icon\.

1. Repeat steps 3 through 6 to add the second set of TXT records specified by the Let’s Encrypt certificate request\.

1. Keep the Lightsail console browser window open—you return to it later in this tutorial\. Continue to the [next section](#confirm-the-text-records-have-propagated-lets-encrypt-wordpress) of this tutorial\.

## Step 5: Confirm that the TXT records have propagated<a name="confirm-the-text-records-have-propagated-lets-encrypt-wordpress"></a>

Use the MxToolbox utility to confirm that the TXT records have propagated to the internet’s DNS\. DNS record propagation might take a while depending on your DNS hosting provider, and the configured time to live \(TTL\) for your DNS records\. It is important that you complete this step, and confirm that your TXT records have propagated, before continuing your Certbot certificate request\. Otherwise, your certificate request fails\.

**To confirm the TXT records have propagated to the internet’s DNS**

1. Open a new browser window and go to [https://mxtoolbox\.com/TXTLookup\.aspx](https://mxtoolbox.com/TXTLookup.aspx)\.

1. Enter the following text into the text box\. Be sure to replace `domain` with your domain\.

   ```
   _acme-challenge.domain
   ```

   Example:

   ```
   _acme-challenge.example.com
   ```  
![\[MXTookbox TXT record lookup.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-mxtoobox-text-record-lookup.png)

1. Choose **TXT Lookup** to run the check\.

1. One of the following responses occurs:
   + If your TXT records have propagated to the internet’s DNS, you see a response similar to the one shown in the following screenshot\. Close the browser window and continue to the [next section](#complete-the-lets-encrypt-certificate-request-wordpress) of this tutorial\.  
![\[Confirmation that TXT records propagated.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-mxtoobox-propagated-text-record-lookup.png)
   + If your TXT records have not propagated to the internet’s DNS, you see a **DNS Record not found** response\. Confirm that you added the correct DNS records to your domains’ DNS zone\. If you added the correct records, wait a while longer to let your domain’s DNS records propagate, and run the TXT lookup again\.

## Step 6: Complete the Let’s Encrypt SSL certificate request<a name="complete-the-lets-encrypt-certificate-request-wordpress"></a>

Go back to the Lightsail browser\-based SSH session for your WordPress instance and complete the Let’s Encrypt certificate request\. Certbot saves your SSL certificate, chain, and key files to a specific directory on your WordPress instance\.

**To complete the Let’s Encrypt SSL certificate request**

1. In the Lightsail browser\-based SSH session for your WordPress instance, press **Enter** to continue your Let’s Encrypt SSL certificate request\. If successful, a response similar to the one shown in the following screenshot appears:  
![\[Successful Let's Encrypt cretificate request.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ssh-lets-encrypt-request-success.png)

   The message confirms that your certificate, chain, and key files are stored in the `/etc/letsencrypt/live/domain/` directory\. Make sure to replace `domain` with your domain, such as `/etc/letsencrypt/live/example.com/`\.

1. Make note of the expiration date specified in the message\. You use it to renew your certificate by that date\.  
![\[Let's Encrypt certificate renewal date.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ssh-lets-encrypt-renewal-date.png)

1. Now that you have the Let’s Encrypt SSL certificate, continue to the [next section](#link-the-lets-encrypt-certificate-files-in-the-apache-directory-wordpress) of this tutorial\.

## Step 7: Create links to the Let’s Encrypt certificate files in the Apache server directory<a name="link-the-lets-encrypt-certificate-files-in-the-apache-directory-wordpress"></a>

Create links to the Let’s Encrypt SSL certificate files in the Apache server directory on your WordPress instance\. Also, back up your existing certificates, in case you need them later\.

**To create links to the Let’s Encrypt certificate files in the Apache server directory**

1. In the Lightsail browser\-based SSH session for your WordPress instance, enter the following command to stop the underlying services:

   ```
   sudo /opt/bitnami/ctlscript.sh stop
   ```

   You should see a response similar to the following:  
![\[Instance services stopped.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ssh-stop-services.png)

1. Enter the following command to set an environment variable for your domain\. You can more efficiently copy and paste commands to link the certificate files\. Be sure to replace `domain` with the name of your registered domain name\.

   ```
   DOMAIN=domain
   ```

   Example:

   ```
   DOMAIN=example.com
   ```

1. Enter the following command to confirm the variables return the correct values:

   ```
   echo $DOMAIN
   ```

   You should see a result similar to the following:  
![\[Confirm the the domain environment variable.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ssh-lets-encrypt-confirm-domain-variable.png)

1. Enter the following commands individually to rename your existing certificate files as backups, if any:

   ```
   sudo mv /opt/bitnami/apache2/conf/server.crt /opt/bitnami/apache2/conf/server.crt.old
   ```

   ```
   sudo mv /opt/bitnami/apache2/conf/server.key /opt/bitnami/apache2/conf/server.key.old
   ```

   ```
   sudo mv /opt/bitnami/apache2/conf/server.csr /opt/bitnami/apache2/conf/server.csr.old
   ```

1. Enter the following commands individually to create links to your Let’s Encrypt certificate files in the Apache directory:

   ```
   sudo ln -s /etc/letsencrypt/live/$DOMAIN/privkey.pem /opt/bitnami/apache2/conf/server.key
   ```

   ```
   sudo ln -s /etc/letsencrypt/live/$DOMAIN/fullchain.pem /opt/bitnami/apache2/conf/server.crt
   ```

1. Enter the following command to start the underlying services that you had stopped earlier:

   ```
   sudo /opt/bitnami/ctlscript.sh start
   ```

   You should see a result similar to the following:  
![\[Instance services started.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ssh-start-services.png)

   The SSL certificate files for your WordPress instance are now in the correct directory\.

1. Continue to the [next section](#integrate-certificates-with-wordpress-using-really-simple-ssl-plugin) of this tutorial\.

## Step 8: Integrate the SSL certificate with your WordPress site using the Really Simple SSL plugin<a name="integrate-certificates-with-wordpress-using-really-simple-ssl-plugin"></a>

Install the Really Simple SSL plugin to your WordPress site, and use it to integrate the SSL certificate\. Really Simple SSL also configures HTTP to HTTPS redirection to ensure that users who visit your site are always on the HTTPS connection\.

**To integrate the SSL certificate with your WordPress site using the Really Simple SSL plugin**

1. In the Lightsail browser\-based SSH session for your WordPress instance, enter the following command to set your wp\-config\.php file to be writeable\. The Really Simple SSL plugin will write to the wp\-config\.php file to configure your certificates\.

   ```
   sudo chmod 666 /opt/bitnami/apps/wordpress/htdocs/wp-config.php
   ```

1. Open a new browser window and sign in to the administration dashboard of your WordPress instance\.
**Note**  
For more information, see [Getting the application user name and password for your 'Certified by Bitnami' instance in Amazon Lightsail](log-in-to-your-bitnami-application-running-on-amazon-lightsail.md)\.

1. Choose **Plugins** from the left navigation pane\.

1. Choose **Add New** from the top of the Plugins page\.  
![\[Add a new plugin in WordPress.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wordpress-add-new-plugin.png)

1. Search for **Really Simple SSL**\.

1. Choose **Install Now** next to the Really Simple SSL plugin in the search results\.  
![\[The Really Simple SSL plugin for WordPress.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wordpress-really-simple-ssl-plugin.png)

1. After it’s done installing, choose **Activate**\.

1. In the prompt that appears, choose **Go ahead, activate SSL\!** You may be redirected to the sign in page for the administration dashboard of your WordPress instance\.

   Your WordPress instance is now configured to use SSL encryption\. Additionally, your WordPress instance is now configured to automatically redirect connections from HTTP to HTTPS\. When a visitor goes to `http://example.com`, they are automatically redirected to the encrypted HTTPS connection \(i\.e\., `https://example.com`\)\.

## Step 9: Renew the Let's Encrypt certificates every 90 days<a name="renew-a-lets-encrypt-certificate-wordpress"></a>

Let’s Encrypt certificates are valid for 90 days\. Certificates can be renewed 30 days before they expire\. To renew the Let's Encrypt certificates, run the original command used to obtain them\. Repeat the steps in the [Request a Let’s Encrypt SSL wildcard certificate](#request-a-lets-encrypt-certificate-wordpress) section of this tutorial\.