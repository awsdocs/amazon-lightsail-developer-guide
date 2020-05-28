# Creating Amazon EBS volumes from exported Amazon Lightsail disk snapshots<a name="amazon-lightsail-creating-ebs-volumes-from-exported-snapshots"></a>

 *Last updated: November 28, 2018* 

After a Lightsail block storage disk snapshot is exported and available in Amazon EC2 \(as an EBS snapshot\), you can create an EBS volume from the snapshot using the Amazon EC2 console\.

**Note**  
To create EC2 instances from exported instance snapshots, see [Creating Amazon EC2 instances from exported snapshots in Lightsail](amazon-lightsail-creating-ec2-instances-from-exported-snapshots.md#amazon-lightsail-creating-ec2-instances-from-exported-snapshots.title)\.

You can also create new EBS volumes using the Amazon EC2 API, AWS CLI, or SDKs\. For more information, see [Launching an Instance Using the Launch Instance Wizard](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/launching-instance.html) or [Restoring an Amazon EBS Volume from a Snapshot](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-restoring-volume.html) in the Amazon EC2 documentation\.

**Important**  
We recommend getting familiar with the Lightsail export process before completing the steps in this guide\. For more information, see [Exporting Amazon Lightsail snapshots](amazon-lightsail-exporting-snapshots.md)\.

## Prerequisites<a name="creating-ebs-volumes-from-exported-snapshots-prerequisites"></a>

Export a Lightsail block storage disk snapshot to Amazon EC2\. For more information, see [Exporting Amazon Lightsail snapshots to Amazon EC2](amazon-lightsail-exporting-snapshots-to-amazon-ec2.md)\.

## Create an EBS volume from an exported Lightsail block storage disk snapshot<a name="create-an-ebs-volume-from-exported-snapshot"></a>

Use the Amazon EC2 console to create a new EBS volume from an exported Lightsail block storage disk snapshot\.

**Note**  
These steps are also in the Amazon EC2 documentation\. To learn more, see [Restoring an Amazon EBS Volume from a Snapshot](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-restoring-volume.html) in the Amazon EC2 documentation\.

**To create an EBS volume from an exported Lightsail block storage disk snapshot**

1. Sign in to the [Amazon EC2 console](https://console.aws.amazon.com/ec2/)\.

1. From the navigation bar, select the region that your snapshot is located in\.

1. In the navigation pane, choose **Elastic Block Store**, and then choose **Snapshots**\.

1. Locate and select the exported Lightsail block storage disk snapshot\.

   Exported disk snapshot can be identified by the *A disk snapshot exported from Amazon Lightsail* description of the EBS snapshot as shown in the following screenshot:  
![\[EBS snapshots in the Amazon EC2 console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ec2-console-ebs-snapshots.png)

1. Choose **Actions**, then choose **Create Volume**\.

1. Choose a volume type from the **Volume Type** drop\-down menu\. For more information, see [Amazon EBS Volume Types](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSVolumeTypes.html) in the Amazon EC2 documentation\.

1. For **Size \(GiB\)**, type the size of the volume, or verify that the default size of the snapshot is adequate\.

1. With a Provisioned IOPS SSD volume, for **IOPS**, type the maximum number of input/output operations per second \(IOPS\) that the volume should support\.

1. For **Availability Zone**, choose the Availability Zone in which to create the volume\. EBS volumes can only be attached to EC2 instances in the same Availability Zone\.

1. \(Optional\) Choose **Create additional tags** to add tags to the volume\. For each tag, provide a tag key and a tag value\.

1. Choose **Create Volume**\. After your volume is created, it is listed in the **Elastic Block Store > Volumes** section of the Amazon EC2 console\.

## Next steps<a name="creating-ebs-volumes-from-exported-snapshots-next-steps"></a>

Here are a few additional steps you can perform after creating a new Amazon EC2 instance:
+ After you've restored a volume from a snapshot, you can attach it to an instance to begin using it\. For more information, see [Attaching an Amazon EBS Volume to an Instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-attaching-volume.html) in the Amazon EC2 documentation\.
+ If you restored a snapshot to a larger volume than the default for that snapshot, you must extend the file system on the volume to take advantage of the extra space\. For more information, see [Modifying the Size, IOPS, or Type of an EBS Volume on Linux](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-modify-volume.html) in the Amazon EC2 documentation\.