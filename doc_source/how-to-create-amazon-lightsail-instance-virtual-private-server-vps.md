# Create an Amazon Lightsail instance<a name="how-to-create-amazon-lightsail-instance-virtual-private-server-vps"></a>

 *Last updated: August 18, 2021* 

You can create a Lightsail instance, also known as a virtual private server \(VPS\), running an application like WordPress or a development stack like LAMP in seconds\. After your instance starts running, you can connect to it via SSH without leaving Lightsail\. Here's how\.

1. On the home page, choose **Create instance**\.

1. Select a location for your instance \(an AWS Region and Availability Zone\)\.

   Choose **Change Region and zone** to create your instance in another location\.

1. Optionally, you can change the Availability Zone\.

   Choose an Availability Zone from the dropdown list\.

1. Pick an application \(**Apps \+ OS**\) or an operating system \(**OS Only**\)\.

   To learn more about Lightsail instance images, see [Choose an Amazon Lightsail instance image](compare-options-choose-lightsail-instance-image.md)\.

1. Choose your instance plan\.

   You can try the $3\.50 USD Lightsail plan free for one month \(up to 750 hours\)\. We will credit one free month to your account\. Learn more on our [Lightsail pricing page](http://www.amazonlightsail.com/pricing/)\.
**Note**  
For a limited time, Lightsail is extending its free trial to include three months free on select instance plans\. The offer applies to new or existing AWS accounts who started using Lightsail on or after July 8, 2021\. Offer only applies to one bundle per account\. Standard charges apply after the first 750 hours of usage of the selected bundle each month\.  
You can use the following instance plans free for three months:  
Linux/Unix instance plans: $3\.50 USD per month, $5 USD per month, and $10 USD per month
Windows instance plans: $8 USD per month, $12 USD per month, and $20 USD per month

1. Enter a name for your instance\.

   Resource names:
   + Must be unique within each AWS Region in your Lightsail account\.
   + Must contain 2 to 255 characters\.
   + Must start and end with an alphanumeric character or number\.
   + Can include alphanumeric characters, numbers, periods, dashes, and underscores\.

1. Choose one of the following options to add tags to your instance:
   + **Add key\-only tags** or **Edit key\-only tags** \(if tags have already been added\)\. Enter your new tag into the tag key text box, and press **Enter**\. Choose **Save** when you’re done entering your tags to add them, or choose **Cancel** to not add them\.  
![\[Key-only tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-key-only-tags.png)
   + **Create a key\-value tag**, then enter a key into the **Key** text box, and a value into the **Value** text box\. Choose **Save** when you’re done entering your tags, or choose **Cancel** to not add them\.

     Key\-value tags can only be added one at a time before saving\. To add more than one key\-value tag, repeat the previous steps\.  
![\[Key-value tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-key-value-tag.png)
**Note**  
For more information about key\-only and key\-value tags, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

1. Choose **Create instance**\.

   For advanced creation options, see [Use a launch script to configure your Amazon Lightsail instance when it starts up](lightsail-how-to-configure-server-additional-data-shell-script.md) or [Set up SSH for your Linux/Unix\-based Lightsail instances](lightsail-how-to-set-up-ssh.md)\.

Within minutes, your Lightsail instance is ready and you can connect to it via SSH, without leaving Lightsail\!

## How to connect to your instance<a name="create-an-instance-connect-to-your-instance"></a>

1. From the Lightsail home page, choose the menu on the right of your instance's name, and then choose **Connect**\.  
![\[Connect to your instance from the home page\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-connect-to-your-instance.png)

   Alternately, you can open your instance management page and choose the **Connect** tab\.  
![\[Connect to your instance from the instance management page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-connect-to-your-instance-from-instance-management-page.png)
**Note**  
If you want to connect to your instance using an SSH client such as PuTTy, you can follow this procedure: [Set up PuTTy to connect to your Lightsail instance](lightsail-how-to-set-up-putty-to-connect-using-ssh.md)\.

1. You can now type commands into the terminal and manage your Lightsail instance without setting up an SSH client\.  
![\[Browser-based SSH terminal in Amazon Lightsail\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-bitnami-terminal-window.png)

## Next steps<a name="create-an-instance-next-steps"></a>

Now that you can connect to your instance, what you do next depends on how you plan to use it\. For example:
+ [Get started with WordPress](getting-started-with-wordpress-and-lightsail.md) if you're connecting your blog\.
+ [Create a static IP address](lightsail-create-static-ip.md) for your instance to keep the same IP address each time you restart your Lightsail instance\.
+ [Create a snapshot of your instance](lightsail-how-to-create-a-snapshot-of-your-instance.md) as a backup\.