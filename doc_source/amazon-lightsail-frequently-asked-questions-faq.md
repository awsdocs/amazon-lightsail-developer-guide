# Frequently Asked Questions in Amazon Lightsail<a name="amazon-lightsail-frequently-asked-questions-faq"></a>

 *Last updated: February 27, 2020* 

This topic answers frequently asked questions \(FAQ\)\. If you have a FAQ that is not answered here, use the **Questions? Comments?** feedback button at the bottom of the page\. You can also post a question in the [Lightsail discussion forum](https://forums.aws.amazon.com/forum.jspa?forumID=231)\.

**Contents**
+ [General](#amazon-lightsail-frequently-asked-questions-faq-general)
+ [Instances](#amazon-lightsail-faq-instances)
+ [Databases](#amazon-lightsail-faq-databases)
+ [Block storage](#amazon-lightsail-faq-block-storage)
+ [Load balancers](#amazon-lightsail-faq-load-balancers)
+ [Certificates](#amazon-lightsail-faq-certificates)
+ [Manual and automatic snapshots](#amazon-lightsail-faq-snapshots)
+ [Networking](#amazon-lightsail-faq-networking)
+ [Billing and account management](#amazon-lightsail-frequently-asked-questions-faq-billing-and-account-management)
+ [Export to Amazon Elastic Compute Cloud \(Amazon EC2\)](#amazon-lightsail-faq-export-to-ec2)
+ [Tags in Lightsail](#amazon-lightsail-faq-tagging)
+ [Contacts and notifications](#faq-contacts-and-notifications)
+ [Metrics and alarms](#faq-metrics-and-alarms)

## General<a name="amazon-lightsail-frequently-asked-questions-faq-general"></a>

**What is Amazon Lightsail?**  
Amazon Lightsail is the easiest way to get started with AWS, providing everything you need to get your project running in the cloud\. Lightsail provides developers compute, storage, and networking capacity and capabilities to deploy and manage websites, web applications, and databases in the cloud\. Lightsail includes everything you need to launch your project quickly – a virtual machine, a managed database, SSD\-based storage, data transfer, DNS management, and a static IP – for a low, predictable monthly price\. You can also scale out your application or website over time and improve its availability and redundancy by adding other Lightsail resources, like load balancers, attached block storage and managed databases\.

**What can I do with Lightsail?**  
You can create preconfigured virtual private servers \(instances\) that include everything to easily deploy and manage your application, or create databases for which the security and health of the underlying infrastructure and operating system is managed by Lightsail\. Lightsail is best suited to projects that require a few dozen instances or less, and developers who prefer a simple management interface\. Common use cases for Lightsail include running websites, web applications, business software, blogs, e\-commerce sites, and more\. As your project grows, you can use load balancers and attached block storage with your instance to increase redundancy and uptime and access dozens of other AWS services to add new capabilities\.

**Does Lightsail offer an API?**  
Yes\. Everything you do in the Lightsail console is backed by a publically available API\. Learn how to install and use the Lightsail [CLI](https://docs.aws.amazon.com/cli/latest/reference/lightsail/index.html) and [API](http://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/Welcome.html)\.

**How do I sign up for Lightsail?**  
To start using Lightsail, choose [Get Started](https://portal.aws.amazon.com/gp/aws/developer/registration/index.html?client=lightsail) and log in\. You use your Amazon Web Services account to access Lightsail; if you don't already have one, you'll be prompted to create one\.

**In which AWS Regions is Lightsail available?**  
Lightsail is currently available in all the Availability Zones in the following AWS Regions:  
• US East \(Ohio\) \(us\-east\-2\)  
• US East \(N\. Virginia\) \(us\-east\-1\)  
• US West \(Oregon\) \(us\-west\-2\)  
• Asia Pacific \(Mumbai\) \(ap\-south\-1\)  
• Asia Pacific \(Seoul\) \(ap\-northeast\-2\)  
• Asia Pacific \(Singapore\) \(ap\-southeast\-1\)  
• Asia Pacific \(Sydney\) \(ap\-southeast\-2\)  
• Asia Pacific \(Tokyo\) \(ap\-northeast\-1\)  
• Canada \(Central\) \(ca\-central\-1\)  
• EU \(Frankfurt\) \(eu\-central\-1\)  
• EU \(Ireland\) \(eu\-west\-1\)  
• EU \(London\) \(eu\-west\-2\)  
• EU \(Paris\) \(eu\-west\-3\)  
For more information, see [AWS Regions and Availability Zones in Lightsail](understanding-regions-and-availability-zones-in-amazon-lightsail.md)\.

**What are Availability Zones?**  
Availability Zones are collections of data centers that run on physically distinct, independent infrastructure and are engineered to be highly reliable\. Common points of failure such as generators and cooling equipment are not shared between Availability Zones\. Additionally, Availability Zones are physically separate, so that even extremely uncommon disasters such as fires, tornados, or flooding can affect only a single Availability Zone\.

**What are the Lightsail service quotas?**  
You can currently create up to 20 Lightsail instances, 5 static IPs, 3 DNS zones, 20 TB of attached block storage, 40 databases, and 5 load balancers in a Lightsail account\. You can also generate up to 20 certificates during each calendar year\. If you need to increase your account quota for instances, static IPs, block storage, or certificates in your account, please open a case with [customer service](https://console.aws.amazon.com/support/home?region=us-east-1)\. We do not currently support increases for DNS zones or load balancers\.

**How can I get more help?**  
We're here for you\. Our context\-sensitive **Help** panel in Lightsail offers immediate helpful tips about your actions in the console\. From the Lightsail console, you can also access a library of [getting started guides](https://lightsail.aws.amazon.com/ls/docs/getting-started), [overviews](https://lightsail.aws.amazon.com/ls/docs/overview), and [how\-to topics](https://lightsail.aws.amazon.com/ls/docs/how-to)\. And if you want to use the Lightsail API, or AWS CLI, Lightsail has a full API reference for all supported programming languages\. You can also use Lightsail support resources\.  
If you have an issue with your account or billing, contact [customer service](https://console.aws.amazon.com/support/home?region=us-east-2#/) online\. You get free 24x7 access with your Lightsail account\.  
If you have a general question about how to use Lightsail, search the Lightsail documentation and [support forums](https://forums.aws.amazon.com/forum.jspa?forumID=231)\.  
Additionally, AWS Support offers an array of paid plans to cover your individual needs\.

## Instances<a name="amazon-lightsail-faq-instances"></a>

**What is a Lightsail instance?**  
A Lightsail instance is a virtual private server \(VPS\) that lives in the AWS Cloud\. Use your Lightsail instances to store your data, run your code, and build web\-based applications or websites\. Your instances can connect to each other and to other AWS resources through both public \(internet\) and private \(VPC\) networking\. You can create, manage, and connect easily to instances right from the Lightsail console\.

**What is a Lightsail plan?**  
Also referred to as a bundle, a Lightsail plan includes a virtual server with a fixed amount of memory \(RAM\) and compute \(vCPUs\), SSD\-based storage \(disks\), and a free data transfer allowance\. Lightsail plans also offer static IP addresses \(5 per account\) and DNS management \(3 domain zones per account\)\. Lightsail plans are charged on an hourly, on\-demand basis, so you only pay for a plan when you're using it\.

**What software can I run on my instances?**  
Lightsail offers a range of operating system and application templates that are automatically installed when you create a new Lightsail instance\. Application templates include WordPress, WordPress Multisite, Django, Drupal, Ghost, Joomla\!, Magento, Redmine, LAMP, Nginx \(LEMP\), MEAN, and Node\.js\.  
You can install additional software on your instances by using the in\-browser SSH or your own SSH client\.

**What operating systems can I use with Amazon Lightsail?**  
Lightsail currently supports 6 Linux or Unix\-like distributions: Amazon Linux, CentOS, Debian, FreeBSD, OpenSUSE, and Ubuntu, as well as two Windows Server versions: 2012 R2 and 2016\.

**How do I create a Lightsail instance?**  
After logging in to Lightsail, you can use the Lightsail [console](https://lightsail.aws.amazon.com/ls/webapp), command line interface \(CLI\), or API to create and manage instances\.  
The first time you log in to the console, choose Create Instance\. The create instance page is where you can choose the software, location, and name for your instance\. Once you choose Create, your new instance will spin up automatically within minutes\.

**How do Lightsail instances perform?**  
Lightsail instances are specifically engineered by AWS for web servers, developer environments, and small database use cases\. Such workloads don't use the full CPU often or consistently, but occasionally need a performance burst\. Lightsail uses burstable performance instances that provide a baseline level of CPU performance with the additional ability to burst above the baseline\. This design enables you to get the performance you need, when you need it, while protecting you from the variable performance or other common side effects that you might typically experience from over\-subscription in other environments\.  
If you need highly configurable environments and instances with consistently high CPU performance for applications such as video encoding or HPC applications, we recommend you use [Amazon EC2](https://aws.amazon.com/ec2/)\.

**How do I know when my instances are bursting?**  
On the CPU utilization metric graphs for your instance, you will see a sustainable zone, and a burstable zone\. Your Lightsail instance can operate in the sustainable zone indefinitely with no impact to the operation of your system\. Your instance may begin operating in the burstable zone when under heavy load\. While operating in the burstable zone your instance is consuming a higher amount of CPU cycles\. Therefore, it can only operate in this zone for a limited period of time\. For more information, see [Viewing instance metrics in Amazon Lightsail](amazon-lightsail-viewing-instance-health-metrics.md)\.  
Add a metric alarm to be notified when your instance’s CPU utilization crosses from the sustainable zone to the bursting zone\. For more information, see [Creating instance alarms in Amazon Lightsail](amazon-lightsail-adding-instance-health-metric-alarms.md)\. 

**How do I connect to a Lightsail instance?**  
Lightsail offers a 1\-click secure connection to your instance's terminal right from your browser, supporting SSH access for Linux/Unix\-based instances and RDP access for Windows\-based instances\. To use 1\-click connections, launch your instance management screens, choose **Connect using SSH** or **Connect using RDP**, and a new browser window opens and automatically connects to your instance\.  
If you prefer to connect to your Linux/Unix\-based instance using your own client, Lightsail will do the SSH key storing and management work for you, and provide you with a secure key to use in your SSH client\.

**How can I back up my instances?**  
If you want to back up your data, you can use the Lightsail console or API to create a manual snapshot of your instance, or enable automatic snapshots to have Lightsail create daily snapshots for you\. If there is a failure or bad code deployment, you can later use your instance snapshot to create a brand new instance\. For more information, see [Snapshots in Amazon Lightsail](understanding-instance-snapshots-in-amazon-lightsail.md)\.

**Can I upgrade my plan?**  
Yes\. You can use a snapshot of your instance to create a new, larger size instance\. For more information, see [Snapshots in Amazon Lightsail](understanding-instance-snapshots-in-amazon-lightsail.md)\.

**How can I connect Lightsail instances to other resources in my AWS account?**  
You can connect your Lightsail instances to Amazon VPC resources in your AWS account privately, by using VPC peering\. Just choose **Enable VPC peering** on your Lightsail account page, and Lightsail does the work for you\. Once VPC peering is enabled, you can address other AWS resources in your default Amazon VPC by using their private IPs\. Find instructions [here](lightsail-how-to-set-up-vpc-peering-with-aws-resources.md)\.  
Note that you need to have a default Amazon VPC set up in your AWS account in order for VPC peering with Lightsail to work\. AWS accounts created before December 2013 do not have a default VPC, and you will need to set one up\. Find out more about setting up your default VPC [here](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/default-vpc.html)\.

**What is the difference between stopping and deleting my instance?**  
When you stop your instance, it is powered down at its current state and is available for you to start again at any time\. Stopping your instance will release its public IP, so it is recommended that you use static IPs for instances that must retain the same IP after they stop\.  
When you delete your instance, you are performing a destructive action\. Unless you have created an instance snapshot, all of your instance data will be lost and you cannot recover it again\. Automatic snapshots are also deleted with the instance unless you keep them by copying them as manual snapshots\. The instance's public and private IPs will also be released\. If you were using a static IP with that instance, the static IP is detached, but remains in your account\.

## Databases<a name="amazon-lightsail-faq-databases"></a>

**What are Lightsail managed databases?**  
Lightsail managed databases are instances that are dedicated to running databases, instead of other workloads like web servers, mail servers, etc\. A managed database can contain multiple user\-created databases, and you can access it by using the same tools and applications that you use with a stand\-alone database\. Lightsail maintains the security and health of your database’s underlying infrastructure and operating system, so that you can run a database without deep expertise in infrastructure management\.  
Like regular Lightsail instances, Lightsail managed databases come with a fixed amount of memory, computing power, and SSD based storage in their plans that you can scale up over time\. Lightsail will automatically install and configure your chosen database for you upon creation\.

**What can I do with Lightsail managed databases?**  
Lightsail managed databases provide an easy, low maintenance way to store your data in the cloud\. You can run managed databases either as a new database or by migrating from an existing on\-premises or hosted database to Lightsail\.  
They can also allow you to scale your application to accept larger amounts of traffic and more intensive loads, by separating out your database into a dedicated instance\. Lightsail managed databases are especially useful for stateful applications – like WordPress and most common CMSs – that need data to be kept in sync when you scale beyond a single instance\. Managed databases can be paired with a Lightsail load balancer and two or more Lightsail instances to create a powerful, scaled application\. By using Lightsail high availability managed database plans, you can also add redundancy to your database, helping to ensure high uptime for your application\.

**What does Lightsail manage for me?**  
Lightsail manages a range of maintenance activities and security for your managed database and its underlying infrastructure\. Lightsail automatically backs up your database and allows point in time restore from the past 7 days using the database restore tool, to help protect against data loss or component failure\. Lightsail also automatically encrypts your data at rest and in motion for increased security and stores your database password for easy and secure connections to your database\. On the maintenance side, Lightsail runs maintenance on your database during your set maintenance window\. This maintenance include automatic upgrades to the latest minor database version and all management of the underlying infrastructure and operating system\.

**What kinds of databases and what versions of these databases does Lightsail support?**  
Lightsail managed databases support the latest major versions of MySQL\. Currently, these versions are MySQL 5\.6, 5\.7, and 8\.0\. Lightsail only provides the latest minor version for each major version option\.

**What managed database plans does Lightsail offer?**  
Lightsail offers 4 sizes of managed databases in standard and high availability plans\. Each plan comes with a fixed amount of storage and a monthly allowance of data transfer\. You can also scale up to larger plans over time, as needed, and switch between standard and high availability plans\. High availability plans mirror the same resources as standard plans and additionally include a standby database running in a separate Availability Zones from your primary database for redundancy\.

**What is a high availability plan?**  
Lightsail managed databases are available in standard and high availability plans\. Standard and high availability plans have identical plan resources, including memory, storage, and data transfer allowance\. High availability plans add redundancy and durability to your database, by automatically creating standby database in a separate Availability Zone from your primary database, synchronously replicating data to the standby database, and providing failover to the standby database in case of infrastructure failure and during maintenance so that you ensure uptime even when databases is being automatically upgraded/maintained by Lightsail\. Use high availability plans for running production applications or software where high uptime is required\.

**How do I scale up or down my Lightsail managed database?**  
You can scale up your Lightsail managed database by taking a snapshot of it and creating a new, larger database plan from snapshot or by creating a new, larger database using the emergency restore feature\. You can also switch from standard to high availability plans and vice versa using either method\. You cannot scale down your database\. For more information, see [Creating a database from a snapshot in Amazon Lightsail](amazon-lightsail-creating-a-database-from-snapshot.md)\.

**How can I back up my Lightsail managed database?**  
Lightsail backs up your data automatically and allows restore of this data from a specific point in time to a new database\. Automatic backup is a free service for your database but only saves the last 7 days of data\. If you delete your database, all automatic backup records are deleted and point\-in\-time restore is no longer possible\. To retain backups of data after deleting your database or to retain a backup for more than 7 days in the past, use manual snapshots\.  
You can take manual snapshots of your Lightsail managed databases from the database management pages\. Manual snapshots contain all the data from your database and can be used as backups for data that you want to store permanently\. You can also use manual snapshots to create a new, larger database or to switch between Standard and High Availability plans\. Manual snapshots are stored until you delete them and are billed at $0\.05 USD/GB\-month\.

**What happens to my data if I delete my Lightsail managed database?**  
If you delete your Lightsail managed database, both your database itself and all automatic backups will be deleted\. There is no way to recover this data unless you take a manual snapshot before deleting your database\. During deletion of your database, Lightsail provides a one\-click option to take a manual snapshot, if desired, to help protect against accidental loss of data\. Taking a manual snapshot before deletion is optional but highly recommended\. You can delete your manual snapshot in the future when you no longer need the stored data\.

**Can I connect my instance\(s\) to a Lightsail managed database running in different AWS Regions or different Availability Zones?**  
You cannot use Lightsail managed databases with instances running in different AWS Regions\. You can, however, use databases across different Availability Zones from your instance\.

**How do I load data onto my Lightsail managed database?**  
In order to load data onto your Lightsail managed database, you should first enable data import mode\. After enabling data import mode, you can continue to manually upload data using your preferred database client\. After you are done loading data, remember to turn off Data import mode so that automatic backups and logging for your databases can resume\. For more information, see [Importing data into your MySQL database in Amazon Lightsail](amazon-lightsail-importing-data-into-your-mysql-database.md) and [Importing data into your PostgreSQL database in Amazon Lightsail](amazon-lightsail-importing-data-into-your-postgres-database.md)\.

**How do I access the data on my Lightsail managed database?**  
You can connect to your database and query your data using any standard SQL client application\. We recommend MySQL Workbench for GUI based administration and querying\. You can find connection data in the database management screen for your database, including the endpoint URL and DNS name\. For more information, see [Connecting to your MySQL database in Amazon Lightsail](amazon-lightsail-connecting-to-your-mysql-database.md) or [Connecting to your PostgreSQL database in Amazon Lightsail](amazon-lightsail-connecting-to-your-postgres-database.md)\.

**How do Lightsail managed databases work with my Lightsail instances?**  
After you create your Lightsail managed database, you can start using it with your application immediately, using your Lightsail instances as web servers or other dedicated workloads for your app\. To connect your Lightsail instance to a database, use your database endpoint and reference your securely stored password to configure the database as your data store in the code of your application\. You can find connection data in the database management screens\. The file name and location for your database configuration file will vary by application\. Note that you can connect many instances to one database, either using the same tables or using different ones\.

**How can I connect Lightsail managed database to EC2 instances running in my AWS account?**  
You can connect your Lightsail managed database to EC2 instances by connecting over the public internet\. Note that connection to all AWS services will consume your database data transfer allowance, and data out over the public internet to AWS services in excess of your data transfer allowance will accrue overage charges\. You cannot use VPC peering between Lightsail managed databases and EC2 instances\.

**What is the difference between public and private modes for my Lightsail managed database?**  
By default, your Lightsail managed database is created in private mode, which secures it by making it accessible only by Lightsail instances\. You can set your database public mode if you need to connect to software or services over the public internet\. To ensure security of your data, we do not recommend keeping public mode enabled long\-term\. You can change between public and private modes at any time from your database management screens\.

**Can I manage the ports used by my Lightsail managed database?**  
No, Lightsail automatically manages your ports for security purposes, opening Port 3306 for MySQL for all Lightsail managed databases in public mode\. If your database is in private mode, your database is only open to resources running in your Lightsail account via the internal network\.

## Block storage<a name="amazon-lightsail-faq-block-storage"></a>

**What can I do with Lightsail block storage?**  
Lightsail block storage provides additional storage volumes \(called "attached disks" in Lightsail\) that you can attach to your Lightsail instance, similar to an individual hard drive\. Attached disks are useful for applications or software that need to separate out specific data from their core service and to protect application data in case of a failure or other issue with your instance and system disk\. Attached disks offers consistent performance and low latency needed for applications or software that frequently access their stored data\.  
Lightsail block storage disks use solid\-state drives \(SSD\)\. This type of block storage balances a low price and good performance and is intended to support the vast majority of workloads that run on Lightsail\. For customers with applications that require sustained IOPS performance, high amounts of throughput per disk, or that are running large databases like MongoDB, Cassandra, etc\., we recommend using Amazon EC2 with GP2 or Provisioned IOPS SSD storage instead of Lightsail\.

**How are attached disks different than the storage included in my Lightsail plan?**  
The system disk included with your Lightsail plan is your instance's root device\. If you terminate your instance, the system disk will be deleted as well\. If you experience an instance failure, the system disk could be impacted\. You also cannot detach your system disk or back it up separately from your instance\. Data stored on an attached disk persists independently of the instance\. Attached disks can be detached and moved between instances\. They can be backed up independently from an instance by creating a manual snapshot of the disk\. To protect your data, we recommend that you use your Lightsail instance's system disk only for temporary data\. For data requiring a higher level of durability, we recommend using attached disks and regularly backing up your disk using disk or instance snapshots\.

**How large can I make my attached disk?**  
Each attached disk can be up to 16 TB, and the total amount of attached block storage in a Lightsail account must not exceed 20 TB\.

**How many disks can I attach per Lightsail instance?**  
You can attach up to 15 disks to a Lightsail instance\.

**Can I attach a disk to more than one instance?**  
No, disks can only be attached to one instance at a time\.

**Does my disk need to be attached to an instance?**  
No, you can choose not to attach a disk to an instance\. The disk will remain in your account in an unattached state\. There is no difference in price if your disk is not attached to an instance\.

**Can I increase the size of my attached disk?**  
Yes, you can increase the size of a disk by taking a disk snapshot and then creating a new, larger disk from that snapshot\.

**Does Lightsail block storage offer encryption?**  
Yes, to help keep your data secure, all Lightsail attached disks and disk snapshots are encrypted at rest by default, using keys that Lightsail manages on your behalf\. Lightsail also provides encryption of data as it moves between Lightsail instances and attached disks\.

**What availability can I expect from Lightsail block storage?**  
Lightsail block storage is designed to be highly available and reliable\. Each attached disk is automatically replicated within its Availability Zone to protect you from component failure\. Lightsail block storage disks are designed for 99\.99% availability\. Lightsail also supports disk snapshots to allow regular backups of your data\.

**How do I back up my attached disk?**  
You can back up your disk by creating a manual snapshot of the disk\. You can also back up your entire instance and any attached disks by creating a manual snapshot of the instance, or by enabling automatic snapshots for the instance with the disk attached\. Disks attached to instances are included in instance manual and automatic snapshots\.

## Load balancers<a name="amazon-lightsail-faq-load-balancers"></a>

**What can I do with Lightsail load balancers?**  
Lightsail load balancers allow you to build highly available websites and applications\. By distributing traffic across instances in different Availability Zones and pointing traffic to only healthy target instances, Lightsail load balancers reduce the risk of your application going down due to an issue with your instance or to a datacenter outage\. With Lightsail load balancers and multiple target instances, your website or application can also accommodate increases in web traffic and maintain good performance for your visitors during peak load times\.  
In addition, you can use Lightsail load balancers to help you build secure applications and accept HTTPS traffic\. Lightsail takes the complexity out of requesting, provisioning, and maintaining SSL/TLS certificates\. The built\-in certificate management requests and renews certificates on your behalf and adds the certificate to your load balancer automatically\.

**Can I use load balancers with instances in different AWS Regions or different Availability Zones?**  
You cannot use load balancers with instances running in different AWS Regions\. You can, however, use target instances across different Availability Zones with your load balancer\. In fact, we recommend that you distribute your target instances across Availability Zones to maximize the availability of your application\.

**How does my Lightsail load balancer deal with traffic spikes?**  
Lightsail load balancers scale automatically to handle traffic spikes to your application without you having to manually adjust them\. If your application experiences a transient spike in traffic, your Lightsail load balancer will automatically scale and continue to efficiently direct traffic to your Lightsail instances\. While your Lightsail load balancer is designed to easily manage traffic spikes, applications that consistently experience very high volume levels of traffic may experience performance degradation or throttling\. If you expect your application consistently to manage more than 5 GB/hour of data or consistently to have a large number of connections \(>400k new connections/hour, >15k active, concurrent connections\), we recommend using Amazon EC2 with Application Load Balancing instead\.

**How do Lightsail load balancers route traffic to my target instances?**  
Lightsail load balancers direct traffic to your healthy target instances based on a round robin algorithm\.

**How does Lightsail know if my target instances are healthy?**  
After you create your load balancer and attach your instances, Lightsail sends a health check request to the root of your web application\. You can customize the location by specifying a path \(a common file or webpage URL\) for Lightsail to ping\. If the target instance can be reached using this path, then Lightsail will route traffic there\. If one of your target instances is unresponsive, the health check fails and Lightsail will not route traffic to that instance\. [Learn more about health checking](enable-set-up-health-checking-for-lightsail-load-balancer-metrics.md)

**How many instances I can attach to my load balancer?**  
You can add as many target instances to your load balancer as you would like \- up to your Lightsail account instance quota\.

**Can I assign one instance to multiple load balancers?**  
Yes, Lightsail supports adding instances as target instances for more than one load balancer, if desired\.

**What happens to my target instances when I delete my load balancer?**  
If you delete your load balancer, the attached target instances will continue to run normally and will appear in the Lightsail console as regular Lightsail instances\. Please note that you will likely need to update your DNS records to direct traffic to one of your former target instances after you delete the load balancer\.

**What is session persistence?**  
Session persistence enables the load balancer to bind a visitor's session to a specific target instance\. This ensures that all requests from the user during the session are sent to the same target instance\. Lightsail supports session persistence for applications that require visitors to hit the same target instances for data consistency\. For example, many applications that require user authentication can benefit from using session persistence\. You can turn on session persistence for specific load balancer from the load balancer management screens after creation\.  
 [Learn more about session persistence](enable-session-stickiness-persistence-or-change-cookie-duration.md) 

**What kind of connections do Lightsail load balancers support?**  
Lightsail load balancers support HTTP and HTTPS connections\.

## Certificates<a name="amazon-lightsail-faq-certificates"></a>

**How can I use Lightsail\-provisioned certificates?**  
SSL/TLS certificates are used to establish the identity of your website or application and secure connections between browsers and your website\. Lightsail provides a signed certificate to use with your load balancer, and the load balancer provides SSL/TLS termination before routing verified traffic to your target instances over the secure AWS network\. Lightsail certificates can only be used with Lightsail load balancers, not with individual Lightsail instances\.

**How do I validate my certificate?**  
Lightsail certificates are domain validated, meaning that you need to provide proof of identity by validating that you own or have access to your website’s domain before the certificate can be provisioned by the certificate authority\. When you request a new certificate, Lightsail will prompt you to add a CNAME to the DNS zone\(s\) of the domain or domains you are validating\. You will add this CNAME wherever you currently manage your DNS zones – either Lightsail DNS management or an external DNS hosting provider \(e\.g\., Route 53, GoDaddy, Namecheap, etc\.\)\. Once your certificate is validated, you can remove the CNAME record from your DNS zone, if desired\.

**What happens if I cannot validate my domain?**  
You must be able to validate that you own a domain for security purposes\. This means if you or someone in your organization can't add a DNS record to validate your certificate for any reason, you will not be able to use an HTTPS\-enabled load balancer with Lightsail\.

**How many domains and subdomains can I add to my certificate?**  
You can add up to 10 domains or subdomains per certificate\. Lightsail does not currently support wild card domains\.

**How can I change the domains associated with my certificate?**  
To change the domains \(add/delete\) associated with your certificate, you will need to resubmit the certificate and revalidate your ownership of the domain\(s\)\. Follow the steps in the certificate management screens to regenerate your certificate and add or remove domains when prompted\.

**How do I renew my certificate?**  
Lightsail provides managed renewal for your SSL/TLS certificates\. This means that Lightsail tries to renew the certificates automatically before they expire with no action required from you\. Your Lightsail certificate must be actively associated with a load balancer before it can be automatically renewed\.

**What happens to my certificate when I delete my load balancer?**  
If your load balancer is deleted, your certificate is deleted as well\. If you need to use a certificate for the same domain\(s\) in the future, you will need to request and validate a new certificate\.

**Can I download my certificate provided by Lightsail?**  
No, Lightsail certificates are bound to your Lightsail account and cannot be removed and used outside of Lightsail\.

## Manual and automatic snapshots<a name="amazon-lightsail-faq-snapshots"></a>

**What are snapshots?**  
Snapshots are point\-in\-time backups of instances, databases, or block storage disks\. You can create a snapshot of your resources at any time, or you can enable automatic snapshots on instances and disks to have Lightsail create snapshots for you\. You can use snapshots as baselines to create new resources or to back up your data\. A snapshot contains all of the data that is needed to restore your resource \(from the moment when the snapshot was taken\)\. When you restore a resource by creating it from a snapshot, the new resource begins as an exact replica of the original resource that was used to create the snapshot\.  
You can manually take snapshots of your Lightsail instances, disks, and databases, or you can use [automatic snapshots](amazon-lightsail-configuring-automatic-snapshots.md) to instruct Lightsail to take daily snapshots of your instances and disks automatically\. For more information, see [Snapshots in Amazon Lightsail](understanding-instance-snapshots-in-amazon-lightsail.md)\.

**What are automatic snapshots?**  
Automatic snapshots are a way to schedule daily snapshots of your Linux/Unix instances in Amazon Lightsail\. You can pick a time of the day, and Lightsail will automatically take a snapshot for you each day at the time you chose and always keep your seven most recent automatic snapshots\. Enabling snapshots is free, you only pay for the actual storage used by your snapshots\.

**What are the differences between manual and automatic snapshots?**  
Automatic snapshots cannot be tagged or exported directly to Amazon EC2\. However, automatic snapshots can be copied and converted into manual snapshots\. To copy an automatic snapshot into a manual one, choose **Keep** from the automatic snapshot’s context menu to copy it as a manual snapshot\.

**What resources support snapshots?**  
Manual snapshots can be created for instances, databases, and disks\.  
Automatic snapshots can be enabled for Linux or Unix instances using the Lightsail console, Lightsail API, or AWS CLI, and for disks using only the Lightsail API, or AWS CLI\. Automatic snapshots are not currently supported for Windows instances, or managed databases\.

**How long can I store snapshots?**  
Manual snapshots are stored until you choose to delete them\. For more information, see [Deleting snapshots in Amazon Lightsail](amazon-lightsail-deleting-snapshots.md)\.  
Automatic snapshots are stored until they are replaced by a newer automatic snapshots\. Lightsail stores the latest seven automatic snapshots before deleting the oldest one and replacing it with the newest one\. However, you can keep a specific automatic snapshot by copying it as a manual snapshot\. For more information, see [Keeping automatic snapshots of instances or disks in Amazon Lightsail](amazon-lightsail-keeping-automatic-snapshots.md)\. You will be billed the [snapshot storage fee](https://aws.amazon.com/lightsail/pricing/) for the automatic snapshots stored in your account\.

**How are automatic snapshots enabled?**  
Automatic snapshots can be enabled using the Lightsail console, Lightsail API, or AWS CLI when you create a Linux or Unix instance, or later after the instance is running\.  
Automatic snapshots can also be enabled for disks when you create them or after they're created; however, it can only be done using the Lightsail API, or AWS CLI\.  
For more information, see [Enabling or disabling automatic snapshots for instances or disks in Amazon Lightsail](amazon-lightsail-configuring-automatic-snapshots.md)\.

**When are automatic snapshots created?**  
When you enable automatic snapshots, a default time is set based on the AWS Region where the resource is located\. You can change the automatic snapshot to your preferred time of day, in hourly increments\. For more information, see [Changing the automatic snapshot time for instances or disks in Amazon Lightsail](amazon-lightsail-changing-automatic-snapshot-time.md)\.

**How many snapshots can I store?**  
You can store as many manual snapshots as you’d like\. However, only the latest seven automatic snapshots are stored before the oldest one is replaced with the newest one\.

**How are snapshots billed?**  
You only pay for the snapshots stored on your Lightsail account\. Lightsail snapshots \(manual and automatic\) cost $0\.05 USD/GB\-month to store\.

**Will I lose my snapshots if I disable automatic snapshots?**  
No\. If you disable automatic snapshots, Lightsail will stop creating a daily snapshot, and your existing automatic snapshots will be kept\. When you re\-enable automatic snapshots, Lightsail will resume taking daily snapshots, deleting the oldest one and replacing it with the newest one\.

**What should I do if I don’t want an automatic snapshot to be replaced?**  
You can keep a specific automatic snapshot by copying it as a manual snapshot\. For more information, see [Keeping automatic snapshots of instances or disks in Amazon Lightsail](amazon-lightsail-keeping-automatic-snapshots.md)\.

**Can I delete an automatic snapshot?**  
You can delete an automatic snapshot at any time by choosing **Delete** from the automatic snapshot’s context menu\. For more information, see [Deleting automatic snapshots of instances or disks in Amazon Lightsail](amazon-lightsail-deleting-automatic-snapshots.md)\.

**How can I use snapshots?**  
Snapshots can be used as a baseline or to create new resources if something goes wrong with the original resource\. Snapshots can also \. For more information, see [Snapshots in Amazon Lightsail](understanding-instance-snapshots-in-amazon-lightsail.md)\.  
Snapshots can also be exported to Amazon EC2 to create new resources within that service\. For more information, see [Exporting Amazon Lightsail snapshots](amazon-lightsail-exporting-snapshots.md)\.

## Networking<a name="amazon-lightsail-faq-networking"></a>

**How do I use IPs in Lightsail?**  
Each Lightsail instance automatically gets a private IP address and a public IP address\. You can use the private IP to transmit data between Lightsail instances and AWS resources privately, for free\. You can use the public IP to connect to your instance from the Internet, such as through a registered domain name or through an SSH or RDP connection from your local computer\. You can also attach a static IP to the instance, which substitutes the public IP with an IP address that doesn't change even if the instance is stopped and started\.

**What is a static IP?**  
A [static IP](understanding-static-ip-addresses-in-amazon-lightsail.md) is a fixed, public IP that is dedicated to your Lightsail account\. You can assign a static IP to an instance, replacing its public IP\. If you decide to replace your instance with another one, you can reassign the static IP to the new instance\. In this way, you don't have to reconfigure any external systems \(like DNS records\) to point to a new IP every time you want to replace your instance\.

**What are DNS records?**  
DNS is a globally distributed service that translates human readable names like www\.example\.com into numeric IP addresses, like 192\.0\.2\.1 that computers use to connect to each other\. With Lightsail, you can easily map your registered domain names such as photos\.example\.com to the public IPs of your Lightsail instances\. In this way, when users type human readable names like example\.com into their browsers, Lightsail automatically translates the address into the IP of the instance you want to direct your users to\. Each of these translations is referred to as a DNS query\.  
It's important to know that to use a domain in Lightsail, you must first register it\. You can register new domains using [Route 53](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/domain-register.html), or your preferred DNS registrar\.

**Can I manage firewall settings for my instance?**  
Yes\. You can control the data traffic for your instances by using the Lightsail firewall\. From the Lightsail console, you can set rules about which ports of your instance are publicly accessible for different types of traffic\.

## Billing and account management<a name="amazon-lightsail-frequently-asked-questions-faq-billing-and-account-management"></a>

**What do Lightsail plans cost?**  
Lightsail plans are billed on an on\-demand hourly rate, so you pay only for what you use\. For every Lightsail plan you use, we charge you the fixed hourly price, up to the maximum monthly plan cost\. The least expensive Lightsail plan starts at $0\.0047 USD/hour \($3\.50 USD/month\)\. Lightsail plans that include a Windows Server license start at $0\.01075 USD/hour \($8 USD/month\)\.

**When am I getting charged for a plan?**  
Lightsail instances and managed databases incur charges until they are deleted\. If you delete your Lightsail instance or managed database before the end of the month, we only charge you a prorated cost, based on the total number of hours that you used your Lightsail instance or managed database for that month\. For example, if you use the least expensive Lightsail instance plan for 100 hours in a month, you will be charged 46 cents \(100\*0\.0046\)\.

**Can I try Lightsail instances for free?**  
Yes\! Whether you're an existing or new AWS customer, you get 750 hours of free usage of the $3\.50 USD Lightsail plan for free\. You also can try Lightsail plans that include a Windows Server license for free using the $8 USD Windows plan\.  
You can use your 750 hours of usage across as many instances as you like\. For example, you can run a single Lightsail instance for a whole month, or 10 Lightsail instances for 75 hours\. The free trial offer is only applicable to usage within the first calendar month from when you sign up to use Lightsail\.

**What do Lightsail managed databases cost?**  
Lightsail managed databases come in 4 plan sizes and start at $15 USD per month for a 1GB RAM database instance with 40 GB of SSD storage and 100 GB data transfer allowance\. High Availability plans costs two times the Standard plan prices, because they run an additional database instance and storage disk in another Availability zone for redundancy\.

**Can I try Lightsail managed databases for free?**  
Yes\! New Lightsail customers get 1 month of the $15 USD Lightsail plan free\.

**What does Lightsail block storage cost?**  
Lightsail block storage costs $0\.10 USD per GB per month\.

**What do Lightsail load balancers cost?**  
Lightsail load balancers cost $18 USD per month\.

**What does certificate management cost?**  
Lightsail certificates and certificate management are free with use of a Lightsail load balancer\.

**What do Lightsail static IPs cost?**  
They're free in Lightsail, as long as you are using them\! You don't pay for a static IP if it is attached to an instance\. Public IPs are a scarce resource and Lightsail is committed to helping to use them efficiently, so we charge a small $0\.005 USD/hour fee for static IPs not attached to an instance for more than 1 hour\.

**What does data transfer cost?**  
Your instance and database plans include a free data transfer allowance\.  
For Lightsail instances, both data transfer in and data transfer out of your instance count toward your data transfer allowance\. If you exceed your data transfer allowance, you will only get charged for data transfer OUT from a Lightsail instance to the internet or to AWS resources using the public IP address of the instance\. Both data transfer IN to Lightsail instances and data transfer OUT from a Lightsail instance when using the instance's private IP address are free beyond your data transfer allowance\.  
For Lightsail managed databases, only data transfer OUT is counted against your allowance\. If you exceed your data transfer allowance, you will only get charged for data transfer OUT from a Lightsail managed database to the internet\.

**How does my data transfer allowance work with my load balancers?**  
Your load balancer does not consume your data transfer allowance\. Traffic between the load balancer and the target instances is metered and counts toward your data transfer allowance for your instances, in the same way that traffic in from and out to the internet is counted toward your data transfer allowance for Lightsail instances that are not behind a load balancer\. Traffic into and out of your load balancer to the internet is not calculated toward the data transfer allowance for your instances\.

**What if I exceed my data transfer plan allowance?**  
We have designed our data transfer plans so that the vast majority of our customers will be fully covered by their allowance and not incur any additional charges\. If you exceed your data transfer allowance, you will be charged an overage fee per GB of data transfer used \(data transfer OUT to the internet only\)\.  
Even if you exceed your data transfer allowance, many types of data transfer are free\. Data transfer IN to Lightsail instances and databases is always free\. Data transfer OUT from a Lightsail instance to another Lightsail instance, in between Lightsail instances and Lightsail managed databases, or to AWS resources in the same Region is also free if private IP addresses are used\.

**What types of data transfer do I get charged for?**  
When you exceed the monthly free data transfer allowance of your plan, you will get charged for data transfer OUT from a Lightsail instance to the internet or to another AWS Region or to AWS resources in the same Region when using public IP addresses\. The charge for these types of data transfer above the free allowance is as follows:  
• US East \(Ohio\) \(us\-east\-2\): $0\.09 USD/GB  
• US East \(N\. Virginia\) \(us\-east\-1\): $0\.09 USD/GB  
• US West \(Oregon\) \(us\-west\-2\): $0\.09 USD/GB  
• Asia Pacific \(Mumbai\) \(ap\-south\-1\): $0\.13 USD/GB  
• Asia Pacific \(Seoul\) \(ap\-northeast\-2\): $0\.13 USD/GB  
• Asia Pacific \(Singapore\) \(ap\-southeast\-1\): $0\.12 USD/GB  
• Asia Pacific \(Sydney\) \(ap\-southeast\-2\): $0\.17 USD/GB  
• Asia Pacific \(Tokyo\) \(ap\-northeast\-1\): $0\.14 USD/GB  
• Canada \(Central\) \(ca\-central\-1\): $0\.09 USD/GB  
• EU \(Frankfurt\) \(eu\-central\-1\): $0\.09 USD/GB  
• EU \(Ireland\) \(eu\-west\-1\): $0\.09 USD/GB  
• EU \(London\) \(eu\-west\-2\): $0\.09 USD/GB  
• EU \(Paris\) \(eu\-west\-3\): $0\.09 USD/GB  
Instances created in different Availability Zones can communicate between zones privately and for free, and are much less likely to be impaired concurrently\. Availability Zones enable you to build highly available applications and websites without increasing the cost of data transfer or compromising your application's security\.

**How do my data transfer plan allowances vary by AWS Region?**  <a name="lightsail-faq-data-transfer-charges"></a>
All AWS Regions have the same data transfer plan allowance as listed on [amazonlightsail\.com](http://amazonlightsail.com) and [amazonlightsail\.com/pricing](http://amazonlightsail.com/pricing), with the exception of the Asia Pacific \(Mumbai\) and the Asia Pacific \(Sydney\) Regions\. In these two AWS Regions, the data transfer plan allowance for instances is as follows:  
• $3\.50 USD/month plan: \.5 TB  
• $5 USD/month plan: 1 TB  
• $10 USD/month plan: 1\.5 TB  
• $20 USD/month plan: 2 TB  
• $40 USD/month plan: 2\.5 TB  
• $80 USD/month plan: 3 TB  
• $160 USD/month plan: 3\.5 TB  
Data transfer allowances for Lightsail managed databases are the same in all regions\.

**How does my data transfer allowance work for instances?**  
Beyond the free data transfer IN and between instances, every single Lightsail plan also includes a healthy amount of free data transfer OUT\. For example, using the least expensive Lightsail bundle you can send up to 1 TB of data to and from the internet within the month, at no extra charge\. Your data transfer allowance resets every month, and you can consume it whenever you need within the month\.  
If you delete your instance early and create another one, the free data transfer allowance is shared between the two instances\. Data transfer overages above the free allowance are charged at $0\.09 USD/GB\.

**What does Lightsail DNS management cost?**  
DNS management is free within Lightsail\. You can create up to 3 DNS zones and as many records as you want for each DNS zone\. You also get a monthly allowance of 3 million DNS queries per month to your zones\. Beyond your first 3 million queries in a month, you are charged $0\.40 USD per 1 million DNS queries\.

**What do Lightsail snapshots cost?**  
Lightsail snapshots \(manual and automatic\) cost $0\.05 USD/GB\-month to store\. This means that if you create a snapshot of an instance that is using 28 GB of space, and keep it for a month, you pay $1\.40 USD for the month\.  
When you take multiple, successive snapshots of the same instance, Lightsail automatically cost\-optimizes your snapshots\. For each new snapshot you take, you're charged only for the part of the data that changed\. In the example above, if your instance data only changes by 2 GB, your second instance snapshot costs only $0\.10 USD per month\.

**How can I manage my AWS account?**  
Lightsail is an AWS service and runs on the AWS trusted and proven cloud infrastructure\. You use the same AWS account and credentials to log in to Lightsail and the AWS Management Console\.  
You can manage your AWS account, including changing your AWS account password, user name, contact information, or billing information from the [AWS Billing and Cost Management console](https://console.aws.amazon.com/billing/home)\.

**What are the Lightsail legal terms of use?**  
Lightsail is an Amazon web service, so to use Lightsail, you first agree to the [AWS Customer Agreement and Service Terms](https://aws.amazon.com/legal/)\. When creating Lightsail instances, you also agree that your use of software is also subject to the end user license agreement of the seller, available for your review on the create instance page\.

**How can I pay my Lightsail bill?**  
You can pay and manage your bill through the AWS Billing and Cost Management console\. AWS accepts most major credit cards\. Learn more about managing your payment methods [here](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/manage-payments.html)\.

## Export to Amazon Elastic Compute Cloud \(Amazon EC2\)<a name="amazon-lightsail-faq-export-to-ec2"></a>

**What is export to Amazon EC2?**  
Export to Amazon EC2 is a feature that allows you to create a copy of your Lightsail instance in Amazon EC2\. When you export to Amazon EC2, you can pick among the wide set of instance types, configurations, and pricing models that Amazon EC2 offers, and have even more fine\-tuned control over your networking, storage, and compute environment\. 

**Why would I want to export to Amazon EC2?**  
Lightsail offers you an easy way to run and scale a wide set of cloud\-based applications, at a bundled, predictable, and low price\. Lightsail also automatically sets up your cloud environment configurations such as networking and access management\.  
Exporting to Amazon EC2 allows you to run your application on a wider set of instance types, ranging from virtual machines with more CPU power, memory, and networking capabilities, to specialized or accelerated instances with FPGAs and GPUs\. In addition, Amazon EC2 performs less automatic management and set\-up, allowing you more control over how you configure your cloud environment, such as your VPC\. 

**How does exporting to Amazon EC2 work?**  
To get started, you need to export your manual snapshot of a Lightsail instance or block storage disk\. Snapshots of Ghost and Django instances cannot be exported to Amazon EC2 at this time\. Customers who are comfortable with Amazon EC2 can then use the Amazon EC2 creation wizard or API to create a new Amazon EC2 instances or Amazon EBS volumes, as they would from an existing EC2 AMI or EBS volume\. Alternatively, Lightsail also provides a guided Lightsail console experience to help you easily create a new EC2 instance\.

**How am I billed?**  
Using the export to Amazon EC2 feature is free\. Once you have exported your manual snapshots to Amazon EC2, you will be charged for the Amazon EC2 image separately and in addition to your Lightsail manual snapshot\. Any new Amazon EC2 instances you launch will also be billed by Amazon EC2, including their Amazon EBS storage volume\(s\) and data transfer\. Refer to the [Amazon EC2 pricing page](https://aws.amazon.com/ec2/pricing/) for details on the pricing for your new instance and resources\. Lightsail resources that continue to run in your Lightsail account will continue to be billed at their regular rates until they are deleted\.

**Can I export managed databases or disk snapshots?**  
The export feature allows you to export manual Lightsail disk snapshots but doesn't currently support manual snapshots of managed databases\. Disk snapshots can be rehydrated as Amazon EBS volumes from the Amazon EC2 console or API\.

**What Lightsail resources can I export?**  
The Lightsail export to Amazon EC2 feature is designed to support the export of Linux and Windows instances and their attached block storage \(if applicable\) to Amazon EC2\. It also supports the export of unattached block storage disks to Amazon EBS\. It does not currently support the export of load balancers, databases, static IPs or DNS records\. Additionally, snapshots of Ghost and Django instances cannot be exported to Amazon EC2 at this time\.

## Tags in Lightsail<a name="amazon-lightsail-faq-tagging"></a>

**What are tags?**  
A tag is a label that you assign to a Lightsail resource\. Each tag consists of a key and a value, both of which you define\. A tag value is optional, so you can choose to create “key\-only” tags for filtering resources in the Lightsail console\.

**How can I use tags in Lightsail?**  
Tags have multiple use cases \- they enable you to group and filter your resources in the Lightsail console and API, track and organize your costs in your bill, and regulate who can see or modify your resources through access management rules\. By tagging your resources you can:  
• Organize \- use the Lightsail console and API filters to view and manage resources based on their tags you have assigned them\. This is useful when you have many resources of the same type—you can quickly identify a specific resource based on the tags you've assigned to it\.  
• Cost\-allocate \- track and allocate costs across different projects or users by tagging your resources and creating “cost allocation tags” in the billing console\. For instance, you can split out your bill and understand your costs by project or by client\.  
• Manage access \- control how users with access to your AWS account can edit, create, and delete Lightsail resources by using AWS Identity and Access Management policies\. This allows you to more easily collaborate with others without needing to give them full access to your Lightsail resources\.  
For more information about using tags in Lightsail, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

**What resources can be tagged?**  
Lightsail currently supports tagging for the following resources:  
• Instances \(Linux and Windows\)  
• Block storage disks  
• Load balancers  
• Databases  
• DNS zones  
• Manual snapshots of instances, disks, and databases  
Manual snapshots support tags; however, you must use the Lightsail API, or AWS CLI to tag snapshots\. If you use the Lightsail console to create a manual snapshot of a tagged instance, disk, or database, the manual snapshot is automatically given the same tags as the source resource\. You can edit these tags when you use the Lightsail console to create a new resource from a tagged manual snapshot\.  
Automatic snapshots cannot be tagged\.

**How can I tag my Lightsail snapshots?**  
The Lightsail console automatically tags manual snapshots with the same tags as its source resource\. If you use the Lightsail API, or AWS CLI to create a snapshot, you can choose the tags for the snapshot yourself\.  
Tags for manual snapshots of databases are not currently included in billing reports \(cost allocation tags\)\.

**What is the difference between key\-value and key\-only tags?**  
Lightsail tags are key\-value pairs, allowing you to organize resources such as instances across different categories \(e\.g\. project:Blog, project:Game, project:Test\)\. This allows you full control across all use cases such as resource organization, bill reporting, and access management\. The Lightsail console also allows you to tag your resources with key\-only tags for quick filtering in the console\.

## Contacts and notifications<a name="faq-contacts-and-notifications"></a>

**What are notifications?**  
You can configure alarms in Lightsail to notify you when a metric for one of your instances, databases, or load balancers crosses a specified threshold\. Notifications can be in the form of a banner displayed in the Lightsail console, an email sent to an address you specify, or an SMS text message sent to a mobile phone number you specify\. To be notified by email and SMS text message, you must add your email address and mobile phone number as notification contacts in each AWS Region where you want to monitor your resources\. For more information about notifications, see [Notifications in Amazon Lightsail](amazon-lightsail-notifications.md)\.

**How many contacts can I add?**  
You can add one email address and one mobile phone number in each AWS Region where you want to monitor your resources\. SMS text messaging is not supported in all AWS Regions in which you can create Lightsail resources, and text messages cannot be sent to some countries and regions of the world\. For more information about notifications, see [Notifications in Amazon Lightsail](amazon-lightsail-notifications.md)\.

## Metrics and alarms<a name="faq-metrics-and-alarms"></a>

**What are metrics?**  
Lightsail reports metric data for instances, databases, and load balancers\. Some metrics include your instance’s CPU utilization percentage, the amount of inbound and outbound network traffic, system and instance error counts, database disk queue depth, database free storage space, load balancer error counts, load balancer response times, and more\. Metrics allow you to monitor and maintain the reliability, availability, and performance of your resources\. Monitor and collect metric data from your resources regularly so that you can more readily debug a multi\-point failure, if one occurs\. For more information, see [Resource metrics in Amazon Lightsail](amazon-lightsail-resource-health-metrics.md)\.

**What are alarms?**  
You can create an alarm in Lightsail that watches a metric for your instances, databases, and load balancers\. The alarm can be configured to notify you based on the value of the metric relative to a threshold that you specify\. For more information, see [Alarms in Amazon Lightsail](amazon-lightsail-alarms.md)\.  
Notifications can be a banner displayed in the Lightsail console, an email sent to your email address, and an SMS text message sent to your mobile phone number\. For more information about notifications, see [Notifications in Amazon Lightsail](amazon-lightsail-notifications.md)\.

**How many alarms can I add?**  
You can configure two alarms for each metric that is available for instances, databases, and load balancers\. For more information, see [Alarms in Amazon Lightsail](amazon-lightsail-alarms.md)\.