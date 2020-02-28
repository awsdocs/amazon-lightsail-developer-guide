# Resource metrics in Amazon Lightsail<a name="amazon-lightsail-resource-health-metrics"></a>

 *Last updated: February 27, 2020* 

**Note**  
Monitor the performance of your instances, databases, and load balancers in Amazon Lightsail by checking and collecting their metric data\. Establish a baseline over time, so that you can configure alarms to more easily detect anomalies and issues with the performance of your resources\.

Amazon Lightsail reports metric data for instances, databases, and load balancers\. You can view and monitor this data in the Lightsail console\. Monitoring is an important part of maintaining the reliability, availability, and performance of your resources\. Monitor and collect metric data from your resources regularly so that you can more readily debug a multi\-point failure, if one occurs\.

**Contents**
+ [Monitoring your resources effectively](#monitoring-resources-effectively)
+ [Metric concepts and terminology](#metrics-concepts)
+ [Metrics available in Lightsail](#available-metrics)
+ [More information about metrics in Lightsail](#metrics-more-information)

## Monitoring your resources effectively<a name="monitoring-resources-effectively"></a>

You should establish a baseline for normal resource performance in your environment\. Measure performance at various times, and under different load conditions\. As you monitor your resources, you should write down and record a history of your resource's performance over time\. Compare the current performance of your resources against the historical data that you collected\. This helps you identify normal performance patterns and performance anomalies, and devise methods to address them\.

For example, you can monitor CPU utilization, network utilization, and status checks for your instances\. When performance falls outside your established baseline, you might need to reconfigure or optimize the instance to reduce CPU utilization, or reduce network traffic\. If your instance continues to operate above your CPU utilization thresholds, you might want to switch to a larger plan for your instance \(e\.g\., use the $5 USD/month plan instead of the $3\.50 USD/month plan\)\. You can switch to a larger plan by creating a new snapshot of your instance, and then creating a new instance from the snapshot using the larger plan\.

After you’ve established a baseline, you can configure alarms in the Lightsail console to notify you when your resources cross the specified thresholds\. For more information, see [Notifications in Amazon Lightsail](amazon-lightsail-notifications.md) and [Alarms in Amazon Lightsail](amazon-lightsail-alarms.md)\.

## Metric concepts and terminology<a name="metrics-concepts"></a>

The following terminology and concepts help you better understand the use of metrics in Lightsail\.

### Metrics<a name="concepts-metrics"></a>

A metric represents a time\-ordered set of data points\. Think of a metric as a variable that you monitor, and the data points as representing the values of that variable over time\. Metrics are uniquely defined by a name\. For example, some instance metrics provided by Lightsail include CPU utilization \(`CPUUtilization`\), incoming network traffic \(`NetworkIn`\), and outgoing network traffic \(`NetworkOut`\)\. For more information about all of the resource metrics available in Lightsail, see [Metrics available in Lightsail](#available-metrics)\.

### Metrics retention<a name="concepts-metrics-retention"></a>

Data points with a period of 60 seconds \(1 minute resolution\) are available for 15 days\. Data points with a period of 300 seconds \(5 minute resolution\) are available for 63 days\. Data points with a period of 3600 seconds \(1 hour resolution\) are available for 455 days \(15 months\)\.

Data points that are initially available with a shorter period are aggregated together for long\-term storage\. For example, data points with a 1 minute granularity remain available for 15 days with 1 minute resolution\. After 15 days this data is still available, but is aggregated and is retrievable only with a resolution of 5 minutes\. After 63 days, the data is further aggregated and is available with a resolution of 1 hour\. If you need availability of metrics longer than these periods, you can use the Lightsail API, AWS Command Line Interface \(AWS CLI\), and SDKs to retrieve the data points for offline or different storage\.

For more information, see [GetInstanceMetricData](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetInstanceMetricData.html), [GetLoadBalancerMetricData](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetLoadBalancerMetricData.html), and [GetRelationalDatabaseMetricData](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseMetricData.html) in the *Lightsail API reference*\.

### Statistics<a name="concepts-statistics"></a>

Metric statistics are the means in which data is aggregated over a period of time\. Example statistics include `Average`, `Sum`, and `Maximum`\. For example, instance CPU utilization metric data can be averaged using the `Average` statistic, database connections can be added using the `Sum` statistic, the maximum load balancer response time can be retrieved using the `Maximum` statistic, and so on\.

For a list of available metric statistics, see [statistics for GetInstanceMetricData](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetInstanceMetricData.html#Lightsail-GetInstanceMetricData-request-statistics), [statistics for GetLoadBalancerMetricData](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetLoadBalancerMetricData.html#Lightsail-GetLoadBalancerMetricData-request-statistics), and [statistics for GetRelationalDatabaseMetricData](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseMetricData.html#Lightsail-GetRelationalDatabaseMetricData-request-statistics) in the *Lightsail API reference*\.

### Units<a name="concepts-units"></a>

Each statistic has a unit of measure\. Example units include `Bytes`, `Seconds`, `Count`, and `Percent`\. For the complete list of the units, see [units for GetInstanceMetricData](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetInstanceMetricData.html#Lightsail-GetInstanceMetricData-request-unit), [units for GetLoadBalancerMetricData](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetLoadBalancerMetricData.html#Lightsail-GetLoadBalancerMetricData-request-unit), and [units for GetRelationalDatabaseMetricData](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseMetricData.html#Lightsail-GetRelationalDatabaseMetricData-request-unit) in the *Lightsail API reference*\.

### Periods<a name="concepts-periods"></a>

A period is the length of time associated with a specific data point—the granularity of the returned data points\. Each data point represents an aggregation of the metric data collected for a specified period of time\. Periods are defined in seconds, and the valid values for period are any multiple of 60 seconds \(1\-minute\) and 300 seconds \(5\-minutes\)\.

When you retrieve data points using the Lightsail API, you can specify a period, start time, and end time\. These parameters determine the overall length of time associated with the data point\. Lightsail reports metric data in either 1\-minute or 5\-minute increments; therefore, you must specify periods in multiples of 60 seconds and 300 seconds\. The values that you specify for the start time and end time determine how many periods Lightsail returns\. If you prefer statistics aggregated in ten\-minute blocks, specify a period of 600\. For statistics aggregated over the entire hour, specify a period of 3600, and so on\.

Periods are also important for Lightsail alarms\. Lightsail evaluates data points for alarms every 5 minutes, and each data point for alarms represents a 5\-minute period of aggregated data\. When you create an alarm to monitor a specific metric, you are asking Lightsail to compare that metric to the threshold value that you specify\. You have extensive control over how Lightsail makes that comparison\. You can specify the period over which the comparison is made, and also specify how many evaluation periods are used to reach a conclusion\. For more information, see [Alarms in Amazon Lightsail](amazon-lightsail-alarms.md)\.

### Alarms<a name="concepts-alarms"></a>

An alarm watches a single metric over a specified period of time, and notifies you when the metric crosses a threshold that you specified\. The notification can be a banner displayed in the Lightsail console, an email sent to an email address you specified, and a SMS text message sent to a mobile phone number you specified\. For more information, see [Alarms in Amazon Lightsail](amazon-lightsail-alarms.md)\.

## Metrics available in Lightsail<a name="available-metrics"></a>

### Instance metrics<a name="overview-instance-metrics"></a>

The following instance metrics are available\. For more information, see [Viewing instance metrics in Amazon Lightsail](amazon-lightsail-viewing-instance-health-metrics.md)\.
+ **CPU utilization \(`CPUUtilization`\)** — The percentage of allocated compute units that are currently in use on the instance\. This metric identifies the processing power to run the applications on the instance\. Tools in your operating system can show a lower percentage than Lightsail when the instance is not allocated a full processor core\.
**Note**  
When viewing the CPU utilization metric graphs for your instances in the Lightsail console, you will see sustainable, and burstable zones\. For more information about what these zones mean, see [CPU utilization sustainable and burstable zones](https://lightsail.aws.amazon.com/ls/docs/en_us/articles/amazon-lightsail-viewing-instance-health-metrics#cpu-utilization-zones)\.
+ **Incoming network traffic \(`NetworkIn`\)** — The number of bytes received on all network interfaces by the instance\. This metric identifies the volume of incoming network traffic to the instance\. The number reported is the number of bytes received during the period\. Because this metric is reported in 5\-minute intervals, divide the reported number by 300 to find Bytes/second\.
+ **Outgoing network traffic \(`NetworkOut`\)** — The number of bytes sent out on all network interfaces by the instance\. This metric identifies the volume of outgoing network traffic from the instance\. The number reported is the number of bytes sent during the period\. Because this metric is reported in 5\-minute intervals, divide the reported number by 300 to find Bytes/second\.
+ **Status check failures \(`StatusCheckFailed`\)** — Reports whether the instance passed or failed both the instance status check and the system status check\. This metric can be either 0 \(passed\) or 1 \(failed\)\. This metric is available at a 1\-minute frequency\.
+ **Instance status check failures \(`StatusCheckFailed_Instance`\)** — Reports whether the instance passed or failed the instance status check\. This metric can be either 0 \(passed\) or 1 \(failed\)\. This metric is available at a 1\-minute frequency\.
+ **System status check failures \(`StatusCheckFailed_System`\)** — Reports whether the instance passed or failed the system status check\. This metric can be either 0 \(passed\) or 1 \(failed\)\. This metric is available at a 1\-minute frequency\.

### Database metrics<a name="overview-database-metrics"></a>

The following database metrics are available\. For more information, see [Viewing database metrics in Amazon Lightsail](amazon-lightsail-viewing-database-health-metrics.md)\.
+ **CPU utilization \(`CPUUtilization`\)** — The percentage of CPU utilization currently in use on the database\.
+ **Database connections \(`DatabaseConnections`\)** — The number of database connections in use\.
+ **Disk queue depth \(`DiskQueueDepth`\)** — The number of outstanding IOs \(read/write requests\) that are waiting to access the disk\.
+ **Free storage space \(`FreeStorageSpace`\)** — The amount of available storage space\.
+ **Network receive throughput \(`NetworkReceiveThroughput`\)** — The incoming \(Receive\) network traffic on the database, including both customer database traffic and AWS traffic used for monitoring and replication\.
+ **Network transmit throughput \(`NetworkTransmitThroughput`\)** — The outgoing \(Transmit\) network traffic on the database, including both customer database traffic and AWS traffic used for monitoring and replication\.

### Load balancer metrics<a name="overview-load-balancer-metrics"></a>

The following load balancer metrics are available\. For more information, see [Viewing load balancer metrics in Amazon Lightsail](amazon-lightsail-viewing-load-balancer-health-metrics.md)\.
+ **Client TLS negotiation error count \(`ClientTLSNegotiationErrorCount`\)** — The number of TLS connections initiated by the client that did not establish a session with the load balancer due to a TLS error generated by the load balancer\. Possible causes include a mismatch of ciphers or protocols\.
+ **Healthy host count \(`HealthyHostCount`\)** — The number of target instances that are considered healthy\.
+ **Unhealthy host count \(`UnhealthyHostCount`\)** — The number of target instances that are considered unhealthy\.
+ **Load balancer HTTP 4XX \(`HTTPCode_LB_4XX_Count`\)** — The number of HTTP 4XX client error codes that originated from the load balancer\. Client errors are generated when requests are malformed or incomplete\. These requests were not received by the target instance\. This count does not include response codes generated by the target instances\.
+ **Load balancer HTTP 5XX \(`HTTPCode_LB_5XX_Count`\)** — The number of HTTP 5XX server error codes that originated from the load balancer\. This does not include any response codes generated by the target instance\. This metric is reported if there are no healthy instances attached to the load balancer, or if the request rate exceeds the capacity of the instances \(spillover\) or the load balancer\.
+ **Instance HTTP 2XX \(`HTTPCode_Instance_2XX_Count`\)** — The number of HTTP 2XX response codes generated by the target instances\. This does not include any response codes generated by the load balancer\.
+ **Instance HTTP 3XX \(`HTTPCode_Instance_3XX_Count`\)** — The number of HTTP 3XX response codes generated by the target instances\. This does not include any response codes generated by the load balancer\.
+ **Instance HTTP 4XX \(`HTTPCode_Instance_4XX_Count`\)** — The number of HTTP 4XX response codes generated by the target instances\. This does not include any response codes generated by the load balancer\.
+ **Instance HTTP 5XX \(`HTTPCode_Instance_5XX_Count`\)** — The number of HTTP 5XX response codes generated by the target instances\. This does not include any response codes generated by the load balancer\.
+ **Instance response time \(`InstanceResponseTime`\)** — The time elapsed, in seconds, after the request leaves the load balancer until a response from the target instance is received\.
+ **Rejected connection count \(`RejectedConnectionCount`\)** — The number of connections that were rejected because the load balancer had reached its maximum number of connections\.
+ **Request count \(`RequestCount`\)** — The number of requests processed over IPv4\. This count includes only the requests with a response generated by a target instance of the load balancer\.

## More information about metrics in Lightsail<a name="metrics-more-information"></a>

Here are some articles to help you view resource metrics in Lightsail:
+ [Viewing instance metrics in Amazon Lightsail](amazon-lightsail-viewing-instance-health-metrics.md)
+ [Viewing database metrics in Amazon Lightsail](amazon-lightsail-viewing-database-health-metrics.md)
+ [Viewing load balancer metrics in Amazon Lightsail](amazon-lightsail-viewing-load-balancer-health-metrics.md)