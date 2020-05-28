# Getting started using WordPress from your Amazon Lightsail instance<a name="getting-started-with-wordpress-and-lightsail"></a>

 *Last updated: May 17, 2017* 

If you're reading this, it means you successfully created a Lightsail instance that's running WordPress\. Congrats\! If you still need to [create a WordPress instance](getting-started-with-amazon-lightsail.md), go ahead and do that now\. We'll wait for you\.\.\.

Now you're ready to get started with some basic administrative tasks\. First, let's log in to your WordPress Dashboard\.

## Step 1: Go to your WordPress blog and log in<a name="go-to-your-wordpress-blog"></a>

Here's how to log in to your WordPress blog\.

1. Go to the Lightsail home page and find your WordPress blog\.

1. Copy the **Public IP** address to the clipboard\. You can find this address on the Lightsail home page or on the instance details page\.

1. Paste the IP address into your browser\.

   You should see something like this:  
![\[WordPress blog made using Lightsail\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/wordpress-blog-lightsail-bitnami-new.png)

1. Choose **Manage** in the lower right corner\.

1. Choose **Login** to log in to the admin console\.

1. Use the default user name \(**user**\)\.

1. To get the password, you need to connect to your instance\.

   Go back to Lightsail and choose **Connect using SSH** to connect to your WordPress instance\.

1. Type the following:

   ```
   cat bitnami_application_password
   ```
**Note**  
If you're in a directory other than the user home directory, then type `cat $HOME/bitnami_application_password`\.

   You should see something like this:  
![\[Getting the WordPress password from the browser-based SSH terminal\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-bitnami-wordpress-password.png)

1. Highlight your password in the terminal screen, then choose the clipboard icon\.

1. Highlight the text you want to copy in the clipboard text box, then press Ctrl\+C or Cmd\+C to copy the text to your local clipboard\.  
![\[Copying text using the browser-based clipboard\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/lightsail-terminal-ssh-rdp-clipboard.png)
**Important**  
You should save your password somewhere at this time\. You can always change it later to something that's easier to remember\.

1. Paste your password into the WordPress login page, and then choose **Log In**\.

   If you succeed, you'll see the WordPress Dashboard\.  
![\[Successful login to the WordPress Dashboard\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wordpress-dashboard.png)

## Step 2: Update your profile or password in the WordPress Dashboard<a name="create-a-new-admin-user-in-wordpress"></a>

Now that you have access to your WordPress Dashboard, you can create another user or change your password to something that's easier to remember\.

1. Choose **Users**\.

1. Choose **user**, and then choose **Edit**\.

1. Update your **Personal Options** on the **Profile** page, and when you're done choose **Update Profile**\.

## Next steps<a name="getting-started-wordpress-lightsail-next-steps"></a>

Visit [Bitnami WordPress for Amazon Web Services](https://docs.bitnami.com/aws/apps/wordpress/) for more tutorials\. Here are some cool things you can do with your new WordPress blog in Lightsail\.
+  [Install plugins](https://docs.bitnami.com/aws/apps/wordpress/#how-to-install-a-plugin-on-wordpress) 
+  [Create a full backup](https://docs.bitnami.com/aws/apps/wordpress/#how-to-create-a-full-backup-of-wordpress) 
+  [Enable HTTPS support with SSL certificates](https://docs.bitnami.com/aws/apps/wordpress/#how-to-enable-https-support-with-ssl-certificates) 