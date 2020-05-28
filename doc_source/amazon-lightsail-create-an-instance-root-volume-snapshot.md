# Creating a snapshot of an instance root volume in Amazon Lightsail<a name="amazon-lightsail-create-an-instance-root-volume-snapshot"></a>

 *Last updated: February 7, 2019* 

Back up an instance root volume in Amazon Lightsail by creating a snapshot of the system disk\. Then, access the files in the backup by creating a new block storage disk from the snapshot and attaching it to another instance\. Do this if you need to:
+ Recover data from the root volume of a botched instance\.
+ Create a backup of your instance's root volume, as you would for a block storage disk\.

You create the instance root volume snapshot using the AWS Command Line Interface \(AWS CLI\)\. After you create the snapshot, use the Lightsail console to create a block storage disk from the snapshot\. Then, attach it to a running instance, and access it from that instance\.

**Contents**
+ [Step 1: Complete the prerequisites](#instance-root-volume-snapshot-prerequisites)
+ [Step 2: Create an instance root volume snapshot](#create-instance-root-volume-snapshot)
+ [Step 3: Create a block storage disk from a snapshot and attach it to an instance](#create-block-storage-disk-from-snapshot)
+ [Step 4: Access a block storage disk from an instance](#access-block-storage-disk-from-an-instance)

## Step 1: Complete the prerequisites<a name="instance-root-volume-snapshot-prerequisites"></a>

If you haven't done so already, install and configure the AWS CLI\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

## Step 2: Create an instance root volume snapshot<a name="create-instance-root-volume-snapshot"></a>

Open a Terminal or Command Prompt window, then type the following command to create an instance root volume snapshot\.

```
aws lightsail create-disk-snapshot --region AWSRegion --instance-name InstanceName --disk-snapshot-name DiskSnapshotName
```

In the command, replace:
+ *AWSRegion* with the AWS Region of the instance\.
+ *InstanceName* with the name of the instance whose root volume you want to back up\.
+ *DiskSnapshotName* with the name of the new disk snapshot to be created\.

**Example:**

```
aws lightsail create-disk-snapshot --region us-west-2 --instance-name Amazon_Linux-32MB-Oregon-1 --disk-snapshot-name root-volume-linux
```

If successful, you will see a result similar to the following:

![\[Back up an instance root volume in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-create-root-volume-disk-snapshot.png)

Wait a few minutes for the snapshot to be created\. After it’s created, you can view it in the Lightsail home page by choosing the **Snapshots** tab and scrolling to the Disk Snapshots section, as shown in the following example\.

![\[Root volume disk snapshot in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-root-volume-disk-snapshot.png)

## Step 3: Create a block storage disk from a snapshot and attach it to an instance<a name="create-block-storage-disk-from-snapshot"></a>

Create a new block storage disk from the instance root volume snapshot and attach it to another instance if you must access its contents\. Do this if you need to recover data from the root volume of a botched instance\.

**Note**  
The new block storage disk is created in the same AWS Region as the source snapshot\. To create the block storage disk in a different Region, copy the snapshot to the desired Region, and then create a new disk from the copied snapshot\. For more information, see [Copying snapshots from one AWS Region to another in Amazon Lightsail](amazon-lightsail-copying-snapshots-from-one-region-to-another.md)\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Snapshots** tab\.

1. Choose the actions menu icon \(⋮\) displayed next to the root volume disk snapshot that you want to use, then choose **Create new disk**\.

1. Choose an Availability Zone for the disk, or accept the default\.

1. Choose a size for the disk that is equal to or greater than the source disk\.

1. Enter a name for the disk\.

   Resource names:
   + Must be unique within each AWS Region in your Lightsail account\.
   + Must contain 2 to 255 characters\.
   + Must start and end with an alphanumeric character or number\.
   + Can include alphanumeric characters, numbers, periods, dashes, and underscores\.

1. Choose one of the following options to add tags to your disk:
   + **Add key\-only tags** or **Edit key\-only tags** \(if tags have already been added\)\. Enter your new tag into the tag key text box, and press **Enter**\. Choose **Save** when you’re done entering your tags to add them, or choose **Cancel** to not add them\.  
![\[Key-only tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-key-only-tags.png)
   + **Create a key\-value tag**, then enter a key into the **Key** text box, and a value into the **Value** text box\. Choose **Save** when you’re done entering your tags, or choose **Cancel** to not add them\.

     Key\-value tags can only be added one at a time before saving\. To add more than one key\-value tag, repeat the previous steps\.  
![\[Key-value tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-key-value-tag.png)
**Note**  
For more information about key\-only and key\-value tags, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

1. Choose **Create disk**\.

1. After the disk is created, choose the instance that you want to attach the disk to in the **Select an instance** drop\-down menu\. This is shown in the following example\.  
![\[Attach a snapshot to an instance in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-attach-root-volume-disk.png)

1. Choose **Attach** to attach the disk to the selected instance\.

   The disk is now attached to the instance\. Next, make it accessible to the applicable operating system by mounting it on Linux, or bringing it online on Windows\. For more information, see the following **Access the block storage from an instance** section of this guide\.

## Step 4: Access a block storage disk from an instance<a name="access-block-storage-disk-from-an-instance"></a>

To access a block storage disk after attaching it to an instance, you must mount it on Linux or Unix, or bring it online on Windows\.

**Mount and access a block storage disk on a Linux or Unix instance**

1. On the [Lightsail home page](https://lightsail.aws.amazon.com/), choose the browser\-based SSH client icon for the Linux or Unix instance to which you attached the block storage disk\.  
![\[The browser-based SSH icon in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ssh-quick-connect.png)

1. After the browser\-based SSH client is connected, enter the following command to view the block storage disk devices attached to the instance:

   ```
   lsblk
   ```

   You should see a result similar to the following example\. In this example, `xvdf1` is the block storage disk attached to the instance that is not yet mounted because it doesn’t have a mount point\. Also, the result omits `/dev/` from the device name, so the device name is actually `/dev/xvdf1`\.  
![\[Blocked storage devices attached to a Linux or Unix instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-attached-block-storage-devices.png)

1. Enter the following command to create a mount point for the block storage disk\.

   ```
   sudo mkdir MountPoint
   ```

   In the command, replace *MountPoint* with the name of the directory where the block storage disk will be mounted and accessible\.

   **Example:**

   ```
   sudo mkdir xvdf
   ```

1. Enter the following command to mount the block storage disk to the mount point you created in the previous step\.

   ```
   sudo mount /dev/DeviceName MountPoint
   ```

   In the command, replace:
   + *DeviceName* with the name of the block storage disk device\.
   + *MountPoint* with the mount point directory that you created in the previous step\.

   **Example:**

   ```
   sudo mount /dev/xvdf1 xvdf
   ```

1. Enter the following command to view the block storage disk devices attached to the instance:

   ```
   lsblk
   ```

   You should see a result similar to the following example\. In this example, the *xvdf1* device is now mounted and accessible at the */home/ec2\-user/xvdf* directory\. You can now access block storage disk and its contents by going to the mount point directory\.  
![\[Blocked storage devices attached to a Linux or Unix instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-attached-block-storage-devices-mounted.png)

**Bring a block storage disk online and access it on a Windows instance**

1. On the [Lightsail home page](https://lightsail.aws.amazon.com/), choose the browser\-based RDP client icon for the Windows instance to which you attached the block storage disk\.  
![\[The browser-based RDP icon in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-rdp-quick-connect.png)

1. After the browser\-based SSH client is connected, search for **Computer Management** in the Windows taskbar, then choose **Computer Management** from the results\.  
![\[Computer Managmeent on a Windows instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-windows-computer-management.png)

1. In the left navigation menu of the **Computer Management** console, choose **Disk Management**, as shown in the following example\.  
![\[Disk Management on a Windows instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-windows-disk-management.png)

1. Locate the disk that you recently attached to the instance\. It should be labeled as Offline\.

1. Right\-click the **Offline** label, then choose **Online**\.  
![\[Offline disk on a Windows instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-windows-disk-management-offline.png)

   The disk should now be labeled as **Online**, and a drive letter should be associated with it\. You can now access the block storage disk and its contents by opening File Explorer and browsing to the designated drive letter\.  
![\[Online disk on a Windows instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-windows-disk-management-online.png)