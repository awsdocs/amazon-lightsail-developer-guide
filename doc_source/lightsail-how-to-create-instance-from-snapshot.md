# Creating an instance from a manual snapshot in Amazon Lightsail<a name="lightsail-how-to-create-instance-from-snapshot"></a>

*Last updated: November 14, 2017*

After you create a snapshot in Lightsail, you can create a new instance from that snapshot\. The new instance will include the system disk and any attached block storage disks you added\.

You must have a snapshot of an instance before you can create another instance from a snapshot\. For more information, see [Creating a snapshot of your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md) or [Creating a snapshot of your Windows Server instance in Amazon Lightsail](prepare-windows-based-instance-and-create-snapshot.md)\.

1. On the Lightsail home page, choose the name of your instance for which you want to create a new instance from a snapshot\.

1. Choose the **Snapshots** tab\.

1. Under the **Manual snapshots** section of the page, choose the actions menu icon \(⋮\) next to the snapshot from which you want to create a new instance, and choose **Create new instance**\.  
![\[Manage snapshot menu\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-create-new-linux-unix-based-lightsail-instance-from-snapshot.png)

1. On the **Create an instance from a snapshot** page, you have a few optional settings to decide on at the top\. For example, you can change the Availability Zone, [add a launch script](lightsail-how-to-configure-server-additional-data-shell-script.md), or [change the way you connect to your instance](understanding-ssh-in-amazon-lightsail.md)\.

   You can accept all the defaults and move on to the next step\.

1. Choose the plan \(or *bundle*\) for your new instance\. At this point, you can choose to create a larger bundle size if you'd like\.
**Note**  
You cannot create a smaller bundle size from a snapshot\. Lightsail will gray out all the bundle options that are smaller than the bundle you originally used to make your snapshot\.

1. Enter a name for your instance\.

   Resource names:
   + Must be unique within each AWS Region in your Lightsail account\.
   + Must contain 2 to 255 characters\.
   + Must start and end with an alphanumeric character or number\.
   + Can include alphanumeric characters, numbers, periods, dashes, and underscores\.

1. Choose one of the following options to add tags to your instance:
   + **Add key\-only tags** or **Edit key\-only tags** \(if tags have already been added\)\. Enter your new tag into the tag key text box, and press **Enter**\. Choose **Save** when you’re done entering your tags to add them, or choose **Cancel** to not add them\.  
![\[Key-only tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-key-only-tags.png)
   + **Create a key\-value tag**, then enter a key into the **Key** text box, and a value into the **Value** text box\. Choose **Save** when you’re done entering your tags, or choose **Cancel** to not add them\.

     Key\-value tags can only be added one at a time before saving\. To add more than one key\-value tag, repeat the previous steps\.  
![\[Key-value tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-key-value-tag.png)
**Note**  
For more information about key\-only and key\-value tags, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

1. Choose **Create instance**\.

   Lightsail takes you to the management page for your new instance, and you can start managing your new instance\.