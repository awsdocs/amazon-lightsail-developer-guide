# Tutorial: Using Let’s Encrypt SSL certificates with your LAMP instance in Amazon Lightsail<a name="amazon-lightsail-using-lets-encrypt-certificates-with-lamp"></a>

 *Last updated: June 7, 2019* 

Amazon Lightsail makes it easy to secure your websites and applications with SSL/TLS using Lightsail load balancers\. However, using a Lightsail load balancer might not generally be the right choice\. Perhaps your site doesn't need the scalability or fault tolerance load balancers provide, or maybe you're optimizing for cost\.

In the latter case, you might consider using Let's Encrypt to obtain a free SSL certificate\. If so, that's no problem\. You can integrate those certificates with Lightsail instances\. This tutorial shows you how to request a Let’s Encrypt wildcard certificate using Certbot, and integrate it with your LAMP instance\.

**Note**  
To learn more about SSL/TLS certificates in Lightsail, see [SSL/TLS certificates in Lightsail](understanding-tls-ssl-certificates-in-lightsail-https.md)\.

**Contents**
+ [Step 1: Complete the prerequisites](#complete-the-prerequisites-lets-encrypt-lamp)
+ [Step 2: Install Certbot on your Lightsail instance](#install-certbot-on-your-instance-lamp)
+ [Step 3: Request a Let’s Encrypt SSL wildcard certificate](#request-a-lets-encrypt-certificate-lamp)
+ [Step 4: Add TXT records to your domain’s DNS zone in Lightsail](#add-a-text-record-to-your-domains-dns-zone-lets-encrypt-lamp)
+ [Step 5: Confirm that the TXT records have propagated](#confirm-the-text-records-have-propagated-lets-encrypt-lamp)
+ [Step 6: Complete the Let’s Encrypt SSL certificate request](#complete-the-lets-encrypt-certificate-request-lamp)
+ [Step 7: Create links to the Let’s Encrypt certificate files in the Apache server directory](#link-the-lets-encrypt-certificate-files-in-the-apache-directory-lamp)
+ [Step 8: Configure HTTP to HTTPS redirection for your web application](#configure-http-to-https-redirection-lamp)
+ [Step 9: Renew the Let's Encrypt certificates every 90 days](#renew-a-lets-encrypt-certificate-lamp)

## Step 1: Complete the prerequisites<a name="complete-the-prerequisites-lets-encrypt-lamp"></a>

Complete the following prerequisites if you haven’t already done so:
+ Create a LAMP instance in Lightsail\. To learn more, see [Create an Amazon Lightsail instance](how-to-create-amazon-lightsail-instance-virtual-private-server-vps.md)\.
+ Register a domain name, and get administrative access to edit its DNS records\. To learn more, see [DNS in Amazon Lightsail](understanding-dns-in-amazon-lightsail.md)\.
**Note**  
We recommend that you manage your domain’s DNS records using a Lightsail DNS zone\. To learn more, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)\.
+ Use the browser\-based SSH terminal in the Lightsail console to perform the steps in this tutorial\. However, you can also use your own SSH client, such as PuTTY\. To learn more about configuring PuTTY, see [Download and set up PuTTY to connect using SSH in Amazon Lightsail](lightsail-how-to-set-up-putty-to-connect-using-ssh.md)\.

After you've completed the prerequisites, continue to the [next section](#install-certbot-on-your-instance-lamp) of this tutorial\.

## Step 2: Install Certbot on your Lightsail instance<a name="install-certbot-on-your-instance-lamp"></a>

Certbot is a client used to request a certificate from Let’s Encrypt and deploy it to a web server\. Let's Encrypt uses the ACME protocol to issue certificates, and Certbot is an ACME\-enabled client that interacts with Let's Encrypt\.

**To install Certbot on your Lightsail instance**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the SSH quick connect icon for the instance that you want to connect to\.  
![\[SSH quick connect on the Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-lamp-ssh-quick-connect.png)

1. After your Lightsail browser\-based SSH session is connected, enter the following command to update the packages on your instance:

   ```
   sudo apt-get update
   ```  
![\[Update the packages on your instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-lamp-ssh-lets-encrypt-update-packages.png)

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

1. Keep the browser\-based SSH terminal window open—you return to it later in this tutorial\. Continue to the [next section](#request-a-lets-encrypt-certificate-lamp) of this tutorial\.

## Step 3: Request a Let’s Encrypt SSL wildcard certificate<a name="request-a-lets-encrypt-certificate-lamp"></a>

Begin the process of requesting a certificate from Let’s Encrypt\. Using Certbot, request a wildcard certificate, which lets you use a single certificate for a domain and its subdomains\. For example, a single wildcard certificate works for the `example.com` top\-level domain, and the `blog.example.com`, and `stuff.example.com` subdomains\.

**To request a Let’s Encrypt SSL wildcard certificate**

1. In the same browser\-based SSH terminal window used in [step 2](#install-certbot-on-your-instance-lamp) of this tutorial, enter the following commands to set an environment variable for your domain\. You can now more efficiently copy and paste commands to obtain the certificate\.

   ```
   DOMAIN=Domain
   ```

   ```
   WILDCARD=*.$DOMAIN
   ```

   In the command, replace *Domain* with your registered domain name\.

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

1. Keep the Lightsail browser\-based SSH session open—you return to it later in this tutorial\. Continue to the [next section](#add-a-text-record-to-your-domains-dns-zone-lets-encrypt-lamp) of this tutorial\.

## Step 4: Add TXT records to your domain’s DNS zone in Lightsail<a name="add-a-text-record-to-your-domains-dns-zone-lets-encrypt-lamp"></a>

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

1. Keep the Lightsail console browser window open—you return to it later in this tutorial\. Continue to the [next section](#confirm-the-text-records-have-propagated-lets-encrypt-lamp) of this tutorial\.

## Step 5: Confirm that the TXT records have propagated<a name="confirm-the-text-records-have-propagated-lets-encrypt-lamp"></a>

Use the MxToolbox utility to confirm that the TXT records have propagated to the internet’s DNS\. DNS record propagation might take a while depending on your DNS hosting provider, and the configured time to live \(TTL\) for your DNS records\. It is important that you complete this step, and confirm that your TXT records have propagated, before continuing your Certbot certificate request\. Otherwise, your certificate request fails\.

**To confirm the TXT records have propagated to the internet’s DNS**

1. Open a new browser window and go to [https://mxtoolbox\.com/TXTLookup\.aspx](https://mxtoolbox.com/TXTLookup.aspx)\.

1. Enter the following text into the text box\.

   ```
   _acme-challenge.Domain
   ```

   Replace *Domain* with your registered domain name\.

   Example:

   ```
   _acme-challenge.example.com
   ```  
![\[MXTookbox TXT record lookup.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-mxtoobox-text-record-lookup.png)

1. Choose **TXT Lookup** to run the check\.

1. One of the following responses occurs:
   + If your TXT records have propagated to the internet’s DNS, you see a response similar to the one shown in the following screenshot\. Close the browser window and continue to the [next section](#complete-the-lets-encrypt-certificate-request-lamp) of this tutorial\.  
![\[Confirmation that TXT records propagated.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-mxtoobox-propagated-text-record-lookup.png)
   + If your TXT records have not propagated to the internet’s DNS, you see a **DNS Record not found** response\. Confirm that you added the correct DNS records to your domains’ DNS zone\. If you added the correct records, wait a while longer to let your domain’s DNS records propagate, and run the TXT lookup again\.

## Step 6: Complete the Let’s Encrypt SSL certificate request<a name="complete-the-lets-encrypt-certificate-request-lamp"></a>

Go back to the Lightsail browser\-based SSH session for your LAMP instance and complete the Let’s Encrypt certificate request\. Certbot saves your SSL certificate, chain, and key files to a specific directory on your LAMP instance\.

**To complete the Let’s Encrypt SSL certificate request**

1. In the Lightsail browser\-based SSH session for your LAMP instance, press **Enter** to continue your Let’s Encrypt SSL certificate request\. If successful, a response similar to the one shown in the following screenshot appears:  
![\[Successful Let's Encrypt cretificate request.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ssh-lets-encrypt-request-success.png)

   The message confirms that your certificate, chain, and key files are stored in the `/etc/letsencrypt/live/Domain/` directory\. *Domain* will be your registed domain name, such as `/etc/letsencrypt/live/example.com/`\.

1. Make note of the expiration date specified in the message\. You use it to renew your certificate by that date\.  
![\[Let's Encrypt certificate renewal date.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ssh-lets-encrypt-renewal-date.png)

1. Now that you have the Let’s Encrypt SSL certificate, continue to the [next section](#link-the-lets-encrypt-certificate-files-in-the-apache-directory-lamp) of this tutorial\.

## Step 7: Create links to the Let’s Encrypt certificate files in the Apache server directory<a name="link-the-lets-encrypt-certificate-files-in-the-apache-directory-lamp"></a>

Create links to tbe Let’s Encrypt SSL certificate files in the Apache server directory on your LAMP instance\. Also, back up your existing certificates, in case you need them later\.

**To create links to the Let’s Encrypt certificate files in the Apache server directory**

1. In the Lightsail browser\-based SSH session for your LAMP instance, enter the following command to stop the underlying LAMP stack services:

   ```
   sudo /opt/bitnami/ctlscript.sh stop
   ```

   You should see a response similar to the following:  
![\[Instance services stopped.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ssh-stop-services.png)

1. Enter the following command to set an environment variable for your domain\.

   ```
   DOMAIN=Domain
   ```

   In the command, replace *Domain* with your registered domain name\.

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

1. Enter the following command to start the underlying LAMP stack services that you had stopped earlier:

   ```
   sudo /opt/bitnami/ctlscript.sh start
   ```

   You should see a result similar to the following:  
![\[Instance services started.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ssh-start-services.png)

   Your LAMP instance is now configured to use SSL encryption\. However, traffic is not automatically redirected from HTTP to HTTPS\.

1. Continue to the [next section](#configure-http-to-https-redirection-lamp) of this tutorial\.

## Step 8: Configure HTTP to HTTPS redirection for your web application<a name="configure-http-to-https-redirection-lamp"></a>

You can configure an HTTP to HTTPS redirect for your LAMP instance\. Automatically redirecting from HTTP to HTTPS makes your site accessible only by your customers using SSL, even when they connect using HTTP\.

**To configure HTTP to HTTPS redirection for your web application**

1. In the Lightsail browser\-based SSH session for your LAMP instance, enter the following command to edit the Apache web server configuration file using the Vim text editor:

   ```
   sudo vim /opt/bitnami/apache2/conf/bitnami/bitnami.conf
   ```
**Note**  
This tutorial uses Vim for demonstration purposes; however, you can use any text editor of your choice for this step\.

1. Press `i` to enter insert mode in the Vim editor\.

1. In the file, enter the following text between `DocumentRoot "/opt/bitnami/apache2/htdocs"` and `<Directory "/opt/bitnami/apache2/htdocs">`:

   ```
   RewriteEngine On
   RewriteCond %{HTTPS} !=on
   RewriteRule ^/(.*) https://%{SERVER_NAME}/$1 [R,L]
   ```

   The result should look like the following:  
![\[Apache configuration file edited for HTTP to HTTPs redirection.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-lamp-ssh-lets-encrypt-apache-config-file.png)

1. Press the **ESC** key, and then enter `:wq` to write \(save\) your edits, and quit Vim\.

1. Enter the following command to restart the underlying LAMP stack services and make your edits effective:

   ```
   sudo /opt/bitnami/ctlscript.sh restart
   ```

   Your LAMP instance is now configured to automatically redirect connections from HTTP to HTTPS\. When a visitor goes to `http://www.example.com`, they are automatically redirected to the encrypted `https://www.example.com` address\.

## Step 9: Renew the Let's Encrypt certificates every 90 days<a name="renew-a-lets-encrypt-certificate-lamp"></a>

Let’s Encrypt certificates are valid for 90 days\. Certificates can be renewed 30 days before they expire\. To renew the Let's Encrypt certificates, run the original command used to obtain them\. Repeat the steps in the [Request a Let’s Encrypt SSL wildcard certificate](#request-a-lets-encrypt-certificate-lamp) section of this tutorial\.