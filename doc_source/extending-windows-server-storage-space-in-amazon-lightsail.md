# Extending the storage space of your Windows Server instance in Amazon Lightsail<a name="extending-windows-server-storage-space-in-amazon-lightsail"></a>

 *Last updated: August 8, 2018* 

After you use a snapshot to create a new Windows Server instance with a larger plan, you may see that the available storage space is lower than that specified by the plan\. This is typically because the additional storage space provided by the larger plan has not been allocated; therefore, it’s not being used by the active volume\. The steps in this topic show you how to extend the file system of your Windows Server instance to use the maximum storage space available\.

**Note**  
This scenario happens only when you create a Windows Server instance using a snapshot that was created before running the System Preparation \(Sysprep\) utility\. For more information, see [Creating a snapshot of your Windows Server instance in Amazon Lightsail](prepare-windows-based-instance-and-create-snapshot.md)\.

**To extend the file system for a Windows Server instance**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the RDP client icon for the instance you want to connect to\.  
![\[Open the browser-based RDP client with quick connect.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/connect-to-windows-instance-using-rdp-connection-shortcut.png)

   The browser\-based RDP client window opens, as shown in the following example:  
![\[Browser-based RDP client in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-web-based-rdp-client.png)

1. On the taskbar, choose the Windows icon, then choose one of the following options:

   1. On Windows Server 2016 instances, choose **Start**, then choose **Windows Administrative Tools**\.

   1. On Windows Server 2012 instances, choose **Start**, then choose **Administrative Tools**\.  
![\[Windows Administrative Tools\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-windows-administrative-tools.png)

1. Choose **Computer Management**\.

1. In the left pane of the Computer Management console, choose **Disk Management**\.

1. On the **Actions** menu, choose **Rescan Disks**\.

   You may see unallocated space associated with a disk\. Extend the active volume on the disk to use the unallocated space\.  
![\[Unallocated disk space in Windows Disk Management\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-windows-unallocated-space.png)

1. Right\-click the active volume on the same disk as the unallocated space, then choose **Extend Volume**\.  
![\[Extend volume in Windows Disk Management\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-windows-extend-volume.png)

1. When the Extend Volume wizard opens, choose **Next**\.

1. In the **Select the amount of space in MB** field, enter the number of megabytes by which to extend the volume\. Normally, you set this to the maximum unallocated space\. The value you enter is the amount of space that you are adding, not the final size of the volume\.  
![\[Select unallocated space in the Windows Extend Volume wizard\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-windows-select-unallocated-space.png)

1. Complete the Extend Volume wizard\.

   The active volume is extended to use the unallocated space that you specified\. The following example shows all of the unallocated space chosen\.  
![\[Allocated disk space in Windows Disk Management\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-windows-allocated-space.png)