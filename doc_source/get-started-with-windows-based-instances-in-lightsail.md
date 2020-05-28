# Get started with Windows Server\-based instances in Lightsail<a name="get-started-with-windows-based-instances-in-lightsail"></a>

 *Last updated: October 16, 2017* 

You can create Lightsail instances that run the Windows Server operating system \(OS\)\. We have two OS blueprints available: Windows Server 2016 or Windows Server 2012 R2\. In addition, we have a blueprint that comes preconfigured with SQL Server Express 2016\.

This topic provides information about choosing your software, creating your Windows Server\-based instance, and connecting to it\.

Learn more about [Windows Server on AWS](https://aws.amazon.com/windows/)

## Choose a Windows Server\-based instance<a name="choose-windows-based-instance-lightsail"></a>

There are three options for creating a Windows Server\-based instance in Lightsail\.

 **Windows Server 2016**   
Unless you need to run Windows Server 2012 R2 for some reason, we recommend using the latest version of Windows Server 2016\.  
Lightsail running Windows Server is a fast and dependable environment for deploying applications using the Microsoft Web Platform\. Lightsail enables you to run any compatible Windows\-based solution on the AWS high\-performance, reliable, cost\-effective, cloud computing platform\. Common Windows Server use cases include Enterprise Windows\-based application hosting, website and web service hosting, data processing, media transcoding, distributed testing, ASP\.NET application hosting, and any other application requiring Windows software\.  
 [Learn more about the Windows Server 2016 image](https://aws.amazon.com/marketplace/pp/B01M7SJEU7) 

 **Windows Server 2012 R2**   
Windows Server 2012 R2 is also available as a base operating system \(OS\)\. If you're migrating an application from somewhere else to Lightsail, and it's not compatible with Windows Server 2016, you may want to use this base OS instead\.  
You can use Windows Server 2012 R2 with the same use cases listed under Windows Server 2016\.  
 [Learn more about the Windows Server 2012 R2 image](https://aws.amazon.com/marketplace/pp/B00KQOWCAQ) 

 **SQL Server Express 2016**   
SQL Server Express is a relational database management system that is free to download, distribute, and use\. It comprises a database specifically targeted for embedded and smaller\-scale applications\. This Lightsail image runs on a base OS of Windows Server 2016\.  
 [Learn more about the SQL Server Express image](https://aws.amazon.com/marketplace/pp/B01MAZHH98) 

## Create a Windows Server\-based Lightsail instance<a name="create-windows-based-instance-lightsail"></a>

You can create a Windows Server\-based instance using the Lightsail console or by using the AWS Command Line Interface \(AWS CLI\)\.

**To create an instance using the console**

1. Sign in to Lightsail, and then go to the home page\.

1. Choose **Create instance**\.

1. Select an AWS Region where you want to create your Windows Server\-based Lightsail instance\.

   For example, `Ohio (us-east-2)`\.

1. Select the **Microsoft Windows** platform\.

1. To choose the Windows Server 2016 or 2012 R2 blueprint, choose **OS Only**\.

   To choose the SQL Server Express blueprint, choose **Apps \+ OS**\.

1. Choose your instance plan\.

   A plan includes a low, predictable cost and a machine configuration \(RAM, SSD, vCPU\), as well as data transfer\.
**Note**  
Some instance plans are not available for some blueprints\. For example, you can't use the two smallest plans with the SQL Server Express blueprint\. At a minimum, you must use the plan that has 2 GB RAM and 50 GB SSD, or choose one of the larger plans\.

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

**To create an instance using the AWS CLI**

1. If you haven't done so already, install and configure the AWS CLI\.

   For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a command prompt or a terminal window\.

1. If you haven't done so already, configure the AWS CLI using `aws configure` and select the AWS Region where you want to create your Lightsail resources\.

1. Type the following AWS CLI command to create a $40 USD per month Windows Server 2016 instance running in the Ohio region:

   ```
   aws lightsail create-instances --instance-names InstanceName --availability-zone us-east-2a --blueprint-id windows_server_2016_2017_09_13 --bundle-id medium_win_1_0
   ```

   In the command, replace *InstanceName* with the name of your new instance\.

   If successful, you'll see the following output from the AWS CLI\.

   ```
   {
       "operations": [
           {
               "status": "Started",
               "resourceType": "Instance",
               "isTerminal": false,
               "statusChangedAt": 1508086226.4,
               "location": {
                   "availabilityZone": "us-east-2a",
                   "regionName": "us-east-2"
               },
               "operationType": "CreateInstance",
               "resourceName": "my-windows-instance",
               "id": "344acdc8-f9c4-4eda-8232-12345EXAMPLE",
               "createdAt": 1508086225.467
           }
       ]
   }
   ```
**Note**  
To get a list of available blueprints, use the [get\-blueprints](http://docs.aws.amazon.com/cli/latest/reference/lightsail/get-blueprints.html) command\. To get a list of available bundles, use the [get\-bundles](http://docs.aws.amazon.com/cli/latest/reference/lightsail/get-bundles.html) command\. Learn more about getting the password for your instance using the [get\-instance\-access\-details](http://docs.aws.amazon.com/cli/latest/reference/lightsail/get-instance-access-details.html) command\.

## Connect to your instance<a name="connect-to-windows-based-instance-lightsail"></a>

Once you create your Windows Server\-based Lightsail instance, you can connect to it using either the browser\-based RDP client or the remote desktop client of your choice\.

**Note**  
After you create your instance, you may need to wait up to 15 minutes before you can connect to it\.

**To connect using the Lightsail browser\-based RDP client**

1. On the home page, choose the **Connect using RDP** icon next to your instance\.  
![\[The quickest way to connect to your Windows Server-based Lightsail instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/connect-to-windows-instance-using-rdp-connection-shortcut.png)

1. Alternately, you can connect to your instance from the shortcut menu or the instance management page\.

**To connect using your own RDP client**

1. To get your IP address, go to the Lightsail home page\.

1. Copy the IP address to the clipboard\.

1. Open an RDP client such as **Remote Desktop Connection** in Windows\.

1. Paste the IP address into the **Computer** field\.

1. Choose **Show Options**, and then type `Administrator` for your **User name**\.  
![\[Remote Desktop Connection application in Windows\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/remote-desktop-connection-windows-server-based-instance-lightsail.png)

1. Choose **Connect**\.

1. To get your password, go to the instance management page in Lightsail\.

   You can get to the instance management page by choosing the name of your instance \(or choosing **Manage** from the shortcut menu\) on the Lightsail home page\.

1. Choose **Show default password**\.

1. Copy the default password to the clipboard\.

1. Paste your password into **Remote Desktop Connection**, and then choose **Remember me** to prevent this dialog box from appearing in the future\.  
![\[Enter credentials in Remote Desktop Connection in Windows\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/remote-desktop-connection-enter-credentials-lightsail-windows.png)

1. Choose **OK**\.

1. Choose **Don't ask me again for connections to this computer**, and then choose **Yes**\.