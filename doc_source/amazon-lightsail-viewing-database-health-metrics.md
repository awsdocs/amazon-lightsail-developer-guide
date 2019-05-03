# Viewing your database health metrics in Amazon Lightsail<a name="amazon-lightsail-viewing-database-health-metrics"></a>

 *Last updated: March 15, 2019* 

Monitoring your database health metrics in Amazon Lightsail is an important part of maintaining the reliability, availability, and performance of your managed database and associated applications\.

To effectively monitor your database, establish a baseline of normal database performance in your environment\. You do this by measuring performance at various times and under different load conditions\. As you monitor your database, consider storing historical monitoring data\. This stored data provides you a baseline to compare with current performance data, identify performance patterns and anomalies, and devise ways to address issues\.

**To view your database health metrics**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Databases** tab\.

1. Choose the name of the database for which you want to view health metrics\.

1. Choose the **Metrics** tab\.

1. The following database health metrics display:
   + **CPUUtilization** — The percentage of CPU utilization\.
   + **DatabaseConnections** — The number of database connections in use\.
   + **DiskQueueDepth** — The number of outstanding IOs \(read/write requests\) waiting to access the disk\.
   + **FreeStorageSpace** — The amount of available storage space\. Measured in bytes\.
   + **NetworkReceiveThroughput** — The incoming \(receive\) network traffic on the database\. This includes both customer database traffic and Amazon traffic used for monitoring and replication\. Measured in bytes per second\.
   + **NetworkTransmitThroughput** — The outgoing \(Transmit\) network traffic on the database\. This includes both customer database traffic and Amazon traffic used for monitoring and replication\. Measured in bytes per second\.