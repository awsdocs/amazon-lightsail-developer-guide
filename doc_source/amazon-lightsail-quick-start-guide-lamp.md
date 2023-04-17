# Quick start guide: LAMP on Amazon Lightsail<a name="amazon-lightsail-quick-start-guide-lamp"></a>

 *Last updated: December 8, 2022* 

Here are a few steps you should take to get started after your LAMP instance is up and running on Amazon Lightsail:

## Step 1: Get the default application password for your LAMP instance<a name="amazon-lightsail-lamp-get-the-default-user-password"></a>

You need the default application password to access pre\-installed applications or services on your instance\.

1. On your instance management page, under the **Connect** tab, choose **Connect using SSH**\.

1. After you're connected, enter the following command to get the application password:

   ```
   cat bitnami_application_password
   ```
**Note**  
If you're in a directory other than the user home directory, then enter `cat $HOME/bitnami_application_password`\.

   You should see a response similar to this, which contains the default application password:  
![\[Bitnami default application password.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-bitnami-application-password.png)

For more information, see [Getting the application user name and password for your Bitnami instance in Amazon Lightsail](log-in-to-your-bitnami-application-running-on-amazon-lightsail.md)\.

## Step 2: Attach a static IP address to your LAMP instance<a name="amazon-lightsail-lamp-attach-static-ip"></a>

The default dynamic public IP address attached to your instance changes every time you stop and start the instance\. Create a static IP address, and attach it to your instance, to keep the public IP address from changing\. Later, when you use your domain name with your instance, you don’t have to update your domain’s DNS records each time you stop and start the instance\. You can attach one static IP to an instance\.

On your instance management page, under the **Networking** tab, choose **Create static IP**, then follow the instructions on the page\.

For more information, see [Create a static IP and attach it to an instance in Amazon Lightsail](lightsail-create-static-ip.md)\.

## Step 3: Visit your LAMP instance welcome page<a name="amazon-lightsail-lamp-sign-in"></a>

Navigate to the public IP address of your instance to access the application installed on it, access phpMyAdmin, or access the Bitnami documentation\.

1. On your instance management page, under the **Connect** tab, make note of the public IP\.

1. Browse to the public IP address, for example by going to `http://192.0.2.3`\.

For more information, see [Getting the application user name and password for your Bitnami instance in Amazon Lightsail](log-in-to-your-bitnami-application-running-on-amazon-lightsail.md)\.

## Step 4: Map your domain name to your LAMP instance<a name="amazon-lightsail-lamp-map-your-domain-to-your-instance"></a>

To map your domain name, such as `example.com`, to your instance, you add a record to the domain name system \(DNS\) of your domain\. DNS records are typically managed and hosted at the registrar where you registered your domain\. However, we recommend that you transfer management of your domain's DNS records to Lightsail so that you can administer it using the Lightsail console\.

On the Lightsail console home page, under the **Domains & DNS** tab, choose **Create DNS zone**, then follow the instructions on the page\.

For more information, see [Creating a DNS zone to manage your domain’s DNS records in Lightsail](lightsail-how-to-create-dns-entry.md)\.

## Step 5: Read the Bitnami documentation<a name="amazon-lightsail-lamp-read-the-bitnami-documentation"></a>

Read the Bitnami documentation to learn how to deploy your application, enable HTTPs support with SSL certificates, upload files to the server with SFTP, and more\.

For more information, see the [Bitnami LAMP for AWS Cloud](https://docs.bitnami.com/aws/infrastructure/lamp/)\.

## Step 6: Create a snapshot of your LAMP instance<a name="amazon-lightsail-lamp-create-a-snapshot"></a>

A snapshot is a copy of the system disk and original configuration of an instance\. The snapshot includes such information as memory, CPU, disk size, and data transfer rate\. You can use a snapshot as a baseline for new instances, or as a data backup\.

Under the **Snapshot** tab of your instance’s management page, enter a name for the snapshot, then choose **Create snapshot**\.

For more information, see [Creating a snapshot of your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md)\.