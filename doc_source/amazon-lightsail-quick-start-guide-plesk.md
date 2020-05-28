# Quick start guide: Plesk on Amazon Lightsail<a name="amazon-lightsail-quick-start-guide-plesk"></a>

 *Last updated: February 11, 2020* 

Here are a few steps you should take to get started after your Plesk instance is up and running on Amazon Lightsail:

## Step 1: Get the one\-time login URL for your Plesk instance<a name="amazon-lightsail-plesk-one-time-login-url"></a>

You need the one\-time login URL to access the Plesk panel as an administrator\.

1. On your instance management page, under the **Connect** tab, choose **Connect using SSH**\.

1. After you're connected, enter the following command to get the one\-time login URL:

   ```
   sudo plesk login | grep -v internal:8
   ```

   You should see a response similar to the following example, which contains the one\-time login URL:  
![\[One-time sign in for your Plesk instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/plesk-one-time-sign-in.png)
**Important**  
If you recently attached a static IP to your Plesk instance, you might get a one\-time login URL that uses the old public IP address\. Reboot the instance, and then run the above command again to get a one\-time login URL that uses the new static, public IP address\.

1. Copy the URL to your clipboard, or make note of it\. You will need it later to sign in to the Plesk panel for the first time\.

For more information, see [Set up and configure Plesk on Lightsail](set-up-and-configure-plesk-stack-on-lightsail.md)\.

## Step 2: Sign in to the Plesk panel for the first time<a name="amazon-lightsail-plesk-sign-in"></a>

Paste the one\-time login URL into a web browser\. Follow the instructions on the page to create your sign in credentials for Plesk\. You should see an option to add your domain to Plesk when you sign in for the first time\.

**Note**  
You might see a browser warning that your connection is not private, not secure, or that there’s a security risk\. This happens because your Plesk instance does not yet have an SSL/TLS certified applied to it\. In the browser window, choose **Advanced**, **Details**, or **More information** to view the options that are available\. Then choose to proceed to the website even if it’s not private or secure\.

For more information, see [Set up and configure Plesk on Lightsail](set-up-and-configure-plesk-stack-on-lightsail.md)\.

## Step 3: Attach a static IP address to your Plesk instance<a name="amazon-lightsail-plesk-attach-static-ip"></a>

The default dynamic public IP address attached to your instance changes every time you stop and start the instance\. Create a static IP address, and attach it to your instance, to keep the public IP address from changing\. Later, when you use your domain name with your instance, you don’t have to update your domain’s DNS records each time you stop and start the instance\.

On your instance management page, under the **Networking** tab, choose **Create static IP**, then follow the instructions on the page\.

For more information, see [Create a static IP and attach it to an instance in Amazon Lightsail](lightsail-create-static-ip.md)\.

## Step 4: Map your domain name to your Plesk instance<a name="amazon-lightsail-plesk-map-your-domain-to-your-instance"></a>

**Note**  
You can map a domain to your Plesk instance, which you can use to access your Plesk panel\. You can also map multiple domains within the Plesk panel, which you can use to manage websites within the Plesk panel\. This section describes how to map your domain to your Plesk instance\. For more information about mapping multiple domains within the Plesk panel, see [Adding a Domain in Plesk](https://docs.plesk.com/en-US/obsidian/quick-start-guide/plesk-tutorial/step-6-change-your-password-and-log-out.74376/#adding-a-domain-in-plesk) in the *Plesk Documentation and Help Portal*\.

To map your domain name, such as `example.com`, to your instance, you add a record to the domain name system \(DNS\) of your domain\. DNS records are typically managed and hosted at the registrar where you registered your domain\. However, we recommend that you transfer management of your domain's DNS records to Lightsail so that you can administer it using the Lightsail console\.

On the Lightsail console home page, under the **Networking** tab, choose **Create DNS zone**, then follow the instructions on the page\.

For more information, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)\.

## Step 5: Read the Plesk documentation<a name="amazon-lightsail-plesk-read-the-bitnami-documentation"></a>

Read the Plesk documentation to learn how to administer web sites using Plesk, customize the Plesk panel, and more\.

For more information, see the [Getting Started with Managing Websites in Plesk](https://docs.plesk.com/en-US/obsidian/quick-start-guide/read-me-first.74371/) in the *Plesk Documentation and Help Portal*\.

## Step 6: Create a snapshot of your Plesk instance<a name="amazon-lightsail-plesk-create-a-snapshot"></a>

A snapshot is a copy of the system disk and original configuration of an instance\. The snapshot includes such information as memory, CPU, disk size, and data transfer rate\. You can use a snapshot as a baseline for new instances, or as a data backup\.

Under the **Snapshot** tab of your instance’s management page, enter a name for the snapshot, then choose **Create snapshot**\.

For more information, see [Creating a snapshot of your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md)\.