# Set up and configure Plesk on Lightsail<a name="set-up-and-configure-plesk-stack-on-lightsail"></a>

 *Last updated: February 11, 2020* 

You can create a Plesk hosting stack in Amazon Lightsail that includes the following features\.
+ WordPress Toolkit, featuring automation in a graphical user interface
+ Let's Encrypt support for SSL certificates and configuring encrypted \(HTTPS\) traffic on a single instance
+ FTP access to transfer files to and from your instance
+ Docker Proxy Rules
+ Web\-based server management and security tools, including Plesk Firewall, Logs, and ModSecurity

This guide shows you how to create a Plesk instance in Lightsail, and how to sign in to the Plesk panel for the first time by creating a username and password\.

## Create a Plesk instance in Lightsail<a name="create-plesk-instance"></a>

Complete the following steps to create a Plesk instance in Lightsail\.

1. Sign in to the Lightsail console at [https://lightsail\.aws\.amazon\.com/](https://lightsail.aws.amazon.com/)\.

1. In the **Instances** tab of the Lightsail home page, choose **Create instance**\.

1. Choose the location where you want to create your instance\.

   Choose **Change AWS Region and Availability Zone** to change your instance location\.

1. Under **Apps \+ OS**, choose **Plesk Hosting Stack on Ubuntu**\.

1. Choose your instance plan\.
**Note**  
Plesk is not supported on the $3\.50 USD per month Lightsail plan\.

1. Enter a name for your instance\.

   Resource names:
   + Must be unique within each AWS Region in your Lightsail account\.
   + Must contain 2 to 255 characters\.
   + Must start and end with an alphanumeric character or number\.
   + Can include alphanumeric characters, numbers, periods, dashes, and underscores\.

1. Choose one of the following options to add tags to your instance:
   + **Add key\-only tags** or **Edit key\-only tags** \(if tags have already been added\)\. Enter your new tag into the tag key text box, and press **Enter**\. Choose **Save** when you’re done entering your tags to add them, or choose **Cancel** to not add them\.  
![\[Key-only tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-key-only-tags.png)
   + **Create a key\-value tag**, then enter a key into the **Key** text box, and a value into the **Value** text box\. Choose **Save** when you’re done entering your tags, or choose **Cancel** to not add them\.

     Key\-value tags can only be added one at a time before saving\. To add more than one key\-value tag, repeat the previous steps\.  
![\[Key-value tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-key-value-tag.png)
**Note**  
For more information about key\-only and key\-value tags, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

1. Choose **Create instance**\.

   The instance requires a few minutes to provision and become available after you create it\.
**Note**  
If you want to use Plesk on Amazon Lightsail for web hosting, you should [attach a static IP address to your instance](lightsail-create-static-ip.md)\. If you attach a static IP, you will need to reboot your instance in Lightsail before you can log into it for the first time\.

## Configure a username and password for your Plesk instance<a name="first-time-login-instructions-plesk"></a>

Complete the following steps to configure a username and password for your Plesk instance, and sign in to the Plesk panel for the first time\.

1. In the **Instances** tab of the Lightsail home page, choose the SSH quick connect icon for the Plesk instance that you want to set up\.  
![\[Connect to your Plesk on Amazon Lightsail instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/connect-quickly-to-your-plesk-instance-terminal.png)

1. Enter the following command\.

   ```
   sudo plesk login | grep -v internal:8
   ```

   You should see a result similar to the following example\.  
![\[One-time sign in for your Plesk instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/plesk-one-time-sign-in.png)
**Important**  
If you recently attached a static IP to your Plesk instance, you might get a one\-time login URL that uses the old public IP address\. Reboot the instance, and run the above command again to get a one\-time login URL that uses the new static IP address\.

1. Highlight the URL shown in the browser\-based SSH window, then choose the clipboard icon, and copy the URL to your local clipboard\.  
![\[The clipboard for the web-based SSH session.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/plesk-clipboard-copy.png)

1. Open a new browser window, and browse to the URL that you copied\.

   You might see a browser warning that your connection is not private, not secure, or that there’s a security risk\. This happens because your Plesk instance does not yet have an SSL/TLS certified applied to it\. The prompt may be different than what is shown in the following example depending on the browser you use\.  
![\[Chrome warning for private connection.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/chrome-private-connection.png)

1. Complete one of the following steps depending on the browser that you use:
   + **Chrome** — Choose **Advanced**, and then choose **Proceed** to continue to the Plesk set up page\.
   + **Edge** — Choose **Details**, and then choose **Go on to the webpage \(Not recommended\)** to continue to the Plesk set up page\.
   + **Firefox** — Choose **Advanced**, and then choose **Accept the Risk and Continue** to continue to the Plesk set up page\.
   + **Internet Explorer** — Choose **More information**, and then choose **Go on to the webpage \(Not recommended\)** to continue to the Plesk set up page\.

1. Enter your contact name, email address, and password\.

   In this page, you can change the default `admin` contact name if you prefer to use something different\. However, that is only the display name; your username to sign in to Plesk will continue to be `admin`\.  
![\[Configuring your username, and password, for Plesk.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/plesk-sign-in-configuration.png)

1. Confirm that you accept the end\-user license agreement, and choose **Enter Plesk**\.

   If successful, you will be signed in to the Plesk panel where you can add your domain, and begin managing your websites\.  
![\[The Plesk panel.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/plesk-panel.png)

If you need to sign in again later, just navigate to `https://PublicIPAddress:8443`\. Replace *PublicIPAddress* with the public IP address or static IP address of your instance\. For example, `https://192.0.2.0/:8443`\. Then enter the username and password you created earlier to sign in to the Plesk panel\.

For more information about using Plesk, see [Getting Started with Managing Websites in Plesk](https://docs.plesk.com/en-US/obsidian/quick-start-guide/read-me-first.74371/) in the *Plesk Documentation and Help Portal*\.