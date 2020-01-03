# Set up and configure Plesk on Lightsail<a name="set-up-and-configure-plesk-stack-on-lightsail"></a>

 *Last updated: January 2, 2020* 

You can create a Plesk hosting stack in Lightsail that includes the following features\.
+ WordPress Toolkit, featuring automation in a graphical user interface
+ Let's Encrypt support for SSL certificates and configuring encrypted \(HTTPS\) traffic on a single instance
+ FTP access to transfer files to and from your instance
+ Docker Proxy Rules
+ Web\-based server management and security tools, including Plesk Firewall, Logs, and ModSecurity

## Create a Lightsail instance running Plesk<a name="create-plesk-instance"></a>

1. On the Lightsail home page, choose **Create instance**\.

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
![\[Key-only tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/aa4810f664dabff907209ee92babaa14/images/amazon-lightsail-key-only-tags.png)
   + **Create a key\-value tag**, then enter a key into the **Key** text box, and a value into the **Value** text box\. Choose **Save** when you’re done entering your tags, or choose **Cancel** to not add them\.

     Key\-value tags can only be added one at a time before saving\. To add more than one key\-value tag, repeat the previous steps\.  
![\[Key-value tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/aa4810f664dabff907209ee92babaa14/images/amazon-lightsail-key-value-tag.png)
**Note**  
For more information about key\-only and key\-value tags, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

1. Choose **Create instance**\.
**Note**  
If you want to use Plesk on Amazon Lightsail for web hosting, you need to [attach a static IP address to your instance](lightsail-create-static-ip.md)\. If you attach a static IP, you will need to reboot your instance in Lightsail before you can log into it for the first time\.

## Log in to your instance and set up your account and Webspace<a name="first-time-login-instructions-plesk"></a>

The following instructions are for your first\-time login to your Lightsail instance running Plesk\.

1. On the Lightsail home page, under **Instances**, choose the terminal connection icon on your Plesk on Amazon Lightsail instance to manage it\.  
![\[Connect to your Plesk on Amazon Lightsail instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/aa4810f664dabff907209ee92babaa14/images/connect-quickly-to-your-plesk-instance-terminal.png)

1. Enter the following command\.

   ```
   sudo plesk login | grep -v internal:8
   ```

   You should see a result similar to the following:

   ```
   https://192.0.2.0:1234/login?secret=12345EXAMPLESECRET.
   ```

1. Copy the URL to the clipboard by choosing the copy icon\.

1. Paste the URL into a browser\.

   You're taken to the Plesk Web Admin Edition **Settings** page\.

1. By default, Lightsail generates and assigns a **Full hostname** to the instance once you start it\.

   Some spam filters \(including the default Plesk greylisting\) treat mail sent from servers with such hostnames as spam\. We recommend using a registered domain name as the server hostname\.

1. The **Default IP address** should be prepopulated with your private IP address where it says **Select an address**\.

1. Change the default administrator password to a strong password\.

   If you forget this password, you can re\-run the following command: `sudo plesk login | grep -v internal:8`\. The Plesk Websites and Domains dashboard also has a username and password recovery feature\.

1. Choose **OK**\.

1. On the **Administrator information** page, fill in your **Name**, **Email**, and any other fields\.

1. Accept the **End\-User License Agreement**, and then choose **OK**\.

1. On the **Create Your Webspace** page, create a **username** and **password**, and then choose **OK**\.

   If successful, you're logged into the Plesk dashboard\.  
![\[Plesk dashboard\]](https://d9yljz1nd5001.cloudfront.net/en_us/aa4810f664dabff907209ee92babaa14/images/plesk-admin-dashboard.png)

   To log in again, just navigate to `https://public IP or static IP of instance:8443` and log in using username 'admin' and the password you created earlier\.