# Creating and attaching a block storage disk to your Windows Server instance in Amazon Lightsail<a name="create-and-attach-additional-block-storage-disks-windows"></a>

 *Last updated: September 5, 2018* 

If you need additional storage space, you can create and attach block storage disks to your Windows Server instance in Amazon Lightsail\. For more information about block storage disks, see [Block storage disks in Lightsail](elastic-block-storage-and-ssd-disks-in-amazon-lightsail.md)\.

This guide shows you how to create a new block storage disk and attach it to your Windows Server instance using the Lightsail console\. It also describes how to connect to your Windows Server instance using RDP so that you can bring the disk online and initialize it\.

This procedure is the same in Windows Server 2016 and Windows Server 2012 R2\.

**Note**  
If you have a Linux or Unix instance, see [Create and attach disks to your Linux or Unix instances in Amazon Lightsail](create-and-attach-additional-block-storage-disks-linux-unix.md)\.

## Step 1: Create a new block storage disk and attach it to your instance<a name="create-attach-new-disk-to-windows-server-instance"></a>

Create a new block storage disk and attach it to your instance using the Amazon Lightsail console\.

**To create a new block storage disk and attach it to your instance**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Choose the **Storage** tab, then choose **Create disk**\.

1. Choose the AWS Region and Availability Zone where your Lightsail instance is located\.

1. Choose a disk size\.

1. Enter a name for your storage disk\.

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

   After a few seconds, the disk is created and you can view information about it on the disk management page\.

1. Choose your instance from the list, and then choose **Attach** to attach the new disk to your instance\.  
![\[Choosing your instance from the dropdown list and attaching the disk to the instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/animated-gif-attach-disk-to-windows-server-instance.gif)

   Continue to the [Step 2: Connect to your instance and bring the block storage disk online](#connect-to-windows-server-instance-using-rdp-format-mount-disk) section of this guide to bring the block storage disk online\.

## Step 2: Connect to your instance and bring the block storage disk online<a name="connect-to-windows-server-instance-using-rdp-format-mount-disk"></a>

Connect to your Windows Server instance and use the Disk Management utility to bring the recently attached block storage disk online\.

**To connect to your instance and bring the block storage disk online**

1. Navigate to the [Lightsail console home page](https://lightsail.aws.amazon.com/)\.

1. Choose the name of the instance to which you attached the additional storage disk earlier in this guide\.

1. Under the **Connect** tab, choose **Connect using RDP**\.

1. On the Windows Start menu, search for **Computer Management**, and in the search results, choose **Computer Management**\.  
![\[Create and format hard disks search in Windows\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-computer-management-search.png)

1. In Computer Management, in the left pane, choose **Disk Management**\.

1. In the bottom pane of the Disk Management utility, select the disk labeled as **Unknown / Offline**\. This is the block storage disk that you attached to your instance earlier in this guide\.  
![\[Unallocated disk attached to your Windows Server instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/lightsail-disk-management-windows-server-2016-unallocated.png)

1. With the disk selected, on the **Action** menu, choose **All Tasks**, and then choose **Online**\.  
![\[Bring the block storage disk online using the Action menu\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/lightsail-windows-server-2016-disk-management-action-all-tasks-online.png)

   You should see the status of the block storage disk update to **Not Initialized**\. The block storage disk is not yet online\. Continue to the [Step 3: Initialize the block storage disk](#initialize-your-disk-windows-server-lightsail) section of this guide to initialize the block storage disk\.

## Step 3: Initialize the block storage disk<a name="initialize-your-disk-windows-server-lightsail"></a>

Initialize the block storage disk so that you can format it\.

**Important**  
If you're mounting a disk that already has data on it, such as a disk that you created from a snapshot, be sure that you don't reformat the disk and delete the existing data\.

**To initialize the block storage disk**

1. In the bottom pane of the Disk Management utility, select the disk labeled as **Unknown / Not initialized**\.  
![\[Unallocated disk attached to your Windows Server instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/lightsail-disk-management-windows-server-2016-not-initialized.png)

1. With the disk selected, on the **Action** menu, choose **All Tasks**, and then choose **Initialize Disk**\.  
![\[Initialize the block storage disk using the Action menu\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/lightsail-windows-server-2016-disk-management-action-all-tasks-initialize.png)

1. Choose the partition style for your new disk, and then choose **OK**\.
**Note**  
For more information about partition styles, see the [About partition styles \- GPT and MBR](https://docs.microsoft.com/en-us/windows-server/storage/disk-management/initialize-new-disks#about-partition-styles---gpt-and-mbr) article from Microsoft\.

   You should see the status of the block storage disk update to **Online**\. Continue to the [Step 4: Format the disk with a file system](#run-new-simple-volume-wizard-windows-server-lightsail) section of this guide to format your block storage disk with a file system\.

## Step 4: Format the disk with a file system<a name="run-new-simple-volume-wizard-windows-server-lightsail"></a>

Use the New Simple Volume wizard in Windows Server to assign a drive letter and format the disk with a file system\.

**To format the disk with a file system**

1. In the bottom pane of the Disk Management utility, select the partition on the block storage disk labeled as **Unallocated**\.  
![\[Unallocated disk attached to your Windows Server instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/lightsail-disk-management-windows-server-2016-unallocated-partition.png)

1. With the partition selected, on the **Action** menu, choose **All Tasks**, and then choose **New Simple Volume**\.  
![\[Begin the New Simple Volume wizard using the Action menu\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/lightsail-windows-server-2016-disk-management-action-all-tasks-new-simple-volume.png)

1. Follow the instructions in the New Simple Volume wizard to choose an NTFS, FAT32, or ReFS file system type and format the disk\.
**Note**  
For more information about each of these file systems, see the [NTFS overview](https://docs.microsoft.com/en-us/windows-server/storage/file-server/ntfs-overview), [Resilient File System \(ReFS\) overview](https://docs.microsoft.com/en-us/windows-server/storage/refs/refs-overview), and [Description of the FAT32 File System](https://support.microsoft.com/en-us/help/154997/description-of-the-fat32-file-system) articles from Microsoft\.

   When complete, you see a drive letter and the following message in the Disk Management utility\.  
![\[New Simple Volume wizard showing success in Windows Server 2016\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/windows-server-2016-new-volume-wizard-success.png)