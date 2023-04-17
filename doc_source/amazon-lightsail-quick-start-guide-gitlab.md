# Quick start guide: GitLab CE on Amazon Lightsail<a name="amazon-lightsail-quick-start-guide-gitlab"></a>

 *Last updated: December 8, 2022* 

Here are a few steps you should take to get started after your GitLab CE instance is up and running on Amazon Lightsail:

**Contents**
+ [Step 1: Read the Bitnami documentation](#amazon-lightsail-read-the-bitnami-documentation-gitlab)
+ [Step 2: Get the default application password to access the GitLab CE admin area](#amazon-lightsail-get-the-default-user-password-gitlab)
+ [Step 3: Attach a static IP address to your instance](#amazon-lightsail-attach-static-ip-gitlab)
+ [Step 4: Sign in to the admin area of your Gitlab CE website](#amazon-lightsail-sign-in-gitlab)
+ [Step 5: Route traffic for your registered domain name to your GitLab CE website](#amazon-lightsail-map-your-domain-to-your-instance-gitlab)
+ [Step 6: Configure HTTPS for your GitLab CE website](#amazon-lightsail-https-gitlab)
+ [Step 7: Read the GitLab CE documentation and continue configuring your website](#amazon-lightsail-read-documentation-gitlab)
+ [Step 8: Create a snapshot of your instance](#amazon-lightsail-create-a-snapshot-gitlab)

## Step 1: Read the Bitnami documentation<a name="amazon-lightsail-read-the-bitnami-documentation-gitlab"></a>

Read the Bitnami documentation to learn how to configure your GitLab CE application\. For more information, see the [GitLab CE Packaged By Bitnami For AWS Cloud](https://docs.bitnami.com/aws/apps/gitlab/)\.

## Step 2: Get the default application password to access the GitLab CE admin area<a name="amazon-lightsail-get-the-default-user-password-gitlab"></a>

Complete the following procedure to get the default application password required to access the admin area for your GitLab CE website\. For more information, see [Getting the application user name and password for your Bitnami instance in Amazon Lightsail](log-in-to-your-bitnami-application-running-on-amazon-lightsail.md)\.

1. On your instance management page, under the **Connect** tab, choose **Connect using SSH**\.  
![\[Connect using SSH in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-connect-to-your-instance.png)

1. After you're connected, enter the following command to get the application password:

   ```
   cat $HOME/bitnami_application_password
   ```

   You should see a response similar to the following example, which contains the default application password:  
![\[Bitnami default application password.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-bitnami-application-password.png)

## Step 3: Attach a static IP address to your instance<a name="amazon-lightsail-attach-static-ip-gitlab"></a>

The public IP address assigned to your instance when you first create it will change every time you stop and start your instance\. You should create and attach a static IP address to your instance to ensure its public IP address doesn't change\. Later, when you use a registered domain name, such as `example.com`, with your instance, you don’t have to update your domain’s DNS records every time you stop and start your instance\. You can attach one static IP to an instance\.

On the instance management page, under the **Networking** tab, choose **Create a static IP** or **Attach static IP** \(if you previously created a static IP that you can attach to your instance\), then follow the instructions on the page\. For more information, see [Create a static IP and attach it to an instance in Amazon Lightsail](lightsail-create-static-ip.md)\.

![\[Attach static IP address in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-static-ip-address.png)

After the new static IP address is attached to your instance, you must complete the following steps to make the application aware of the new static IP address\.

1. Make a note of the static IP address of your instance\. It's listed in the header section of your instance management page\.  
![\[Public or static IP address of a Lightsail instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-public-static-ip.png)

1. On the instance management page, under the **Connect** tab, choose **Connect using SSH**\.  
![\[Connect to your instance using SSH\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-connect-using-ssh.png)

1. After you're connected, enter the following command\. Replace *<StaticIP>* with the new static IP address of your instance\.

   ```
   sudo /opt/bitnami/configure_app_domain --domain <StaticIP>
   ```

   **Example:**

   ```
   sudo /opt/bitnami/configure_app_domain --domain 203.0.113.0
   ```

   You should see a response similar to the following example\. The application on your instance should now be aware of the new static IP address\.  
![\[Result of the domain configuration tool\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-configure-domain-ip-gitlab.png)

## Step 4: Sign in to the admin area of your Gitlab CE website<a name="amazon-lightsail-sign-in-gitlab"></a>

Now that you have the default user password, navigate to your GitLab CE website's home page, and sign in to the admin area\. After you’re signed in, you can start customizing your website and making administrative changes\. For more information about what you can do in GitLab CE, see the [Step 7: Read the GitLab CE documentation and continue configuring your website](#amazon-lightsail-read-documentation-gitlab) section later in this guide\.

1. On your instance management page, under the **Connect** tab, make note of the public IP address of your instance\. The public IP address is also displayed in the header section of your instance management page\.  
![\[Public IP address of an instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-public-ip.png)

1. Browse to the public IP address of your instance, for example by going to `http://203.0.113.0`\.

   The home page of your Gitlab CE website should appear\. You might also see a browser warning that your connection is not private, not secure, or that there’s a security risk\. This happens because your GitLab CE instance does not yet have an SSL/TLS certificate applied to it\. In the browser window, choose **Advanced**, **Details**, or **More information** to view the options that are available\. Then choose to proceed to the website even if it’s not private or secure\.

1. Sign in using the default user name \(`root`\) and the default password retrieved earlier in this guide\.

   The Gitlab CE administration dashboard appears\.  
![\[The Gitlab CE administration dashboard\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-gitlab-dashboard.png)

## Step 5: Route traffic for your registered domain name to your GitLab CE website<a name="amazon-lightsail-map-your-domain-to-your-instance-gitlab"></a>

To route traffic for your registered domain name, such as `example.com`, to your GitLab CE website, you add a record to the domain name system \(DNS\) of your domain\. DNS records are typically managed and hosted at the registrar where you registered your domain\. However, we recommend that you transfer management of your domain's DNS records to Lightsail so that you can administer it using the Lightsail console\.

On the Lightsail console home page, under the **Networking** tab, choose **Create DNS zone**, then follow the instructions on the page\. For more information, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)\.

![\[Create a DNS zone in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-create-dns-zone.png)

After your domain name is routing traffic to your instance, you must complete the following procedure to make GitLab CE aware of the domain name\.

1. On the instance management page, under the **Connect** tab, choose **Connect using SSH**\.  
![\[Connect to your instance using SSH\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-connect-using-ssh.png)

1. After you're connected, enter the following command\. Replace *<DomainName>* with the domain name that is routing traffic to your instance\.

   ```
   sudo /opt/bitnami/configure_app_domain --domain <DomainName>
   ```

   **Example:**

   ```
   sudo /opt/bitnami/configure_app_domain --domain example.com
   ```

   You should see a response similar to the following example\. Your GitLab CE instance should now be aware of the domain name\.  
![\[Result of the domain configuration tool\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-configure-domain-example-gitlab.png)

   If that command fails, you might be using an older version of the GitLab CE instance\. Try running the following commands instead\. Replace *<DomainName>* with the domain name that is routing traffic to your instance\.

   ```
   cd /opt/bitnami/apps/gitlab
   sudo ./bnconfig --machine_hostname <DomainName>
   ```

   After running those commands, enter the following command to keep the bnconfig tool from automatically running every time the server restarts\.

   ```
   sudo mv bnconfig bnconfig.disabled
   ```

Next, you should generate and configure an SSL/TLS certificate to enable HTTPS connections for your GitLab CE website\. For more information, continue to the next [Step 6: Configure HTTPS for your GitLab CE website](#amazon-lightsail-https-gitlab) section of this guide\.

## Step 6: Configure HTTPS for your GitLab CE website<a name="amazon-lightsail-https-gitlab"></a>

Complete the following procedure to configure HTTPS on your GitLab CE website\. These steps show you how to use the [Lego client](https://github.com/go-acme/lego), which is a command line tool for requesting Let's Encrypt SSL/TLS certificates\.

**Important**  
Before starting with this procedure, make sure that you configured your domain to route traffic to your GitLab CE instance\. Otherwise, the SSL/TLS certificate validation process will fail\. To route traffic for your registered domain name, you add a record to the DNS of your domain\. DNS records are typically managed and hosted at the registrar where you registered your domain\. However, we recommend that you transfer management of your domain's DNS records to Lightsail so that you can administer it using the Lightsail console\.  
On the Lightsail console home page, under the **Domains & DNS** tab, choose **Create DNS zone**, then follow the instructions on the page\. For more information, see [Creating a DNS zone to manage your domain’s DNS records in Lightsail](lightsail-how-to-create-dns-entry.md)\.

1. On your instance management page, under the **Connect** tab, choose **Connect using SSH**\.  
![\[Connect using SSH in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-connect-to-your-instance.png)

1. After you're connected, enter the following command to change directory to the temporary \(/tmp\) directory\.

   ```
   cd /tmp
   ```

1. Enter the following command to download the latest version of the Lego client\. This command downloads a tape archive \(tar\) file\.

   ```
   curl -Ls https://api.github.com/repos/xenolf/lego/releases/latest | grep browser_download_url | grep linux_amd64 | cut -d '"' -f 4 | wget -i -
   ```

1. Enter the following command to extract the files from the tar file\. Replace *X\.Y\.Z* with the version of the Lego client that you downloaded\.

   ```
   tar xf lego_vX.Y.Z_linux_amd64.tar.gz
   ```

   **Example:**

   ```
   tar xf lego_v4.7.0_linux_amd64.tar.gz
   ```

1. Enter the following command to create the `/opt/bitnami/letsencrypt` directory where you will move the Lego client files into\.

   ```
   sudo mkdir -p /opt/bitnami/letsencrypt
   ```

1. Enter the following command to move the Lego client files into the directory you created\.

   ```
   sudo mv lego /opt/bitnami/letsencrypt/lego
   ```

1. Enter the following commands one by one to stop the application services that are running on your instance\.

   ```
   sudo service bitnami stop
   sudo service gitlab-runsvdir stop
   ```

1. Enter the following command to use the Lego client to request a Let's Encrypt SSL/TLS certificate\.

   ```
   sudo /opt/bitnami/letsencrypt/lego --tls --email="EmailAddress" --domains="RootDomain" --domains="WwwSubDomain" --path="/opt/bitnami/letsencrypt" run
   ```

   In the command, replace the following example values with your own:
   + `EmailAddress` — Your email address for registration notifications\.
   + `RootDomain` — The primary root domain that is routing traffic to your GitLab CE website \(for example, `example.com`\)\.
   + `WwwSubDomain` — The `www` subdomain of the primary root domain that is routing traffic to your GitLab CE website \(for example, `www.example.com`\)\.

     You can specify multiple domains for your certificate by specifying additional `--domains` parameters in your command\. When you specify multiple domains, Lego creates a subject alternate names \(SAN\) certificate which results in only one certificate being valid for all domains you specified\. The first domain in your list is added as the “CommonName” of the certificate and the rest are added as “DNSNames” to the SAN extension within the certificate\.

   **Example:**

   ```
   sudo /opt/bitnami/letsencrypt/lego --tls --email="user@example.com" --domains="example.com" --domains="www.example.com" --path="/opt/bitnami/letsencrypt" run
   ```

1. Press **Y** and **Enter** when to accept the terms of service when prompted\.

   You should see a response similar to the following example\.  
![\[Successful Lego client response to certificate request\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-configure-domain-cert-response-gitlab.png)

   If successful, a set of certificates are saved to the `/opt/bitnami/letsencrypt/certificates` directory\. This set includes the server certificate file \(for example, `example.com.crt`\) and the server certificate key file for \(example, `example.com.key`\)\.

1. Enter the following commands one by one to rename the existing certificates on your instance\. Later, you will replace these existing certificates with your new Let's Encrypt certificates\.

   ```
   sudo mv /etc/gitlab/ssl/server.crt /etc/gitlab/ssl/server.crt.old
   sudo mv /etc/gitlab/ssl/server.key /etc/gitlab/ssl/server.key.old
   sudo mv /etc/gitlab/ssl/server.csr /etc/gitlab/ssl/server.csr.old
   ```

1. Enter the following commands one by one to create symbolic links for your new Let's Encript certificates in the `/etc/gitlab/ssl` directory, which is the default certificates directory on your GitLab CE instance\.

   ```
   sudo ln -sf /opt/bitnami/letsencrypt/certificates/Domain.key /etc/gitlab/ssl/server.key
   sudo ln -sf /opt/bitnami/letsencrypt/certificates/Domain.crt /etc/gitlab/ssl/server.crt
   ```

   In the command, replace *Domain* with the primary root domain that you specified when requesting your Let's Encrypt certificates\.

   **Example:**

   ```
   sudo ln -sf /opt/bitnami/letsencrypt/certificates/example.com.key /etc/gitlab/ssl/server.key
   sudo ln -sf /opt/bitnami/letsencrypt/certificates/example.com.crt /etc/gitlab/ssl/server.crt
   ```

1. Enter the following commands one by one to change the permissions of your new Let's Encrypt certificates in the directory you moved them into\.

   ```
   sudo chown root:root /etc/gitlab/ssl/server*
   sudo chmod 600 /etc/gitlab/ssl/server*
   ```

1. Enter the following command to restart the application services on your GitLab CE instance\.

   ```
   sudo service bitnami start
   ```

Next time you browse to your GitLab CE website using the domain you configured, you should see that it redirects to the HTTPS connection\. Note that it can take up to an hour for the GitLab CE instance to recognize the new certificates\. If your GitLab CE website refuses your connection, stop and start the instance, and try again\.

## Step 7: Read the GitLab CE documentation and continue configuring your website<a name="amazon-lightsail-read-documentation-gitlab"></a>

Read the GitLab CE documentation to learn how to administer and customize your website\. For more information, see the [GitLab Documentation](https://docs.gitlab.com/ee/index.html)\.

## Step 8: Create a snapshot of your instance<a name="amazon-lightsail-create-a-snapshot-gitlab"></a>

After you configure your GitLab CE website the way you want it, create periodic snapshots of your instance to back it up\. You can create snapshots manually, or enable automatic snapshots to have Lightsail create daily snapshots for you\. If something goes wrong with your instance, you can create a new replacement instance using the snapshot\. For more information, see [Snapshots in Amazon Lightsail](understanding-instance-snapshots-in-amazon-lightsail.md)\.

On the instance management page, under the **Snapshot** tab, choose **Create a snapshot** or choose to enable automatic snapshots\.

![\[Create an instance snapshot in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-instance-snapshots.png)

For more information, see Creating a snapshot of your [Linux or Unix instance in Amazon Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md) or [Enabling or disabling automatic snapshots for instances or disks in Amazon Lightsail](amazon-lightsail-configuring-automatic-snapshots.md)\.