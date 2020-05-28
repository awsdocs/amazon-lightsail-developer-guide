# Enabling or disabling automatic snapshots for instances or disks in Amazon Lightsail<a name="amazon-lightsail-configuring-automatic-snapshots"></a>

 *Last updated: October 2, 2019* 

When you enable the automatic snapshots feature for an instance or block storage disk, Lightsail creates daily snapshots of the resource during the default automatic snapshot time, or during a [time you specify](amazon-lightsail-changing-automatic-snapshot-time.md)\.

Just like a manual snapshot, an automatic snapshot can be used as a baseline, or to create a new resource if something goes wrong with the original resource\. However, a manual snapshot is stored until you delete it\. With automatic snapshots, only the latest seven automatic snapshots are stored before the oldest one is replaced with the newest one\. If you want to keep a specific automatic snapshot from being replaced, you can [copy it as a manual snapshot](amazon-lightsail-keeping-automatic-snapshots.md)\. When you disable the automatic snapshot feature for a resource, the existing automatic snapshots of the resource are kept until you re\-enable the feature and they are replaced by newer snapshots, or [delete the automatic snapshots](amazon-lightsail-deleting-automatic-snapshots.md)\.

You will be billed the [snapshot storage fee](https://aws.amazon.com/lightsail/pricing/) for the automatic snapshots stored on your Lightsail account\.

**Contents**
+ [Automatic snapshot restrictions](#automnatic-snapshot-restrictions)
+ [Enabling or disabling automatic snapshots for instances using the Lightsail console](#configuring-automatic-snapshots-using-console)
+ [Enabling or disabling automatic snapshots for instances or block storage disks using the AWS CLI](#configuring-automatic-snapshots-using-cli)

## Automatic snapshot restrictions<a name="automnatic-snapshot-restrictions"></a>

The following restrictions apply to automatic snapshots:
+ Automatic snapshots cannot be enabled or disabled for block storage disks using the Lightsail console\. To enable or disable automatic snapshots for block storage disks, you must use the Lightsail API, AWS Command Line Interface \(AWS CLI\), or SDKs\. For more information, see [Enabling or disabling automatic snapshots using the AWS CLI](#configuring-automatic-snapshots-using-cli)\.
+ Automatic snapshot is currently not supported for Windows instances, or managed databases\. Instead, you must create manual snapshots of your Windows instances or managed databases to back them up\. For more information, see [Creating a snapshot of your Windows Server instance in Amazon Lightsail](prepare-windows-based-instance-and-create-snapshot.md) and [Creating a snapshot of your database in Amazon Lightsail](amazon-lightsail-creating-a-database-snapshot.md)\. Managed databases also have the point\-in\-time backup feature enabled by default, which you can use to restore your data to a new database\. For more information, see [Creating a database from a point\-in\-time backup in Amazon Lightsail](amazon-lightsail-creating-a-database-from-point-in-time-backup.md)\.
+ Automatic snapshots don't retain tags from the source resource\. To keep a tag from the source resource on a new resource created from an automatic snapshot, you must manually add the tag when you create the new resource from the automatic snapshot\. For more information, see [Adding tags to a resource in Amazon Lightsail](amazon-lightsail-adding-tags-to-a-resource.md)\.

## Enabling or disabling automatic snapshots for instances using the Lightsail console<a name="configuring-automatic-snapshots-using-console"></a>

Complete the following steps to enable or disable automatic snapshots for an instance using the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Instances** tab\.  
![\[The Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-home-page-instances-storage.png)

1. Choose the name of the instance for which you want to enable or disable automatic snapshots\.

1. On the instance management page, choose the **Snapshots** tab\.  
![\[The instance management page in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-instance-management-snapshots.png)

1. Under the **Automatic snapshots** section, choose the toggle to enable it\. Likewise, choose the toggle to disable it if it's enabled\.

1. At the prompt, choose **Yes, enable** to enable automatic snapshots, or **Yes, disable** to disable the feature\.

   The automatic snapshot is enabled or disabled after a few moments\.
   + If you *enabled* the automatic snapshots feature, you may want to also change the automatic snapshot time\. For more information, see [Changing the automatic snapshot time for instances or block storage disks in Amazon Lightsail](amazon-lightsail-changing-automatic-snapshot-time.md)\.
   + If you *disabled* the automatic snapshots feature, the existing automatic snapshots of the resource are kept until you re\-enable the feature and they are replaced by new snapshots, or until you delete them\. You will be billed the [snapshot storage fee](https://aws.amazon.com/lightsail/pricing/) for the automatic snapshots stored on your Lightsail account\. For more information about deleting automatic snapshots, see [Deleting automatic snapshots of instances or disks in Amazon Lightsail](amazon-lightsail-deleting-automatic-snapshots.md)\.

## Enabling or disabling automatic snapshots for instances or block storage disks using the AWS CLI<a name="configuring-automatic-snapshots-using-cli"></a>

Complete the following steps to enable or disable automatic snapshots for an instance or block storage disk using the AWS CLI\.

1. Open a Terminal or Command Prompt window\.

   If you haven't already, [install the AWS CLI](lightsail-how-to-set-up-and-configure-aws-cli.md) and [configure it to work with Lightsail](lightsail-how-to-set-up-access-keys-to-use-sdk-api-cli.md)\.

1. Enter one of the commands described in this step depending on whether you want to enable or disable automatic snapshots:
**Note**  
The `autoSnapshotAddOnRequest={snapshotTimeOfDay=HH:00}` parameter is optional in these commands\. If you don't specify a daily automatic snapshot time when you enable automatic snapshots, Lightsail assigns a default snapshot time for your resource\. For more information, see [Changing the automatic snapshot time for instances or block storage disks in Amazon Lightsail](amazon-lightsail-changing-automatic-snapshot-time.md)\.
   + Enter the following command to enable automatic snapshots for an existing resource:

     ```
     aws lightsail enable-add-on --region Region --resource-name ResourceName --add-on-request addOnType=AutoSnapshot,autoSnapshotAddOnRequest={snapshotTimeOfDay=HH:00}
     ```

     In the command, replace:
     + *Region* with the AWS Region in which the resource is located\.
     + *ResourceName* with the name of the resource\.
     + *HH:00* with the daily automatic snapshot time in an hourly increment, and in Coordinated Universal Time \(UTC\)\.

     **Example:**

     ```
     aws lightsail enable-add-on --region us-west-2 --resource-name WordPress-1 --add-on-request addOnType=AutoSnapshot,autoSnapshotAddOnRequest={snapshotTimeOfDay=18:00}
     ```
   + Enter the following command to enable automatic snapshots when creating a new instance:

     ```
     aws lightsail create-instances --region Region --availability-zone AvailabilityZone --blueprint-id BlueprintID --bundle-id BundleID --instance-name InstanceName --add-ons addOnType=AutoSnapshot,autoSnapshotAddOnRequest={snapshotTimeOfDay=HH:00}
     ```

     In the command, replace:
     + *Region* with the AWS Region in which the instance should be created\.
     + *AvailabilityZone* with the availability zone in which the instance should be created\.
     + *BlueprintID* with the blueprint ID to use for the instance\.
     + *BundleID* with the bundle ID to use for the instance\.
     + *InstanceName* with the name to use for the instance\.
     + *HH:00* with the daily automatic snapshot time in an hourly increment, and in Coordinated Universal Time \(UTC\)\.

     **Example:**

     ```
     aws lightsail create-instances --region us-west-2 --availability-zone us-west-2a --blueprint-id wordpress_5_1_1_2 --bundle-id medium_2_0 --instance-name WordPressInstance --add-ons addOnType=AutoSnapshot,autoSnapshotAddOnRequest={snapshotTimeOfDay=20:00}
     ```
   + Enter the following command to enable automatic snapshots when creating a new disk:

     ```
     aws lightsail create-disk --region Region --availability-zone AvailabilityZone --size-in-gb Size --disk-name DiskName --add-ons addOnType=AutoSnapshot,autoSnapshotAddOnRequest={snapshotTimeOfDay=HH:00}
     ```

     In the command, replace:
     + *Region* with the AWS Region in which the disk should be created\.
     + *AvailabilityZone* with the availability zone in which the disk should be created\.
     + *Size* with the desired size of the disk in GB\.
     + *DiskName* with the name to use for the disk\.
     + *HH:00* with the daily automatic snapshot time in an hourly increment, and in Coordinated Universal Time \(UTC\)\.

     **Example:**

     ```
     aws lightsail create-disk --region us-west-2 --availability-zone us-west-2a --size-in-gb 32 --disk-name Disk01 --add-ons addOnType=AutoSnapshot,autoSnapshotAddOnRequest={snapshotTimeOfDay=18:59}
     ```
   + Enter the following command to disable automatic snapshots for a resource:

     ```
     aws lightsail disable-add-on --region Region --resource-name ResourceName --add-on-type AutoSnapshot
     ```

     In the command, replace:
     + *Region* with the AWS Region in which the resource is located\.
     + *ResourceName* with the name of the resource\.

     **Example:**

     ```
     aws lightsail disable-add-on --region us-west-1 --resource-name MyFirstWordPressWebsite01 --add-on-type AutoSnapshot
     ```

   You should see a result similar to the following example:  
![\[Enable auto snapshot operation result.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-enable-auto-backup-operation.png)

   The automatic snapshot is enabled or disabled after a few moments\.
   + If you *enabled* automatic snapshots, you may want to also change the automatic snapshot time\. For more information, see [Changing the automatic snapshot time for instances or block storage disks in Amazon Lightsail](amazon-lightsail-changing-automatic-snapshot-time.md)\.
   + If you *disabled* automatic snapshots, the existing automatic snapshots are kept until you re\-enable the feature and they are replaced by new snapshots, or until you delete them\. You will be billed the [snapshot storage fee](https://aws.amazon.com/lightsail/pricing/) for the automatic snapshots stored on your Lightsail account\. For more information about deleting automatic snapshots, see [Deleting automatic snapshots of instances or disks in Amazon Lightsail](amazon-lightsail-deleting-automatic-snapshots.md)\.
**Note**  
For more information about the EnableAddOn and DisableAddOn API operations in these commands, see [EnableAddOn](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_EnableAddOn.html) and [DisableAddOn](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DisableAddOn.html) in the Lightsail API documentation\.