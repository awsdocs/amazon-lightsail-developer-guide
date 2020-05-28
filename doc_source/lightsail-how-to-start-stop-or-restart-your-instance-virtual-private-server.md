# Start, stop, or restart your Amazon Lightsail instance<a name="lightsail-how-to-start-stop-or-restart-your-instance-virtual-private-server"></a>

 *Last updated: October 16, 2017* 

When Lightsail creates your instance, your machine goes into a **Pending** state before it starts **Running**\. After your instance is running, you can restart it or stop and then restart it\. The cycle looks like this:

![\[Instance states\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-instance-state-cycle.png)

You can see the instance state when you manage your instance or view your instance on the home page\.

**Important**  
If you stop or restart your instance without first creating a static IP address, you will lose your IP address when your instance restarts\. It's always a good idea to create a static IP address for your instance\. Here's how: [Create a static IP address in Lightsail](lightsail-create-static-ip.md)\.

## Restart your instance while it's running<a name="lightsail-instance-restart"></a>
+ On the home page, choose the instance you want to restart, or choose **Restart** from the manage instance menu\.  
![\[Restart your instance from the manage instance menu\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-restart-instance-from-manage-instance-menu.png)

  If you're viewing your instance from the instance management page, choose **Restart**, and then choose **Confirm** when prompted\.
**Note**  
To **Restart** your instance, it must be in a **Running** state\.

## Stop a running instance<a name="lightsail-instance-stop"></a>
+ On the home page, choose the instance you want to stop, or choose **Stop** from the manage instance menu\.  
![\[Stop your instance from the manage instance menu\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-stop-instance-from-manage-instance-menu.png)

  If you're viewing your instance from the instance management page, choose **Stop**, and then choose **Confirm** when prompted\.
**Note**  
To **Stop** your instance, it must be in a **Running** state\.

## Start your instance after it's stopped<a name="lightsail-instance-start"></a>
+ On the home page, choose the instance you want to start, or choose **Start** from the manage instance menu\.  
![\[Start your instance from the manage instance menu\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-start-instance-from-manage-instance-menu.png)

  If you're viewing your instance from the instance management page, choose **Start**\.
**Note**  
To **Start** your instance, it must be in a **Stopped** state\.