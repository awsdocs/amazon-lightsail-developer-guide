# Detach and delete a block storage disk in Lightsail<a name="detach-and-delete-block-storage-disks"></a>

 *Last updated: November 14, 2017* 

If you no longer need a block storage disk, you can detach it from your stopped Lightsail instance, and then delete it\. This topic describes how to back up your data and safely delete a disk\.

## Prerequisites<a name="delete-block-storage-disk-prerequisites"></a>
+ Stop your instance from running\. You have to do this before you can detach and then delete your disk\. [Learn how to stop your instance](lightsail-how-to-start-stop-or-restart-your-instance-virtual-private-server.md)
+ \(Optional\) We recommend that you create a snapshot of your disk\. That way, you have a backup in case you change your mind\. For more information, see [Creating a snapshot of your database in Amazon Lightsail](create-block-storage-disk-snapshot.md)

## Detach and delete your disk<a name="delete-block-storage-disk-detach-and-delete"></a>

Once you stop your Lightsail instance, you can safely detach and delete your disk\.

1. On the home page, choose **Storage**\.

1. Choose the name of your attached disk to manage it\.  
![\[Example of a block storage disk that is still attached to a Lightsail instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/example-disk-still-attached-home-page-storage-tab.png)

1. On the disk management page, choose **Detach**\.

   After a few seconds, the disk is detached and ready to be deleted or reattached\.

1. Choose the **Delete** tab\.

1. Choose **Delete disk**, and then confirm by choosing **Yes, delete**\.
**Important**  
This is a permanent operation and can't be undone\. You will lose all data on the disk when you delete it\.