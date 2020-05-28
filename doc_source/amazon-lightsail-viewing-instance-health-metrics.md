# Viewing instance metrics in Amazon Lightsail<a name="amazon-lightsail-viewing-instance-health-metrics"></a>

 *Last updated: February 27, 2020* 

After you launch an instance in Amazon Lightsail, you can view its metric graphs on the **Metrics** tab of the instance’s management page\. Monitoring metrics is an important part of maintaining the reliability, availability, and performance of your resources\. Monitor and collect metric data from your resources regularly so that you can more readily debug a multi\-point failure, if one occurs\. For more information about metrics, see [Metrics in Amazon Lightsail](amazon-lightsail-resource-health-metrics.md)\.

When monitoring your resources, you should establish a baseline for normal resource performance in your environment\. Then you can configure alarms in the Lightsail console to notify you when your resources are performing outside of specified thresholds\. For more information, see [Notifications in Amazon Lightsail](amazon-lightsail-notifications.md) and [Alarms in Amazon Lightsail](amazon-lightsail-alarms.md)\.

**Contents**
+ [Instance metrics available in Lightsail](#instance-metrics)
+ [CPU utilization sustainable and burstable zones](#cpu-utilization-zones)
+ [Viewing instance metrics in the Lightsail console](#viewing-instance-metrics-console)
+ [Next steps after viewing instance metrics](#next-steps-viewing-instance-metrics)

## Instance metrics available in Lightsail<a name="instance-metrics"></a>

The following instance metrics are available:
+ **CPU utilization \(`CPUUtilization`\)** — The percentage of allocated compute units that are currently in use on the instance\. This metric identifies the processing power to run the applications on the instance\. Tools in your operating system can show a lower percentage than Lightsail when the instance is not allocated a full processor core\.
**Note**  
When viewing the CPU utilization metric graphs for your instances in the Lightsail console, you will see sustainable, and burstable zones\. For more information about these zones, see [CPU utilization sustainable and burstable zones](#cpu-utilization-zones)\.
+ **Incoming network traffic \(`NetworkIn`\)** — The number of bytes received on all network interfaces by the instance\. This metric identifies the volume of incoming network traffic to the instance\. The number reported is the number of bytes received during the period\. Because this metric is reported in 5\-minute intervals, divide the reported number by 300 to find Bytes/second\.
+ **Outgoing network traffic \(`NetworkOut`\)** — The number of bytes sent out on all network interfaces by the instance\. This metric identifies the volume of outgoing network traffic from the instance\. The number reported is the number of bytes sent during the period\. Because this metric is reported in 5\-minute intervals, divide the reported number by 300 to find Bytes/second\.
+ **Status check failures \(`StatusCheckFailed`\)** — Reports whether the instance passed or failed both the instance status check and the system status check\. This metric can be either 0 \(passed\) or 1 \(failed\)\. This metric is available at a 1\-minute frequency\.
+ **Instance status check failures \(`StatusCheckFailed_Instance`\)** — Reports whether the instance passed or failed the instance status check\. This metric can be either 0 \(passed\) or 1 \(failed\)\. This metric is available at a 1\-minute frequency\.
+ **System status check failures \(`StatusCheckFailed_System`\)** — Reports whether the instance passed or failed the system status check\. This metric can be either 0 \(passed\) or 1 \(failed\)\. This metric is available at a 1\-minute frequency\.

## CPU utilization sustainable and burstable zones<a name="cpu-utilization-zones"></a>

Lightsail uses burstable instances which provide a baseline amount of CPU performance, but also have the ability to temporarily provide additional CPU performance above the baseline as needed\. This is referred to as bursting\. With burstable instances, you don’t have to over\-provision your instance to handle occasional performance spikes—you don’t have to pay for capacity you never use\.

On the CPU utilization metric graph for your instances, you will see a sustainable zone, and a burstable zone\. Your Lightsail instance can operate in the sustainable zone indefinitely with no impact to the operation of your system\.

![\[Sustainable and burstable zones on the CPU utilization graph.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/cpu-utilization-burstable-zone.png)

Your instance may begin operating in the burstable zone when under heavy load, such as when compiling code, installing new software, running a batch job, or serving peak load requests\. While operating in the burstable zone, your instance is consuming a higher amount of CPU cycles\. Therefore, it can only operate in this zone for a limited period of time\.

The period of time your instance can operate in the burstable zone is dependent on how far into the burstable zone it is\. An instance operating in the lower end of the burstable zone can burst for a longer period of time than an instance operating in the higher end of the burstable zone\. However, an instance that is anywhere in the burstable zone for a sustained period of time will eventually use up all the CPU capacity until it operates in the sustainable zone again\.

Monitor your instance’s CPU utilization metric to see how its performance is distributed between the sustainable and burstable zones\. If your system only occasionally moves into the burstable zone, you should be fine continuing to use the instance that you’re running\. However, if you see your instance spending a considerable amount of time in the burstable zone, you might want to switch to a larger plan for your instance \(e\.g\., use the $10 USD/month plan instead of the $3\.50 USD/month plan\)\. You can switch to a larger plan by creating a new snapshot of your instance, and then creating a new instance from the snapshot\.

## Viewing instance metrics in the Lightsail console<a name="viewing-instance-metrics-console"></a>

Complete the following steps to view instance metrics in the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Instances** tab\.

1. Choose the name of the instance for which you want to view metrics\.

1. Choose the **Metrics** tab on the instance management page\.

1. Choose the metric that you want to view in the drop\-down menu under the **Metrics graphs** heading\.

   The graph displays a visual representation of the data points for the chosen metric\.
**Note**  
When viewing the CPU utilization metric graphs for your instances in the Lightsail console, you will see sustainable, and burstable zones\. For more information about these zones, see [CPU utilization sustainable and burstable zones](#cpu-utilization-zones)\.

1. You can perform the following actions on the metrics graph:
   + Change the view of the graph to show data for 1 hour, 6 hours, 1 day, 1 week, and 2 weeks\.
   + Pause your cursor on a data point to view detailed information about that data point\.
   + Add an alarm for the chosen metric to be notified when the metric crosses a threshold you specify\. For more information, see [Alarms in Amazon Lightsail](amazon-lightsail-alarms.md) and [Creating instance metric alarms in Amazon Lightsail](amazon-lightsail-adding-instance-health-metric-alarms.md)\.

## Next steps after viewing your instance metrics<a name="next-steps-viewing-instance-metrics"></a>

There are a few additional tasks that you can perform for your instance metrics:
+ Add an alarm for the chosen metric to be notified when the metric crosses a threshold you specify\. For more information, see [Alarms in Amazon Lightsail](amazon-lightsail-alarms.md) and [Creating instance metric alarms in Amazon Lightsail](amazon-lightsail-adding-instance-health-metric-alarms.md)\.
+ When an alarm is triggered, a notification banner is displayed in the Lightsail console\. To be notified by email and SMS text message, you must add your email address and mobile phone number as notification contacts in each AWS Region where you want to monitor your resources\. For more information, see [Adding notification contacts in Amazon Lightsail](amazon-lightsail-adding-editing-notification-contacts.md)\.
+ To stop receiving notifications, you can remove your email and mobile phone from Lightsail\. For more information, see [Deleting or disabling metric alarms in Amazon Lightsail](amazon-lightsail-deleting-notification-contacts.md)\. You can also disable or delete an alarm to stop receiving notifications for a specific alarm\. For more information, see [Deleting or disabling metric alarms in Amazon Lightsail](amazon-lightsail-deleting-health-metric-alarms.md)\.