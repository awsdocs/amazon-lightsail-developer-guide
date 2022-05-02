# Start, stop, or restart your Amazon Lightsail instance<a name="lightsail-how-to-start-stop-or-restart-your-instance-virtual-private-server"></a>

 *Last updated: April 17, 2021* 

When Lightsail creates your instance, your machine goes into a **Pending** state before it starts **Running**\. After your instance is running, you can restart it or stop and then restart it\. The cycle looks like this:

![\[Instance states\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-instance-state-cycle.png)

You can see the instance state when you manage your instance or view your instance on the home page\.

**Important**  
The default public IPv4 address that is assigned to your instance when you create it will change when you stop and start your instance\. You can optionally create and attach a static IPv4 address to your instance\. The static IPv4 address replaces the default public IPv4 address of your instance, and it stays the same when you stop and start your instance\. For more information, see [Create a static IP and attach it to an instance in Amazon Lightsail](lightsail-create-static-ip.md)\.

## Restart your instance while it's running<a name="lightsail-instance-restart"></a>
+ On the home page, choose the instance you want to restart, or choose **Restart** from the manage instance menu\.  
![\[Restart your instance from the manage instance menu\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-restart-instance-from-manage-instance-menu.png)

  If you're viewing your instance from the instance management page, choose **Restart**, and then choose **Confirm** when prompted\.
**Note**  
To **Restart** your instance, it must be in a **Running** state\.

## Stop a running instance<a name="lightsail-instance-stop"></a>
+ On the home page, choose the instance you want to stop, or choose **Stop** from the manage instance menu\.  
![\[Stop your instance from the manage instance menu\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-stop-instance-from-manage-instance-menu.png)

  If you're viewing your instance from the instance management page, choose **Stop**, and then choose **Confirm** when prompted\.
**Note**  
To **Stop** your instance, it must be in a **Running** state\.

## Start your instance after it's stopped<a name="lightsail-instance-start"></a>
+ On the home page, choose the instance you want to start, or choose **Start** from the manage instance menu\.  
![\[Start your instance from the manage instance menu\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-start-instance-from-manage-instance-menu.png)

  If you're viewing your instance from the instance management page, choose **Start**\.
**Note**  
To **Start** your instance, it must be in a **Stopped** state\.