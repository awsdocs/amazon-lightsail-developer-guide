# Using Amazon Lightsail with other AWS services<a name="using-lightsail-with-other-aws-services"></a>

 *Last updated: March 24, 2017* 

Amazon Lightsail uses a focused set of AWS services like Amazon EC2 and AWS Identity and Access Management to make it easier to get started\. But that doesn't mean you're limited to those services\!

You can integrate Lightsail resources with other AWS services through Amazon VPC peering\. [Learn how to set up VPC peering in Lightsail](lightsail-how-to-set-up-vpc-peering-with-aws-resources.md)\.

Follow the links below to learn more about other AWS services\.

## Virtual machines \(virtual private servers\)<a name="virtual-machines-virtual-private-servers"></a>

**Amazon EC2**  
Amazon Elastic Compute Cloud \(Amazon EC2\) is a web service that provides resizable compute capacity in the cloud\. It's designed to make web\-scale cloud computing easier for developers\.  
The simple web service interface of Amazon EC2 enables you to obtain and configure capacity with minimal friction\. It provides you with complete control of your computing resources and lets you run on Amazon’s proven computing environment\. Amazon EC2 reduces the time required to obtain and boot new server instances to minutes, so you can quickly scale capacity, both up and down, as your computing requirements change\. Amazon EC2 changes the economics of computing by enabling you to pay only for capacity that you actually use\. Amazon EC2 provides developers with tools to build failure resilient applications and isolate themselves from common failure scenarios\.  
[Learn more about Amazon EC2](https://aws.amazon.com/ec2/)\.

**Amazon VPC**  
Amazon Virtual Private Cloud \(Amazon VPC\) lets you provision a logically isolated section of the AWS Cloud, where you can launch AWS resources in a virtual network that you define\. You have complete control over your virtual networking environment, including selection of your own IP address range, creation of subnets, and configuration of route tables and network gateways\.  
You can easily customize the network configuration for your Amazon VPC\. For example, you can create a public\-facing subnet for your web servers that has access to the Internet, and place your backend systems such as databases or application servers in a private\-facing subnet with no Internet access\. You can leverage multiple layers of security, including security groups and network access control lists, to help control access to Amazon EC2 instances in each subnet\.  
Additionally, you can create a Hardware Virtual Private Network \(VPN\) connection between your corporate datacenter and your VPC and leverage the AWS Cloud as an extension of your corporate datacenter\.  
[Learn more about Amazon VPC](https://aws.amazon.com/vpc/)\.

## Serverless computing<a name="serverless-lambda"></a>

**AWS Lambda**  
AWS Lambda lets you run code without provisioning or managing servers\. You pay only for the compute time you consume \- there is no charge when your code isn't running\. With Lambda, you can run code for virtually any type of application or backend service \- all with zero administration\. Just upload your code and Lambda takes care of everything required to run and scale your code with high availability\. You can set up your code to automatically trigger from other AWS services or call it directly from any web or mobile app\.  
[Learn more about AWS Lambda](https://aws.amazon.com/lambda/)\.

**Amazon API Gateway**  
Amazon API Gateway is a fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale\. With a few clicks in the AWS Management Console, you can create an API that acts as a "front door" for applications to access data, business logic, or functionality from your backend services\. These include workloads running on Amazon EC2, code running on Lambda, or any Web application\. Amazon API Gateway handles all the tasks involved in accepting and processing up to hundreds of thousands of concurrent API calls\. These include traffic management, authorization and access control, monitoring, and API version management\. Amazon API Gateway has no minimum fees or startup costs\. You pay only for the API calls you receive and the amount of data transferred out\.  
[Learn more about Amazon API Gateway](https://aws.amazon.com/api-gateway/)\.

## Databases<a name="databases"></a>

**Amazon DynamoDB**  
Amazon DynamoDB is a fast and flexible NoSQL database service for all applications that need consistent, single\-digit millisecond latency at any scale\. It's a fully managed cloud database and supports both document and key\-value store models\. Its flexible data model and reliable performance make it a great fit for mobile, web, gaming, ad tech, IoT, and many other applications\.  
[Learn more about DynamoDB](https://aws.amazon.com/dynamodb/)\.

**Amazon RDS**  
Amazon Relational Database Service \(Amazon RDS\) makes it easy to set up, operate, and scale a relational database in the cloud\. It provides cost\-efficient and resizable capacity while managing time\-consuming database administration tasks, freeing you to focus on your applications and business\. Amazon RDS provides you six familiar database engines to choose from, including Amazon Aurora, PostgreSQL, MySQL, MariaDB, Oracle, and Microsoft SQL Server\.  
[Learn more about Amazon RDS](https://aws.amazon.com/rds/)\.

**Amazon Aurora**  
Amazon Aurora is a MySQL\-compatible relational database engine that combines the speed and availability of high\-end commercial databases with the simplicity and cost\-effectiveness of open source databases\. Aurora provides up to five times better performance than MySQL with the security, availability, and reliability of a commercial database at one tenth the cost\.  
[Learn more about Amazon Aurora](https://aws.amazon.com/rds/aurora/)\.

## Load balancers<a name="load-balancers"></a>

**Elastic Load Balancing**  
Elastic Load Balancing automatically distributes incoming application traffic across multiple Amazon EC2 instances\. It enables you to achieve fault tolerance in your applications, seamlessly providing the required amount of load balancing capacity needed to route application traffic\.  
Elastic Load Balancing offers two types of load balancers\. Both feature high availability, automatic scaling, and robust security\. These include the Classic Load Balancer that routes traffic based on either application or network\-level information, and the Application Load Balancer that routes traffic based on advanced application\-level information that includes the content of the request\. The Classic Load Balancer is ideal for simple load balancing of traffic across multiple Amazon EC2 instances\. The Application Load Balancer is ideal for applications needing advanced routing capabilities, microservices, and container\-based architectures\. Application Load Balancer offers the ability to route traffic to multiple services or to load balance across multiple ports on the same Amazon EC2 instance\.   
[Learn more about Elastic Load Balancing](https://aws.amazon.com/elasticloadbalancing/)\.

**Application Load Balancer**  
An Application Load Balancer is a load balancing option for the Elastic Load Balancing service that operates at the application layer and allows you to define routing rules based on content across multiple services or containers running on one or more Amazon EC2 instances\.  
[Learn more about Application Load Balancer](https://aws.amazon.com/elasticloadbalancing/applicationloadbalancer/)\.

## Big data<a name="big-data"></a>

**Amazon Kinesis services**  
 Amazon Kinesis services make it easy to work with real\-time streaming data in the AWS cloud\. Amazon Kinesis services include the following: [Amazon Kinesis Data Firehose](https://aws.amazon.com/kinesis/firehose/) to easily load massive volumes of streaming data into AWS, [Amazon Kinesis Data Analytics](https://aws.amazon.com/kinesis/analytics/) to analyze streaming data with standard SQL, and [Amazon Kinesis Data Streams](https://aws.amazon.com/kinesis/streams/) to build your own custom applications that process or analyze streaming data\.   
[Learn more about Amazon Kinesis services](https://aws.amazon.com/kinesis/)\.

**Amazon EMR**  
Amazon EMR provides a managed Hadoop framework that makes it easy, fast, and cost\-effective to process vast amounts of data across dynamically scalable Amazon EC2 instances\. You can also run other popular distributed frameworks such as Apache Spark, HBase, Presto, and Flink in Amazon EMR, and interact with data in other AWS data stores such as Amazon S3 and DynamoDB\.  
Amazon EMR securely and reliably handles a broad set of big data use cases, including log analysis, web indexing, data transformations \(ETL\), machine learning, financial analysis, scientific simulation, and bioinformatics\.  
[Learn more about Amazon EMR](https://aws.amazon.com/emr/)\.

**Amazon Redshift**  
Amazon Redshift is a fast, fully managed, petabyte\-scale data warehouse that makes it simple and cost\-effective to analyze all your data using your existing business intelligence tools\.  
[Learn more about Amazon Redshift](https://aws.amazon.com/redshift/)\.

## Storage<a name="storage"></a>

**Amazon Simple Storage Service \(Amazon S3\)**  
Amazon S3, provides developers and IT teams with secure, durable, highly scalable cloud storage\. Amazon S3 is easy\-to\-use object storage, with a simple web service interface to store and retrieve any amount of data from anywhere on the web\. With Amazon S3, you pay only for the storage you actually use\. There's no minimum fee and no setup cost\.  
Amazon S3 offers a range of storage classes designed for different use cases including Amazon S3 Standard for general\-purpose storage of frequently accessed data, Amazon S3 Standard \- Infrequent Access \(Standard \- IA\) for long\-lived, but less frequently accessed data, and S3 Glacier for long\-term archive\. Amazon S3 also offers configurable lifecycle policies for managing your data throughout its lifecycle\. Once a policy is set, your data automatically migrates to the most appropriate storage class without any changes to your applications\.  
Amazon S3 can be used alone or together with other AWS services such as Amazon EC2 and IAM, as well as cloud data migration services and gateways for initial or ongoing data ingestion\. Amazon S3 provides cost\-effective object storage for a wide variety of use cases including backup and recovery, nearline archive, big data analytics, disaster recovery, cloud applications, and content distribution\.  
[Learn more about Amazon S3](https://aws.amazon.com/s3/)\.

**Amazon Elastic Block Store \(Amazon EBS\)**  
Amazon EBS provides persistent block storage volumes for use with Amazon EC2 instances in the AWS Cloud\. Each Amazon EBS volume is automatically replicated within its Availability Zone to protect you from component failure, offering high availability and durability\. Amazon EBS volumes offer the consistent and low\-latency performance needed to run your workloads\. With Amazon EBS, you can scale your usage up or down within minutes – all while paying a low price for only what you provision\.  
[Learn more about Amazon EBS](https://aws.amazon.com/ebs/)\.

## Monitoring and alarms<a name="monitoring-and-alarms"></a>

**Amazon CloudWatch**  
Amazon CloudWatch is a monitoring service for AWS Cloud resources and the applications you run on AWS\. You can use CloudWatch to collect and track metrics, collect and monitor log files, set alarms, and automatically react to changes in your AWS resources\. CloudWatch can monitor AWS resources such as Amazon EC2 instances, Amazon DynamoDB tables, and Amazon RDS DB instances, as well as custom metrics generated by your applications and services, and any log files your applications generate\. You can use CloudWatch to gain system\-wide visibility into resource utilization, application performance, and operational health\. You can use these insights to react and keep your application running smoothly\.  
[Learn more about Amazon CloudWatch](https://aws.amazon.com/cloudwatch/)\.

## Application deployment<a name="application-deployment"></a>

**AWS Elastic Beanstalk**  
AWS Elastic Beanstalk is an easy\-to\-use service for deploying and scaling web applications and services developed with Java, \.NET, PHP, Node\.js, Python, Ruby, Go, and Docker on familiar servers such as Apache, Nginx, Passenger, and IIS\.  
You can simply upload your code and Elastic Beanstalk automatically handles the deployment, from capacity provisioning, load balancing, and auto\-scaling to application health monitoring\. At the same time, you retain full control over the AWS resources powering your application and can access the underlying resources at any time\.  
[Learn more about Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk/)\.

## Application containers<a name="application-containers"></a>

**Amazon Elastic Container Service \(Amazon ECS\)**  
Amazon ECS is a highly scalable, high\-performance container management service that supports Docker containers and enables you to easily run applications on a managed cluster of Amazon EC2 instances\. Amazon ECS eliminates the need for you to install, operate, and scale your own cluster management infrastructure\. With simple API calls, you can launch and stop Docker\-enabled applications, query the complete state of your cluster, and access many familiar features like security groups, Elastic Load Balancing, Amazon EBS volumes, and IAM roles\. You can use Amazon ECS to schedule the placement of containers across your cluster based on your resource needs and availability requirements\. You can also integrate your own scheduler or third\-party schedulers to meet business or application\-specific requirements\.  
[Learn more about Amazon ECS](https://aws.amazon.com/ecs/)\.

## Security and User Sign\-in<a name="security-and-user-sign-in"></a>

**AWS Identity and Access Management \(IAM\)**  
IAM lets you securely control access to AWS services and resources for your users\. Using IAM, you can create and manage AWS users and groups and use permissions to allow and deny their access to AWS resources\.  
[Learn more about IAM](https://aws.amazon.com/iam/)\.

**Amazon Cognito User Pools**  
Amazon Cognito lets you easily add user sign\-up and sign\-in to your mobile and web apps\. With Amazon Cognito, you also have the options to authenticate users through social identity providers such as Facebook, Twitter, or Amazon, with SAML identity solutions, or by using your own identity system\. In addition, Amazon Cognito enables you to save data locally on users' devices, allowing your applications to work even when the devices are offline\. You can then synchronize data across users' devices so that their app experience remains consistent, regardless of the device they use\.  
With Amazon Cognito, you can focus on creating great app experiences instead of worrying about building, securing, and scaling a solution to handle user management, authentication, and sync across devices\.  
[Learn more about Amazon Cognito](https://aws.amazon.com/cognito/)\.

## Source Control and Application Lifecycle Management<a name="source-control"></a>

**AWS CodeCommit**  
AWS CodeCommit is a fully managed source control service that makes it easy for companies to host secure and highly scalable private Git repositories\. AWS CodeCommit eliminates the need to operate your own source control system or worry about scaling its infrastructure\. You can use AWS CodeCommit to securely store anything from source code to binaries, and it works seamlessly with your existing Git tools\.  
[Learn more about AWS CodeCommit](https://aws.amazon.com/codecommit/)\.

## Queues and Messaging<a name="queues-and-messaging"></a>

**Amazon SQS**  
Amazon Simple Queue Service \(Amazon SQS\) is a fast, reliable, scalable, fully managed message queuing service\. Amazon SQS makes it simple and cost\-effective to decouple the components of a cloud application\. You can use Amazon SQS to transmit any volume of data, without losing messages or requiring other services to be always available\. Amazon SQS includes *standard queues* with high throughput and at\-least\-once processing, and *FIFO queues* that provide FIFO \(first\-in, first\-out\) delivery and exactly\-once processing\.   
With Amazon SQS, you can offload the administrative burden of operating and scaling a highly available messaging cluster, while paying a low price for only what you use\.  
[Learn more about Amazon SQS](https://aws.amazon.com/sqs/)\.

**Amazon SNS**  
Amazon Simple Notification Service \(Amazon SNS\) is a fast, flexible, fully managed push notification service that lets you send individual messages or to fan out messages to large numbers of recipients\. Amazon SNS makes it simple and cost\-effective to send push notifications to mobile device users or email recipients, or even to send messages to other distributed services\.   
With Amazon SNS, you can send notifications to Apple Push Notification Service \(APNS\), Google Cloud Messaging \(GCM\), Fire OS, and Windows devices, as well as to Android devices in China with Baidu Cloud Push\. You can use Amazon SNS to send SMS messages to mobile device users worldwide\.  
Beyond these endpoints, Amazon SNS can also deliver messages to Amazon SQS, AWS Lambda functions, or to any HTTP endpoint\.  
[Learn more about Amazon SNS](https://aws.amazon.com/sns/)\.

**Amazon SES**  
Amazon Simple Email Service \(Amazon SES\) is a cost\-effective email service built on the reliable and scalable infrastructure that Amazon\.com developed to serve its own customer base\. With Amazon SES, you can send and receive email with no required minimum commitments\. You pay as you go, and you only pay for what you use\.  
[Learn more about Amazon SES](https://aws.amazon.com/ses/)\.

## Workflow<a name="simple-workflow-service"></a>

**Amazon Simple Workflow Service \(Amazon SWF\)**  
Amazon SWF helps developers build, run, and scale background jobs that have parallel or sequential steps\. You can think of Amazon SWF as a fully managed state tracker and task coordinator in the cloud\.  
If your app's steps take more than 500 milliseconds to complete, you need to track the state of processing, and you need to recover or retry if a task fails\. Amazon SWF can help you\.  
[Learn more about Amazon SWF](https://aws.amazon.com/swf/)\.

## Streaming applications<a name="streaming-applications"></a>

**Amazon AppStream**  
Amazon AppStream lets you deliver your Windows applications to any device\.  
Amazon AppStream enables you to stream your existing Windows applications from the cloud, reaching more users on more devices, without code modifications\. With Amazon AppStream, your application is deployed and rendered on AWS infrastructure and the output is streamed to mass\-market devices, such as personal computers, tablets, and mobile phones\. Because your application is running in the cloud, it can scale to handle vast computational and storage needs, regardless of the devices your customers are using\. Amazon AppStream provides an SDK for streaming your application from the cloud\. You can integrate your own custom clients, subscriptions, identity, and storage solution with Amazon AppStream to build a custom streaming solution that meets the needs of your business\.  
[Learn more about Amazon AppStream](https://aws.amazon.com/appstream/)\.