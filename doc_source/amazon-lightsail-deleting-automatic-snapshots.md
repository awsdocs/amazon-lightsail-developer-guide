# Deleting automatic snapshots of instances or disks in Amazon Lightsail<a name="amazon-lightsail-deleting-automatic-snapshots"></a>

 *Last updated: October 2, 2019* 

You can delete automatic snapshots of an instance or block storage disk in Amazon Lightsail at any time; whether the feature is enabled, or if it's disabled after it had been enabled\. You will be billed the [snapshot storage fee](https://aws.amazon.com/lightsail/pricing/) for the automatic snapshots stored on your Lightsail account\. Follow the steps in this guide to delete automatic snapshots if you no longer need them\. For example, if you've [copied an automatic snapshot to a manual snapshot](amazon-lightsail-keeping-automatic-snapshots.md) and you no longer need the original, or if you've [disabled the automatic snapshots feature](amazon-lightsail-configuring-automatic-snapshots.md) for your resource and you don't need the existing automatic snapshots that were kept\.

**Contents**
+ [Deleting automatic snapshots restriction](#deleting-automatic-snapshots-restrictions)
+ [Deleting automatic snapshots of an instance using the Lightsail console](#deleting-automatic-snapshots-using-console)
+ [Deleting automatic snapshots of an instance or block storage disk using the AWS CLI](#deleting-automatic-snapshots-using-cli)

## Deleting automatic snapshots restriction<a name="deleting-automatic-snapshots-restrictions"></a>

Automatic snapshots of block storage disks cannot be deleted using the Lightsail console\. To delete an automatic snapshot of a block storage disk, you must use the Lightsail API, AWS Command Line Interface \(AWS CLI\), or SDKs\. For more information, see [Deleting automatic snapshots of an instance or block storage disk using the AWS CLI](#deleting-automatic-snapshots-using-cli)\.

## Deleting automatic snapshots of an instance using the Lightsail console<a name="deleting-automatic-snapshots-using-console"></a>

Complete the following steps to delete automatic snapshots of an instance using the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Instances** tab\.  
![\[The Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-home-page-instances-storage.png)

1. Choose the name of the instance for which you want to delete automatic snapshots\.

1. On the instance management page, choose the **Snapshots** tab\.  
![\[The instance management page in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-instance-management-snapshots.png)

1. Under the **Automatic snapshots** section, choose the ellipsis icon next to the automatic snapshot that you want to delete, then choose **Delete snapshot**\.

1. At the prompt, choose **Yes** to confirm that you want to delete the snapshot\.

   The automatic snapshot is deleted after a few moments\.

## Deleting automatic snapshots of an instance or block storage disk using the AWS CLI<a name="deleting-automatic-snapshots-using-cli"></a>

Complete the following steps to delete automatic snapshots of an instance or block storage disk using the AWS CLI\.

1. Open a Terminal or Command Prompt window\.

   If you haven't already, [install the AWS CLI](lightsail-how-to-set-up-and-configure-aws-cli.md) and [configure it to work with Lightsail](lightsail-how-to-set-up-access-keys-to-use-sdk-api-cli.md)\.

1. Enter the following command to get the dates of the available automatic snapshots for a specific resource\. You will need the date of the automatic snapshot to specify as the `date` parameter in the subsequent command\.

   ```
   aws lightsail --region Region get-auto-snapshots --resource-name ResourceName
   ```

   In the command, replace:
   + *Region* with the AWS Region in which the resource is located\.
   + *ResourceName* with the name of the resource\.

   **Example:**

   ```
   aws lightsail --region us-west-2 get-auto-snapshots --resource-name MyFirstWordPressWebsite01
   ```

   You should see a result similar to the following, which lists the available automatic snapshots:  
![\[Get auto snapshots operation results containing the available auto snapshots for an instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-available-auto-backups-operation.png)

1. Enter the following command to delete an automatic snapshot:

   ```
   aws lightsail --region Region delete-auto-snapshot --resource-name ResourceName --date YYYY-MM-DD
   ```

   In the command, replace:
   + *Region* with the AWS Region in which the resource is located\.
   + *ResourceName* with the name of the resource\.
   + *YYYY\-MM\-DD* with the date of the available auto snapshot that you obtained using the preceding command\.

   **Example:**

   ```
   aws lightsail --region us-west-2 delete-auto-snapshot --resource-name MyFirstWordPressWebsite01 --date 2019-09-16
   ```

   You should see a result similar to the following example:  
![\[Delete auto snapshot operation result.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-delete-auto-backup-operation.png)

   The automatic snapshot is deleted after a few moments\.
**Note**  
For more information about the GetAutoSnapshots and DeleteAutoSnapshot API operations in these commands, see [GetAutoSnapshots](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetAutoSnapshots.html) and [DeleteAutoSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteAutoSnapshot.html) in the Lightsail API documentation\.