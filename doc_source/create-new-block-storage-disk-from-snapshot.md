# Create a new block storage disk from a snapshot in Amazon Lightsail<a name="create-new-block-storage-disk-from-snapshot"></a>

 *Last updated: November 14, 2017* 

You can create a new block storage disk from a disk snapshot\. If you're creating an entirely new disk, see one of the following topics instead: [Create additional block storage disks \(Linux/Unix\)](create-and-attach-additional-block-storage-disks-linux-unix.md) or [Creating and attaching block storage disks to your Windows Server instance in Amazon Lightsail](create-and-attach-additional-block-storage-disks-windows.md)\.

You can use the snapshot of a disk as a baseline for new disks or for data backup\. If you make periodic snapshots of a disk, the snapshots are incremental\. Only the blocks on the device that have changed after your last snapshot are saved in the new snapshot\. Even though snapshots are saved incrementally, the snapshot deletion process is designed so that you need to retain only the most recent snapshot to restore the entire disk\. If you still need to create a snapshot, see the following topic: [Create a disk snapshot](create-block-storage-disk-snapshot.md)\.

## Step 1: Find your disk snapshot and choose to create a new disk<a name="find-your-snapshot-and-choose-create-new-disk"></a>

You can create a new instance from a disk snapshot in one of two places in Lightsail: on the **Snapshots** tab of the home page, or on the **Storage** tab of the disk management page\.

**From the Lightsail home page**

1. On the home page, choose **Snapshots**\.

1. Find the disk name, and then expand to see all your disk snapshots \(e\.g\., choose **1 disk snapshot**\)\.  
![\[Expand the disk snapshots and then use the shortcut menu to create a new disk from a snapshot\]](https://d9yljz1nd5001.cloudfront.net/en_us/b2fb86c05aa70ef4defbdc74847a0bb8/images/create-new-disk-from-snapshot-snapshots-tab-home-page.gif)

1. Use the shortcut menu next to the snapshot from which you want to create your new disk, and then choose **Create new disk**\.

**From the disk management page in Lightsail**

1. Choose the **Snapshots** tab\.  
![\[Choose the Snapshots tab from the disk management page\]](https://d9yljz1nd5001.cloudfront.net/en_us/b2fb86c05aa70ef4defbdc74847a0bb8/images/lightsail-disk-management-page-choose-snapshots-tab.png)

1. Under **Recent snapshots**, find the snapshot from which you want to create your new disk\. Use the shortcut menu and choose **Create new disk**\.  
![\[Use the shortcut menu to create a new disk from a snapshot\]](https://d9yljz1nd5001.cloudfront.net/en_us/b2fb86c05aa70ef4defbdc74847a0bb8/images/create-new-disk-from-snapshot-disk-management-page.gif)

## Step 2: Create a new disk from a disk snapshot<a name="create-new-disk-from-disk-snapshot"></a>

1. Choose an Availability Zone for your new disk, or accept the default \(e\.g\., `us-east-2a`\)\.

   You must create the new disk in the same AWS Region as the source disk\.

1. Choose a size for your new disk that is equal to or greater than the source snapshot\.

1. Enter a name for your disk\.

1. Choose one of the following options to add tags to your disk:
   + **Add key\-only tags** or **Edit key\-only tags** \(if tags have already been added\)\. Enter your new tag into the tag key text box, and press **Enter**\. Choose **Save** when you’re done entering your tags to add them, or choose **Cancel** to not add them\.  
![\[Key-only tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/b2fb86c05aa70ef4defbdc74847a0bb8/images/amazon-lightsail-key-only-tags.png)
   + **Create a key\-value tag**, then enter a key into the **Key** text box, and a value into the **Value** text box\. Choose **Save** when you’re done entering your tags, or choose **Cancel** to not add them\.

     Key\-value tags can only be added one at a time before saving\. To add more than one key\-value tag, repeat the previous steps\.  
![\[Key-value tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/b2fb86c05aa70ef4defbdc74847a0bb8/images/amazon-lightsail-key-value-tag.png)
**Note**  
For more information about key\-only and key\-value tags, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

1. Choose **Create disk**\.