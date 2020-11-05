# Amazon Lightsail health metrics<a name="understanding-instance-health-metrics-in-amazon-lightsail"></a>

**Note**  
Lightsail provides several health metrics for your resources to help you keep your application running smoothly\. You can quickly look at CPU utilization, data transfer rates, and status check metrics over a specified time period\.

 *Last updated: July 23, 2020* 

You can view the following Amazon Lightsail resource metrics over different time periods\. For more informationa bout resource metrics in Lightsail, see [Resource metrics in Amazon Lightsail](amazon-lightsail-resource-health-metrics.md)\.

## Instance metrics<a name="understanding-instance-metrics"></a>

The following instance metrics are available\. For more information, see [Viewing instance metrics in Amazon Lightsail](amazon-lightsail-viewing-instance-health-metrics.md)\.
+ **Burst capacity \(`BurstCapacityPercentage` and `BurstCapacityTime`\)** — Burst capacity percentage represents the percentage of burst capacity available to your instance\. Burst capacity minutes represents the time available for your instance to burst at 100% CPU utilization\. Your instance consumes burst capacity when operating in the bursting zone and accrues it when in the sustainable zone\. Burst capacity minutes is consumed at the full rate only when your instance operates at 100% CPU utilization\. For more information about instance burst capacity, see [Viewing instance burst capacity in Amazon Lightsail](amazon-lightsail-viewing-instance-burst-capacity.md)\.
+ **CPU utilization \(`CPUUtilization`\)** — The percentage of allocated compute units that are currently in use on the instance\. This metric identifies the processing power to run the applications on the instance\. Tools in your operating system can show a lower percentage than Lightsail when the instance is not allocated a full processor core\.

  When viewing the CPU utilization metric graphs for your instances in the Lightsail console, you will see sustainable, and burstable zones\. For more information about what these zones mean, see [CPU utilization sustainable and burstable zones](https://lightsail.aws.amazon.com/ls/docs/en_us/articles/amazon-lightsail-viewing-instance-health-metrics#cpu-utilization-zones)\.
+ **Incoming network traffic \(`NetworkIn`\)** — The number of bytes received on all network interfaces by the instance\. This metric identifies the volume of incoming network traffic to the instance\. The number reported is the number of bytes received during the period\. Because this metric is reported in 5\-minute intervals, divide the reported number by 300 to find Bytes/second\.
+ **Outgoing network traffic \(`NetworkOut`\)** — The number of bytes sent out on all network interfaces by the instance\. This metric identifies the volume of outgoing network traffic from the instance\. The number reported is the number of bytes sent during the period\. Because this metric is reported in 5\-minute intervals, divide the reported number by 300 to find Bytes/second\.
+ **Status check failures \(`StatusCheckFailed`\)** — Reports whether the instance passed or failed both the instance status check and the system status check\. This metric can be either 0 \(passed\) or 1 \(failed\)\. This metric is available at a 1\-minute frequency\.
+ **Instance status check failures \(`StatusCheckFailed_Instance`\)** — Reports whether the instance passed or failed the instance status check\. This metric can be either 0 \(passed\) or 1 \(failed\)\. This metric is available at a 1\-minute frequency\.
+ **System status check failures \(`StatusCheckFailed_System`\)** — Reports whether the instance passed or failed the system status check\. This metric can be either 0 \(passed\) or 1 \(failed\)\. This metric is available at a 1\-minute frequency\.

## Database metrics<a name="understanding-database-metrics"></a>

The following database metrics are available\. For more information, see [Viewing database metrics in Amazon Lightsail](amazon-lightsail-viewing-database-health-metrics.md)\.
+ **CPU utilization \(`CPUUtilization`\)** — The percentage of CPU utilization currently in use on the database\.
+ **Database connections \(`DatabaseConnections`\)** — The number of database connections in use\.
+ **Disk queue depth \(`DiskQueueDepth`\)** — The number of outstanding IOs \(read/write requests\) that are waiting to access the disk\.
+ **Free storage space \(`FreeStorageSpace`\)** — The amount of available storage space\.
+ **Network receive throughput \(`NetworkReceiveThroughput`\)** — The incoming \(Receive\) network traffic on the database, including both customer database traffic and AWS traffic used for monitoring and replication\.
+ **Network transmit throughput \(`NetworkTransmitThroughput`\)** — The outgoing \(Transmit\) network traffic on the database, including both customer database traffic and AWS traffic used for monitoring and replication\.

## Distribution metrics<a name="understanding-distribution-metrics"></a>

The following distribution metrics are available\. For more information, see [Viewing distribution metrics in Amazon Lightsail](amazon-lightsail-viewing-distribution-health-metrics.md)\.
+ **Requests** — The total number of viewer requests received by your distribution, for all HTTP methods, and for both HTTP and HTTPS requests\.
+ **Bytes uploaded** — The number of bytes uploaded to your origin by your distribution, using POST and PUT requests\.
+ **Bytes downloaded** — The number of bytes downloaded by viewers for GET, HEAD, and OPTIONS requests\.
+ **Total error rate** — The percentage of all viewer requests for which the response’s HTTP status code was 4xx or 5xx\.
+ **HTTP 4xx error rate** — The percentage of all viewer requests for which the response’s HTTP status code was 4xx\. In these cases, the client or client viewer may have made an error\. For example, a status code of 404 \(Not Found\) means that the client requested an object that could not be found\.
+ **HTTP 5xx error rate** — The percentage of all viewer requests for which the response’s HTTP status code was 5xx\. In these cases, the origin server did not satisfy the request\. For example, a status code of 503 \(Service Unavailable\) means that the origin server is currently unavailable\.

## Load balancer metrics<a name="understanding-load-balancer-metrics"></a>

The following load balancer metrics are available\. For more information, see [Viewing load balancer metrics in Amazon Lightsail](amazon-lightsail-viewing-load-balancer-health-metrics.md)\.
+ **Healthy host count \(`HealthyHostCount`\)** — The number of target instances that are considered healthy\.
+ **Unhealthy host count \(`UnhealthyHostCount`\)** — The number of target instances that are considered unhealthy\.
+ **Load balancer HTTP 4XX \(`HTTPCode_LB_4XX_Count`\)** — The number of HTTP 4XX client error codes that originated from the load balancer\. Client errors are generated when requests are malformed or incomplete\. These requests were not received by the target instance\. This count does not include response codes generated by the target instances\.
+ **Load balancer HTTP 5XX \(`HTTPCode_LB_5XX_Count`\)** — The number of HTTP 5XX server error codes that originated from the load balancer\. This does not include any response codes generated by the target instance\. This metric is reported if there are no healthy instances attached to the load balancer, or if the request rate exceeds the capacity of the instances \(spillover\) or the load balancer\.
+ **Instance HTTP 2XX \(`HTTPCode_Instance_2XX_Count`\)** — The number of HTTP 2XX response codes generated by the target instances\. This does not include any response codes generated by the load balancer\.
+ **Instance HTTP 3XX \(`HTTPCode_Instance_3XX_Count`\)** — The number of HTTP 3XX response codes generated by the target instances\. This does not include any response codes generated by the load balancer\.
+ **Instance HTTP 4XX \(`HTTPCode_Instance_4XX_Count`\)** — The number of HTTP 4XX response codes generated by the target instances\. This does not include any response codes generated by the load balancer\.
+ **Instance HTTP 5XX \(`HTTPCode_Instance_5XX_Count`\)** — The number of HTTP 5XX response codes generated by the target instances\. This does not include any response codes generated by the load balancer\.
+ **Instance response time \(`InstanceResponseTime`\)** — The time elapsed, in seconds, after the request leaves the load balancer until a response from the target instance is received\.
+ **Request count \(`RequestCount`\)** — The number of requests processed over IPv4\. This count includes only the requests with a response generated by a target instance of the load balancer\.
+ **Client TLS negotiation error count \(`ClientTLSNegotiationErrorCount`\)** — The number of TLS connections initiated by the client that did not establish a session with the load balancer due to a TLS error generated by the load balancer\. Possible causes include a mismatch of ciphers or protocols\.
+ **Rejected connection count \(`RejectedConnectionCount`\)** — The number of connections that were rejected because the load balancer had reached its maximum number of connections\.