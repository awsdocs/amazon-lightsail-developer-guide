# Create a larger Lightsail instance from a snapshot using the console<a name="how-to-create-larger-instance-from-snapshot-using-console"></a>

 *Last updated: November 14, 2017* 

It happens\. Your cloud project is growing and you need more compute power right away\! We can help you with that\. You can do everything from within the Lightsail console, or you can use the AWS Command Line Interface \(AWS CLI\) to do it\.

We'll show you how to take a *snapshot* of your current Lightsail instance and create a new, larger one with the compute power you need based on that snapshot\. The new instance will include any additional block storage disks that you attached to your instance\. Make sure to take a snapshot of your instance after you attach your additional disks\.

**Note**  
At this time, we don't support creating a smaller instance size \(or bundle\) from a snapshot\. You can only create the same size instance or a larger instance\.

## Prerequisites<a name="create-larger-instance-from-snapshot-using-console-prerequisites"></a>
+ You'll need a snapshot of your instance to work from\. If you haven't created a snapshot yet, see this topic: [Create a snapshot in Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md)\.

## Create your instance<a name="create-larger-instance-from-snapshot-using-console-get-your-snapshot-name"></a>

1. On the home page, choose the instance from which you want to create your snapshot\. Or choose **Manage** from the instance menu\.  
![\[Manage instance menu\]](https://d9yljz1nd5001.cloudfront.net/en_us/b380b072d417d05346bbc87239d4fd76/images/linux-instance-manage-instance-from-shortcut-menu-home-page.gif)

1. Choose **Snapshots**\.

1. Choose **Create new instance** from the snapshot menu\.  
![\[Manage snapshot menu\]](https://d9yljz1nd5001.cloudfront.net/en_us/b380b072d417d05346bbc87239d4fd76/images/animated-gif-create-new-linux-unix-based-lightsail-instance-from-snapshot.gif)

1. On the **Create an instance from a snapshot** page, you have a few optional settings to decide on at the top\. For example, you can change the Availability Zone, [add a launch script](lightsail-how-to-configure-server-additional-data-shell-script.md), or [change the way you connect to your instance](understanding-ssh-in-amazon-lightsail.md)\.

   You can accept all the defaults and move on to the next step\.

1. Choose the plan \(or *bundle*\) for your new instance\. At this point, you can choose to create a larger bundle size if you'd like\.
**Note**  
You cannot create a smaller bundle size from a snapshot\. Lightsail will gray out all the bundle options that are smaller than the bundle you originally used to make your snapshot\.

1. Give your instance and disks new, unique names, and then choose **Create**\.

   Lightsail takes you to the management page for your new instance, and you can start managing your new instance\.