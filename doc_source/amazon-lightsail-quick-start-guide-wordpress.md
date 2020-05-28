# Quick start guide: WordPress on Amazon Lightsail<a name="amazon-lightsail-quick-start-guide-wordpress"></a>

 *Last updated: August 13, 2018* 

Here are a few steps you should take to get started after your WordPress instance is up and running on Amazon Lightsail:

## Step 1: Get the default application password for your WordPress website<a name="amazon-lightsail-wordpress-get-the-default-user-password"></a>

You need the default application password to sign in to your WordPress website’s administration dashboard\.

1. On your instance management page, under the **Connect** tab, choose **Connect using SSH**\.

1. After you're connected, enter the following command to get the default application password:

   ```
   cat bitnami_application_password
   ```
**Note**  
If you're in a directory other than the user home directory, then enter `cat $HOME/bitnami_application_password`\.

   You should see a response similar to this, which contains the default application password:  
![\[Bitnami default application password.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-bitnami-application-password.png)

For more information, see [Getting the application user name and password for your 'Certified by Bitnami' instance in Amazon Lightsail](log-in-to-your-bitnami-application-running-on-amazon-lightsail.md)\.

## Step 2: Sign in to your WordPress website<a name="amazon-lightsail-wordpress-sign-in"></a>

Now that you have the default user password, navigate to your WordPress website’s home page, and sign in to the administration dashboard\. After you’re signed in, you can change the default password to something that is easier to remember\.

1. On your instance management page, under the **Connect** tab, make note of the public IP\.

1. Browse to the public IP address, for example by going to `http://192.0.2.3`\.

1. Choose **Manage** in the bottom right corner of your WordPress website home page\.

1. Sign in using the default user name \(user\) and the default password retrieved earlier in this guide\.

   The WordPress administration dashboard appears\.  
![\[The WordPress administration dashboard.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wordpress-dashboard.png)

For more information, see [Getting the application user name and password for your 'Certified by Bitnami' instance in Amazon Lightsail](log-in-to-your-bitnami-application-running-on-amazon-lightsail.md)

To change the default user password, see [Resetting your password in the WordPress documentation](https://codex.wordpress.org/Resetting_Your_Password)\.

## Step 3: Attach a static IP address to your WordPress instance<a name="amazon-lightsail-wordpress-attach-static-ip"></a>

The default dynamic public IP address attached to your instance changes every time you stop and start the instance\. Create a static IP address, and attach it to your instance, to keep the public IP address from changing\. Later, when you use your domain name with your instance, you don’t have to update your domain’s DNS records each time you stop and start the instance\.

On your instance management page, under the **Networking** tab, choose **Create static IP**, then follow the instructions on the page\.

For more information, see [Create a static IP and attach it to an instance in Amazon Lightsail](lightsail-create-static-ip.md)\.

## Step 4: Map your domain name to your WordPress website<a name="amazon-lightsail-wordpress-map-your-domain-to-your-instance"></a>

To map your domain name, such as `example.com`, to your WordPress website, you add a record to the domain name system \(DNS\) of your domain\. DNS records are typically managed and hosted at the registrar where you registered your domain\. However, we recommend that you transfer management of your domain's DNS records to Lightsail so that you can administer it using the Lightsail console\.

On the Lightsail console home page, under the **Networking** tab, choose **Create DNS zone**, then follow the instructions on the page\.

For more information, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)\.

## Step 5: Read the Bitnami documentation<a name="amazon-lightsail-wordpress-read-the-bitnami-documentation"></a>

Read the Bitnami documentation to learn how to perform administrative tasks on your WordPress website, such as install plugins, customize the theme, and upgrade your version of WordPress\.

For more information, see the [Bitnami WordPress for AWS cloud](https://docs.bitnami.com/aws/apps/wordpress/)\.

## Step 6: Create a snapshot of your WordPress instance<a name="amazon-lightsail-wordpress-create-a-snapshot"></a>

A snapshot is a copy of the system disk and original configuration of an instance\. The snapshot includes such information as memory, CPU, disk size, and data transfer rate\. You can use a snapshot as a baseline for new instances, or as a data backup\.

On your instance management page, under the **Snapshot** tab, enter a name for the snapshot, then choose **Create snapshot**\.

For more information, see [Creating a snapshot of your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md)\.