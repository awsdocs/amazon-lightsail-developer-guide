# Creating Amazon EC2 instances from exported snapshots in Lightsail<a name="amazon-lightsail-creating-ec2-instances-from-exported-snapshots"></a>

 *Last updated: November 28, 2018* 

After a Lightsail instance snapshot is exported and available in Amazon EC2 \(as an AMI and an EBS snapshot\), you can create an Amazon EC2 instance from the snapshot using the **Create an Amazon EC2 instance** page in the Amazon Lightsail console, also known as the Upgrade to Amazon EC2 wizard\. It guides you through the EC2 instance configuration options, such as choosing an EC2 instance type that matches your requirements, configuring your security group ports, adding a launch script, and more\. The wizard in the Lightsail console simplifies the process of creating new EC2 instances and their related resources\.

**Note**  
To create Amazon Elastic Block Store \(Amazon EBS\) volumes from exported block storage disk snapshots, see [Creating Amazon EBS volumes from exported Amazon Lightsail disk snapshots](amazon-lightsail-creating-ebs-volumes-from-exported-snapshots.md)\.

You can also create new EC2 instances using the Lightsail API, AWS CLI, or SDKs\. For more information, see the [CreateCloudFormationStack operation](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateCloudFormationStack.html) in the Lightsail API documentation, or the [create\-cloud\-formation\-stack command](https://docs.aws.amazon.com/cli/latest/reference/lightsail/create-cloud-formation-stack.html) in the AWS CLI documentation\. Or if you're comfortable with Amazon EC2, you can use the EC2 console, Amazon EC2 API, AWS CLI, or SDKs\. For more information, see [Launching an Instance Using the Launch Instance Wizard](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/launching-instance.html) or [Restoring an Amazon EBS Volume from a Snapshot](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-restoring-volume.html) in the Amazon EC2 documentation\.

**Important**  
We recommend getting familiar with the Lightsail export process before completing the steps in this guide\. For more information, see [Exporting Amazon Lightsail snapshots](amazon-lightsail-exporting-snapshots.md)\.

**Contents**
+ [AWS CloudFormation stack for Lightsail](#aws-cloud-formation-stack)
+ [Prerequisites](#creating-ec2-instances-from-exported-snapshots-prerequisites)
+ [Access the Create an Amazon EC2 instance page in the Lightsail console](#access-the-create-an-instance-page)
+ [Create an Amazon EC2 instance](#create-new-instances)
+ [Track the status of your new Amazon EC2 instance](#track-the-status)
+ [Next steps](#creating-ec2-instances-from-exported-snapshots-next-steps)

## AWS CloudFormation stack for Lightsail<a name="aws-cloud-formation-stack"></a>

Lightsail uses an AWS CloudFormation stack to create EC2 instances and their related resources\. For more information about the CloudFormation stacks for Lightsail, see [AWS CloudFormation stacks for Amazon Lightsail](amazon-lightsail-cloudformation-stacks.md)\.

The following additional permissions may need to be configured in IAM depending on the user that will create the EC2 instance using the **Create an Amazon EC2 instance** page:
+ If the [Amazon account root user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html) will create the EC2 instance, then continue to the [Prerequisites section](#creating-ec2-instances-from-exported-snapshots-prerequisites) of this guide\. The root user already has the required permissions to create EC2 instances using Lightsail\.
+ If an IAM user will create the EC2 instance, then an AWS account administrator must add the following permissions to the user\. For more information about how to change permissions for a user, see [Changing Permissions for an IAM User](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_change-permissions.html#users_change_permissions-add-console) in the IAM documentation\.
  + The following permissions are required for users to create Amazon EC2 instances using Lightsail:
**Note**  
These permissions allow the CloudFormation stack to be created\. However, if the creation fails, the rollback process might require more permissions\. Lack of permissions may lead to remaining resources not rolled back in Amazon EC2\. If this happens, you can go to the AWS CloudFormation console and manually delete the EC2 resources\. For more information, see [AWS CloudFormation stacks for Amazon Lightsail](amazon-lightsail-cloudformation-stacks.md)
    + ec2:DescribeAvailabilityZones
    + ec2:DescribeSubnets
    + ec2:DescribeRouteTables
    + ec2:DescribeInternetGateways
    + ec2:DescribeVpcs
    + cloudformation:CreateStack
    + cloudformation:ValidateTemplate
    + iam:CreateServiceLinkedRole
    + iam:PutRolePolicy
  + The following permissions are required if the user will configure ports in the security group for the EC2 instance:
    + ec2:DescribeSecurityGroups
    + ec2:CreateSecurityGroup
    + ec2:AuthorizeSecurityGroupIngress
  + The following permissions are required if the user is creating a Windows Server instance in Amazon EC2:
    + ec2:DescribeKeyPairs
    + ec2:ImportKeyPair
  + The following permissions are required if the user is creating Amazon EC2 instances for the first time, or when the virtual private cloud \(VPC\) fails to configure completely:
    + ec2:AssociateRouteTable
    + ec2:AttachInternetGateway
    + ec2:CreateInternetGateway
    + ec2:CreateRoute
    + ec2:CreateRouteTable
    + ec2:CreateSubnet
    + ec2:CreateVpc
    + ec2:ModifySubnetAttribute
    + ec2:ModifyVpcAttribute

## Prerequisites<a name="creating-ec2-instances-from-exported-snapshots-prerequisites"></a>

Export a Lightsail instance snapshot to Amazon EC2\. For more information, see [Exporting Amazon Lightsail snapshots to Amazon EC2](amazon-lightsail-exporting-snapshots-to-amazon-ec2.md)\.

## Access the Create an Amazon EC2 instance page in the Lightsail console<a name="access-the-create-an-instance-page"></a>

The **Create an Amazon EC2 instance** page in the Lightsail console can be accessed from the task monitor only after an instance snapshot is successfully exported to EC2\.

**To access the Create an Amazon EC2 instance page in the Lightsail console**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. From the top navigation pane, choose the **Task monitor** icon\.

1. Locate the completed instance snapshot export in the **Task history** section, then choose **Create a new Amazon EC2 instance**\.  
![\[Task monitor in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-task-monitor-create-instance.png)

   The **Create an Amazon EC2 instance** page appears\. Continue to the following [Create an Amazon EC2 instance](#create-new-instances) section of this guide to learn how to configure and create an EC2 instance using this page\.

## Create an Amazon EC2 instance<a name="create-new-instances"></a>

Use the **Create an Amazon EC2 instance** page to create an EC2 instance\. To create more than one EC2 instance from an exported Lightsail snapshot, repeat the following steps multiple times but wait until each instance is created before creating the next one\.

**To create an Amazon EC2 instance**

1. On the **Amazon EC2 AMI details** section of the page, confirm that the Amazon Machine Image \(AMI\) details displayed match the specifications of the source Lightsail instance\.  
![\[Amazon EC2 AMI details on the Create an Amazon EC2 instance page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-create-an-ec2-instance-ami-details.png)

1. On the **Resource location** section of the page, change the Availability Zone of your instance if necessary\. The Amazon EC2 resources are created in the same AWS Region as the source Lightsail snapshot\.
**Note**  
Not all Availability Zones may be available for all users\. Choosing an unavailable Availability Zone will result in an error when creating the EC2 instance\.  
![\[Resource location options on the Create an Amazon EC2 instance page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-create-an-ec2-instance-resource-location.png)

1. On the **Compute resource** section of the page, choose one of the following options:  
![\[Compute resource options on the Create an Amazon EC2 instance page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-create-an-ec2-instance-compute-resource.png)

   1. **Find closest match** to automatically select an Amazon EC2 instance type that closely matches the specifications of the source Lightsail instance\.

   1. **Help me choose** to answer a quick questionnaire about the specifications of your new Amazon EC2 instance\. You can select from instance types that are compute optimized, memory optimized, or balanced between the two\.

   1. **Select manually** to view a list of instance types available through the **Create an Amazon EC2 instance** page\.
**Note**  
Some Lightsail instances are incompatible with the current generation EC2 instance types \(T3, M5, C5, or R5\) because they are not enabled for enhanced networking\. If your source Lightsail instance is incompatible, you will need to choose a previous generation instance type \(T2, M4, C4, or R4\) when creating an EC2 instance from your exported snapshot\. These instance type options are presented to you on the **Create an Amazon EC2 instance** page in the Lightsail console\.  
To use the latest generation EC2 instance types when the source Lightsail instance is incompatible, you need to create the new EC2 instance using a previous generation instance type \(T2, M4, C4, or R4\), update the networking driver, and then upgrade the instance to the desired current generation instance type\. For more information, see [Updating Amazon EC2 instances for enhanced networking](amazon-lightsail-updating-ec2-instances.md)\.

1. On the **Optional** section of the page:  
![\[Optional settings on the Create an Amazon EC2 instance page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-create-an-ec2-instance-optional-settings.png)

   1. Choose **Specify port configuration** to select the firewall settings for your Amazon EC2 instance, then choose one of the following options:  
![\[Security group settings on the Create an Amazon EC2 instance page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-create-an-ec2-instance-security-groups.png)

      1. **Use the default firewall settings from the Lightsail image** to configure the default ports from the source Lightsail blueprint on your new EC2 instance\. For more information about the default ports for Lightsail blueprints, see [Firewall and ports in Amazon Lightsail](understanding-firewall-and-port-mappings-in-amazon-lightsail.md)\.

      1. **Use the source Lightsail instance firewall settings** to configures the ports from the source Lightsail instance on your new EC2 instance\. This option is only available when the source Lightsail instance is still active\.

   1. On the **Launch script** section of the page, choose **Add launch script** if you wish to add a script that configures your EC2 instance when it launches\.

1. On the **Connection security** section of the page, determine how you connected to the source Lightsail instance\. This ensures that you get the correct SSH key to connect to your new EC2 instance\. You may have connected to the source Lightsail instance using one of the following methods:

   1. **Using the default Lightsail key pair for the source instance’s region** — Download and use the unique default Lightsail key for that AWS Region to connect to your EC2 instance\.
**Note**  
The default Lightsail key pair is always used on Windows Server instances in Lightsail\.

   1. **Using your own key pair** — Locate the private key and use it to connect to your EC2 instance\.
**Note**  
Lightsail does not store your personal private keys\. Therefore; the option to download your private key is not provided\. If you are unable to locate your private key, then you will not be able to connect to your EC2 instance\.

1. On the **Storage resources** section of the page, confirm that the EBS volumes being created match the system disk and any attached block storage disks for the source Lightsail instance\.  
![\[Storage resources on the Create an Amazon EC2 instance page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-create-an-ec2-instance-storage-resources.png)

1. Review the important details about creating resources outside of Lightsail\.

1. If you agree to create the instance in Amazon EC2, choose **Create resources in EC2**\.

   Lightsail confirms that your instance is being created, and information about the AWS CloudFormation stack is displayed\. Lightsail uses a CloudFormation stack to create the EC2 instance and its related resources\. For more information, see [AWS CloudFormation stacks for Amazon Lightsail](amazon-lightsail-cloudformation-stacks.md)\.

   Continue to the [Track the status of your new Amazon EC2 instance](#track-the-status) section of this guide to track the status of your new EC2 instance\.
**Important**  
Wait until after your new EC2 instance is created to create another EC2 instance from the same exported snapshot\.

## Track the status of your new Amazon EC2 instance<a name="track-the-status"></a>

Use the task monitor in the Lightsail console to track the status of your new EC2 instance\. It can be accessed from the top navigation pane on all pages of the Lightsail console\. For more information, see [Task monitor in Amazon Lightsail](amazon-lightsail-task-monitor.md#amazon-lightsail-task-monitor.title)\.

The following information is displayed in the task monitor for EC2 instances being created:

![\[Task monitor in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-task-monitor-create-details.png)
+ **Source name** — The name of the source Lightsail snapshot\.
+ **Started** — The date and time that the create request was started\.

The following information is displayed in the task monitor for EC2 instances that have been created:
+ **Created** is displayed if the Amazon EC2 resources were successfully created\. Continue to the [Next steps](#creating-ec2-instances-from-exported-snapshots-next-steps) section of this guide for the next steps after your new EC2 instance is ready\.
+ **Failed** is displayed if there was a problem creating EC2 instance\.

## Next steps<a name="creating-ec2-instances-from-exported-snapshots-next-steps"></a>

Here are a few additional steps you can perform after creating an Amazon EC2 instance:
+ You can connect to Amazon EC2 instances similar to how you connect to Lightsail instances\. This means using SSH for Linux and Unix instances and RDP for Windows Server instances\. However, the browser\-based SSH/RDP client that you might have used in the Lightsail console might not be available in Amazon EC2 depending on the browser version that you're using, so you might need to configure your own SSH/RDP client to connect to your EC2 instances\. For more information, see the following guides:
  + [Connecting to a Linux or Unix instance in Amazon EC2 created from an Amazon Lightsail snapshot](amazon-lightsail-connecting-to-linux-unix-amazon-ec2-instances.md)
  + [Connecting to a Windows Server instance in Amazon EC2 created from an Amazon Lightsail snapshot](amazon-lightsail-connecting-to-windows-server-amazon-ec2-instances.md)
+ Linux or Unix instances in Amazon EC2 created from Lightsail snapshots may contain residual SSH keys from Lightsail\. We recommend removing these keys to better secure your EC2 instance\. For more information, see [Securing a Linux or Unix instance in Amazon EC2 created from an Amazon Lightsail snapshot](amazon-lightsail-securing-linux-unix-amazon-ec2-instances.md)\.

After your EC2 instance is created, you might need to perform a few more steps so that it's configured the same way as the source Lightsail instance\. Here are a few additional steps to configure your EC2 instance:
+ Configure the firewall settings by editing the security group for your Amazon EC2 instance\. For more information, see [Amazon EC2 Security Groups for Linux Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html) or [Amazon EC2 Security Groups for Windows Instances](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/using-network-security.html) in the Amazon EC2 documentation\.
+ If you created a Lightsail static IP, and attached it to your Lightsail instance, then you should create and attach an Elastic IP to your Amazon EC2 instance\. For more information, see [Elastic IP Addresses](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html) in the Amazon EC2 documentation\.
+ If you created a Lightsail DNS zone, and configured a domain for your Lightsail instance, then you should create an Amazon Route 53 DNS zone, use it to manage your domain's DNS, and point your domain to your new Amazon EC2 instance\. For more information, see [Configuring Amazon Route 53 as Your DNS Service and Making Amazon Route 53 the DNS Service for an Existing Domain](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-configuring.html) in the Amazon Route 53 documentation\.
+ If you created a Lightsail load balancer, and configured it for your Lightsail instances, then you should configure an Application Load Balancer for your Amazon EC2 instances\. For more information, see [Getting Started with Application Load Balancers](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/application-load-balancer-getting-started.html) in the Elastic Load Balancing documentation\.
+ Lightsail databases cannot be accessed by Amazon EC2 instances\. If the Lightsail instance you exported to Amazon EC2 is connected to a Lightsail database; then you will need to manually migrate that database to Amazon Relational Database Service \(Amazon RDS\) to access its data from the new Amazon EC2 instance\. For more information, see [Importing Data to an Amazon RDS MySQL or MariaDB DB Instance with Reduced Downtime](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/MySQL.Procedural.Importing.NonRDSRepl.html) and [Connecting to an Amazon RDS DB Instance](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_CommonTasks.Connect.html)\.