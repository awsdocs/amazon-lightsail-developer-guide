# Creating a snapshot of your Windows Server instance in Amazon Lightsail<a name="prepare-windows-based-instance-and-create-snapshot"></a>

 *Last updated: August 9, 2018* 

A snapshot is a copy of the system disk and original configuration of an instance\. The snapshot includes such information as memory, CPU, disk size, and data transfer rate\. For more information, see [Snapshots in Amazon Lightsail](understanding-instance-snapshots-in-amazon-lightsail.md)\.

To create a snapshot of your Windows Server instance in Lightsail, first create a backup snapshot\. Next, create a second snapshot using a special utility known as System Preparation \(Sysprep\)\. Sysprep generalizes the Windows Server installation so that the instance can be backed up as a snapshot\. Then, when you create an instance from that snapshot, you have an out\-of\-box experience as if you were running that Windows instance for the first time\.

**Contents**
+ [Step 1: Create a backup snapshot before running Sysprep](#lightsail-create-a-backup-snapshot)
+ [Step 2: Connect to your instance and shut it down using Sysprep](#lightsail-connect-and-shutdown-instance-using-sysprep)
+ [Step 3: Create a snapshot after running Sysprep](#lightsail-create-snapshot-after-running-sysprep)

**Note**  
To create a snapshot of a Linux or Unix instance, see Create a snapshot of your Linux or Unix instance in Amazon Lightsail\.

## Step 1: Create a backup snapshot before running Sysprep<a name="lightsail-create-a-backup-snapshot"></a>

When you run Sysprep to create a snapshot, system\-specific information is removed from your instance\. This may have unintended consequences for the applications running on the instance\. Therefore, you should first create a backup snapshot before running Sysprep to make sure that you have an alternate snapshot if something goes wrong\.

When you create a snapshot before running Sysprep, instances that you create using the backup snapshot have the same administrator password as the original instance\. You cannot connect to those instances using the browser\-based RDP client in the Lightsail console\. However, you can connect using your own RDP client and the same administrator password as the original instance\. 

**To create a backup snapshot before running Sysprep**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the name of the Windows Server instance for which you want to create a snapshot\.

1. Choose **Stop** at the top of the instance management page to stop your instance\.  
![\[Stop your Windows Server instance before creating a snapshot.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-stop-a-windows-instance.png)
**Note**  
Stopping an instance makes any website or service on it unavailable until you start it again\.

1. Choose the **Snapshots** tab\.

1. Under the **Manual snapshots** section of the page, choose **Create snapshot**, then enter a name for your snapshot\.

   Resource names:
   + Must be unique within each AWS Region in your Lightsail account\.
   + Must contain 2 to 255 characters\.
   + Must start and end with an alphanumeric character or number\.
   + Can include alphanumeric characters, numbers, periods, dashes, and underscores\.

1. Choose **Create**\.

1. At the prompt, choose **Create snapshot** again to confirm\.

   The snapshot process takes a few minutes to complete\.

1. After the snapshot is created, choose **Start** at the top of the instance management page to start your instance again\.

## Step 2: Connect to your instance and shut it down using Sysprep<a name="lightsail-connect-and-shutdown-instance-using-sysprep"></a>

Now that you have a backup snapshot, it’s time to run Sysprep on your Windows Server instance\. This causes the instance to shut down so that you can take a snapshot\. For more information about Sysprep, see [Sysprep Overview](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/sysprep--system-preparation--overview) in the Microsoft documentation\.

In this step, connect to your instance and run Sysprep through a preinstalled application\. The application is called **EC2Launch** on Windows Server 2016 instances, and **EC2Config** on Windows Server 2012 instances\.

**To connect to your instance and run Sysprep**

1. On the instance management page, choose the **Connect** tab, then choose **Connect using RDP**\.

   The browser\-based RDP window opens, as shown in the following example:  
![\[The browser-based RDP client in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-web-based-rdp-client.png)

1. On the taskbar, choose the Windows icon, or choose **Win** to open the Start menu\.

1. Choose one of these options:
   + On Windows Server 2016 instances, choose **Start**, then choose **Ec2LaunchSettings**\.
   + On Windows Server 2012 instances, choose **Start**, then choose **Ec2ConfigService Settings**\.

1. In the Administrator Password section, choose **Random \(Retrieve from console\)**, then choose **Shutdown with Sysprep**\.

   On the Ec2ConfigService Settings application found in Windows Server 2012 instances, the **Random \(Retrieve from console\)** and **Shutdown with Sysprep** options are listed under the **Launch** tab\.  
![\[The Ec2 Launch Settings application on Windows Server 2016 instances.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ec2launchsettings.png)

1. Choose **Yes** to confirm that you want to run Sysprep and shut down the instance\.

   Your instance begins running Sysprep, your RDP connection shuts down, and your Lightsail instance stops running after a few minutes\.

## Step 3: Create a snapshot after running Sysprep<a name="lightsail-create-snapshot-after-running-sysprep"></a>

After your instance is in a stopped state, create a snapshot in the Lightsail console\. When you create a snapshot of your Windows Server instance after running Sysprep, all instances that you create based on the snapshot have a unique administrator password\. You can connect to those instances by using the browser\-based RDP client in the Lightsail console\.

**To create a snapshot in the Lightsail console**

1. Toggle back to the Lightsail console\.

1. On the instance management page for your Windows Server instance, choose the **Snapshots** tab

1. Under the **Manual snapshots** section of the page, choose **Create snapshot**, then enter a name for your snapshot\.

   Resource names:
   + Must be unique within each AWS Region in your Lightsail account\.
   + Must contain 2 to 255 characters\.
   + Must start and end with an alphanumeric character or number\.
   + Can include alphanumeric characters, numbers, periods, dashes, and underscores\.

1. Choose **Create**\.

1. At the prompt, choose **Create snapshot** to confirm that you prepared the instance for the snapshot\.

   The snapshot process takes a few minutes to complete\.

1. After the snapshot is created, choose **Start** at the top of the instance management page to start your instance again\.

   At this point, you should have two snapshots of your Windows Server instance as shown in the following example:  
![\[Recent snapshots in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-recent-windows-snapshots.png)

   Use the Sysprep snapshot to create new instances\. Use the backup snapshot only if the original instance doesn’t function as expected after running Sysprep\.

## Next steps<a name="windows-snapshot-next-steps"></a>

Now that you have the Sysprep and backup snapshots, here are some next steps you should complete:
+ Connect to your original instance, and confirm that your applications on it function as expected after running Sysprep\. For more information, see [Connect to your Windows Server instance using Amazon Lightsail](connect-to-your-windows-based-instance-using-amazon-lightsail.md)\.
+ Create a new instance using the Sysprep snapshot, connect to it, and confirm that your applications on the new instance function as expected\. For more information, see [Creating an instance from a snapshot in Amazon Lightsail](lightsail-how-to-create-instance-from-snapshot.md)\.
+ Delete your backup snapshot after you confirm that the original instance functions as expected after running Sysprep\. For more information, see [Deleting snapshots in Amazon Lightsail](amazon-lightsail-deleting-snapshots.md)\.
+ If your instance doesn't function as expected after running Sysprep, then follow the steps in [Creating an instance from a snapshot in Amazon Lightsail](lightsail-how-to-create-instance-from-snapshot.md) to create a new instance from the backup snapshot\.