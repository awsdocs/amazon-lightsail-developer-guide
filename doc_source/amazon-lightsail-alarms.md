# Alarms in Amazon Lightsail<a name="amazon-lightsail-alarms"></a>

 *Last updated: February 27, 2020* 

You can create an alarm in Amazon Lightsail that watches a single metric for your instances, databases, and load balancers\. The alarm can be configured to notify you based on the value of the metric relative to a threshold that you specify\. Notifications can be a banner displayed in the Lightsail console, an email sent to your email address, and an SMS text message sent to your mobile phone number\. In this guide, we describe the alarm conditions and settings that you can configure\.

**Contents**
+ [Configuring an alarm](#configuring-alarm)
+ [Alarms states](#alarm-states)
+ [Alarm example](#alarm-example)
+ [Configure how Lightsail alarms treat missing data](#missing-data)
+ [How alarm state is evaluated when data is missing](#alarm-evaluation)
+ [Missing data in graphed examples](#missing-data-examples)
+ [More information about alarms](#more-information-alarms)

## Configuring an alarm<a name="configuring-alarm"></a>

To add an alarm in the Lightsail console, browse to the **Metrics** tab of your instance, database, or load balancer\. You then choose the metric you want to monitor, and choose **Add alarm**\. You can add two alarms per metric\. For more information about metrics, see [Resource metrics in Amazon Lightsail](amazon-lightsail-resource-health-metrics.md)\.

To configure the alarm, you first identify a threshold value, which is the metric value at which point the alarm will change states \(e\.g\., change from an `OK` state to an `ALARM` state, or vice versa\)\. For more information, see [Alarms states](#alarm-states)\. You then select a comparison operator that will be used to compare the metric to the threshold\. The available operators are **greater than or equal to**, **greater than**, **less than**, and **less than or equal to**\.

You then specify the number of times the threshold must be crossed, and the period of time the metric will be evaluated, for the alarm to change states\. Lightsail evaluates data points for alarms every 5 minutes, and each data point represents a 5 minute period of aggregated data\. For example, if you specify the alarm to trigger when the threshold is crossed 2 times, then the evaluation period must be *in the last 10 minutes* or greater \(up to 24 hours\)\. If you specify the alarm to trigger when the threshold is crossed 10 times, then the evaluation period must be *in the last 50 minutes* or greater \(up to 24 hours\)\.

After you configure the conditions for the alarm, you can configure how you would like to be notified\. Notification banners always display in the Lightsail console when the alarm changes from an `OK` state to an `ALARM` state\. You can also choose to be notified by email and SMS text message, but you must configure notification contacts for those\. For more information, see [Notifications in Amazon Lightsail](amazon-lightsail-notifications.md)\. If you choose to be notified by email and/or SMS text message, you can also choose to be notified when the alarm state changes from an `ALARM` state to an `OK` state, which is considered as an *all clear* notification\.

Within the **Advanced settings** for the alarm, you can choose how Lightsail treats missing metric data\. For more information, see [Configure how Lightsail alarms treat missing data](#missing-data)\.

## Alarms states<a name="alarm-states"></a>

An alarm is always in one of the following states:
+ **ALARM** — The metric is outside of the defined threshold\.

  For example, if you choose a **greater than** comparison operator, the alarm will be in an `ALARM` state when the metric is greater than the specified threshold\. If you choose a **less than** comparison operator, the alarm will be in an `ALARM` state when the metric is less than the specified threshold\.
+ **OK** — The metric is within the defined threshold\.

  For example, if you choose a **greater than** comparison operator, the alarm will be in an `OK` state when the metric is less than the specified threshold\. If you choose a **less than** comparison operator, the alarm will be in an `OK` state when the metric is greater than the specified threshold\.
+ **INSUFFICIENT\_DATA** — The alarm has just started, the metric is not available, or there is not enough metric data available for the alarm to determine the alarm state\.

Alarms are triggered for state changes only\. Alarms are not triggered simply because they are in a particulate state—the state must have changed\. When an alarm is triggered, a banner is displayed in the Lightsail console\. You can also configure alarms to notify you by email, and SMS text message\.

## Alarm example<a name="alarm-example"></a>

With the previously described alarm conditions in mind, you can configure an alarm that goes into an `ALARM` state when an instance’s CPU utilization is greater than or equal to 5 percent one time in a single 5\-minute period\. The following example shows the settings for this alarm in the Lightsail console\.

![\[Example of a CPU utilization alarm.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-cpu-utilization-alarm-example.png)

In this example, if the instance’s CPU utilization metric reports a 5 percent or above utilization in just one data point, the alarm changes from an `OK` state to an `ALARM` state\. Each subsequent data point reported that is 5 percent or above utilization maintains the alarm at an `ALARM` state\. When the instance’s CPU utilization metric reports a 4\.9 percent or below utilization in just one data point, the alarm changes from an `ALARM` state to an `OK` state\.

The following graph further illustrates this alarm\. The dotted red line represents the 5% CPU utilization threshold, and the blue dots represent metric data points\. The alarm is in an `OK` state for the first data point\. The second data point changes the alarm to an `ALARM` state because the data point is greater than the threshold\. The third and fourth data points maintain the `ALARM` state, because the data points continue to be greater than the threshold\. The fifth data point changes the alarm to an `OK` state because the data point is less than the threshold\.

![\[Example of an alarming metric.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-graphed-metric-example.png)

## Configure how Lightsail alarms treat missing data<a name="missing-data"></a>

In some cases, some data points for a metric with an alarm are not reported\. For example, this can happen when a connection is lost, or a server goes down\.

Lightsail lets you specify how to treat missing data points when configuring an alarm\. This helps you configure your alarm to go to the ALARM state when appropriate for the type of data being monitored\. You can avoid false positives when missing data doesn't indicate a problem\.

Similar to how each alarm is always in one of three states, each specific data point reported falls under one of three categories:
+ **Not breaching** — The data point is within the threshold\.

  For example, if you choose a **greater than** comparison operator, the data point will be `Not breaching` when it is less than the specified threshold\. If you choose a **less than** comparison operator, the data point will be `Not breaching` when it is greater than the specified threshold\.
+ **Breaching** — The data point is outside of the threshold\.

  For example, if you choose a **greater than** comparison operator, the data point will be `Breaching` when it is greater than the specified threshold\. If you choose a **less than** comparison operator, the data point will be `Breaching` when it is less than the specified threshold\.
+ **Missing** — The behavior for missing data points is specified by the `treat missing data` parameter\.

For each alarm, you can specify Lightsail to treat missing data points as any of the following:
+ **Not breaching** — Missing data points are treated as "good" and within the threshold\.
+ **Breaching** — Missing data points are treated as "bad" and breaching the threshold\.
+ **Ignore** — The current alarm state is maintained\.
+ **Missing** — The alarm doesn't consider missing data points when evaluating whether to change state\. This is the default behavior for alarms\.

The best choice depends on the type of metric\. For a metric such as an instance’s CPU utilization, you might want to treat missing data points as breaching\. This is because the missing data points might indicate that something is wrong\. But for a metric that generates data points only when an error occurs, such as a load balancer’s HTTP 500 server error count, you might want to treat missing data as not breaching\.

Choosing the best option for your alarm prevents unnecessary and misleading alarm condition changes\. It also more accurately indicates the health of your system\.

## How alarm state is evaluated when data is missing<a name="alarm-evaluation"></a>

No matter what value you set for how to treat missing data, when an alarm evaluates whether to change state, Lightsail attempts to retrieve a greater number of data points than specified by **Evaluation Periods**\. The exact number of data points it attempts to retrieve depends on the length of the alarm period\. The time frame of the data points that it attempts to retrieve is the evaluation range\.

After Lightsail retrieves these data points, the following happens:
+ If no data points in the evaluation range are missing, Lightsail evaluates the alarm based on the most recent data points collected\.
+ If some data points in the evaluation range are missing, but the number of existing data points collected is equal to or more than the alarm's **Evaluation periods**, Lightsail evaluates the alarm state based on the most recent existing data points that were successfully collected\. In this case, the value you set for how to treat missing data is not needed, and is then ignored\.
+ If some data points in the evaluation range are missing, and the number of existing data points that were collected is less than the alarm's number of **Evaluation periods**, Lightsail fills in the missing data points with the result you specified for how to treat missing data, and then evaluates the alarm\. However, any real data points in the evaluation range, no matter when they were reported, are included in the evaluation\. Lightsail uses missing data points only as few times as possible\.

In all of these situations, the number of data points evaluated is equal to the value of **Evaluation periods**\. If fewer than the value of **Data points to alarm** are breaching, the alarm state is set to OK\. Otherwise, the state is set to ALARM\.

**Note**  
A particular case of this behavior is that Lightsail alarms might repeatedly re\-evaluate the last set of data points for a period of time after the metric has stopped flowing\. This re\-evaluation might cause the alarm to change state and re\-execute actions, if it had changed state immediately before the metric stream stopping\. To mitigate this behavior, use shorter periods\.

## Missing data in graphed examples<a name="missing-data-examples"></a>

The following graphs in this section help illustrate examples of the alarm evaluation behavior\. In graphs A, B, C, D, and E, the number data points that must be braching to alarm, and the evaluation periods, are both 3\. The dotted red line represents the threshold, the blue dots represent valid data points, and the dashes represent missing data\. Data points above the threshold line are breaching, and data points below the threshold are not breaching\. In case some of the most recent three data points are missing, Lightsail will attempt to retrieve additional valid data points\.

**Note**  
If data points are missing soon after you create an alarm, and the metric was being reported to Lightsail before you created the alarm, Lightsail retrieves the most recent data points from before the alarm was created when evaluating the alarm\.

### Graph A<a name="missing-data-graph-a"></a>

![\[Missing data graph A.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-alarm-graph-a.png)

In the preceding graphed metric, data point 1 is within threshold, data point 2 is missing, data point 3 is breaching, data point 4 is missing, and data point 5 is breaching\. Given that there are three valid data points in the evaluation range, this metric has zero missing data points\. If you configured an alarm to treat missing data points as:
+ **Not breaching** — The alarm would be in an OK state\.
+ **Breaching** — The alarm would be in an OK state\.
+ **Ignore** — The alarm would be in an OK state\.
+ **Missing** — The alarm would be in an OK state\.

### Graph B<a name="missing-data-graph-b"></a>

![\[Missing data graph B.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-alarm-graph-b.png)

In the preceding graphed metric, data point 1 is within threshold, and data points 2 through 5 are missing\. Given that there is only one data point in the evaluation range, this metric has two missing data points\. If you configured an alarm to treat missing data points as:
+ **Not breaching** — The alarm would be in an OK state\.
+ **Breaching** — The alarm would be in an OK state\.
+ **Ignore** — The alarm would be in an OK state\.
+ **Missing** — The alarm would be in an OK state\.

In this scenario, the alarm would stay in an OK state, even if missing data is treated as breaching\. This is because the one existing data point is not breaching, and this is evaluated along with two missing data points that are treated as breaching\. The next time this alarm is evaluated, if the data is still missing it goes to ALARM\. This is because that non\-breaching data point is no longer be among the five most recent data points retrieved\.

### Graph C<a name="missing-data-graph-c"></a>

![\[Missing data graph C.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-alarm-graph-c.png)

All data points are missing in the preceding graphed metric\. Given that all data points are missing in the evaluation range, this metric has three missing data points\. If you configured an alarm to treat missing data points as:
+ **Not breaching** — The alarm would be in an OK state\.
+ **Breaching** — The alarm would be in an ALARM state\.
+ **Ignore** — The alarm would maintain the current state\.
+ **Missing** — The alarm would be in an INSUFFICIENT\_DATA state\.

### Graph D<a name="missing-data-graph-d"></a>

![\[Missing data graph D.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-alarm-graph-d.png)

In the preceding graphed metric, data point 1 is within threshold, data point 2 is breaching, data point 3 is breaching, data point 4 is missing, and data point 5 is breaching\. Given that there are four valid data points in the evaluation range, this metric has zero missing data points\. If you configured an alarm to treat missing data points as:
+ **Not breaching** — The alarm would be in an ALARM state\.
+ **Breaching** — The alarm would be in an ALARM state\.
+ **Ignore** — The alarm would be in an ALARM state\.
+ **Missing** — The alarm would be in an ALARM state\.

In this scenario, the alarm goes to ALARM state in all cases\. This is because there are enough real data points that the setting for how to treat missing data is not needed, and is then ignored\.

### Graph E<a name="missing-data-graph-e"></a>

![\[Missing data graph E.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-alarm-graph-e.png)

In the preceding graphed metric, data points 1 and 2 are missing, data point 3 is breaching, and data point 4 and 5 are missing\. Given that there is only one data point in the evaluation range, this metric has two missing data points\. If you configured an alarm to treat missing data points as:
+ **Not breaching** — The alarm would be in an OK state\.
+ **Breaching** — The alarm would be in an ALARM state\.
+ **Ignore** — The alarm would maintain the current state\.
+ **Missing** — The alarm would be in an ALARM state\.

In graphs F, G, H, I, and J, the **Datapoints to alarm** is 2 while **Evaluation periods** is 3\. This is a 2 out of 3, M out of N alarm\. 5 is the evaluation range for the alarm\.

### Graph F<a name="missing-data-graph-f"></a>

![\[Missing data graph F.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-alarm-graph-f.png)

In the preceding graphed metric, data point 1 within threshold, data point 2 is missing, data point 3 is breaching, data point 4 is missing, and data point 5 is breaching\. Given that there are three data points in the evaluation range, this metric has zero missing data points\. If you configured an alarm to treat missing data points as:
+ **Not breaching** — The alarm would be in an ALARM state\.
+ **Breaching** — The alarm would be in an ALARM state\.
+ **Ignore** — The alarm would be in an ALARM state\.
+ **Missing** — The alarm would be in an ALARM state\.

### Graph G<a name="missing-data-graph-g"></a>

![\[Missing data graph G.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-alarm-graph-g.png)

In the preceding graphed metric, data points 1 and 2 are within threshold, data point 3 is breaching, data point 4 is within threshold, data point 5 is breaching\. Given that there are five data points in the evaluation range, this metric has zero missing data points\. If you configured an alarm to treat missing data points as:
+ **Not breaching** — The alarm would be in an ALARM state\.
+ **Breaching** — The alarm would be in an ALARM state\.
+ **Ignore** — The alarm would be in an ALARM state\.
+ **Missing** — The alarm would be in an ALARM state\.

### Graph H<a name="missing-data-graph-h"></a>

![\[Missing data graph H.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-alarm-graph-h.png)

In the preceding graphed metric, data point 1 is within threshold, data point 2 is missing, data point 3 is breaching, and data points 4 and 5 are missing\. Given that there are two data points in the evaluation range, this metric has one missing data point\. If you configured an alarm to treat missing data points as:
+ **Not breaching** — The alarm would be in an OK state\.
+ **Breaching** — The alarm would be in an ALARM state\.
+ **Ignore** — The alarm would be in an OK state\.
+ **Missing** — The alarm would be in an OK state\.

### Graph I<a name="missing-data-graph-i"></a>

![\[Missing data graph I.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-alarm-graph-i.png)

In the preceding graphed metric, data points 1 through 4 are missing, and data point 5 is within threshold\. Given that there is one data point in the evaluation range, this metric has two missing data points\. If you configured an alarm to treat missing data points as:
+ **Not breaching** — The alarm would be in an OK state\.
+ **Breaching** — The alarm would be in an ALARM state\.
+ **Ignore** — The alarm would be in an OK state\.
+ **Missing** — The alarm would be in an OK state\.

### Graph J<a name="missing-data-graph-j"></a>

![\[Missing data graph J.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-alarm-graph-j.png)

In the preceding graphed metric, data points 1 and 2 are missing, data point 3 is breaching, and data point 4 and 5 are missing\. Given that there is one data point in the evaluation range, this metric has two missing data points\. If you configured an alarm to treat missing data points as:
+ **Not breaching** — The alarm would be in an OK state\.
+ **Breaching** — The alarm would be in an ALARM state\.
+ **Ignore** — The alarm would maintain the current state\.
+ **Missing** — The alarm would be in an ALARM state\.

## More information about alarms<a name="more-information-alarms"></a>

Here are some articles to help you manage alarms in Lightsail:
+ [Creating instance metric alarms in Amazon Lightsail](amazon-lightsail-adding-instance-health-metric-alarms.md)
+ [Creating database metric alarms in Amazon Lightsail](amazon-lightsail-adding-database-health-metric-alarms.md)
+ [Creating load balancer metric alarms in Amazon Lightsail](amazon-lightsail-adding-load-balancer-health-metric-alarms.md)
+ [Deleting or disabling metric alarms in Amazon Lightsail](amazon-lightsail-deleting-health-metric-alarms.md)