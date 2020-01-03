# Creating a snapshot of your Linux or Unix instance in Amazon Lightsail<a name="lightsail-how-to-create-a-snapshot-of-your-instance"></a>

*Last updated: June 28, 2018*

You can create snapshots of your Linux/Unix\-based Lightsail instances\. An *instance snapshot* is a copy of the system disk and matches the original machine configuration \(memory, CPU, disk size, and data transfer rate\)\. If you've attached block storage disks to your instance, Lightsail copies those additional disks as part of your snapshot\. For more information, see [Snapshots in Amazon Lightsail](understanding-instance-snapshots-in-amazon-lightsail.md)\.

**Note**  
The steps to create a snapshot of a Windows Server\-based Lightsail instance are different\. For more information, see [Creating a snapshot of your Windows Server instance in Amazon Lightsail](prepare-windows-based-instance-and-create-snapshot.md)\.

You must already have an instance in Lightsail to create a snapshot of it\. After you have an instance, follow these steps to create a snapshot:

1. On the Lightsail home page, choose the name of your instance for which you want to create a snapshot\.

1. Choose the **Snapshots** tab\.

1. Under the **Manual snapshots** section of the page, choose **Create snapshot**, then enter a name for your snapshot\.

   Resource names:
   + Must be unique within each AWS Region in your Lightsail account\.
   + Must contain 2 to 255 characters\.
   + Must start and end with an alphanumeric character or number\.
   + Can include alphanumeric characters, numbers, periods, dashes, and underscores\.

1. Choose **Create**\.

   You can see the snapshot you just created with a status of **Snapshotting\.\.\.**\.

   After the snapshot is finished, you can [create another instance from the snapshot](lightsail-how-to-create-instance-from-snapshot.md)\. For example, you may want to choose a larger size bundle than you had previously\.

**Important**  
When you create a new instance from a snapshot, Lightsail lets you create an instance bundle that is either the same size or larger size\. We do not currently support creating a *smaller* instance size from a snapshot\. The smaller options will be grayed out when you create a new instance from a snapshot\.

To create a larger instance size from a snapshot, you can use the Lightsail console, the **create\-instances\-from\-snapshot** CLI command\. or the **CreateInstancesFromSnapshot** API operation\. For more information, see [Creating an instance from a snapshot in Amazon Lightsail](lightsail-how-to-create-instance-from-snapshot.md)\.

For more information about Lightsail bundles, see [Lightsail Pricing](https://amazonlightsail.com/pricing/)\.