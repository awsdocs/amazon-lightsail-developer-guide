# Billing in Amazon Lightsail<a name="understanding-your-amazon-lightsail-bill"></a>

 *Last updated: July 23, 2019* 

Billing for Amazon Lightsail is handled through Amazon Web Services \(AWS\) billing\. To view your Lightsail bill, go to the [AWS Billing and Cost Management Dashboard](https://console.aws.amazon.com/billing/), or choose **Billing** on the top navigation bar of the Lightsail console\. For more information about pricing, see the [Lightsail pricing page](https://aws.amazon.com/lightsail/pricing/)\.

## Viewing your detailed Lightsail bill<a name="viewing-your-detailed-lightsail-bill"></a>

To view a detailed breakdown of your monthly Lightsail bill:

1. Sign in to the [AWS Billing and Cost Management Dashboard](https://console.aws.amazon.com/billing/)\.

   The billing dashboard home page displays a high\-level month\-to\-date breakdown of your bill\.

1. Choose **Bill Details** on the dashboard home page, or choose **Bills** in the left navigation pane, to view a detailed version of your monthly bill\.  
![\[AWS Billing and Cost Management Dashboard home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-billing-dashboard-home-page.png)

1. Choose the **Date** drop\-down menu to select a month other than the current month\.  
![\[Date selector in the AWS Billing and Cost Management Dashboard.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-billing-dashboard-date-drop-down.png)

1. Scroll down on the **Bills** page, and expand the Lightsail line item to view detailed usage for each region\.  
![\[Detailed monthly bill for Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-detailed-monthly-bill.png)

## Billing usage types<a name="billing-usage-types"></a>

The following list describes the usage types that appear in your Lightsail billing and usage reports\. These usage types help identify the charges on your monthly bill for Lightsail resources\.

**Note**  
For the following usage types that specify a **Region** code, see the [Region codes in your bill](#amazon-lightsail-region-codes-in-bill) section of this guide to identify the corresponding AWS Region\.
+ **Amazon Lightsail Bundle:SizeGB:** The Linux or Unix instance plan used \(in hours\)\. The **Size** defines the memory specification of the instance plan used\. For example, if **4GB** of memory is specified, then the billed hours for the $20 USD/month Linux or Unix instance plan is displayed\.
+ **Amazon Lightsail Bundle:SizeGB \(Windows\):** The Windows instance plan used \(in hours\)\. The **Size** defines the memory specification of the instance plan used\. For example, if **4GB** of memory is specified, then the billed hours for the $40 USD/month Windows instance plan is displayed\.
+ **Amazon Lightsail RelationalDatabase:SizeGB:** The standard database plans used \(in hours\)\. The **Size** defines the memory specification of the database plan used\. For example, if **4GB** of memory is specified, then the billed hours for the $60 USD/month standard database plan is displayed\.
+ **Amazon Lightsail RelationalDatabase:SizeGB \(high availability\):** The high availability database plans used \(in hours\)\. The **Size** defines the memory specification of the database plan used\. For example, if **4GB** of memory is specified, then the billed hours for the $120 USD/month high availability database plan is displayed\.
+ **Amazon Lightsail Region\-DiskUsage:** The amount of block storage disk used \(in gigabytes per month\)\.
+ **Amazon Lightsail DNS\-Queries:** The number \(count\) of DNS queries for the month\.
+ **Amazon Lightsail Load Balancer:** The amount of load balancers used \(in hours\)\.
+ **Amazon Lightsail Region\-SnapshotUsage:** The amount of stored snapshot data \(in gigabytes per month\)\.
+ **Amazon Lightsail Region\-UnusedStaticIP:** The amount of un\-attached static IPs \(in hours\)\.
+ **Amazon Lightsail Region\-TotalDataXfer\-In\-Bytes:** The total amount of data transferred in \(in gigabytes\)\.
+ **Amazon Lightsail Region\-TotalDataXfer\-Out\-Bytes:** The total amount of data transferred out \(in gigabytes\)\.
+ **Amazon Lightsail Region\-DataXfer\-Out\-Overage\-Bytes:** The amount of data transferred out to the internet or public IPs that is over the allowance of the instance or database plan\(s\) used \(in gigabytes\)\.
+ **Amazon Lightsail Region\-DataXfer\-Out\-Free\-Bytes \(deprecated\):** The amount of data transferred out that is within the allowance of the instance or database plan\(s\) used \(in gigabytes\)\.
+ **Amazon Lightsail Region\-DataXfer\-Out\-Other\-Bytes \(deprecated\):** The amount of data transferred out to private IPs that is over the allowance of the instance or database plan\(s\) used \(in gigabytes\)\. This overage is free when the transfer is to an AWS resource over a private IP\.

## Region codes in your bill<a name="amazon-lightsail-region-codes-in-bill"></a>

Lightsail billing and usage reports use codes and abbreviations\. For example, for usage type, region is replaced with one of the following abbreviations:
+ **APN1:** Tokyo \(ap\-northeast\-1\)
+ **APN2:** Seoul \(ap\-northeast\-2\)
+ **APS1:** Singapore \(ap\-southeast\-1\)
+ **APS2:** Sydney \(ap\-southeast\-2\)
+ **APS3:** Mumbai \(ap\-south\-1\)
+ **CAN1:** Montreal \(ca\-central\-1\)
+ **EU:** Ireland \(eu\-west\-1\)
+ **EUC1:** Frankfurt \(eu\-central\-1\)
+ **EUW2:** London \(eu\-west\-2\)
+ **EUW3:** Paris \(eu\-west\-3\)
+ **USE1:** Virginia \(us\-east\-1\)
+ **USE2:** Ohio \(us\-east\-2\)
+ **USW2:** Oregon \(us\-west\-2\)