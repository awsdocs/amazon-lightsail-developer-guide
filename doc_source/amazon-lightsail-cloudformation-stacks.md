# AWS CloudFormation stacks for Amazon Lightsail<a name="amazon-lightsail-cloudformation-stacks"></a>

 *Last updated: November 28, 2018* 

Amazon Lightsail uses AWS CloudFormation to create Amazon Elastic Compute Cloud \(Amazon EC2\) instances from exported snapshots\. A CloudFormation stack is created when you request to create an Amazon EC2 instance using the Lightsail console or Lightsail API\. The stack performs a series of actions in your Amazon Web Services \(AWS\) account to create all of the related resources for the instance, such as the Amazon EC2 instance from an Amazon Machine Image \(AMI\), the Elastic Block Store \(EBS\) system volume from an EBS snapshot, and the security group for the instance\. To learn more about AWS CloudFormation stacks, see [Working with Stacks](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacks.html) in the AWS CloudFormation documentation\.

You can access the AWS CloudFormation stacks through the Lightsail console or in the AWS CloudFormation console\. This guide shows you how to access both\.

**Note**  
The AWS CloudFormation stack used to create your Amazon EC2 resources is permanently linked to your Amazon EC2 resources\. If you delete the stack, then all related resources are automatically deleted\. Because of this, you should not delete any of the AWS CloudFormation stacks created by Lightsail, and instead delete your Amazon EC2 resources using the EC2 console\.

## Accessing the AWS CloudFormation stacks through the Lightsail console<a name="accessing-the-cloud-formation-stack"></a>

After you choose to create an instance in Amazon EC2 using the Lightsail console or the Lightsail API, an AWS CloudFormation stack is created and its status is tracked using the task monitor\. To learn more about the task monitor, see [Task monitor in Amazon Lightsail](amazon-lightsail-task-monitor.md)\.

**To view your AWS CloudFormation stacks in the Lightsail console**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Choose the task monitor in the top navigation pane\.

1. To access a CloudFormation stack for a previously created Amazon EC2 instance, choose **View details** for a task labeled with **Creating resources in Amazon EC2** or **Created resources in Amazon EC2**\.  
![\[The task monitor in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-task-manager-cloud-formation-stack.png)

1. The confirmation page that appears lists the CloudFormation stack for the task\. Choose the stack name to open the stack details in the AWS CloudFormation console\.  
![\[AWS CloudFormation stack details in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-console-cloud-formation-stack.png)

## Accessing the stacks in the AWS CloudFormation console<a name="accessing-the-stacks-in-the-cloud-formation-console"></a>

You can also access your stack details through the [AWS CloudFormation console](https://console.aws.amazon.com/cloudformation)\. The stacks created by Lightsail begin with “Lightsail\-stack” and have a description of “CloudFormation stack used to create Amazon EC2 resources” as shown in the following screenshot\.

Stacks with a **CREATE\_IN\_PROGRESS** status are in the process of creating Amazon EC2 resources from your exported Lightsail snapshots\. Stacks with a **CREATE\_COMPLETED** status have completed the process of creating Amazon EC2 resources\. To view the resources created by a stack, choose the checkbox next to the stack name, and then choose the **Resources** tab\.

![\[AWS CloudFormation stack details.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-cloud-formation-stack-details.png)