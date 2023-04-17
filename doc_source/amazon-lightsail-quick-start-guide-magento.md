# Quick start guide: Magento on Amazon Lightsail<a name="amazon-lightsail-quick-start-guide-magento"></a>

 *Last updated: December 8, 2022* 

Here are a few steps you should complete to get started after your Magento instance is up and running on Amazon Lightsail\.

**Contents**
+ [Step 1: Get the default application password for your Magento website](#amazon-lightsail-magento-get-the-default-user-password)
+ [Step 2: Attach a static IP address to your Magento instance](#amazon-lightsail-magento-attach-static-ip)
+ [Step 3: Sign in to the administration dashboard of your Magento website](#amazon-lightsail-magento-sign-in)
+ [Step 4: Route traffic for your registered domain name to your Magento website](#amazon-lightsail-magento-map-your-domain-to-your-instance)
+ [Step 5: Configure HTTPS for your Magento website](#amazon-lightsail-magento-https)
+ [Step 6: Configure SMTP for email notifications](#amazon-lightsail-magento-smtp)
+ [Step 7: Read the Bitnami and Magento documentation](#amazon-lightsail-magento-read-the-bitnami-documentation)
+ [Step 8: Create a snapshot of your Magento instance](#amazon-lightsail-magento-create-a-snapshot)

## Step 1: Get the default application password for your Magento website<a name="amazon-lightsail-magento-get-the-default-user-password"></a>

Complete the following steps to get the default application password for your Magento website\. For more information, see [Getting the application user name and password for your Bitnami instance in Amazon Lightsail](log-in-to-your-bitnami-application-running-on-amazon-lightsail.md)\.

1. On the instance management page, under the **Connect** tab, choose **Connect using SSH\.**  
![\[Connect using SSH in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-connect-to-your-instance.png)

1. After you're connected, enter the following command to get the default application password:

   ```
   cat $HOME/bitnami_application_password
   ```

   You should see a response similar to the following example, which contains the default application password\. Store this password in a safe place\. You will use it in the next section of this tutorial to sign in to the administration dashboard of your Magento website\.  
![\[Default application password for Bitnami instances\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/magento-quick-start-ssh-default-application-password.png)

## Step 2: Attach a static IP address to your Magento instance<a name="amazon-lightsail-magento-attach-static-ip"></a>

The public IP address assigned to your instance when you first create it will change every time you stop and start your instance\. You should create and attach a static IP address to your instance to ensure its public IP address doesn't change\. Later, when you use a registered domain name, such as `example.com`, with your instance, you don’t have to update your domain’s DNS records every time you stop and start your instance\. You can attach one static IP to an instance\.

On the instance management page, under the **Networking** tab, choose **Create a static IP** or **Attach static IP** \(if you previously created a static IP that you can attach to your instance\), then follow the instructions on the page\. For more information, see [Create a static IP and attach it to an instance in Amazon Lightsail](lightsail-create-static-ip.md)\.

![\[Attach static IP address in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-static-ip-address.png)

After the new static IP address is attached to your instance, you must complete the following steps to make the Magento software aware of the new static IP address\.

1. Make a note of the static IP address of your instance\. It's listed in the header section of your instance management page\.  
![\[Public or static IP address of a Lightsail instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-public-static-ip.png)

1. On the instance management page, under the **Connect** tab, choose **Connect using SSH**\.  
![\[Connect to your instance using SSH\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-connect-using-ssh.png)

1. After you're connected, enter the following command\. Be sure to replace *<StaticIP>* with the new static IP address of your instance\.

   ```
   sudo /opt/bitnami/configure_app_domain --domain <StaticIP>
   ```

   **Example:**

   ```
   sudo /opt/bitnami/configure_app_domain --domain 203.0.113.0
   ```

   You should see a response similar to the following example\. The Magento software should now be aware of the new static IP address\.  
![\[Result of the domain configuration tool\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-configure-domain-ip.png)

**Note**  
Magento does not currently support IPv6 addresses\. You can enable IPv6 for the instance, but the Magento software will not respond to requests over the IPv6 network\.

## Step 3: Sign in to the administration dashboard of your Magento website<a name="amazon-lightsail-magento-sign-in"></a>

Complete the following step to access your Magento website and sign in to its administration dashboard\. To sign in, you will use the default user name \(`user`\) and the default application password that you got earlier in this guide\.

1. In the Lightsail console, make note of the public or static IP address that is listed in the header area of the instance management page\.  
![\[Public or static IP address of a Lightsail instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-public-static-ip.png)

1. Browse to the following address to access the sign in page for the administration dashboard of your Magento website\. Be sure to replace *<InstanceIpAddress>* with the public or static IP address of your instance\.

   ```
   http://<InstanceIpAddress>/admin
   ```

   **Example: **

   ```
   http://203.0.113.0/admin
   ```
**Note**  
You might need to reboot the instance if you can't access the sign in page for the Magento administration dashboard\.

1. Enter the default user name \(`user`\), the default application password you got earlier in this guide, and choose **Sign in**\.  
![\[The Magento administration dashboard sign in page\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/magento-quick-start-magento-sign-in-page.png)

   The Magento administration dashboard appears\.  
![\[Magento administration dashboard\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/magento-quick-start-magento-administration-dashboard.png)

To change the default user name or password that you use to sign in to the administration dashboard of your Magento website, choose **System** in the navigation pane, and then choose **All Users**\. For more information, see [Adding users](https://docs.magento.com/user-guide/system/permissions-users-all.html) in the *Magento documentation*\.

![\[All users option in the Magento navigation pane\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/magento-quick-start-all-users.png)

For more information about the administration dashboard, see [Magento 2\.4 User Guide](https://docs.magento.com/user-guide/) \.

## Step 4: Route traffic for your registered domain name to your Magento website<a name="amazon-lightsail-magento-map-your-domain-to-your-instance"></a>

To route traffic for your registered domain name, such as `example.com`, to your Magento website, you add a record to the domain name system \(DNS\) of your domain\. DNS records are typically managed and hosted at the registrar where you registered your domain\. However, we recommend that you transfer management of your domain's DNS records to Lightsail so that you can administer it using the Lightsail console\.

On the Lightsail console home page, under the **Domains & DNS** tab, choose **Create DNS zone**, then follow the instructions on the page\. For more information, see [Creating a DNS zone to manage your domain’s DNS records in Lightsail](lightsail-how-to-create-dns-entry.md)\.

After your domain name is routing traffic to your instance, you must complete the following steps to make the Magento software aware of the domain name\.

1. On the instance management page, under the **Connect** tab, choose **Connect using SSH**\.  
![\[Connect to your instance using SSH\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-connect-using-ssh.png)

1. After you're connected, enter the following command\. Be sure to replace *<DomainName>* with the domain name that is routing traffic to your instance\.

   ```
   sudo /opt/bitnami/configure_app_domain --domain <DomainName>
   ```

   **Example:**

   ```
   sudo /opt/bitnami/configure_app_domain --domain www.example.com
   ```

   You should see a response similar to the following example\. The Magento software should now be aware of the domain name\.  
![\[Result of the domain configuration tool\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-configure-domain.png)

## Step 5: Configure HTTPS for your Magento website<a name="amazon-lightsail-magento-https"></a>

Complete the following steps to configure HTTPS on your Magento website\. These steps show you how to use the Bitnami HTTPS configuration tool \(bncert\), which is a command line tool for requesting SSL/TLS certificates, setting up redirections \(e\.g\. HTTP to HTTPS\), and renewing certificates\.

**Important**  
The bncert tool will issue certificates only for domains that are currently routing traffic to the public IP address of your Magento instance\. Before starting with these steps, make sure that you add DNS records to the DNS of all domains that you want to use with your Magento website\.

1. On the instance management page, under the Connect tab, choose **Connect using SSH**\.  
![\[Connect using SSH in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-connect-to-your-instance.png)

1. After you're connected, enter the following command to start the bncert\-tool\.

   ```
   sudo /opt/bitnami/bncert-tool
   ```

   You should see a response similar to the following example:  
![\[Running the bncert tool\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/magento-quick-start-run-bncert-tool-success.png)

1. Enter your primary domain name and alternate domain names separated by a space as shown in the following example\.  
![\[Entering the primary and alternate domain names\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/magento-quick-start-bncert-domain-names.png)

1. The changes that are going to be made are listed\. Type `Y` and press **Enter** to confirm and continue\.  
![\[Confirming the changes\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/magento-quick-start-bncert-confirm-changes.png)

1. Enter your email address to associate with your Let's Encrypt certificate and press **Enter**\.  
![\[Associating your email address with your Let's Encrypt certificate\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/magento-quick-start-bncert-email-address.png)

1. Review the Let's Encrypt Subscriber Agreement\. Type `Y` and press **Enter** to accept the agreement and continue\.  
![\[Review the Let's Encrypt subscriber agreement\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/magento-quick-start-bncert-lets-ecrypt-agreement.png)

   The actions are performed to enable HTTPS on your instance, including requesting the certificate and configuring the redirections you specified\.  
![\[Actions being performed\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/magento-quick-start-bncert-performing-actions.png)

   Your certificate is successfully issued and validated, and the redirections are successfully configured on your instance if you see a message similar to the following example\.  
![\[Actions successfully completed\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/magento-quick-start-bncert-success-conf.png)

   The `bncert` tool will perform an automatic renewal of your certificate every 80 days before it expires\. Continue to the next set of steps to finish enabling HTTPS on your Magento website\.

1. Browse to the following address to access the sign in page for the administration dashboard of your Magento website\. Be sure to replace *<DomainName>* with the registered domain name that is routing traffic to your instance\.

   ```
   http://<DomainName>/admin
   ```

   **Example: **

   ```
   http://www.example.com/admin
   ```

1. Enter the default user name \(`user`\), the default application password you got earlier in this guide, and choose **Sign in**\.  
![\[The Magento administration dashboard sign in page\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/magento-quick-start-magento-sign-in-page.png)

   The Magento administration dashboard appears\.  
![\[Magento administration dashboard\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/magento-quick-start-magento-administration-dashboard.png)

1. Choose **Stores** in the navigation pane, and then choose **Configuration**\.  
![\[Magento administration dashboard\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/magento-quick-start-magento-configuration.png)

1. Choose **Web**, and then expand the **Base URLs** node\.

1. In the **Base URL** text box, enter the full URL of your website, for example `https://www.example.com/`\.  
![\[Magento administration dashboard\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/magento-quick-start-magento-base-urls.png)

1. Expand the Base URLs \(Secure\) node\.

1. In the **Secure Base URL** text box, enter the full URL of your website, for example `https://www.example.com/`\.  
![\[Magento administration dashboard\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/magento-quick-start-magento-base-urls-secure.png)

1. Choose **Yes** for the **Use Secure URLs on Storefront**, **Use Secure URLs in Admin**, and **Upgrade Insecure Requests** options\.  
![\[Magento administration dashboard\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/magento-quick-start-magento-base-urls-secure-options.png)

1. Choose Save Config at the top of the page\.

   HTTPS is now configured for your Magento website\. When customers browse to the HTTP version \(e\.g\., `http://www.example.com`\) of your Magento website, they will be automatically redirected to the HTTPS version \(e\.g\., `https://www.example.com`\)\.

## Step 6: Configure SMTP for email notifications<a name="amazon-lightsail-magento-smtp"></a>

Configure the SMTP settings of your Magento website to enable email notifications for it\. For more information, see [Install the Magento Magepal SMTP extension](https://docs.bitnami.com/aws/apps/magento/configuration/install-extension-smtp/) in the *Bitnami documentation*\.

**Important**  
If you configure SMTP to use ports 25, 465, or 587, then you must open those ports in the firewall of your instance in the Lightsail console\. For more information, see [Adding and editing instance firewall rules in Amazon Lightsail](amazon-lightsail-editing-firewall-rules.md)\.  
If you configure your Gmail account to send email on your Magento website, then you must use an app password instead of using the standard password that you use to sign in to Gmail\. For more information, see [Sign in with App Passwords](https://support.google.com/accounts/answer/185833?hl=en)\.

## Step 7: Read the Bitnami and Magento documentation<a name="amazon-lightsail-magento-read-the-bitnami-documentation"></a>

Read the Bitnami documentation to learn how to perform administrative tasks on your Magento instance and website, such as install plugins and customize the theme\. For more information, see [Bitnami Magento Stack for AWS Cloud](https://docs.bitnami.com/aws/apps/magento/) in the *Bitnami documentation*\.

You should also read the Magento documentation to learn how to administer your Magento website\. For more information, see the [Magento 2\.4 User Guide](https://docs.magento.com/user-guide/)\.

## Step 8: Create a snapshot of your Magento instance<a name="amazon-lightsail-magento-create-a-snapshot"></a>

After you configure your Magento website the way you want it, create periodic snapshots of your instance to back it up\. You can create snapshots manually, or enable automatic snapshots to have Lightsail create daily snapshots for you\. If something goes wrong with your instance, you can create a new replacement instance using the snapshot\. For more information, see [Snapshots in Amazon Lightsail](understanding-instance-snapshots-in-amazon-lightsail.md)\.

On the instance management page, under the **Snapshot** tab, choose **Create a snapshot** or choose to enable automatic snapshots\.

![\[Create an instance snapshot in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-instance-snapshots.png)

For more information, see Creating a snapshot of your [Linux or Unix instance in Amazon Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md) or [Enabling or disabling automatic snapshots for instances or disks in Amazon Lightsail](amazon-lightsail-configuring-automatic-snapshots.md)\.