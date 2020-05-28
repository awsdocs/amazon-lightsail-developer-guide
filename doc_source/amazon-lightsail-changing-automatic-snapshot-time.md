# Changing the automatic snapshot time for instances or disks in Amazon Lightsail<a name="amazon-lightsail-changing-automatic-snapshot-time"></a>

 *Last updated: October 2, 2019* 

When you [enable the automatic snapshots feature](amazon-lightsail-configuring-automatic-snapshots.md) for an instance or block storage disk, Lightsail creates daily snapshots of the resource during the [default automatic snapshot time](#default-automatic-snapshot-times), or a time you specify\. Follow the steps in this guide to change the automatic snapshot time for your resource\.

**Contents**
+ [Automatic snapshot time restrictions](#automatic-snapshot-time-restrictions)
+ [Default automatic snapshot times for AWS Regions](#default-automatic-snapshot-times)
+ [Changing the automatic snapshot time for instances using the Lightsail console](#changing-automatic-snapshot-time-using-console)
+ [Changing the automatic snapshot time for instances and block storage disks using the AWS CLI](#changing-automatic-snapshot-time-using-cli)

## Automatic snapshot time restrictions<a name="automatic-snapshot-time-restrictions"></a>

The following restrictions apply to the automatic snapshot time:
+ The automatic snapshot time cannot be changed for block storage disks using the Lightsail console\. To change the automatic snapshot time for block storage disks, you must use the Lightsail API, AWS Command Line Interface \(AWS CLI\), or SDKs\. For more information, see [Changing the automatic snapshot time using the AWS CLI](#changing-automatic-snapshot-time-using-cli)\.
+ The automatic snapshot time can be specified only in hourly increments\. It also must be a time that is more than 30 minutes from your current time\. Lightsail creates the automatic snapshot between the time you specify and up to 45 minutes after\.
**Important**  
You cannot create manual snapshots when an automatic snapshot is being created\.
+ When you change the automatic snapshot time for a resource, it is typically effective immediately, except under the following conditions:
  + If an automatic snapshot has been created for the current day, and you change the snapshot time to a later time of day, then the new snapshot time will be effective the following day\. This ensures that two snapshots are not created for the current day\.
  + If an automatic snapshot has not yet been created for the current day, and you change the snapshot time to an earlier time of day, then the new snapshot time will be effective the following day\. Also, a snapshot is automatically created at the previously set time for the current day\. This ensures that a snapshot is created for the current day\.
  + If an automatic snapshot has not yet been created for the current day, and you change the snapshot time to a time that is within 30 minutes from your current time, then the new snapshot time will be effective the following day\. Also, a snapshot is automatically created at the previously set time for the current day\. This ensures that a snapshot is created for the current day, because 30 minutes is required between your current time and the new snapshot time that you specify\.
  + If an automatic snapshot is scheduled to be created within 30 minutes from your current time and you change the snapshot time, then the new snapshot time will be effective the following day\. Also, a snapshot is automatically created at the previously set time for the current day\. This ensures that a snapshot is created for the current day, because 30 minutes is required between your current time and the new snapshot time that you specify\.

  When any of these conditions are true, a message displays in the Lightsail console to notify you that the new snapshot time may take up to 24 hours to take effect\.

## Default automatic snapshot times for AWS Regions<a name="default-automatic-snapshot-times"></a>

If you don't specify an automatic snapshot time when you enable automatic snapshots, then Lightsail assigns one of the following default automatic snapshot times\. The times depend on the AWS Region where your instance or block storage disk is located:
+ US East \(Ohio\): 03:00 UTC
+ US East \(N\. Virginia\): 06:00 UTC
+ US West \(Oregon\): 06:00 UTC
+ Asia Pacific \(Mumbai\): 17:00 UTC
+ Asia Pacific \(Seoul\): 13:00 UTC
+ Asia Pacific \(Singapore\): 14:00 UTC
+ Asia Pacific \(Sydney\): 12:00 UTC
+ Asia Pacific \(Tokyo\): 13:00 UTC
+ Canada \(Central\): 06:00 UTC
+ EU \(Frankfurt\): 20:00 UTC
+ EU \(Ireland\): 22:00 UTC
+ EU \(London\): 06:00 UTC
+ EU \(Paris\): 07:00 UTC

## Changing the automatic snapshot time for instances using the Lightsail console<a name="changing-automatic-snapshot-time-using-console"></a>

Complete the following steps to change the automatic snapshot time for an instance using the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Instances** tab\.  
![\[The Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-home-page-instances-storage.png)

1. Choose the name of the instance for which you want to change the automatic snapshot time\.

1. On the instance management page, choose the **Snapshots** tab\.  
![\[The instance management page in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-instance-management-snapshots.png)

1. Under the **Automatic snapshots** section, choose **Change snapshot time**\.

1. Choose a time of day when you'd like Lightsail to create an automatic snapshot\. The time that you choose must be in Coordinated Universal Time \(UTC\)\.

1. Choose **Change** to save the new snapshot time\.

   The automatic snapshot time is updated after a few moments\. A restriction may apply to the effective date of your new automatic snapshot time\. For more information, see [Automatic snapshot time restrictions](#automatic-snapshot-time-restrictions)\.

## Changing the automatic snapshot time for instances and block storage disks using the AWS CLI<a name="changing-automatic-snapshot-time-using-cli"></a>

Complete the following steps to change the automatic snapshot time for an instance or block storage disk using the AWS CLI\.

1. Open a Terminal or Command Prompt window\.

   If you haven't already, [install the AWS CLI](lightsail-how-to-set-up-and-configure-aws-cli.md) and [configure it to work with Lightsail](lightsail-how-to-set-up-access-keys-to-use-sdk-api-cli.md)\.

1. Enter the following command to change the automatic snapshot time for a resource:

   ```
   aws lightsail enable-add-on --region Region --resource-name ResourceName --add-on-request addOnType=AutoSnapshot,autoSnapshotAddOnRequest={snapshotTimeOfDay=HH:00}
   ```

   In the command, replace:
   + *Region* with the AWS Region in which the resource is located\.
   + *ResourceName* with the name of the resource\.
   + *HH:00* with the daily automatic snapshot time in an hourly increment, and in Coordinated Universal Time \(UTC\)\.

   **Example:**

   ```
   aws lightsail enable-add-on --region us-west-1 --resource-name MyFirstWordPressWebsite01 --add-on-request addOnType=AutoSnapshot,autoSnapshotAddOnRequest={snapshotTimeOfDay=12:00}
   ```

   You should see a result similar to the following example:  
![\[Enable auto snapshot operation result.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-update-auto-snapshot-time-operation.png)

   The automatic snapshot time is updated after a few moments\. A restriction may apply to the effective date of your new automatic snapshot time\. For more information, see [Automatic snapshot time restrictions](#automatic-snapshot-time-restrictions)\.
**Note**  
For more information about the EnableAddOn API operation in this command, see [EnableAddOn](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_EnableAddOn.html) in the Lightsail API documentation\.