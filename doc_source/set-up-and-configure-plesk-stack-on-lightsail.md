# Set up and configure Plesk on Lightsail<a name="set-up-and-configure-plesk-stack-on-lightsail"></a>

 *Last updated: May 7, 2017* 

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

   Plesk is not supported on the $3\.50 USD per month Lightsail plan\.

1. Enter a name for your instance\.

1. Choose one of the following options to add tags to your instance:
   + **Add key\-only tags** or **Edit key\-only tags** \(if tags have already been added\)\. Enter your new tag into the tag key text box, and press **Enter**\. Choose **Save** when you’re done entering your tags to add them, or choose **Cancel** to not add them\.  
![\[Key-only tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/1cade0c7e07039bf59652df47a09d228/images/amazon-lightsail-key-only-tags.png)
   + **Create a key\-value tag**, then enter a key into the **Key** text box, and a value into the **Value** text box\. Choose **Save** when you’re done entering your tags, or choose **Cancel** to not add them\.

     Key\-value tags can only be added one at a time before saving\. To add more than one key\-value tag, repeat the previous steps\.  
![\[Key-value tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/1cade0c7e07039bf59652df47a09d228/images/amazon-lightsail-key-value-tag.png)
**Note**  
For more information about key\-only and key\-value tags, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

1. Choose **Create instance**\.
**Note**  
If you want to use Plesk on Amazon Lightsail for web hosting, you need to [assign a static IP address to your instance](lightsail-create-static-ip.md)\. If you attach a static IP, you will need to reboot your instance in Lightsail before you can log into it for the first time\.

## Configure your firewall settings<a name="configure-plesk-firewall-settings"></a>

Before you can log in to your instance, you need to configure some firewall settings\.

1. From the Lightsail home page, under **Instances**, choose the name of the Plesk on Amazon Lightsail instance you want to manage\.

1. Choose the **Networking** tab\.

1. Under **Firewall**, choose **Add another**\.

1. Add the following entries, and choose **Save**:
   + Custom > TCP > 53
   + Custom > UDP > 53
   + Custom > TCP > 8443
   + Custom > TCP > 8447  
![\[Plesk firewall entries in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/1cade0c7e07039bf59652df47a09d228/images/amazon-lightsail-plesk-firewall.png)

   Port 8447 is needed for updates and upgrades under **Tools and Settings**\.

   Port 53 is needed for DNS management\.

1. \(Optional\) \- If you know what application you want to use, you can open other ports for them at this time\. For example, if you want to set up an FTP server, set up the following Custom TCP port ranges: `TCP 20-21` \(Active FTP\), `TCP 990` \(Implicit FTPS\), and `TCP 49152-65535` \(Passive FTP\)\.

   For more information about application\-specific ports, see [Installation and Prerequisites](https://docs.plesk.com/en-US/onyx/migration-guide/installation-and-prerequisites.75498/) in the Plesk documentation\.
**Note**  
For security reasons, we recommend that you allow access only to services you want to use\. Keep the ports corresponding to the services you do not want to use closed\.

## Log in to your instance and set up your account and Webspace<a name="first-time-login-instructions-plesk"></a>

The following instructions are for your first\-time login to your Lightsail instance running Plesk\.

1. On the Lightsail home page, under **Instances**, choose the terminal connection icon on your Plesk on Amazon Lightsail instance to manage it\.  
![\[Connect to your Plesk on Amazon Lightsail instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/1cade0c7e07039bf59652df47a09d228/images/connect-quickly-to-your-plesk-instance-terminal.png)

1. Type the following command\.

   ```
   sudo plesk login | grep -v internal:8
   ```

   You see a login URL like the following: https://12\.345\.678\.910:1234/login?secret=12345EXAMPLESECRET\.

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
![\[Plesk dashboard\]](https://d9yljz1nd5001.cloudfront.net/en_us/1cade0c7e07039bf59652df47a09d228/images/plesk-admin-dashboard.png)

   To log in again, just navigate to `https://public IP or static IP of instance:8443` and log in using username 'admin' and the password you created earlier\.