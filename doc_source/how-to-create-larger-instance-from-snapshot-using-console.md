# Creating a larger instance, block storage disk, or database from a snapshot in Amazon Lightsail<a name="how-to-create-larger-instance-from-snapshot-using-console"></a>

 *Last updated: July 12, 2019* 

It happens\. Your cloud project is growing and you need more compute power right away\! We can help you with that\. To upsize your Lightsail instance, block storage disk, or database, create a snapshot of your resource, and then create a new, larger version of that resource using the snapshot\.

**Note**  
You cannot create a resource from a snapshot using a smaller plan size than the original resource\. For example, you can't go from an 8 GB instance to a 2 GB instance\.

## Prerequisites<a name="create-larger-instance-from-snapshot-using-console-prerequisites"></a>

You'll need a snapshot of your Lightsail instance, block storage disk, or database\. For more information, see [Snapshots in Amazon Lightsail](understanding-instance-snapshots-in-amazon-lightsail.md)\.

## Create your resource<a name="create-larger-resource-from-snapshot"></a>

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Choose the **Snapshots** tab\.

1. Find the Lightsail resource whose snapshot you want to use to create a new, larger resource, and choose the right\-arrow to expand the list of snapshots\.

1. Choose the ellipsis icon next to the snapshot you want to use, and choose **Create new**\.  
![\[Create new resource from a snapshot in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-create-resource-from-snapshot-menu-option.png)

1. On the **Create** page, you have a few optional settings to choose from\. For example, you can change the Availability Zone\. For instances, you can [add a launch script](lightsail-how-to-configure-server-additional-data-shell-script.md), or [change the SSH key you use to connect to it](understanding-ssh-in-amazon-lightsail.md)\.

   You can accept all the defaults and move on to the next step\.

1. Choose the plan \(or *bundle*\) for your new resource\. At this point, you can choose a larger bundle size than the original resource, if you'd like\.
**Note**  
You cannot create the resource using a smaller plan size than the original resource\. The bundle options that are smaller than the original resource will be unavailable\.

1. Enter a name for your instance\.

   Resource names:
   + Must be unique within each AWS Region in your Lightsail account\.
   + Must contain 2 to 255 characters\.
   + Must start and end with an alphanumeric character or number\.
   + Can include alphanumeric characters, numbers, periods, dashes, and underscores\.

1. Choose **Create**\.

   Lightsail takes you to the management page for your new resource, and you can start managing it\.