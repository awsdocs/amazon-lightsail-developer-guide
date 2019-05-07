# Quick start guide: Plesk on Amazon Lightsail<a name="amazon-lightsail-quick-start-guide-plesk"></a>

 *Last updated: August 13, 2018* 

Here are a few steps you should take to get started after your Plesk instance is up and running on Amazon Lightsail:

## Step 1: Configure firewall settings for your Plesk instance<a name="amazon-lightsail-plesk-get-the-default-user-password"></a>

Configuring firewall settings allows you to access the Plesk panel for your instance, which is covered later in this guide\.

1. On the **Networking** tab of your instance’s management page, choose **Add another** under the Firewall section\.

1. Add the following entries, and choose **Save**:
   + Custom > TCP > 53
   + Custom > UDP > 53
   + Custom > TCP > 8443
   + Custom > TCP > 8447  
![\[Plesk firewall entries in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/b2fb86c05aa70ef4defbdc74847a0bb8/images/amazon-lightsail-plesk-firewall.png)

For more information, see [Set up and configure Plesk on Lightsail](set-up-and-configure-plesk-stack-on-lightsail.md)\.

## Step 2: Get the one\-time login URL for your Plesk instance<a name="amazon-lightsail-plesk-one-time-login-url"></a>

You need the one\-time login URL to access the Plesk panel as an administrator\.

1. On your instance management page, under the **Connect** tab, choose **Connect using SSH**\.

1. After you're connected, enter the following command to get the one\-time login URL:

   ```
   sudo plesk login
   ```

   You should see a response similar to this, which contains the one\-time login URL:  
![\[Plesk panel one-time login URL.\]](https://d9yljz1nd5001.cloudfront.net/en_us/b2fb86c05aa70ef4defbdc74847a0bb8/images/amazon-lightsail-plesk-password.png)

1. Copy the URL to your clipboard, or make note of it\. You will need it later to sign in to the Plesk panel for the first time\.

For more information, see [Set up and configure Plesk on Lightsail](set-up-and-configure-plesk-stack-on-lightsail.md)\.

## Step 3: Sign in to the Plesk panel for the first time<a name="amazon-lightsail-plesk-sign-in"></a>

Paste the one\-time login URL into a web browser\. Follow the instructions on the page to create your sign in credentials for Plesk\.

For more information, see [Set up and configure Plesk on Lightsail](set-up-and-configure-plesk-stack-on-lightsail.md)\.

## Step 4: Attach a static IP address to your Plesk instance<a name="amazon-lightsail-plesk-attach-static-ip"></a>

The default dynamic public IP address attached to your instance changes every time you stop and start the instance\. Create a static IP address, and attach it to your instance, to keep the public IP address from changing\. Later, when you use your domain name with your instance, you don’t have to update your domain’s DNS records each time you stop and start the instance\.

On your instance management page, under the **Networking** tab, choose **Create static IP**, then follow the instructions on the page\.

For more information, see [Create a static IP and attach it to an instance in Amazon Lightsail](lightsail-create-static-ip.md)\.

## Step 5: Map your domain name to your Plesk instance<a name="amazon-lightsail-plesk-map-your-domain-to-your-instance"></a>

To map your domain name, such as `example.com`, to your instance, you add a record to the domain name system \(DNS\) of your domain\. DNS records are typically managed and hosted at the registrar where you registered your domain\. However, we recommend that you transfer management of your domain's DNS records to Lightsail so that you can administer it using the Lightsail console\.

On the Lightsail console home page, under the **Networking** tab, choose **Create DNS zone**, then follow the instructions on the page\.

For more information, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)\.

## Step 5: Read the Plesk documentation<a name="amazon-lightsail-plesk-read-the-bitnami-documentation"></a>

Read the Plesk documentation to learn how to administer web sites using Plesk, customize the Plesk panel, and more\.

For more information, see the [Plesk administrator's guide](https://docs.plesk.com/en-US/onyx/administrator-guide/about-plesk.70559/)\.

## Step 6: Create a snapshot of your Plesk instance<a name="amazon-lightsail-plesk-create-a-snapshot"></a>

A snapshot is a copy of the system disk and original configuration of an instance\. The snapshot includes such information as memory, CPU, disk size, and data transfer rate\. You can use a snapshot as a baseline for new instances, or as a data backup\.

Under the **Snapshot** tab of your instance’s management page, enter a name for the snapshot, then choose **Create snapshot**\.

For more information, see the [Create a snapshot of your Linux/Unix\-based instance in Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md)\.