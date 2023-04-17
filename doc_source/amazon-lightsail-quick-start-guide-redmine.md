# Quick start guide: Redmine on Amazon Lightsail<a name="amazon-lightsail-quick-start-guide-redmine"></a>

 *Last updated: December 8, 2022* 

Here are a few steps you should take to get started after your Redmine instance is up and running on Amazon Lightsail:

**Contents**
+ [Step 1: Read the Bitnami documentation](#amazon-lightsail-read-the-bitnami-documentation-redmine)
+ [Step 2: Get the default application password to access the Redmine administration dashboard](#amazon-lightsail-get-the-default-user-password-redmine)
+ [Step 3: Attach a static IP address to your instance](#amazon-lightsail-attach-static-ip-redmine)
+ [Step 4: Sign in to the administration dashboard of your Redmine website](#amazon-lightsail-sign-in-redmine)
+ [Step 5: Route traffic for your registered domain name to your Redmine website](#amazon-lightsail-map-your-domain-to-your-instance-redmine)
+ [Step 6: Configure HTTPS for your Redmine website](#amazon-lightsail-https-redmine)
+ [Step 7: Read the Redmine documentation and continue configuring your website](#amazon-lightsail-read-documentation-redmine)
+ [Step 8: Create a snapshot of your instance](#amazon-lightsail-create-a-snapshot-redmine)

## Step 1: Read the Bitnami documentation<a name="amazon-lightsail-read-the-bitnami-documentation-redmine"></a>

Read the Bitnami documentation to learn how to configure your Redmine application\. For more information, see the [Redmine Packaged By Bitnami For AWS Cloud](https://docs.bitnami.com/aws/apps/redmine/)\.

## Step 2: Get the default application password to access the Redmine administration dashboard<a name="amazon-lightsail-get-the-default-user-password-redmine"></a>

Complete the following procedure to get the default application password required to access the administration dashboard for your Redmine website\. For more information, see [Getting the application user name and password for your Bitnami instance in Amazon Lightsail](log-in-to-your-bitnami-application-running-on-amazon-lightsail.md)\.

1. On your instance management page, under the **Connect** tab, choose **Connect using SSH**\.  
![\[Connect using SSH in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-connect-to-your-instance.png)

1. After you're connected, enter the following command to get the application password:

   ```
   cat $HOME/bitnami_application_password
   ```

   You should see a response similar to the following example, which contains the default application password:  
![\[Bitnami default application password.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-bitnami-application-password.png)

## Step 3: Attach a static IP address to your instance<a name="amazon-lightsail-attach-static-ip-redmine"></a>

The public IP address assigned to your instance when you first create it will change every time you stop and start your instance\. You should create and attach a static IP address to your instance to ensure its public IP address doesn't change\. Later, when you use a registered domain name, such as `example.com`, with your instance, you don’t have to update your domain’s DNS records every time you stop and start your instance\. You can attach one static IP to an instance\.

On the instance management page, under the **Networking** tab, choose **Create a static IP** or **Attach static IP** \(if you previously created a static IP that you can attach to your instance\), then follow the instructions on the page\. For more information, see [Create a static IP and attach it to an instance in Amazon Lightsail](lightsail-create-static-ip.md)\.

![\[Attach static IP address in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-static-ip-address.png)

## Step 4: Sign in to the administration dashboard of your Redmine website<a name="amazon-lightsail-sign-in-redmine"></a>

Now that you have the default application password, complete the following procedure to navigate to your Redmine website's home page, and sign in to the administration dashboard\. After you’re signed in, you can start customizing your website and making administrative changes\. For more information about what you can do in Joomla\!, see the [Step 7: Read the Redmine documentation and continue configuring your website](#amazon-lightsail-read-documentation-redmine) section later in this guide\.

1. On your instance management page, under the **Connect** tab, make note of the public IP address of your instance\. The public IP address is also displayed in the header section of your instance management page\.  
![\[Public IP address of an instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-public-ip.png)

1. Browse to the public IP address of your instance, for example by going to `http://203.0.113.0`\.

   The home page of your Redmine website should appear\.

1. Choose **Manage** in the bottom right corner of your Redmine website home page\.

   If the **Manage** banner is not shown, you can reach the sign in page by browsing to `http://<PublicIP>/admin`\. Replace `<PublicIP>` with the public IP address of your instance\.

1. Sign in using the default user name \(`user`\) and the default password retrieved earlier in this guide\.

   The Redmine administration dashboard appears\.  
![\[The Redmine administration dashboard\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-redmine-dashboard.png)

## Step 5: Route traffic for your registered domain name to your Redmine website<a name="amazon-lightsail-map-your-domain-to-your-instance-redmine"></a>

To route traffic for your registered domain name, such as `example.com`, to your Redmine website, you add a record to the DNS of your domain\. DNS records are typically managed and hosted at the registrar where you registered your domain\. However, we recommend that you transfer management of your domain's DNS records to Lightsail so that you can administer it using the Lightsail console\.

On the Lightsail console home page, under the **Domains & DNS** tab, choose **Create DNS zone**, then follow the instructions on the page\. For more information, see [Creating a DNS zone to manage your domain’s DNS records in Lightsail](lightsail-how-to-create-dns-entry.md)\.

If you browse to the domain name that you configured for your instance, you should be redirected to the home page of your Redmine website\. Next, you should generate and configure an SSL/TLS certificate to enable HTTPS connections for your Redmine website\. For more information, continue to the next [Step 6: Configure HTTPS for your Redmine website](#amazon-lightsail-https-redmine) section of this guide\.

## Step 6: Configure HTTPS for your Redmine website<a name="amazon-lightsail-https-redmine"></a>

Complete the following procedure to configure HTTPS on your Redmine website\. These steps show you how to use the Bitnami HTTPS Configuration Tool \(`bncert-tool`\), which is a command line tool for requesting Let's Encrypt SSL/TLS certificates\. For more information see [Learn About The Bitnami HTTPS Configuration Tool](https://docs.bitnami.com/aws/how-to/understand-bncert/) in the *Bitnami documentation*\.

**Important**  
Before starting with this procedure, make sure that you configured your domain to route traffic to your Redmine instance\. Otherwise, the SSL/TLS certificate validation process will fail\.

1. On your instance management page, under the **Connect** tab, choose **Connect using SSH**\.  
![\[Connect using SSH in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-connect-to-your-instance.png)

1. After you're connected, enter the following command to confirm the bncert tool is installed on your instance\.

   ```
   sudo /opt/bitnami/bncert-tool
   ```

   You should see one of the following responses:
   + If you see command not found in the response, then the bncert tool is not installed on your instance\. Continue to the next step in this procedure to install the bncert tool on your instance\.
   + If you see **Welcome to the Bitnami HTTPS configuration tool** in the response, then the bncert tool is installed on your instance\. Continue to the step 8 of this procedure\.
   + If the bncert tool has been installed on your instance for a while, then you might see a message indicating that an updated version of the tool is available\. Choose to download it, and then enter the `sudo /opt/bitnami/bncert-tool` command to run the bncert tool again\. Continue to the step 8 of this procedure\.

1. Enter the following command to download the bncert run file to your instance\.

   ```
   wget -O bncert-linux-x64.run https://downloads.bitnami.com/files/bncert/latest/bncert-linux-x64.run
   ```

1. Enter the following command to create a directory for the bncert tool run file on your instance\.

   ```
   sudo mkdir /opt/bitnami/bncert
   ```

1. Enter the following command to make the bncert run a file that can be executed as a program\.

   ```
   sudo chmod +x /opt/bitnami/bncert/bncert-linux-x64.run
   ```

1. Enter the following command to create a symbolic link that runs the bncert tool when you enter the sudo /opt/bitnami/bncert\-tool command\.

   ```
   sudo ln -s /opt/bitnami/bncert/bncert-linux-x64.run /opt/bitnami/bncert-tool
   ```

   You are now done installing the bncert tool on your instance\.

1. Enter the following command to run the bncert tool\.

   ```
   sudo /opt/bitnami/bncert-tool
   ```

1. Enter your primary domain name and alternate domain names separated by a space as shown in the following example\.

   If your domain is not configured to route traffic to the public IP address of your instance, the `bncert` tool will ask you to make that configuration before continuing\. Your domain must be routing traffic to the public IP address of the instance from which you are using the `bncert` tool to enable HTTPS on the instance\. This confirms that you own the domain, and serves as the validation for your certificate\.  
![\[Entering the primary and alternate domain names\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/bncert-domain-names.png)

1. The `bncert` tool will ask you how you want your website's redirection to be configured\. These are the options available: 
   + **Enable HTTP to HTTPS redirection** \- Specifies whether users who browse to the HTTP version of your website \(i\.e\., `http:/example.com`\) are automatically redirected to the HTTPS version \(i\.e\., `https://example.com`\)\. We recommend enabling this option because it forces all visitors to use the encrypted connection\. Type `Y` and press **Enter** to enable it\.
   + **Enable non\-www to www redirection** \- Specifies whether users who browse to the apex of your domain \(i\.e\., `https://example.com`\) are automatically redirected to your domain's `www` subdomain \(i\.e\., `https://www.example.com`\)\. We recommend enabling this option\. However, you may want to disable it and enable the alternate option \(enable `www` to non\-`www` redirection\) if you have specified the apex of your domain as your preferred website address in search engine tools like Google's webmaster tools, or if your apex points directly to your IP and your `www` subdomain references your apex via a CNAME record\. Type `Y` and press **Enter** to enable it\.
   + **Enable www to non\-www redirection** \- Specifies whether users who browse to your domain's `www` subdomain \(i\.e\., `https://www.example.com`\) are automatically redirected to the apex of your domain \(i\.e\., `https://example.com`\)\. We recommend disabling this, if you enabled non\-`www` redirection to `www`\. Type `N` and press **Enter** to disable it\.

   Your selections should look like the following example\.  
![\[Website redirection options\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/bncert-enable-disable-redirection.png)

1. The changes that are going to be made are listed\. Type `Y` and press **Enter** to confirm and continue\.  
![\[Confirming the changes\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/bncert-confirm-changes.png)

1. Enter your email address to associate with your Let's Encrypt certificate and press **Enter**\.  
![\[Associating your email address with your Let's Encrypt certificate\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/bncert-email-address.png)

1. Review the Let's Encrypt Subscriber Agreement\. Type `Y` and press **Enter** to accept the agreement and continue\.  
![\[Review the Let's Encrypt subscriber agreement\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/bncert-lets-ecrypt-agreement.png)

   The actions are performed to enable HTTPS on your instance, including requesting the certificate and configuring the redirections you specified\.  
![\[Actions being performed\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/bncert-performing-actions.png)

   Your certificate is successfully issued and validated, and the redirections are successfully configured on your instance if you see a message similar to the following example\.  
![\[Actions successfully completed\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/bncert-success-conf.png)

   The `bncert` tool will perform an automatic renewal of your certificate every 80 days before it expires\. Repeat the above steps if you wish to use additional domains and subdomains with your instance, and you want to enable HTTPS for those domains\.

   You are now done enabling HTTPS on your Redmine instance\. Next time you browse to your Redmine website using the domain you configured, you should see that it redirects to the HTTPS connection\.

## Step 7: Read the Redmine documentation and continue configuring your website<a name="amazon-lightsail-read-documentation-redmine"></a>

Read the Redmine documentation to learn how to administer and customize your website\. For more information, see the [Redmine guide](https://www.redmine.org/guide)\.

## Step 8: Create a snapshot of your instance<a name="amazon-lightsail-create-a-snapshot-redmine"></a>

After you configure your Redmine website the way you want it, create periodic snapshots of your instance to back it up\. You can create snapshots manually, or enable automatic snapshots to have Lightsail create daily snapshots for you\. If something goes wrong with your instance, you can create a new replacement instance using the snapshot\. For more information, see [Snapshots in Amazon Lightsail](understanding-instance-snapshots-in-amazon-lightsail.md)\.

On the instance management page, under the **Snapshot** tab, choose **Create a snapshot** or choose to enable automatic snapshots\.

![\[Create an instance snapshot in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-instance-snapshots.png)

For more information, see Creating a snapshot of your [Linux or Unix instance in Amazon Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md) or [Enabling or disabling automatic snapshots for instances or disks in Amazon Lightsail](amazon-lightsail-configuring-automatic-snapshots.md)\.