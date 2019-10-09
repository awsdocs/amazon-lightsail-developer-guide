# Creating a snapshot of your block storage disk in Amazon Lightsail<a name="create-block-storage-disk-snapshot"></a>

 *Last updated: November 14, 2017* 

You can create disk snapshots in Lightsail as backups of your additional block storage disks\.

You can use the snapshot of a disk as a baseline for new disks or for data backup\. If you make periodic snapshots of a disk, the snapshots are incremental\. Only the blocks on the device that have changed after your last snapshot are saved in the new snapshot\. Even though snapshots are saved incrementally, the snapshot deletion process is designed so that you need to retain only the most recent snapshot to restore the entire disk\.

For more information, see [Snapshots in Amazon Lightsail](understanding-instance-snapshots-in-amazon-lightsail.md)\.

1. On the Lightsail home page, choose the **Storage** tab\.

1. Choose the block storage disk that you want to take a snapshot of, or choose **Manage** from the shortcut menu\.  
![\[Use the shortcut menu to manage your block storage disk\]](https://d9yljz1nd5001.cloudfront.net/en_us/cfefe1b500656f5beb2491eaf820d8f4/images/animated-gif-manage-block-storage-disk-shortcut-menu.gif)

1. Choose **Snapshots**\.

1. Type a name for your snapshot, and then choose **Create snapshot**\.