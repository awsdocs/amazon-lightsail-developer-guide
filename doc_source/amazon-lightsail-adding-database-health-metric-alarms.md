# Creating database metric alarms in Amazon Lightsail<a name="amazon-lightsail-adding-database-health-metric-alarms"></a>

 *Last updated: February 27, 2020* 

You can create an Amazon Lightsail alarm that watches a single database metric\. An alarm can be configured to notify you based on the value of the metric relative to a threshold that you specify\. Notifications can be a banner displayed in the Lightsail console, an email sent to your email address, and an SMS text message sent to your mobile phone number\. For more information about alarms, see [Alarms in Amazon Lightsail](amazon-lightsail-alarms.md)\.

**Contents**
+ [Database alarm limits](#database-alarm-limits)
+ [Best practices for configuring database alarms](#database-alarms-best-practices)
+ [Default alarm settings](#default-database-alarm-settings)
+ [Creating database metric alarms using the Lightsail console](#creating-database-alarms)
+ [Testing database metric alarms using the Lightsail console](#testing-database-alarms)
+ [Next steps after creating database alarms](#next-steps-creating-database-alarms)

## Database alarm limits<a name="database-alarm-limits"></a>

The following limits apply to alarms:
+ You can configure two alarms per metric\.
+ Alarms are evaluated in 5 minute intervals, and each data point for alarms represents a 5 minute period of aggregated metric data\.
+ You can only configure an alarm to notify you when the alarm state changes to `OK` if you configure the alarm to notify you by email and/or SMS text message\.
+ You can only test the `OK` alarm notification if you configure the alarm to notify you by email and/or SMS text message\.
+ You can only configure an alarm to notify you when the alarm state changes to `INSUFFICIENT_DATA` if you configure the alarm to notify you by email and/or SMS text message, and if you choose the **Do not evaluate the missing data** option for missing data points\.
+ You can only test notifications if the alarm is in an OK state\.

## Best practices for configuring database alarms<a name="database-alarms-best-practices"></a>

Before you configure a metric alarm for your database, you should view the historical data of the metric\. Identify the metric's low\-levels, mid\-levels, and high\-levels over a period of the last two weeks\. In the following network transmit throughput \(`NetworkTransmitThroughput`\) metric graph example, the low\-levels are 0\-10 KB/second per hour, the mid\-levels are between 10\-20 KB/second per hour, and the high\-levels are between 20\-80 KB/second per hour\.

![\[Database NetworkTransmitThroughput example.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-networkout-transmit-example.png)

If you configure the alarm threshold to be **greater than or equal to** somewhere in the low\-level range \(e\.g\., 5 KB/second per hour\), then you will get more frequent, and potentially unnecessary alarm notifications\. If you configure the alarm threshold to be **greater than or equal to** somewhere in the high\-level range \(e\.g\., 20 KB per hour\), then you will get less frequent alarm notifications, but that might be more important to investigate\. When you configure an alarm, and enable it, an alarm line representing the threshold appears on the graph as shown in the following example\. The alarm line labeled as 1 represents the threshold for Alarm 1, and the alarm line labeled as 2 represents the threshold for Alarm 2\.

![\[Database NetworkTransmitThroughput example, with alarm line.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-networkout-transmit-graph-example-alarmed.png)

## Default alarm settings<a name="default-database-alarm-settings"></a>

Default alarm settings are prepopulated when you add a new alarm in the Lightsail console\. That is the recommended alarm configuration for the metric you selected\. However, you should confirm that the default alarm configuration is appropriate for your resource\. For example, the default alarm threshold for the free storage space \(`FreeStorageSpace`\) metric is **less than** 5 Bytes for 1 time within the last 5 minutes\. However, that free storage space threshold might be too low for your database\. You might want to modify the alarm threshold to be **less than** 4 GB for 1 time within the last 5 minutes\.

## Creating database metric alarms using the Lightsail console<a name="creating-database-alarms"></a>

Complete the following steps to create a database metric alarm using the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Databases** tab\.

1. Choose the name of the database for which you want to create alarms\.

1. Choose the **Metrics** tab on the database management page\.

1. Choose the metric for which you want to create an alarm in the drop\-down menu under the **Metrics Graphs** heading\. For more information, see [Resource metrics in Amazon Lightsail](amazon-lightsail-resource-health-metrics.md)\.

1. Choose **Add alarm** in the **Alarms** section of the page\.

1. Choose a comparison operator value in the drop\-down menu\. Example values are greater than or equal to, greater than, less than, or less than or equal to\.

1. Enter a threshold for the alarm\.

1. Enter the data points to alarm\.

1. Choose the evaluation periods\. The period can be specified in 5\-minute increments, from 5 minutes up to 24 hours\.

1. Choose one of the following notification methods:
   + **Email** — You are notified by email when the alarm state changes to ALARM\.
   + **SMS text message** — You are notified by SMS text message when the alarm state changes to ALARM\. SMS messaging is not supported in all AWS Regions in which you can create Lightsail resources, and SMS text messages cannot be sent to all countries/regions\. For more information, see [SMS text messaging support](amazon-lightsail-adding-editing-notification-contacts.md#sms-support)\.
**Note**  
You are required to add an email address or mobile phone number if you select to be notified by email or SMS but you haven’t yet configured a notification contact in the resource’s AWS Region\. For more information, see [Notifications in Amazon Lightsail](amazon-lightsail-notifications.md)\.

1. \(Optional\) Choose **Send me a notification when the alarm state change to OK** to be notified when the alarm state changes to OK\. This option is available only if you choose to be notified by Email or SMS text message\.

1. \(Optional\) Choose **Advanced settings**, and then choose one of the following options:
   + Choose how the alarm should treat missing data The following options are available:
     + **Assume it's not within the threshold \(Breaching threshold\)** — Missing data points are treated as "bad" and breaching the threshold\.
     + **Assume it's within the threshold \(Not breaching threshold\)** — Missing data points are treated as "good" and within the threshold\.
     + **Use the value of the last good datapoint \(Ignore and maintain the current alarm state\)** — The current alarm state is maintained\.
     + **Do not evaluate it \(Treat missing data as missing\)** — The alarm doesn't consider missing data points when evaluating whether to change state\.
   + Choose **Send a notification if there is insufficient data** to be notified when the alarm state changes to INSUFFICIENT\_DATA\. This option is available only if you choose to be notified by Email or SMS text message\.

1. Choose **Create** to add the alarm\.

   To edit the alarm later, choose the ellipsis icon \(⋮\) next to the alarm you want to edit, and choose **Edit alarm**\.

## Testing database metric alarms using the Lightsail console<a name="testing-database-alarms"></a>

Complete the following steps to test an alarm using the Lightsail console\. You might want to test an alarm to confirm that the configured notification options are working, such as to ensure that you receive an email or an SMS text message when the alarm is triggered\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Databases** tab\.

1. Choose the name of the database for which you want to test an alarm\.

1. Choose the **Metrics** tab on the database management page\.

1. Choose the metric for which you want to test an alarm in the drop\-down menu under the **Metrics Graphs** heading\.

1. Scroll down to the **Alarms** section of the page, and choose the ellipsis icon \(⋮\) next to the alarm you want to test\.

1. Choose one of the following options:
   + **Test alarm notification** — Choose this option to test the notifications for when the alarm state changes to `ALARM`\.
   + **Test OK notification** — Choose this option to test the notifications for when the alarm state changes to `OK`\.
**Note**  
If either of these options is unavailable, you might not have configured the notification options for the alarm, or the alarm might currently be in an `ALARM` state\. For more information, see [Database alarm limits](#database-alarm-limits)\.

   The alarm momentarily changes to an `ALARM` or `OK` state depending on the test option you chose, and an email and/or SMS text message is sent depending on what you configured as the notification method for the alarm\. A notification banner displays in the Lightsail console only if you chose to test the `ALARM` notification\. A notification banner is not displayed if you chose to test the `OK` notification\. The alarm will return to its actual state often after a few seconds\.

## Next steps after creating database alarms<a name="next-steps-creating-database-alarms"></a>

There are a few additional tasks that you can perform for your database alarms:
+ To stop receiving notifications, you can remove your email and mobile phone from Lightsail\. For more information, see [Deleting or disabling metric alarms in Amazon Lightsail](amazon-lightsail-deleting-notification-contacts.md)\. You can also disable or delete an alarm to stop receiving notifications for a specific alarm\. For more information, see [Deleting or disabling metric alarms in Amazon Lightsail](amazon-lightsail-deleting-health-metric-alarms.md)\.