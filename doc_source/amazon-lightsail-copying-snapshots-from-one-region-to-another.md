# Copying snapshots from one AWS Region to another in Amazon Lightsail<a name="amazon-lightsail-copying-snapshots-from-one-region-to-another"></a>

 *Last updated: November 28, 2018* 

Amazon Lightsail lets you copy instance snapshots and block storage disk snapshots from one AWS Region to another, or within the same Region\. Copy snapshots between Regions if you created and configured resources in one Region, but later decide that a different Region is more appropriate\. Or, if you want to replicate your resources across multiple Regions\. This guide describes the process of copying Lightsail snapshots\.

## Prerequisites<a name="copying-snapshots-from-one-region-to-another-prerequisites"></a>

Create a snapshot of the Lightsail instance or block storage disk that you want to copy\. For more information, see one of the following guides:
+ [Creating a snapshot of your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md)
+ [Creating a snapshot of your Windows Server instance in Amazon Lightsail](prepare-windows-based-instance-and-create-snapshot.md)
+ [Creating a snapshot of your block storage disk in Amazon Lightsail](create-block-storage-disk-snapshot.md)

## Copy a Lightsail snapshot<a name="copy-a-snapshot-from-one-region-to-another"></a>

You can copy instance snapshots and block storage disk snapshots from one AWS Region to another, or within the same Region\.

**To copy a Lightsail snapshot**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. From the Lightsail home page, choose the **Snapshots** tab\.

1. Locate the instance or block storage disk that you want to copy, and expand the node to view the available snapshots for that resource\.

1. Choose the actions menu icon \(⋮\) for the desired snapshot, then choose **Copy to another Region**\.  
![\[Copy snapshot to another Region in the Amazon Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-copy-snapshot-to-another-region.png)

1. On the **Copy a snapshot** page, in the **Snapshot to copy** section, confirm that the snapshot details displayed match the specifications of the source instance or block storage disk\.  
![\[Snapshot to copy in the Amazon Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-copy-snapshot-snapshot-to-copy.png)

1. In the **Select a Region** section of the page, choose the Region for your snapshot copy\.

1. Enter a name for your snapshot copy\.

   Resource names:
   + Must be unique within each AWS Region in your Lightsail account\.
   + Must contain 2 to 255 characters\.
   + Must start and end with an alphanumeric character or number\.
   + Can include alphanumeric characters, numbers, periods, dashes, and underscores\.

1. Choose **Copy snapshot**\.  
![\[Copy snapshot in the Amazon Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-copy-snapshot-name-snapshot.png)

   Your snapshot copy should be available soon\. It depends on the size and configuration of the source instance\. You can check the status of your snapshot copy by browsing to the **Snapshots** tab on the Lightsail home page, and looking for the snapshot with a status of **Creating** as shown in the following screenshot\. The status will change when the snapshot is ready\.  
![\[Creating snapshot copy in the Amazon Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-copy-snapshot-creating-snapshot-copy.png)

## Next steps<a name="copying-snapshots-from-one-region-to-another-next-steps"></a>

Here are a few additional steps you can perform after copying a snapshot to another Region in Lightsail:
+ Create a new instance from the copied snapshot after it’s available\. For more information, see [Creating an instance from a snapshot in Amazon Lightsail](lightsail-how-to-create-instance-from-snapshot.md)\.
+ Delete the source snapshot if you no longer need it\. Otherwise, you will be billed for storing the snapshot\.