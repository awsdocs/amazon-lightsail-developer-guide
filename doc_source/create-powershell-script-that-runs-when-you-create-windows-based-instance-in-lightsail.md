# Configure your new Lightsail instance using Windows PowerShell or a batch script<a name="create-powershell-script-that-runs-when-you-create-windows-based-instance-in-lightsail"></a>

 *Last updated: October 16, 2017* 

When you create a Windows\-based instance, you can configure it using a Windows PowerShell script or any other batch script\. This is a one\-time script that runs right after your instance launches\. This topic shows the syntax of the scripts and provides an example to get you started\. We also show you how to test your script to see if it ran successfully\.

## Create an instance that launches and runs a PowerShell script<a name="windows-powershell-create-instance"></a>

The following procedure installs a tool called *chocolatey* on a new instance, right after the instance launches\.

1. On the Lightsail home page, choose **Create instance**\.

1. Choose the AWS Region and Availability Zone where you want to create your instance\.

1. Under **Select a platform**, choose **Microsoft Windows**\.

1. Choose **OS Only**, and then choose **Windows Server 2016**\.

1. Choose **Add launch script**\.

1. Type the following:

   ```
   <powershell>
   iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
   </powershell>
   ```
**Note**  
You must always wrap your PowerShell scripts in `<powershell></powershell>` tags\. You can enter non\-PowerShell commands or batch scripts using `<script></script>` tags or without any tags at all\.

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

## Verify that your script ran successfully<a name="windows-powershell-verify-script-ran-successfully"></a>

You can log in to your instance to verify that the script ran successfully\. It can take up to 15 minutes for a Windows\-based instance to be ready to accept RDP connections\. Once it's ready, log in using the browser\-based RDP client or configure your own RDP client\. For more information, see [Connect to your Windows\-based instance](connect-to-your-windows-based-instance-using-amazon-lightsail.md)\.

1. Once you can connect to your Lightsail instance, open a command prompt \(or open Windows Explorer\)\.

1. Change to the `Log` directory by typing the following:

   ```
   cd C:\ProgramData\Amazon\EC2-Windows\Launch\Log
   ```
**Note**  
In Windows Server 2012, the command is `cd C:\Program Files\Amazon\Ec2ConfigService\Logs`\.

1. Open `UserdataExecution.log` in a text editor, or type the following: `type UserdataExecution.log`\.

   You should see the following in your log file\.

   ```
   2017/10/11 20:32:12Z: <powershell> tag was provided.. running powershell content
   2017/10/11 20:32:13Z: Message: The output from user scripts: iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
   
   2017/10/11 20:32:13Z: Userdata execution done
   ```