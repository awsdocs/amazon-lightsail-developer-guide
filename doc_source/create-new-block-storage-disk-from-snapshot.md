# Creating a block storage disk from a snapshot in Amazon Lightsail<a name="create-new-block-storage-disk-from-snapshot"></a>

 *Last updated: November 14, 2017* 

You can create a new block storage disk from a disk snapshot\. If you're creating an entirely new disk, see one of the following topics instead: [Create additional block storage disks \(Linux/Unix\)](create-and-attach-additional-block-storage-disks-linux-unix.md) or [Creating and attaching block storage disks to your Windows Server instance in Amazon Lightsail](create-and-attach-additional-block-storage-disks-windows.md)\.

You can use the snapshot of a block storage disk as a baseline for new disks or for data backup\. If you make periodic snapshots of a disk, the snapshots are incremental\. Only the blocks on the disk that have changed after your last snapshot are saved in the new snapshot\. Even though snapshots are saved incrementally, the snapshot deletion process is designed so that you need to retain only the most recent snapshot to restore the entire disk\. To create a snapshot of your block storage disk, see [Creating a snapshot of your block storage disk in Amazon Lightsail](create-block-storage-disk-snapshot.md)\.

## Step 1: Find your disk snapshot and choose to create a new disk<a name="find-your-snapshot-and-choose-create-new-disk"></a>

You can create a new instance from a disk snapshot in one of two places in Lightsail: on the **Snapshots** tab of the Lightsail home page, or on the **Snapshots** tab of the disk management page\.

**From the Lightsail home page**

1. On the Lightsail home page, choose the **Snapshots** tab\.  
![\[Snapshots tab on the Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-home-page-snapshots-tab.png)

1. Find the name of the disk, then expand the node below it to see all of the available snapshots of that disk\.  
![\[Expand the disk snapshots in the Snapshots tab of the Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-snapshots-tab-available-disk-snapshots.png)

1. Choose the actions menu icon \(⋮\) next to the snapshot from which you want to create your new disk, and then choose **Create new disk**\.  
![\[Create a new disk from a snapshots in the Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-action-menu-create-new-disk.png)

**From the disk management page in Lightsail**

1. On the Lightsail home page, choose the **Storage** tab\.

1. Choose the name of the disk for which you want to view snapshots\.

1. Choose the **Snapshots** tab\.  
![\[Choose the Snapshots tab from the disk management page\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-disk-management-snapshots-tab.png)

1. Under the **Manual snapshots** section of the page, choose the actions menu icon \(⋮\) next to the snapshot from which you want to create a new disk, and choose **Create new disk**\.  
![\[Use the actions menu to create a new disk from a snapshot\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/create-new-disk-from-snapshot-disk-management-page.png)

## Step 2: Create a new disk from a disk snapshot<a name="create-new-disk-from-disk-snapshot"></a>

1. Choose an Availability Zone for your new disk, or accept the default \(e\.g\., `us-east-2a`\)\.

   You must create the new disk in the same AWS Region as the source disk\.

1. Choose a size for your new disk that is equal to or greater than the source snapshot\.

1. Enter a name for your disk\.

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