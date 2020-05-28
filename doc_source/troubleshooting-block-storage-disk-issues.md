# Troubleshooting disk issues in Lightsail<a name="troubleshooting-block-storage-disk-issues"></a>

 *Last updated: November 14, 2017* 

You might encounter errors with your block storage disks in Lightsail\. This topic identifies common issues and workarounds for those errors\.

## General disk errors<a name="general-disk-errors"></a>

Choose the issue below that best describes your problem, and follow the links to fix the issue\. If you encounter an issue that's not in the list, use the **Questions? Comments?** link at the bottom of this page to submit feedback or contact AWS Customer Support\.

**I can't delete a disk because it's still attached to an instance\.**  
Try detaching the disk from your instance first, and then try to delete the disk\. For more information, see [Detach and delete a block storage disk in Lightsail](detach-and-delete-block-storage-disks.md)\.  
 *Actual error message:* **You can't perform this operation because the disk is still attached to a Lightsail instance: *YOUR\_INSTANCE*** 

**I can't detach a disk because the Lightsail instance is still running\.**  
Try stopping your instance first, and then try to detach the disk\. For more information, see [Stop an instance in Lightsail](lightsail-how-to-start-stop-or-restart-your-instance-virtual-private-server.md)\.  
 *Actual error message:* **You can't detach this disk right now\. The state of this disk is: *DISK\_STATE*** 

**I can't specify a custom disk size above 16 TB \(16,384 GB\)\.**  
Try creating a smaller disk\. Additional disks can be up to 16 TB\. If your disk is less than 16 TB and you still can't create it, you might encounter the next error in the list \(too many big disks\)\. That's because you can't have more than 20 TB in additional disk storage across your AWS account\. For more information, see [Block storage disks in Lightsail](elastic-block-storage-and-ssd-disks-in-amazon-lightsail.md)\.  
 *Actual error message:* **The size of a block storage disk must be between 8 and 16384 GB\.** 

**I can't create any more disks in Lightsail\.**  
You might have reached your quota for the number of disks you can create\. Or you might have created too many big disks \(the total size of disk storage can't exceed 20 TB\) in your AWS account\. For more information, see [Block storage disks in Lightsail](elastic-block-storage-and-ssd-disks-in-amazon-lightsail.md)\.  
*Actual error message:***You've reached the maximum size limit of all disks in this account\.** or **You've reached the limit of disks in this account\.**

**I can't attach my disk to my Lightsail instance**  
If you encounter the following error, you need to recreate your disk in the same AWS Region and Availability Zone as the instance where you plan to attach the disk\.  

![\[Block storage disk can't be attached because it's in the wrong Availability Zone\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/block-storage-disk-in-different-zone-than-lightsail-instance.png)
 *Actual error message:* **There are currently no instances in the *AWS Region* that can use this disk\.** 