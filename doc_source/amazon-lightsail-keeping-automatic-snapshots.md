# Keeping automatic snapshots of instances or disks in Amazon Lightsail<a name="amazon-lightsail-keeping-automatic-snapshots"></a>

 *Last updated: October 2, 2019* 

When you [enable the automatic snapshots feature](amazon-lightsail-configuring-automatic-snapshots.md) for an instance or block storage disk in Amazon Lightsail, only the latest seven automatic snapshots of the resource are stored\. Then, the oldest one is replaced with the newest one\. If you want to keep a specific automatic snapshot from being replaced, you can copy it as a manual snapshot\. Manual snapshots are kept until you delete them\.

Follow the steps in this guide to keep an automatic snapshot by copying it as a manual snapshot\. You will be billed the [snapshot storage fee](https://aws.amazon.com/lightsail/pricing/) for the automatic snapshots stored on your Lightsail account\.

**Note**  
If you disable the automatic snapshots feature for a resource, the existing automatic snapshots of the resource are kept until you re\-enable the feature and they are replaced by newer snapshots, or you until you [delete the automatic snapshots](amazon-lightsail-deleting-automatic-snapshots.md)\.

**Contents**
+ [Keeping automatic snapshots restriction](#keeping-automatic-snapshots-restrictions)
+ [Keeping automatic snapshots of instances using the Lightsail console](#keeping-automatic-snapshots-using-console)
+ [Keeping automatic snapshots of instances and block storage disks using the AWS CLI](#keeping-automatic-snapshots-using-cli)

## Keeping automatic snapshots restriction<a name="keeping-automatic-snapshots-restrictions"></a>

Automatic snapshots of block storage disks cannot be copied to manual snapshots using the Lightsail console\. To copy an automatic snapshot of a block storage disk, you must use the Lightsail API, AWS Command Line Interface \(AWS CLI\), or SDKs\. For more information, see [Keeping automatic snapshots of instances and block storage disks using the AWS CLI](#keeping-automatic-snapshots-using-cli)\.

## Keeping automatic snapshots of instances using the Lightsail console<a name="keeping-automatic-snapshots-using-console"></a>

Complete the following steps to keep automatic snapshots for an instance using the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Instances** tab\.  
![\[The Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-home-page-instances-storage.png)

1. Choose the name of the instance for which you want to keep automatic snapshots\.

1. On the instance management page, choose the **Snapshots** tab\.  
![\[The instance management page in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-instance-management-snapshots.png)

1. Under the **Automatic snapshots** section, choose the ellipsis icon next to the automatic snapshot that you want to keep, then choose **Keep snapshot**\.

1. At the prompt, choose **Yes, save** to confirm that you want to keep the automatic snapshot\.

   The automatic snapshot is copied as a manual snapshot after a few moments\. Manual snapshots are kept until you delete them\.
**Important**  
If you no longer need the automatic snapshot, we recommend that you delete it\. Otherwise, you will be billed the [snapshot storage fee](https://aws.amazon.com/lightsail/pricing/) for the automatic snapshot and the duplicate manual snapshot stored on your Lightsail account\. For more information, see [Deleting automatic snapshots of instances or disks in Amazon Lightsail](amazon-lightsail-deleting-automatic-snapshots.md)\.

## Keeping automatic snapshots of instances and block storage disks using the AWS CLI<a name="keeping-automatic-snapshots-using-cli"></a>

Complete the following steps to keep automatic snapshots for an instance or block storage disk using the AWS CLI\.

1. Open a Terminal or Command Prompt window\.

   If you haven't already, [install the AWS CLI](lightsail-how-to-set-up-and-configure-aws-cli.md) and [configure it to work with Lightsail](lightsail-how-to-set-up-access-keys-to-use-sdk-api-cli.md)\.

1. Enter the following command to get the dates of the available automatic snapshots for a specific resource\. You need the date of the automatic snapshot to specify as the `restore date` parameter in the subsequent command\.

   ```
   aws lightsail get-auto-snapshots --region Region --resource-name ResourceName
   ```

   In the command, replace:
   + *Region* with the AWS Region in which the resource is located\.
   + *ResourceName* with the name of the resource\.

   **Example:**

   ```
   aws lightsail get-auto-snapshots --region us-west-2 --resource-name MyFirstWordPressWebsite01
   ```

   You should see a result similar to the following, which lists the available automatic snapshots:  
![\[Get auto snapshots operation results containing the available auto snapshots for an instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-available-auto-backups-operation.png)

1. Enter the following command to keep an automatic snapshot for a specific resource:

   ```
   aws lightsail copy-snapshot --region TargetRegion --source-resource-name ResourceName --restore-date YYYY-MM-DD --source-region SourceRegion --target-snapshot-name SnapshotName
   ```

   In the command, replace:
   + *TargetRegion* with the AWS Region in which you want to copy the snapshot to\.
   + *ResourceName* with the name of the resource\.
   + *YYYY\-MM\-DD* with the date of the available auto snapshot that you obtained using the preceding command\.
   + *SourceRegion* with the AWS Region in which the automatic snapshot is currently in\.
   + *SnapshotName* with the name of the new snapshot to be created\.

   **Example:**

   ```
   aws lightsail copy-snapshot --region us-west-2 --source-resource-name MyFirstWordPressWebsite01 --restore-date 2019-09-16 --source-region us-west-2 --target-snapshot-name Snapshot-Copied-From-Auto-Snapshot
   ```

   You should see a result similar to the following example:  
![\[Copy snapshot operation result.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-copy-snapshot-operation.png)

   The automatic snapshot is copied as a manual snapshot after a few moments\. Manual snapshots are kept until you delete them\.
**Important**  
If you no longer need the automatic snapshot, we recommend that you delete it\. Otherwise, you will be billed the [snapshot storage fee](https://aws.amazon.com/lightsail/pricing/) for the automatic snapshot and duplicate manual snapshot stored on your Lightsail account\. For more information, see [Deleting automatic snapshots of instances or disks in Amazon Lightsail](amazon-lightsail-deleting-automatic-snapshots.md)\.
**Note**  
For more information about the GetAutoSnapshots and CopySnapshot API operations in these commands, see [GetAutoSnapshots](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetAutoSnapshots.html) and [CopySnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CopySnapshot.html) in the Lightsail API documentation\.