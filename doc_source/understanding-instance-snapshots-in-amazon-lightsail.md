# Snapshots in Amazon Lightsail<a name="understanding-instance-snapshots-in-amazon-lightsail"></a>

 *Last updated: October 2, 2019* 

You can create point\-in\-time snapshots of instances, databases, and block storage disks in Amazon Lightsail, and use them as baselines to create new resources or for data backup\. A snapshot contains all of the data that is needed to restore your resource \(from the moment when the snapshot was taken\)\. When you restore a resource by creating it from a snapshot, the new resource begins as an exact replica of the original resource that was used to create the snapshot\. You will be billed a [snapshot storage fee](https://aws.amazon.com/lightsail/pricing/) for snapshots on your Lightsail account; whether they are manual snapshots, automatic snapshots, copied snapshots, or system disk snapshots\. Your resources can fail at any time—create snapshots frequently to avoid permanently losing your data\.

**Contents**
+ [Manual snapshots](#manual-snapshots)
+ [Automatic snapshots](#automatic-snapshots)
+ [System disk snapshots](#system-disk-snapshots)
+ [Creating new resources from snapshots](#rehydrating-snapshots)
+ [Copying snapshots](#copying-snapshots)
+ [Exporting snapshots](#exporting-snapshots)
+ [Deleting snapshots](#deleting-snapshots)

## Manual snapshots<a name="manual-snapshots"></a>

Create manual snapshots of instances, managed databases, and block storage disks at any time\. Manual snapshots are stored indefinitely until you delete them\.

For more information about creating manual snapshots, see the following guides:
+ [Creating a snapshot of your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md)
+ [Creating a snapshot of your Windows Server instance in Amazon Lightsail](prepare-windows-based-instance-and-create-snapshot.md)
+ [Creating a snapshot of your database in Amazon Lightsail](amazon-lightsail-creating-a-database-snapshot.md)
+ [Creating a snapshot of your block storage disk in Amazon Lightsail](create-block-storage-disk-snapshot.md)

## Automatic snapshots<a name="automatic-snapshots"></a>

If you're hosting critical information on your Lightsail instance or block storage disk, you should back them up often by creating manual snapshots\. However, it's not always easy to find the time to perform frequent administrative tasks\. If that's the case for you, then use automatic snapshots to have Lightsail create daily backups of your instance or block storage disk on your behalf, without manual interaction\. The latest seven automatic snapshots are stored before the oldest one is replaced with the newest one\.

For more information about automatic snapshots, see the following guides:
+ [Enabling or disabling automatic snapshots for instances or disks in Amazon Lightsail](amazon-lightsail-configuring-automatic-snapshots.md)
+ [Changing the automatic snapshot time for instances or disks in Amazon Lightsail](amazon-lightsail-changing-automatic-snapshot-time.md)
+ [Keeping automatic snapshots of instances or disks in Amazon Lightsail](amazon-lightsail-keeping-automatic-snapshots.md)
+ [Deleting automatic snapshots of instances or disks in Amazon Lightsail](amazon-lightsail-deleting-automatic-snapshots.md)

## System disk snapshots<a name="system-disk-snapshots"></a>

If your instance becomes unresponsive and you need to access the files on the system disk, you can back up the instance root volume by creating a snapshot of it\. Then, you can access the files in the system disk by creating a new block storage disk from the snapshot and attaching it to another instance\. For more information, see [Creating a snapshot of an instance root volume in Amazon Lightsail](amazon-lightsail-create-an-instance-root-volume-snapshot.md)\.

## Creating new resources from snapshots<a name="rehydrating-snapshots"></a>

Use snapshots to create new Lightsail resources using the same plan, or larger plan, than the original resource\. When you create a resource based on a snapshot, the new resource begins as a replica of the original resource that was used to create the snapshot\. Snapshots cannot be used to create new resources using a smaller Lightsail plan\.

For more information, see the following guides:
+ [Creating an instance from a snapshot in Amazon Lightsail](lightsail-how-to-create-instance-from-snapshot.md)
+ [Creating a database from a snapshot in Amazon Lightsail](amazon-lightsail-creating-a-database-from-snapshot.md)
+ [Creating a block storage disk from a snapshot in Amazon Lightsail](create-new-block-storage-disk-from-snapshot.md)
+ [Creating a larger instance, block storage disk, or database from a snapshot in Amazon Lightsail](how-to-create-larger-instance-from-snapshot-using-console.md)

## Copying snapshots<a name="copying-snapshots"></a>

Instance and block storage disk snapshots can be copied from one Amazon Web Services \(AWS\) Region to another within the same Lightsail account\. Database snapshots cannot be copied between regions\. For more information, see [Copying snapshots from one AWS Region to another in Amazon Lightsail](amazon-lightsail-copying-snapshots-from-one-region-to-another.md)\.

## Exporting snapshots<a name="exporting-snapshots"></a>

Lightsail is the easiest way to get started with AWS\. However, there are limitations with Lightsail that are not present in Amazon EC2 or other AWS services\. Export your Lightsail instance and block storage disk snapshots to Amazon EC2 to take advantage of the wider range of instance types available, and use the full range of services in AWS\. For more information, see [Exporting Amazon Lightsail snapshots](amazon-lightsail-exporting-snapshots.md)\.

**Note**  
Snapshots of Ghost and Django instances cannot be exported to Amazon EC2 at this time\.

## Deleting snapshots<a name="deleting-snapshots"></a>

Delete Lightsail snapshots when you no longer need them to avoid incurring a monthly [snapshot storage fee](https://aws.amazon.com/lightsail/pricing/)\. For more information, see [Deleting snapshots in Amazon Lightsail](amazon-lightsail-deleting-snapshots.md)\.