# Exporting Amazon Lightsail snapshots to Amazon EC2<a name="amazon-lightsail-exporting-snapshots-to-amazon-ec2"></a>

 *Last updated: November 28, 2018* 

You can export Amazon Lightsail instance and block storage disk snapshots to Amazon Elastic Compute Cloud \(Amazon EC2\)\. Exporting a Lightsail instance snapshot results in an Amazon Machine Image \(AMI\) and an Amazon Elastic Block Store \(Amazon EBS\) snapshot being created in Amazon EC2\. This is because Lightsail instances are comprised of an image and a system disk, but both are grouped together as a single instance entity in the Lightsail console to make them more efficient to manage\. If the source Lightsail instance has one or more block storage disks attached to it when the snapshot is created, then additional EBS snapshots for each attached disk are created in Amazon EC2\.

Exporting a Lightsail block storage disk snapshot results in a single EBS snapshot being created in Amazon EC2\. All exported resources in Amazon EC2 have their own distinct unique identifiers that are different than their Lightsail counterparts\.

This guide describes how to export a Lightsail snapshot, track the status of your export, and the next steps after the exported snapshot is available in Amazon EC2 \(as an AMI, EBS snapshot, or both\)\.

**Important**  
We recommend getting familiar with the Lightsail export process before completing the steps in this guide\. For more information, see [Exporting Amazon Lightsail snapshots](amazon-lightsail-exporting-snapshots.md)\.

**Contents**
+ [Service\-linked role and required IAM permissions to export Lightsail snapshots](#service-linked-role-details)
+ [Prerequisites](#exporting-snapshots-to-amazon-ec2-prerequisites)
+ [Export a Lightsail snapshot to Amazon EC2](#exporting-a-lightsail-snapshot)
+ [Track the status of your export](#track-the-status-of-your-export)

## Service\-linked role and required IAM permissions to export Lightsail snapshots<a name="service-linked-role-details"></a>

Lightsail uses an AWS Identity and Access Management \(IAM\) service\-linked role \(SLR\) to export snapshots to Amazon EC2\. For more information about SLRs, see [Using service\-linked roles for Amazon Lightsail](amazon-lightsail-using-service-linked-roles.md)\.

The following additional permissions may need to be configured in IAM depending on the user that will perform the snapshot export:
+ If the [Amazon account root user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html) will perform the export, then continue to the [Prerequisites section](#exporting-snapshots-to-amazon-ec2-prerequisites) of this guide\. The account root user already has the required permissions to perform the snapshot export\.
+ If an IAM user will perform the export, then an AWS account administrator must add the following policy to the user\. For more information about how to change permissions for a user, see [Changing Permissions for an IAM User](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_change-permissions.html#users_change_permissions-add-console) in the IAM documentation\.

  ```
  {
      "Version": "2012-10-17",
      "Statement": [
          {
              "Effect": "Allow",
              "Action": "iam:CreateServiceLinkedRole",
              "Resource": "arn:aws:iam::*:role/aws-service-role/lightsail.amazonaws.com/AWSServiceRoleForLightsail*",
              "Condition": {"StringLike": {"iam:AWSServiceName": "lightsail.amazonaws.com"}}
          },
          {
              "Effect": "Allow",
              "Action": "iam:PutRolePolicy",
              "Resource": "arn:aws:iam::*:role/aws-service-role/lightsail.amazonaws.com/AWSServiceRoleForLightsail*"
          }
      ]
  }
  ```

## Prerequisites<a name="exporting-snapshots-to-amazon-ec2-prerequisites"></a>

Create a snapshot of the Lightsail instance or block storage disk that you want to export to Amazon EC2\. For more information, see one of the following guides:
+ [Creating a snapshot of your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md)
+ [Creating a snapshot of your Windows Server instance in Amazon Lightsail](prepare-windows-based-instance-and-create-snapshot.md)
+ [Creating a snapshot of your block storage disk in Amazon Lightsail](create-block-storage-disk-snapshot.md)

## Export a Lightsail snapshot to Amazon EC2<a name="exporting-a-lightsail-snapshot"></a>

The most efficient way to export a snapshot to Amazon EC2 is by using the Lightsail console\. You can also export snapshots using the Lightsail API, AWS Command Line Interface \(AWS CLI\), or SDKs\. For more information, see the [ExportSnapshot operation](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_ExportSnapshot.html) in the Lightsail API documentation, or the [export\-snapshot command](https://docs.aws.amazon.com/cli/latest/reference/lightsail/export-snapshot.html) in the AWS CLI documentation\.

**Note**  
Snapshots are exported to the same AWS Region from Lightsail to Amazon EC2\. To export snapshots to a different Region, first copy the snapshot to a different Region in Lightsail, then perform the export\. For more information, see [Copying snapshots from one AWS Region to another in Amazon Lightsail](amazon-lightsail-copying-snapshots-from-one-region-to-another.md)\.

**To export a Lightsail snapshot to Amazon EC2**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Snapshots** tab\.

1. Locate the instance or block storage disk that you want to export, and expand the node to view the available snapshots for that resource\. 

1. Choose the **Action** menu for the desired snapshot, then choose **Export to Amazon EC2**\.  
![\[Export snapshot in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-action-menu-export-snapshot.png)
**Note**  
Snapshots of Ghost and Django instances cannot be exported to Amazon EC2 at this time\.

1. Review the important details displayed on the prompt\.

1. If you agree to export to Amazon EC2, choose **Yes, continue** to begin the process\.

   The export process can take a while\. It depends on the size and configuration of the source instance or block storage disk\. Continue to the [Track the status of your export](#track-the-status-of-your-export) section of this guide to track the status of your export\.

## Track the status of your export<a name="track-the-status-of-your-export"></a>

Use the task monitor in the Lightsail console to track the status of your export\. It can be accessed from the top navigation pane on all pages of the Lightsail console\. For more information, see [Task monitor in Amazon Lightsail](amazon-lightsail-task-monitor.md#amazon-lightsail-task-monitor.title)\.

The following information is displayed in the task monitor for snapshot exports:

![\[The task monitor in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-task-monitor-export-snapshot.png)
+ **Snapshot name** — The name of the source Lightsail snapshot\.
+ **Export started** — The date and time the snapshot export was started\.
+ **Snapshot created** — The date and time the source Lightsail snapshot was created\.
+ **Source specs** — The specifications of the source Lightsail instance, such as the memory, processing, and storage\.
+ **Snapshot type** — The type of the Lightsail snapshot\. It’s either an instance snapshot or disk snapshot\.

The following information is displayed in the task monitor for completed snapshot exports:
+ **Exported** is displayed if the snapshot was successfully exported to Amazon EC2\.
+ **Failed** is displayed if there was a problem exporting the snapshot\.

If the snapshot was successfully exported, then the task monitor displays the following options for the completed export:
+ **Create a new Amazon EC2 instance** — Choose this option to create a new instance in Amazon EC2 using the Lightsail console\. For more information, see [Creating Amazon EC2 instances from exported snapshots in Amazon Lightsail](amazon-lightsail-creating-ec2-instances-from-exported-snapshots.md)\.
+ **Open the Amazon EC2 console** — Choose this option to use the Amazon EC2 console to create new EC2 resources from your exported snapshot\. If you exported a Lightsail block storage disk snapshot, then you must use Amazon EC2 to create an EBS volume from the snapshot \(an EBS snapshot\)\. For more information, see [Launching an Instance Using the Launch Instance Wizard](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/launching-instance.html) or [Restoring an Amazon EBS Volume from a Snapshot](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-restoring-volume.html) in the Amazon EC2 documentation\.

**Note**  
Delete the source Lightsail snapshot if you no longer need it\. Otherwise, you will be billed for storing it\.