# Viewing database metrics in Amazon Lightsail<a name="amazon-lightsail-viewing-database-health-metrics"></a>

 *Last updated: February 27, 2020* 

After you launch a database in Amazon Lightsail, you can view its metric graphs on the **Metrics** tab of the database’s management page\. Monitoring metrics is an important part of maintaining the reliability, availability, and performance of your resources\. Monitor and collect metric data from your resources regularly so that you can more readily debug a multi\-point failure, if one occurs\. For more information about metrics, see [Metrics in Amazon Lightsail](amazon-lightsail-resource-health-metrics.md)\.

When monitoring your resources, you should establish a baseline for normal resource performance in your environment\. After you’ve established a baseline, you can configure alarms in the Lightsail console to notify you when your resources are performing outside of specified thresholds\. For more information, see [Notifications in Amazon Lightsail](amazon-lightsail-notifications.md) and [Alarms in Amazon Lightsail](amazon-lightsail-alarms.md)\.

**Contents**
+ [Database metrics available in Lightsail](#database-metrics)
+ [Viewing database metrics in the Lightsail console](#viewing-database-metrics-console)
+ [Next steps after viewing your database metrics](#next-steps-viewing-database-metrics)

## Database metrics available in Lightsail<a name="database-metrics"></a>

The following database metrics are available:
+ **CPU utilization \(`CPUUtilization`\)** — The percentage of CPU utilization currently in use on the database\.
+ **Database connections \(`DatabaseConnections`\)** — The number of database connections in use\.
+ **Disk queue depth \(`DiskQueueDepth`\)** — The number of outstanding IOs \(read/write requests\) that are waiting to access the disk\.
+ **Free storage space \(`FreeStorageSpace`\)** — The amount of available storage space\.
+ **Network receive throughput \(`NetworkReceiveThroughput`\)** — The incoming \(Receive\) network traffic on the database, including both customer database traffic and AWS traffic used for monitoring and replication\.
+ **Network transmit throughput \(`NetworkTransmitThroughput`\)** — The outgoing \(Transmit\) network traffic on the database, including both customer database traffic and AWS traffic used for monitoring and replication\.

## Viewing database metrics in the Lightsail console<a name="viewing-database-metrics-console"></a>

Complete the following steps to view database metrics in the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Databases** tab\.

1. Choose the name of the database for which you want to view metrics\.

1. Choose the **Metrics** tab on the database management page\.

1. Choose the metric that you want to view in the drop\-down menu under the **Metrics graphs** heading\.

   The graph displays a visual representation of the data points for the chosen metric\.

1. You can perform the following actions on the metrics graph:
   + Change the view of the graph to show data for 1 hour, 6 hours, 1 day, 1 week, and 2 weeks\.
   + Pause your cursor on a data point to view detailed information about that data point\.
   + Add an alarm for the chosen metric to be notified when the metric crosses a threshold you specify\. For more information, see [Alarms in Amazon Lightsail](amazon-lightsail-alarms.md) and [Creating database metric alarms in Amazon Lightsail](amazon-lightsail-adding-database-health-metric-alarms.md)\.

## Next steps after viewing your database metrics<a name="next-steps-viewing-database-metrics"></a>

There are a few additional tasks that you can perform for your database metrics:
+ Add an alarm for the chosen metric to be notified when the metric crosses a threshold you specify\. For more information, see [Alarms in Amazon Lightsail](amazon-lightsail-alarms.md) and [Creating database metric alarms in Amazon Lightsail](amazon-lightsail-adding-database-health-metric-alarms.md)\.
+ When an alarm is triggered, a notification banner is displayed in the Lightsail console\. To be notified by email and SMS text message, you must add your email address and mobile phone number as notification contacts in each AWS Region where you want to monitor your resources\. For more information, see [Adding notification contacts in Amazon Lightsail](amazon-lightsail-adding-editing-notification-contacts.md)\.
+ To stop receiving notifications, you can remove your email and mobile phone from Lightsail\. For more information, see [Deleting or disabling metric alarms in Amazon Lightsail](amazon-lightsail-deleting-notification-contacts.md)\. You can also disable or delete an alarm to stop receiving notifications for a specific alarm\. For more information, see [Deleting or disabling metric alarms in Amazon Lightsail](amazon-lightsail-deleting-health-metric-alarms.md)\.