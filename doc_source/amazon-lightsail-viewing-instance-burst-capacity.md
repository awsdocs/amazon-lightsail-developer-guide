# Viewing instance burst capacity in Amazon Lightsail<a name="amazon-lightsail-viewing-instance-burst-capacity"></a>

 *Last updated: May 20, 2021* 

Amazon Lightsail offers instances that provide a baseline amount of CPU performance, but also have the ability to temporarily provide additional CPU performance above the baseline as needed\. This is referred to as bursting\. The baseline performance and ability to burst are governed by the following instance metrics:
+ **CPU utilization** – The percentage of allocated compute units that are in use on your instance\. This metric identifies the processing power used to run applications on your instance\.
+ **CPU burst capacity percentage** – The percentage of CPU performance available to your instance\.
+ **CPU burst capacity minutes** – The amount of time available for your instance to burst at 100% CPU utilization\.

In this guide, we show you how to monitor these metrics to maximize the availability of your instance\.

**Contents**
+ [Understanding baseline CPU performance and burst capacity accrual](#baseline-cpu-performance)
+ [Identifying when your instance bursts](#identifying-instance-burst)
+ [Monitoring CPU burst capacity](#monitoring-cpu-burst-capacity)
+ [Troubleshooting high CPU utilization](#troubleshooting-high-cpu-utilization)
+ [Viewing instance burst capacity](#viewing-instance-burst-capacity)

## Understanding baseline CPU performance and burst capacity accrual<a name="baseline-cpu-performance"></a>

Lightsail instances continuously earn \(at a millisecond\-level resolution\) a set rate of CPU burst capacity per hour, which is also consumed when your instance's CPU utilization is greater than 0%\. The accounting process for whether burst capacity is accrued or consumed also happens at a millisecond\-level resolution, so you don't have to worry about overspending CPU burst capacity; a short burst of CPU uses a small fraction of burst capacity\.

If your instance uses fewer CPU resources than is required for baseline performance \(such as when it is idle\), the unspent CPU burst capacity is accrued in the form of CPU burst capacity percentage and minutes\. If your instance needs to burst above the baseline performance level, it spends the accrued CPU burst capacity\. The more CPU burst capacity that your instance has accrued, the more time it can burst beyond its baseline when more performance is needed\.

### Baseline CPU performance<a name="baseline-cpu-instance-plans"></a>

The following list outlines the performance baselines for each Lightsail instance plan:
+ The **Linux or Unix $3\.50 USD/month** and **Windows $8 USD/month** \(1 vCPU, 512 MB memory, 30 GB storage\) instance plans include a 5% CPU utilization performance baseline\.
+ The **Linux or Unix $5 USD/month** and **Windows $12 USD/month** \(1 vCPU, 1 GB memory, 40 GB storage\) instance plans include a 10% CPU utilization performance baseline\.
+ The **Linux or Unix $10 USD/month** and **Windows $20 USD/month** \(1 vCPU, 2 GB memory, 60 GB storage\) instance plans include a 20% CPU utilization performance baseline\.
+ The **Linux or Unix $20 USD/month** and **Windows $40 USD/month** \(2 vCPUs, 4 GB memory, 80 GB storage\) instance plans include a 20% CPU utilization performance baseline\.
+ The **Linux or Unix $40 USD /month** and **Windows $70 USD/month** \(2 vCPUs, 8 GB memory, 160 GB storage\) instance plans include a 30% CPU utilization performance baseline\.
+ The **Linux or Unix $80 USD/month** and **Windows $120 USD/month** \(4 vCPUs, 16 GB memory, 320 GB storage\) instance plans include a 22\.5% CPU utilization performance baseline\.
+ The **Linux/Unix $160 USD/month** and **Windows $240 USD/month** \(8 vCPUs, 32 GB memory, 640 GB storage\) instance plans include a 17% CPU utilization performance baseline\.

**Note**  
In the EU \(Stockholm\) \(eu\-north\-1\) AWS Region, the **Linux or Unix $80 USD/month**, **Windows $120 USD/month**, **Linux/Unix $160 USD/month**, and **Windows $240 USD/month** instance plans have a 40% CPU utilization performance baseline\.

These performance baselines are per vCPU\. The CPU utilization metric graph in the Lightsail console averages the CPU utilization and baseline for instances with more than one vCPU\. For example, a Linux or Unix\-based $40 USD/month instance has two vCPUs and an averaged CPU utilization baseline of 30%\. Therefore, if:
+ One vCPU operates at 50% and the other at 0%, a 25% averaged CPU utilization is displayed on the graph\. This puts the instance's CPU utilization below its 30% baseline, and in the sustainable zone\.
+ One vCPU operates at 30%, and the other at 20%, a 25% averaged CPU utilization is displayed on the graph\. This puts the instance's CPU utilization below its 30% baseline, and in the sustainable zone\.
+ One vCPU operates at 35% and the other at 25%, a 30% averaged CPU utilization is displayed on the graph\. This puts the instance's CPU utilization at the 30% baseline\.
+ One vCPU operates at 100% and the other at 90%, a 95% averaged CPU utilization is displayed on the graph\. This puts the instance's CPU utilization above its 30% baseline, and in the burstable zone\.

**Note**  
For more information about the sustainable and burstable zones, see [Identifying when your instance bursts](#identifying-instance-burst) later in this guide\.

### CPU burst capacity accrual<a name="cpu-burst-capacity-accrual"></a>

All Lightsail instance plans accrue 4\.17% of CPU burst capacity per hour\. The maximum CPU burst capacity that can be accrued is equivalent to the amount of CPU burst capacity percentage that can be earned in a 24\-hour period\. Your instance stops accruing CPU burst capacity when the CPU burst capacity percentage reaches 100%\.

![\[CPU burst capacity accrual and consumption\]](https://d9yljz1nd5001.cloudfront.net/en_us/cdafd3c2a6d9edfefee89eda217b0068/images/amazon-lightsail-cpu-burst-capacity-consumption.png)

Accrued CPU burst capacity on a running instance does not expire\. However, CPU burst capacity does not persist between instance stops and starts\. If you stop your instance, it loses all its accrued burst capacity\.

**Note**  
Lightsail instances receive additional CPU burst capacity at launch, this is called launch CPU burst capacity\. Launch CPU burst capacity allows instances to burst immediately after launch before they have accrued additional burst capacity\. Launch CPU burst capacity does not count towards the burst capacity limit\. If your instance has not spent its launch CPU burst capacity, and remains idle over a 24\-hour period while accruing more burst capacity, its CPU burst capacity \(percentage\) metric graph will appear as over 100%\.  
Additionally, some Lightsail instances start in launch mode, which temporarily removes some of the performance limitations that are typically present on burstable instances\. Launch mode allows you to run resource\-intensive scripts at launch without affecting the overall performance of your instance\.

## Identifying when your instance bursts<a name="identifying-instance-burst"></a>

On the CPU utilization metric graph for your instances, you will see a sustainable zone, and a burstable zone\. In the following CPU utilization metric graph example, the performance baseline is 10% because the instance uses the Linux or Unix\-based $5 USD/month instance plan\.

![\[Sustainable and burstable zones on the CPU utilization graph\]](https://d9yljz1nd5001.cloudfront.net/en_us/cdafd3c2a6d9edfefee89eda217b0068/images/cpu-utilization-burstable-zone.png)

Your Lightsail instance can operate in the sustainable zone indefinitely with no impact to the operation of your system\. Your instance may begin operating in the burstable zone when under heavy load, such as when compiling code, installing new software, running a batch job, or serving peak load requests\. While operating in the burstable zone, your instance is consuming a higher amount of CPU cycles\. Therefore, it can only operate in this zone for a limited period of time\.

The period of time your instance can operate in the burstable zone is dependent on how far into the burstable zone it is\. An instance operating in the lower end of the burstable zone can burst for a longer period of time than an instance operating in the higher end of the burstable zone\. However, an instance that is anywhere in the burstable zone for a sustained period of time will eventually use up all the CPU capacity until it operates in the sustainable zone again\. Therefore, it is important to also monitor the remaining CPU burst capacity, which is described in the following section of this guide\.

## Monitoring CPU burst capacity<a name="monitoring-cpu-burst-capacity"></a>

The CPU overview page in the Lightsail console displays your instance's CPU utilization in comparison to its available CPU burst capacity\. In the following CPU overview example, the CPU burst capacity percentage has increased because the instance has continuously operated below its baseline in the sustainable zone\.

![\[CPU overview page in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/cdafd3c2a6d9edfefee89eda217b0068/images/cpu-overview-page.png)

The remaining CPU burst capacity graph view can be switched between CPU burst capacity percentage and minutes\. Your instance consumes more CPU burst capacity when operating in the bursting zone\. The CPU burst capacity minutes metric is the amount of time available for your instance to burst at 100% CPU utilization, It is consumed at the same rate as your instance's current CPU utilization percentage when operating in the burstable zone\. For example, a Linux or Unix\-based $5 USD/month instance has a CPU utilization baseline of 10%, and accrues 3 minutes of CPU burst capacity minutes per hour\. Therefore, if the instance operates at:
+ 100% CPU utilization in the burstable zone for a 60\-minute period, then it consumes CPU burst capacity minutes at a 100% rate in that period\. The instance consumes 60 minutes of CPU burst capacity, and accrues 3 minutes, for a total consumption of 57 minutes\.
+ 50% CPU utilization in the burstable zone for a 60\-minute period, then it consumes CPU burst capacity minutes at a 50% rate in that period\. The instance consumes 30 minutes of CPU burst capacity, and accrues 3 minutes, for a total consumption of 27 minutes\.
+ 10% CPU utilization at the instance's baseline for a 60\-minute period, then it consumes CPU burst capacity minutes at a 10% rate in that period\. The instance consumes 6 minutes of CPU burst capacity, and accrues 6 minutes\. When an instance operates at its baseline, the CPU burst capacity minutes doesn't increase or decrease\.
+ 5% CPU utilization in the sustainable zone for a 60\-minute period, then it consumes CPU burst capacity minutes at a 5% rate in that period\. The instance consumed 3 minutes of CPU burst capacity, and accrued 6 minutes, for a total accrual of 3 minutes\.

Alternately, if the instance has accrued 60 minutes of CPU burst capacity, then it can operate at 100% CPU utilization for 60 minutes, at 50% for 120 minutes, or at 25% at 150 minutes\.

## Troubleshooting high CPU utilization<a name="troubleshooting-high-cpu-utilization"></a>

Your instance will use all of its burst capacity if it operates in the bursting zone frequently, or for extended periods of time\. This can signify that your instance is under\-provisioned\. It could also be that a service is running too frequently, or your instance is running unnecessary software\.

Investigate what is causing your instance to burst using tools like top on Linux/Unix instances, and Task Manager on Windows Server instances\. These tools show you the services that are consuming resources on your instance\. Determine which services are consuming the most resources, and identify if they can be disabled without impacting the workload of your instance\. By disabling services, or uninstalling software, you may be able to lower the bursting of your instance, and avoid having to up\-size your instance\.

If your instance is truly under\-provisioned, and you cannot lower its CPU utilization, then you can mitigate burst capacity consumption by adding more processing power\. You do this by creating a snapshot of your instance, and then creating a new instance from the snapshot using a larger Lightsail instance plan\. For example, use the Linux or Unix\-based $20 USD per month plan on your new instance instead of the Linux or Unix\-based $10 USD per month plan used on the previous instance\. When your new instance is up and running, make changes to your workload's DNS as necessary to swap the old instance with the new one\. Delete your old under\-provisioned instance after traffic starts routing to your new instance\. For more information, see [Snapshots in Amazon Lightsail](understanding-instance-snapshots-in-amazon-lightsail.md)\.

## Viewing instance burst capacity<a name="viewing-instance-burst-capacity"></a>

Complete the following steps to access the CPU overview page, and view your instance's CPU utilization and remaining CPU burst capacity\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Instances** tab\.

1. Choose the name of the instance for which you want to view CPU utilization and burst capacity\.  
![\[Instances tab in the Lightsail home page\]](https://d9yljz1nd5001.cloudfront.net/en_us/cdafd3c2a6d9edfefee89eda217b0068/images/cpu-utilization-instances-tab.png)

1. Choose the **Metrics** tab on the instance management page\.  
![\[Metrics tab in the instance management page\]](https://d9yljz1nd5001.cloudfront.net/en_us/cdafd3c2a6d9edfefee89eda217b0068/images/cpu-utilization-metrics-tab.png)

1. Choose **CPU overview** in the drop\-down menu under the **Metrics graphs** heading\.  
![\[CPU overview option in the metrics tab\]](https://d9yljz1nd5001.cloudfront.net/en_us/cdafd3c2a6d9edfefee89eda217b0068/images/cpu-utilization-cpu-overview.png)

   The page displays **Average CPU utilization per 5 minutes** and **Remaining CPU burst capacity** graphs\.
**Note**  
The **Remaining CPU burst capacity** graph might display a **Launch mode** zone for a short period of time after you create an instance\. Some Lightsail instances start in launch mode, which temporarily removes some of the performance limitations that are typically present on burstable instances\. Launch mode allows you to run resource\-intensive scripts at launch without affecting the overall performance of your instance\.  
![\[CPU overview page in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/cdafd3c2a6d9edfefee89eda217b0068/images/cpu-overview-page.png)

1. You can perform the following actions on the metric graphs:
   + For the burst capacity graph, select **Show capacity as percentage of total** to change the view from burst capacity minutes available to burst capacity percentage available\.
   + Change the view of the graph to show data for 1 hour, 6 hours, 1 day, 1 week, and 2 weeks\.
   + Pause your cursor on a data point to view detailed information about that data point\.
   + Add an alarm to be notified when CPU utilization and burst capacity crosses a threshold you specify\. Alarms cannot be added in the CPU overview page\. You must add them in the individual CPU utilization, CPU burst capacity percentage, and CPU burst capacity minutes metric graph pages\. For more information, see [Alarms in Amazon Lightsail](amazon-lightsail-alarms.md) and [Creating instance metric alarms in Amazon Lightsail](amazon-lightsail-adding-instance-health-metric-alarms.md)\.