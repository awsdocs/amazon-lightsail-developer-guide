# Resilience in Amazon Lightsail<a name="disaster-recovery-resiliency"></a>

 *Last updated: February 18, 2020* 

The AWS global infrastructure is built around AWS Regions and Availability Zones\. AWS Regions provide multiple physically separated and isolated Availability Zones, which are connected with low\-latency, high\-throughput, and highly redundant networking\. With Availability Zones, you can design and operate applications and databases that automatically fail over between zones without interruption\. Availability Zones are more highly available, fault tolerant, and scalable than traditional single or multiple data center infrastructures\. 

For more information about AWS Regions and Availability Zones, see [AWS Global Infrastructure](http://aws.amazon.com/about-aws/global-infrastructure/)\.

In addition to the AWS global infrastructure, Lightsail offers several features to help support your data resiliency and backup needs\.
+ Copying instance and disk snapshots across Regions\. For more information, see [Snapshots in Amazon Lightsail](understanding-instance-snapshots-in-amazon-lightsail.md)\.
+ Automating instance and disk snapshots snapshots\. For more information, see [Snapshots in Amazon Lightsail](understanding-instance-snapshots-in-amazon-lightsail.md)\.
+ Distributing incoming traffic across multiple instances in a single Availability Zone or multiple Availability Zones using a load balancer\. For more information, see [Lightsail load balancers](understanding-lightsail-load-balancers.md)\.