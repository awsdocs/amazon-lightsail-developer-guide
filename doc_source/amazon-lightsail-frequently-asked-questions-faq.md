# Frequently Asked Questions in Amazon Lightsail<a name="amazon-lightsail-frequently-asked-questions-faq"></a>

 *Last updated: July 14, 2021* 

This topic answers frequently asked questions \(FAQ\)\. If you have a FAQ that is not answered here, use the **Questions? Comments?** feedback button at the bottom of the page\. You can also post a question in the [Lightsail discussion forum](https://forums.aws.amazon.com/forum.jspa?forumID=231)\.

**Contents**
+ [General](#amazon-lightsail-frequently-asked-questions-faq-general)
+ [Instances](#amazon-lightsail-faq-instances)
+ [Object storage and buckets](#amazon-lightsail-faq-buckets)
+ [Container services](#amazon-lightsail-faq-containers)
+ [Databases](#amazon-lightsail-faq-databases)
+ [Block storage](#amazon-lightsail-faq-block-storage)
+ [Load balancers](#amazon-lightsail-faq-load-balancers)
+ [Content delivery network distributions](#amazon-lightsail-faq-cdn-distributions)
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
Amazon Lightsail is the easiest way to get started with AWS for developers, small businesses, students, and other users who need a solution to build and host their websites and web applications in the cloud\. Lightsail provides developers compute, storage, and networking capacity\. Lightsail includes everything you need to launch your project quickly – virtual machines, containers, databases, CDN, load balancers, DNS management etc\. – for a low, predictable monthly price\.

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
• EU \(Stockholm\) \(eu\-north\-1\)  
For more information, see [AWS Regions and Availability Zones in Lightsail](understanding-regions-and-availability-zones-in-amazon-lightsail.md)\.

**What are Availability Zones?**  
Availability Zones are collections of data centers that run on physically distinct, independent infrastructure and are engineered to be highly reliable\. Common points of failure such as generators and cooling equipment are not shared between Availability Zones\. Additionally, Availability Zones are physically separate, so that even extremely uncommon disasters such as fires, tornados, or flooding can affect only a single Availability Zone\.

**What are the Lightsail service quotas?**  
For the latest Lightsail service quotas, including which quotas can be increased, see the [Lightsail service quotas](https://docs.aws.amazon.com/general/latest/gr/lightsail.html#limits_lightsail) in the *AWS General Reference*\. If you need to increase a quota, please open a case with [customer service](https://console.aws.amazon.com/support/home?region=us-east-1)\.

**How can I get more help?**  
We're here for you\. Our context\-sensitive **Help** panel in Lightsail offers immediate helpful tips about your actions in the console\. From the Lightsail console, you can also access a library of [getting started guides](https://lightsail.aws.amazon.com/ls/docs/getting-started), [overviews](https://lightsail.aws.amazon.com/ls/docs/overview), and [how\-to topics](https://lightsail.aws.amazon.com/ls/docs/how-to)\. And if you want to use the Lightsail API, or AWS CLI, Lightsail has a full API reference for all supported programming languages\. You can also use Lightsail support resources\.  
If you have an issue with your account or billing, contact [customer service](https://console.aws.amazon.com/support/home?region=us-east-2#/) online\. You get free 24x7 access with your Lightsail account\.  
If you have a general question about how to use Lightsail, search the Lightsail documentation and [support forums](https://forums.aws.amazon.com/forum.jspa?forumID=231)\.  
Additionally, AWS Support offers an array of paid plans to cover your individual needs\.

## Instances<a name="amazon-lightsail-faq-instances"></a>

**What is a Lightsail instance?**  
A Lightsail instance is a virtual private server \(VPS\) that lives in the AWS Cloud\. Use your Lightsail instances to store your data, run your code, and build web\-based applications or websites\. Your instances can connect to each other and to other AWS resources through both public \(internet\) and private \(VPC\) networking\. You can create, manage, and connect easily to instances right from the Lightsail console\.

**What is a Lightsail plan?**  
Also referred to as a bundle, a Lightsail plan includes a virtual server with a fixed amount of memory \(RAM\) and compute \(vCPUs\), SSD\-based storage \(disks\), and a free data transfer allowance\. Lightsail plans also offer static IPv4 addresses, and DNS management\. Lightsail plans are charged on an hourly, on\-demand basis, so you only pay for a plan when you're using it\.

**What software can I run on my instances?**  
Lightsail offers a range of operating system and application templates that are automatically installed when you create a new Lightsail instance\. Application templates include WordPress, WordPress Multisite, cPanel & WHM, PrestaShop, Django, Drupal, Ghost, Joomla\!, Magento, Redmine, LAMP, Nginx \(LEMP\), MEAN, and Node\.js\.  
You can install additional software on your instances by using the in\-browser SSH or your own SSH client\.

**What operating systems can I use with Amazon Lightsail?**  
Lightsail currently supports 7 Linux or Unix\-like distributions: Amazon Linux, Amazon Linux 2, CentOS, Debian, FreeBSD, OpenSUSE, and Ubuntu, as well as three Windows Server versions: 2012 R2, 2016, and 2019\.

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
When you stop your instance, it is powered down at its current state and is available for you to start again at any time\. Stopping your instance will release its public IPv4 address, so it is recommended that you use static IPv4 addresses for instances that must retain the same IP after they are stopped and started\. Note that the public IPv6 addresses attached to instances don't change even when instances are stopped and started\.  
When you delete your instance, you are performing a destructive action\. Unless you have created an instance snapshot, all of your instance data will be lost and you cannot recover it again\. Automatic snapshots are also deleted with the instance unless you keep them by copying them as manual snapshots\. The instance's public and private IP addresses will also be released\. If you were using a static IPv4 address with that instance, the static IPv4 address is detached, but remains in your account\.

## Object storage and buckets<a name="amazon-lightsail-faq-buckets"></a>

**What can I do with Lightsail object storage?**  
You can store your static content, such as images, videos, and HTML files in a bucket in the Lightsail object storage service\. You can use the objects stored in your bucket with your websites and applications\. Lightsail object storage can be associated to your Lightsail CDN distribution with a few simple clicks, making it quick and easy to accelerate the delivery of your content to a global audience\. It can also be used as a low cost, secure backup solution\. For more information, see [Object storage in Amazon Lightsail](buckets-in-amazon-lightsail.md)\.

**What does Lightsail object storage cost?**  
Lightsail object storage has three different fixed\-priced bundles in all AWS Regions where Lightsail is available\. The first bundle is $1/month and is free for the first 12 months\. This bundle includes 5 GB storage capacity and 25 GB of data transfer\. The second bundle is $3 per month and includes 100 GB storage capacity and 250 GB of data transfer\. Lastly, the third bundle is $5 per month and includes 250 GB of storage capacity and 500 GB data transfer\. Lightsail object storage includes unlimited data transfer into your bucket, as the bundled data transfer allowance is used only for data transfer out from your bucket\.

**Does Lightsail object storage have overage charges?**  
When you exceed the monthly storage capacity or data transfer allowance of your object storage plan, you will get charged for the additional amount\. For more information, see the [Lightsail pricing page](https://aws.amazon.com/lightsail/pricing/)\.

**How does my data transfer allowance work with object storage?**  
You can consume your data transfer allowance by transferring data into and out of Lightsail object storage, except for the following:  
• Data transferred into Lightsail object storage from the internet  
• Data transfer between Lightsail object storage resources  
• Data transferred out from Lightsail object storage to another Lightsail resource in the same AWS Region \(including to a resource in a different AWS account, but in the same AWS Region\)  
• Data transferred out from Lightsail object storage to a Lightsail CDN distribution

**Can I change the plan associated with my Lightsail bucket?**  
Yes, you can change your Lightsail object storage plan one time within your monthly AWS billing cycle\.

**Can I copy objects from Lightsail object storage to Amazon S3?**  
Yes, copying from Lightsail object storage to Amazon S3 is supported\. For more information, see [How can I copy all objects from one Amazon S3 bucket to another bucket?](https://aws.amazon.com/premiumsupport/knowledge-center/move-objects-s3-bucket/) in the *AWS Premium Support Knowledge Center*\.

**How do I get started with Lightsail object storage?**  
To use Lightsail object storage, you must first create a bucket that is used to store your data\. For more information, see Creating buckets in Amazon Lightsail\. After your bucket is up and running, you can start adding objects to your bucket by uploading files using the Lightsail console or by configuring your application to put content like logs or other application data in the bucket\. Alternatively, you can also get started with Lightsail object storage through the use of AWS Command Line Interface \(AWS CLI\)\.

**How do I upload objects to my bucket?**  
To upload object\(s\) to your bucket, like images or other static files, choose “Upload” from the “Objects” top navigation tab and select the correct filed or directory from your computer\. Alternately, drag and drop files and directories from your desktop into the marked area in the Lightsail object storage console\.

**Can I block public access to my bucket?**  
Lightsail buckets and objects are set to private by default, meaning that only users with appropriate permissions have access to the bucket and objects\. A user can change this default setting and either make individual objects public and read only in a private bucket or opt to make the entire bucket public and read only\. When a user makes a bucket or object public, anyone in the world can read its content\. For more information, see [Understanding bucket permissions in Amazon Lightsail](amazon-lightsail-understanding-bucket-permissions.md)\.

**How do I provide programmatic access to my bucket?**  
You can use either access keys or roles for programmatic access to your bucket\. First, select the bucket you want to programmatically connect to in the Lightsail console\. Second, under the “Permissions” tab, create an access key or assign a role to your Lightsail instance and then configure your website or application code to use your bucket\. This behavior may vary depending on how you plan to use object storage with your website or application\. For more information, see [Understanding bucket permissions in Amazon Lightsail](amazon-lightsail-understanding-bucket-permissions.md)\.

**How do I share a bucket with other AWS accounts?**  
Lightsail makes cross\-account sharing easy by allowing you to share access to your bucket with the AWS account ID that you specify in the Cross\-account access section of the bucket management page\. After you specify an AWS account ID, that account will have read\-only access to the bucket\. For more information, see [Understanding bucket permissions in Amazon Lightsail](amazon-lightsail-understanding-bucket-permissions.md)\.

**What is versioning?**  
Versioning allows you to preserve, retrieve, and restore every version of every object storage in your bucket, providing an additional level of protection from accidental overwrites and deletes\.\. For more information, see [Enabling and suspending object versioning in a bucket in Amazon Lightsail](amazon-lightsail-managing-bucket-object-versioning.md)\.

**How do I associate my Lightsail bucket to my Lightsail CDN distribution?**  
Lightsail object storage can be associated to Lightsail CDN distributions with a few simple clicks, making it quick and easy to accelerate the delivery of your content to a global audience\. To do so, create a Lightsail CDN distribution and simply select the Lightsail bucket as the origin of your Lightsail CDN distribution\. For more information, see [Using an Amazon Lightsail bucket with a Lightsail content delivery network distribution](amazon-lightsail-using-distributions-with-buckets.md)\.

**What limits are there for the Lightsail object storage service?**  
You can create up to 20 buckets in the Lightsail object storage service per account\. There is no limit to the number of objects that you can store in a bucket\. You can store all of your objects in a single bucket, or you can organize them across several buckets\.

**Does Lightsail object storage support monitoring and alerting?**  
With Lightsail object storage, customers can easily view metrics on the total used space within a bucket and number of objects within the bucket\. Alerting based on these metrics is also supported\. For more information, see [Viewing metrics for your bucket in Amazon Lightsail](amazon-lightsail-viewing-bucket-metrics.md) and [Creating bucket metric alarms in Amazon Lightsail](amazon-lightsail-adding-bucket-metric-alarms.md)\.

## Container services<a name="amazon-lightsail-faq-containers"></a>

**What can I do with Lightsail container services?**  
Lightsail container services provide an easy way to run containerized applications in the cloud\. You can run a variety of applications on a container service, ranging from simple web apps to multi\-tiered micro services\. You just specify the container image, power \(CPU, RAM\) and scale \(number of nodes\) required for your container service\. Lightsail takes care of running the container service without you having to manage any underlying infrastructure\. Lightsail will provide you with a load balanced TLS endpoint to access the application running on the container service\.

**Can Lightsail container service run Docker containers?**  
Yes\. Lightsail supports Linux\-based Docker containers\. Windows containers are currently not supported\.

**How do I use my Docker container images with Lightsail container service?**  
You can use either container images on registries like Amazon ECR Public Registry and Docker Hub, or build your own custom image and push it to Lightsail in a few easy steps using the AWS CLI\. For more information, see [Pushing and managing container images on your Amazon Lightsail container services](amazon-lightsail-pushing-container-images.md)\.

**Can I pull my container images from a private container registry?**  
Currently, only public container registries are supported by Lightsail container services\. Alternately, you can push your custom container images from your local machine to Lightsail to keep them private\. 

**Can I change the power and scale of my service based on demand?**  
Yes, container service power and scale can be changed at any time even after the service is created\.

**Can I customize the name of the HTTPS endpoint created by Lightsail container service?**  
Lightsail provides a HTTPS endpoint for every container service in the format “*<service\-name>*\.*<random\-guid>*\.*<aws\-region\-name>*\.cs\.amazonlightsail\.com\. Only the service name can be customized\. Alternately, you can use a custom domain name\. For more information, see [Enabling and managing custom domains for your Amazon Lightsail container services](amazon-lightsail-enabling-container-services-custom-domains.md)\.

**Can I use custom domains for the HTTPS endpoint of a Lightsail container service?**  
Yes\. You can create and attach an SSL/TLS certificate with custom domain names to your container service in Lightsail\. The certificates must be domain validated\. If you the DNS of your domain using a Lightsail DNS zone, you can add an address \(A for IPv4 or AAAA for IPv6\) to map the apex of your domain \(e\.g\., `example.com`\) or a subdomain \(e\.g\., `www.example.com`\) to your container services\. You can also add a canonical \(CNAME\) record to map a subdomain \(e\.g\., `www.example.com`\) to your container services\. Alternately, you can use a DNS hosting provider who supports adding ALIAS records to map the apex of your domain \(\.e\.g, `example.com`\) to the default domain \(public DNS\) of your Lightsail container service\. For more information, see [Enabling and managing custom domains for your Amazon Lightsail container services](amazon-lightsail-enabling-container-services-custom-domains.md)\.

**What do Lightsail container services cost?**  
Lightsail container services are billed on an on\-demand hourly rate, so you pay only for what you use\. For every Lightsail container service you use, we charge you the fixed hourly price, up to the maximum monthly service price\. Maximum monthly service price can be calculated by multiplying the base price of the power of your service with the scale of your service\. For example, a service of Micro power and scale of 2 will cost a maximum of $10\*2=$20/month\. The least expensive Lightsail container service starts at $0\.0094 USD/hour \($7 USD/month\)\. Additional data transfer charges may apply for usage above the free\-quota of 500 GB per month for each service\. 

**Will I be charged for the whole month even if I run my container service for a few days?**  
Your Lightsail container services are charged only when they're in the running or disabled state\. If you delete your Lightsail container service before the end of the month, we charge you a prorated cost based on the total number of hours that you used your Lightsail container service\. For example, if you use your Lightsail container service with a power of Micro and scale of 1 for 100 hours in a month, you will be charged $1\.34 \($0\.0134\*100\)

**Will I be charged for data transfer in and out of the container service?**  
Every container service comes with a data transfer quota \(500 GB per month\)\. This counts towards both the data transfer IN and OUT of your service\. When you exceed the quota, you will get charged for data transfer OUT from a Lightsail container service to the Internet or to another AWS Region or to AWS resources in the same Region when using public IP addresses\. The charge for these types of data transfer above the free allowance is as follows:  
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
• EU \(Stockholm\) \(eu\-north\-1\): $0\.09 USD/GB

**What is the difference between stopping and deleting my container service?**  
When you disable your container service, your container nodes are in a disabled state and the public endpoint of the service returns a HTTP status code ‘503’\. Enabling the service restores it to the last active deployment\. Power and scale configurations are also retained\. Public endpoint name does not change after re\-enabling\. Deployment history and container images are preserved\.  
When you delete your container service, you are performing a destructive action\. All the container nodes of the service will be permanently deleted\. The HTTPS public endpoint address, container images, deployment history, and logs associated with your service will also be permanently deleted\. You will not be able to recover the endpoint address\.

**Will I be charged if my container service is in a disabled state?**  
Yes, you are charged according to the power and scale configuration of your container service, even when it is in a disabled state\. 

**Can I use container services as the origin to my Lightsail content delivery network \(CDN\) distributions?**  
Container services are currently not supported as origins for Lightsail CDN distributions\. 

**Can I use container services as targets for my Lightsail load balancer?**  
No\. Container services are currently not available as targets for Lightsail load balancers\. However, the public endpoints of container services come with built\-in load balancing\. 

**Can I configure the public endpoint of my container service to redirect HTTP requests to HTTPS?**  
Lightsail container service public endpoints automatically redirect all HTTP requests to HTTPS to ensure that your content is served securely\.

**Do container services support monitoring and alerting?**  
Container services provide metrics for CPU utilization and memory utilization across the nodes of your service\. Alerting based on these metrics is currently not supported\. 

**Do Lightsail container services support IPv6?**  
Lightsail container service HTTPS endpoints support both IPv4 and IPv6\. Pv6 cannot be disabled on container services\.

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

**Do Lightsail managed databases services support IPv6?**  
Lightsail managed databases do not support IPv6\.

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

**Do Lightsail load balancers support IPv6?**  
Lightsail load balancers created after January 12, 2021, operate in dual\-stack mode by default \(i\.e\., they accept client traffic over both IPv4 and IPv6 protocol\)\. IPv6 can be enabled on load balancers created before this date through a toggle on the Networking tab of the load balancer's management page\. IPv6 can be disabled on any load balancer using this toggle too\.

**Do the instances behind a load balancer need to be IPv6 enabled to use the load balancer which is IPv6 enabled?**  
No\. Load balancers accept both IPv4 and IPv6 traffic, and seamlessly convert it to IPv4 when communicating with the instances in the backend\. Hence, instances behind a load balancer can either be dual\-stack or IPv4 only\.

## Content delivery network distributions<a name="amazon-lightsail-faq-cdn-distributions"></a>

**What can I do with Lightsail CDN distributions?**  
Lightsail content delivery network \(CDN\) distributions make it easy for you to accelerate the delivery of content hosted on your Lightsail resources by storing and serving it on Amazon’s global delivery network, powered by Amazon CloudFront\. Distributions also help you enable your website to support HTTPS traffic by providing simple SSL certificate creation and hosting\. Finally, distributions can help reduce the load on your Lightsail resources and help your website handle large traffic spikes\. Like all of Lightsail’s features, setup can be completed with just a few clicks, and you pay a simple monthly price\.

**What types of resources can I use as the origin of my distributions?**  
Lightsail distributions allow you to use your Lightsail instances and load balancers as origins\. Lightsail containers are not currently supported as origins\. Resources outside of Lightsail, such as S3 buckets, are not supported\.

**Do I need to attach a static IPv4 address to my Lightsail instance in order to use it as an origin for my Lightsail distribution?**  
Yes, static IPv4 addresses are required to be attached to instances that are specified as origins\.

**How do I setup a Lightsail distribution with my WordPress website?**  
Simply create your distribution, select your WordPress instance as the origin, choose your plan, and you’re all set\. Lightsail distributions automatically configure your distribution settings to optimize performance for most WordPress configurations\.

**Can I attach multiple origins?**  
Although you cannot attach multiple origins to your Lightsail distribution, you can attach multiple instances to a Lightsail load balancer and specify it as the origin of your distribution\.

**Do Lightsail distributions support certificate creation?**  
Yes\. Lightsail distributions makes it easy to create, verify, and attach certificates directly from your distribution’s management page\.

**Is a certificate required?**  
A certificate is only required if you wish to use your custom domain name with your distribution\. All Lightsail distributions are created with a unique Amazon CloudFront domain name that is HTTPS\-enabled\. However, if you wish to use your custom domain with your distribution, then you need to attach a certificate for your custom domain to your distribution\.

**Is there a limit to the number of certificates I can create?**  
Yes, refer to the [Lightsail service quotas](https://docs.aws.amazon.com/general/latest/gr/lightsail.html#limits_lightsail) for more information\.

**How can I configure my distribution to redirect HTTP requests to HTTPS?**  
Lightsail distributions automatically redirect all HTTP requests to HTTPS to ensure that your content is served securely\.

**How can I configure my apex domain to point to my Lightsail distribution?**  
In order to point your apex domain to your CDN distribution, you must create an ALIAS record in the domain name system \(DNS\) of your domain that maps your apex domain to your distribution’s default domain\. If your DNS hosting provider does not support ALIAS records, you can use Lightsail DNS zones to easily configure your apex domain to point to your distribution’s domain\.

**What are the differences between Lightsail’s instance data transfer quotas and distribution data transfer quotas?**  
While data transfer IN and OUT count toward your instance’s data transfer quota, only data transfer OUT to your origin and to your viewers counts toward you distribution’s quota\. In addition, all data transfer OUT in excess of your distribution’s quota is charged an overage fee, whereas some types of data transfer OUT are free for instances\. Finally, Lightsail distributions use a different regional overage model, though the majority of the rates are the same as those charged for instance overage\.

**Can I change the plan associated with my distribution?**  
Yes, you can change your distribution's plan once per month\. If you wish to change your plan a second time, you must wait until the beginning of the following month to do so\.

**How do I know if my distribution is working?**  
Lightsail distributions provide you with a variety of metrics that track the performance of your distribution, including the total number of requests your distribution has received, the amount of data your distribution has sent to clients and to your origin, and the percentage of requests that have resulted in errors\. Additionally, you can create alerts that are linked to distribution metrics\.

**Can I delete cached content on my Lightsail distribution?**  
You can delete all cached content, but not specific files or folders\.

**When should I use Lightsail distributions versus Amazon CloudFront distributions?**  
Lightsail distributions are designed specifically for users who are hosting websites or web applications on Lightsail resources, such as instances and load balancers\. If you’re using another service in AWS to host your website or app, have complex configuration needs, or have a workload that involves a high number of requests per second or large amount of video streaming, we recommend that you use Amazon CloudFront\.

**Can I move my Lightsail content delivery network \(CDN\) distribution to Amazon CloudFront?**  
Yes, you can move your Lightsail distribution by creating a similarly configured distribution in Amazon CloudFront\. All of the settings that can be configured in a Lightsail distribution can also be configured in a CloudFront distribution\. Complete the following steps to move your distribution to CloudFront:  
+ Take a snapshot of your Lightsail instance that is configured as your distribution's origin\. Export the snapshot to Amazon EC2, and then create a new instance from the snapshot in EC2\. For more information, see [Exporting Amazon Lightsail snapshots](amazon-lightsail-exporting-snapshots.md)\.
**Note**  
 Create an application load balancer in Elastic Load Balancing if you need to load balance your website or web application\. For more information, see the [Elastic Load Balancing User Guide](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html)\.
+ Disable custom domains for your Lightsail distribution to detach certificates that you might have attached to it\. For more information, see [Disabling custom domains for your Amazon Lightsail distributions](amazon-lightsail-disabling-distribution-custom-domains.md)\.
+ Using the AWS Command Line Interface \(AWS CLI\), run the get\-distributions command to get a list of your Lightsail distribution’s settings\. For more information, see [get\-distributions](https://docs.aws.amazon.com/cli/latest/reference/lightsail/get-distributions.html) in the *AWS CLI Reference*\.
+ Sign in to the [CloudFront console](https://console.aws.amazon.com/cloudfront/) and create a distribution with the same configuration settings as your Lightsail distribution\. For more information, see [Creating a Distribution](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/distribution-web-creating-console.html) in the *Amazon CloudFront Developer Guide*\.
+ Create a certificate in AWS Certificate Manager \(ACM\) that you will attach to your CloudFront distribution\. For more information, see [Request a Public Certificate](https://docs.aws.amazon.com/acm/latest/userguide/gs-acm-request-public.html) in the *ACM User Guide*\.
+ Update your CloudFront distribution to use the ACM certificate you created\. For more information, see [Updating your CloudFront distribution](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/cnames-and-https-procedures.html#cnames-and-https-updating-cloudfront) in the *CloudFront User Guide*\.

**How is Lightsail CDN intended to be used?**  
Lightsail CDN distributions are created using fixed\-priced bundles of data transfer to make the cost of using the service simple and predictable\. Distribution bundles are designed to cover a month’s worth of usage\. Using distribution bundles in a way to avoid incurring overage fees \(including, but not limited to, frequently upgrading or downgrading bundles, or using an excessively large number of distributions with a single origin\) is beyond the intended scope of use and is not permitted\. In addition, workloads that involve a high number of requests per second or large amount of video streaming are not permitted\. Engaging in these behaviors may result in throttling or suspension of your data services or account\.

**Do Lightsail CDN distributions support IPv6?**  
All Lightsail CDN distributions have IPv6 enabled by default\. The distribution hostnames resolve to both IPv4 and IPv6 addresses\. IPv6 can be disabled via a toggle on the Networking tab of the CDN's management page\.

**Do the origins need to be IPv6 enabled to work with the Lightsail CDN distributions?**  
No\. CDN distributions accept both IPv6 and IPv4 traffic, and seamlessly convert it to IPv4 when communicating with the origins in the backend\. Hence, origins behind a distribution can either be dual\-stack or IPv4 only\.

## Certificates<a name="amazon-lightsail-faq-certificates"></a>

**How can I use Lightsail\-provisioned certificates?**  
SSL/TLS certificates are used to establish the identity of your website or application and secure connections between browsers and your website\. Lightsail provides a signed certificate to use with your load balancer, and the load balancer provides SSL/TLS termination before routing verified traffic to your target instances over the secure AWS network\. Lightsail certificates can only be used with Lightsail load balancers, not with individual Lightsail instances\.

**How do I validate my certificate?**  
Lightsail certificates are domain validated, meaning that you need to provide proof of identity by validating that you own or have access to your website’s domain before the certificate can be provisioned by the certificate authority\. When you request a new certificate, Lightsail will prompt you to add a CNAME to the DNS zone\(s\) of the domain or domains you are validating\. You will add this CNAME wherever you currently manage your DNS zones – either Lightsail DNS management or an external DNS hosting provider \(e\.g\., Route 53, GoDaddy, Namecheap, etc\.\)\.

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
Each Lightsail instance automatically gets a private IPv4 address, a public IPv4 address, and a public IPv6 address \(IPv6 must be manually enabled for instances created before January 12, 2021\)\. You can use the private IP to transmit data between Lightsail instances and AWS resources privately, for free\. You can use the public IP to connect to your instance from the Internet, such as through a registered domain name or through an SSH or RDP connection from your local computer\. You can also attach a static IPv4 address to the instance, which substitutes the public IPv4 address with an IPv4 address that doesn't change even if the instance is stopped and started\. Lightsail doesn’t currently support static IPv6 addresses\.

**Does Lightsail support IPv6\-only instances?**  
Lightsail instances support dual\-stack \(IPv4 and IPv6\) and IPv4\-only configurations\. Currently, IPv6\-only mode is not supported\.

**What is a static IP?**  
A [static IP](understanding-static-ip-addresses-in-amazon-lightsail.md) is a fixed, public IP that is dedicated to your Lightsail account\. You can assign a static IPv4 address to an instance, replacing its public IPv4\. If you decide to replace your instance with another one, you can reassign the static IP to the new instance\. In this way, you don't have to reconfigure any external systems \(like DNS records\) to point to a new IP address every time you want to replace your instance\. Lightsail currently supports static IPs for IPv4 only\. Static IPv6 addresses are not available\. However, IPv6 addresses assigned to the instance remain unchanged until the instance is deleted or the IPv6 address is manually released by disabling IPv6 on the instance\.

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

**What do Lightsail static IPv4 addresses cost?**  
They're free in Lightsail, as long as you are using them\! You don't pay for a static IPv4 address if it is attached to an instance\. Public IP addresses are a scarce resource and Lightsail is committed to helping to use them efficiently, so we charge a small $0\.005 USD/hour fee for static IPs not attached to an instance for more than 1 hour\.

**What does data transfer cost?**  
Your instance, database, and content delivery network \(CDN\) distribution plans include a data transfer allowance\.  
For Lightsail instances, both data transfer in and data transfer out of your instance count toward your data transfer allowance\. If you exceed your data transfer allowance, you will only get charged for data transfer OUT from a Lightsail instance to the internet or to AWS resources using the public IP address of the instance\. Both data transfer IN to Lightsail instances and data transfer OUT from a Lightsail instance when using the instance's private IP address are free beyond your data transfer allowance\.  
For Lightsail managed databases, only data transfer OUT is counted against your allowance\. If you exceed your data transfer allowance, you will only get charged for data transfer OUT from a Lightsail managed database to the internet\.  
For Lightsail CDN distributions, all data transfer out of your distribution counts toward your allowance\. All data transfer out of your distribution will incur a charge after you exceed your distribution data transfer allowance\.

**How does my data transfer allowance work with my load balancers?**  
Your load balancer does not consume your data transfer allowance\. Traffic between the load balancer and the target instances or distributions is metered and counts toward your data transfer allowance for your instances or distributions, in the same way that traffic in from and out to the internet is counted toward your data transfer allowance for Lightsail instances that are not behind a load balancer\. Traffic into and out of your load balancer to the internet is not calculated toward the data transfer allowance for your instances\.

**What if I exceed my data transfer plan allowance?**  
We have designed our data transfer plans so that the vast majority of our customers will be fully covered by their allowance and not incur any additional charges\. If your instance exceeds its plan data transfer allowance, you will be charged an overage fee per GB of data transfer used \(data transfer OUT to the internet only\)\.  
Even if your instance exceeds its plan data transfer allowance, many types of data transfer are free\. Data transfer IN to Lightsail instances and databases is always free\. Data transfer OUT from a Lightsail instance to another Lightsail instance, in between Lightsail instances and Lightsail managed databases, or to AWS resources in the same Region is also free if private IP addresses are used\.

**What types of data transfer do I get charged for?**  
When you exceed the monthly free data transfer allowance of your instance plan, you will get charged for data transfer OUT from a Lightsail instance to the internet or to another AWS Region or to AWS resources in the same Region when using public IP addresses\. The charge for these types of data transfer above the free allowance is as follows:  
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
• EU \(Stockholm\) \(eu\-north\-1\): $0\.09 USD/GB  
Instances created in different Availability Zones can communicate between zones privately and for free, and are much less likely to be impaired concurrently\. Availability Zones enable you to build highly available applications and websites without increasing the cost of data transfer or compromising your application's security\.  
When you exceed the data transfer allowance of your Lightsail CDN distribution plan, you are charged for all data transfer OUT\. The charge for data transfer above your distribution’s allowance is different from Lightsail instances and is as follows:  
• Asia Pacific: $0\.13 USD/GB  
• Canada: $0\.09 USD/GB  
• Europe: $0\.09 USD/GB  
• India: $0\.13 USD/GB  
• Japan: $0\.14 USD/GB  
• Middle East: $0\.11 USD/GB  
• South Africa: $0\.11 USD/GB  
• South America: $0\.11 USD/GB  
• United States: $0\.09 USD/GB 

**How do my instance data transfer plan allowances vary by AWS Region?**  <a name="lightsail-faq-data-transfer-charges"></a>
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
Every Lightsail instance plan includes a data transfer allowance\. For example, using the $3\.50 USD per month plan, your instance can send to the internet and receive from the internet up to 1 TB of data each month, at no extra charge\. Your data transfer allowance resets every month, and your instance can consume it whenever it needs to within the month\.  
After your instance reaches its data transfer allowance for the month, data transfer out to the internet is billed starting at $0\.09 USD per GB depending on the AWS Region in which your instance is located\. If you delete your instance and create another one in the same month, in the same AWS Region, the free data transfer allowance is shared between the two instances\.

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
To get started, you need to export your manual snapshot of a Lightsail instance or block storage disk\. Customers who are comfortable with Amazon EC2 can then use the Amazon EC2 creation wizard or API to create a new Amazon EC2 instances or Amazon EBS volumes, as they would from an existing EC2 AMI or EBS volume\. Alternatively, Lightsail also provides a guided Lightsail console experience to help you easily create a new EC2 instance\.  
 Snapshots of cPanel & WHM, Django, and Ghost instances cannot be exported to Amazon EC2 at this time\. 

**How am I billed?**  
Using the export to Amazon EC2 feature is free\. Once you have exported your manual snapshots to Amazon EC2, you will be charged for the Amazon EC2 image separately and in addition to your Lightsail manual snapshot\. Any new Amazon EC2 instances you launch will also be billed by Amazon EC2, including their Amazon EBS storage volume\(s\) and data transfer\. Refer to the [Amazon EC2 pricing page](https://aws.amazon.com/ec2/pricing/) for details on the pricing for your new instance and resources\. Lightsail resources that continue to run in your Lightsail account will continue to be billed at their regular rates until they are deleted\.

**Can I export managed databases or disk snapshots?**  
The export feature allows you to export manual Lightsail disk snapshots but doesn't currently support manual snapshots of managed databases\. Disk snapshots can be rehydrated as Amazon EBS volumes from the Amazon EC2 console or API\.

**What Lightsail resources can I export?**  
The Lightsail export to Amazon EC2 feature is designed to support the export of Linux and Windows instance snapshots to Amazon EC2\. It also supports the export of block storage disk snapshots to Amazon EBS\. It does not currently support the export of databases, container services, content delivery network \(CDN\) distributions, load balancers, static IPs, and DNS records\. Additionally, snapshots of Django, Ghost, and cPanel & WHM instances cannot be exported to Amazon EC2 at this time\.

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
• Container services  
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