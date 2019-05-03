# Block storage disk snapshots in Lightsail<a name="block-storage-disk-snapshots-in-amazon-lightsail"></a>

**Note**  
A disk snapshot is an incremental backup of an additional block storage disk\. You can use disk snapshots to back up your data, or as a baseline for creating new disks from a backup\.

 *Last updated: November 14, 2017* 

You can back up the data on your Lightsail block storage disks by taking point\-in\-time snapshots\. These disk snapshots can be used as a baseline for new disks or as data backup\. [Learn how to create a disk snapshot](create-block-storage-disk-snapshot.md)

Snapshots are incremental backups, which means that only the blocks on the device that have changed after your most recent snapshot are saved\. This minimizes the time required to create the snapshot and saves on storage costs by not duplicating data\. When you delete a snapshot, only the data unique to that snapshot is removed\. Each snapshot contains all of the information needed to restore your data \(from the moment when the snapshot was taken\) to a new disk\.

When you create a new disk based on a snapshot, the new disk begins as an exact replica of the original disk that was used to create the snapshot\. The replicated disk loads data lazily in the background so that you can begin using it immediately\. If you access data that hasn't been loaded yet, the disk immediately downloads the requested data from Amazon S3, and then continues loading the rest of the disk's data in the background\.

The snapshot you create is a copy of the disk and matches the original size and configuration\. If you choose to create a new disk from this snapshot, you must choose the same size or larger size disk\. 

For more information, see:
+ [Create a new block storage disk from a snapshot in Amazon Lightsail](create-new-block-storage-disk-from-snapshot.md)
+ [Amazon EBS Snapshots](http://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/EBSSnapshots.html) in the *Amazon EC2 User Guide*\.