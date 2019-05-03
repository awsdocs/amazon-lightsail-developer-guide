# Amazon Lightsail instance health metrics<a name="understanding-instance-health-metrics-in-amazon-lightsail"></a>

**Note**  
Lightsail provides several health metrics about your virtual private server \(or Lightsail *instance*\) to help you keep your application running smoothly\. You can quickly look at CPU utilization, data transfer rates, and status check metrics over a specified time period\.

 *Last updated: March 22, 2018* 

You can view the following metrics over different time periods\.

**CPUUtilization**  
This metric refers to the percentage of CPU capacity that your Lightsail instance is using\. This metric identifies the processing power required to run an application on a selected instance\.  
If you experience a high degree of CPU utilization, your instance might be unable to handle the load that you're asking it to carry\. Maybe your blog hit the big time? To fix a high\-percentage value on **CPUUtilization**, you can add more CPUs or use a Lightsail instance with a faster CPU\. You can also get more information by using the `top` command on Linux\. It shows you all the processes running on your instance and the CPU and memory resources they're using\.

**NetworkIn**  
The number of bytes received on all network interfaces by the Lightsail instance\. This metric identifies the volume of incoming network traffic to an application on a single instance\.   
With **NetworkOut**, this metric helps you measure data transfer rates\. Data transfer rates are important when it comes to billing\. For more information about your bill, see [Lightsail Billing](understanding-your-amazon-lightsail-bill.md)\.  
For troubleshooting, here are some Linux commands you can use to run network input and output diagnostics on your instance: [18 commands to monitor network bandwidth on Linux server](http://www.binarytides.com/linux-commands-monitor-network/)\.

**NetworkOut**  
The number of bytes sent out on all network interfaces by the Lightsail instance\. This metric identifies the volume of outgoing network traffic to an application on a single instance\. With **NetworkIn**, this metric helps you measure data transfer rates\.  
For troubleshooting, here are some Linux commands you can use to run network input and output diagnostics on your instance: [18 commands to monitor network bandwidth on Linux server](http://www.binarytides.com/linux-commands-monitor-network/)\.

**StatusCheckFailed**  
A combination of **StatusCheckFailed\_Instance** and **StatusCheckFailed\_System** that reports if either of the status checks has failed\. Values for this metric are either zero \(0\) or one \(1\)\. A zero indicates that the status check passed\. A one indicates a status check failure\.  
Status check metrics are available at a one\-minute frequency\. For a newly launched instance, status check metric data is available only after the instance completes the **Pending** state\. Status check metrics become available within a few minutes of the instance being in the running state\.

**StatusCheckFailed\_Instance**  
Reports whether the instance passed the Lightsail instance status check in the last minute\. Values for this metric are either zero \(0\) or one \(1\)\. A zero indicates that the status check passed\. A one indicates a status check failure\.  
Status check metrics are available at a one\-minute frequency\. For a newly launched instance, status check metric data is available only after the instance completes the **Pending** state\. Status check metrics become available within a few minutes of the instance being in the running state\.

**StatusCheckFailed\_System**  
Reports whether the instance passed the Lightsail system status check in the last minute\. Values for this metric are either zero \(0\) or one \(1\)\. A zero indicates that the status check passed\. A one indicates a status check failure\.   
Status check metrics are available at a one\-minute frequency\. For a newly launched instance, status check metric data is available only after the instance completes the **Pending** state\. Status check metrics become available within a few minutes of the instance being in the running state\.

For more information, see [Amazon EC2 Metrics and Dimensions](http://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/ec2-metricscollected.html)\.