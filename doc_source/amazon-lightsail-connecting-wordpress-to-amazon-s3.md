# Tutorial: Connect a WordPress website in Amazon Lightsail to an Amazon S3 bucket<a name="amazon-lightsail-connecting-wordpress-to-amazon-s3"></a>

 *Last updated: July 30, 2019* 

This tutorial describes the steps required to connect your WordPress website running on an Amazon Lightsail instance to an Amazon Simple Storage Service \(Amazon S3\) bucket to store website images and attachments\. To do this, you configure a WordPress plugin with a set of Amazon Web Services \(AWS\) account credentials\. The plugin then creates the Amazon S3 bucket for you and configures your website to use the bucket instead of the instance’s disk for website images and attachments\.

**Contents**
+ [Step 1: Complete the prerequisites](#connect-wordpress-to-s3-prerequisites)
+ [Step 2: Install the WP Offload Media plugin on your WordPress website](#install-wp-offload-media-on-wordpress)
+ [Step 3: Create an IAM user and policy](#create-iam-user-and-policy-for-wordpress)
+ [Step 4: Edit the WordPress configuration file](#edit-the-wp-config-file-for-s3-bucket)
+ [Step 5: Create the Amazon S3 bucket using the WP Offload Media plugin](#create-the-amazon-s3-bucket)
+ [Step 6: Next steps](#connect-wordpress-to-s3-prerequisites-next-steps)

## Step 1: Complete the prerequisites<a name="connect-wordpress-to-s3-prerequisites"></a>

Before you get started, create a WordPress instance in Lightsail, and make sure it’s in a running state\. For more information, see [Tutorial: Launch and configure a WordPress instance in Amazon Lightsail](amazon-lightsail-tutorial-launching-and-configuring-wordpress.md)\.

## Step 2: Install the WP Offload Media plugin on your WordPress website<a name="install-wp-offload-media-on-wordpress"></a>

You must use a plugin to configure your website to use an Amazon S3 bucket\. Many plugins are available to configure this; one such plugin is [WP Offload Media Lite](https://wordpress.org/plugins/amazon-s3-and-cloudfront/)\.

Complete the following steps to install the WP Offload Media plugin on your WordPress website:

1. Sign in to your WordPress dashboard as an administrator\.

   For more information, see [Getting the application user name and password for your 'Certified by Bitnami' instance in Amazon Lightsail](log-in-to-your-bitnami-application-running-on-amazon-lightsail.md)\.

1. Hover over **Plugins** in the left navigation menu, and choose **Add New**\.  
![\[Add new plugin menu item in the WordPress dashboard.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wordpress-add-new-plugin-menu.png)

1. Search for **WP Offload Media Lite**\.

1. In the search results, choose **Install Now** next to the **WP Offload Media** plugin\.  
![\[WP Offload Media Lite plugin for WordPress.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wp-offload-media-plugin.png)

1. Choose **Activate** after the plugin is done installing\.

1. In the left navigation menu, choose **Settings**, then choose **Offload Media**\.  
![\[Wordpress dashboard settings.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-offload-media-menu.png)

1. In the **Offload Media** page, choose **Amazon S3** as the storage provider, then choose **Define access keys in wp\-config\.php**\.

   With this option, you must add your AWS account credentials to the `wp-config.php` on the instance\. These steps are covered later in this tutorial\.  
![\[WP Offload Media page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-offload-media-configuration.png)

   Leave the **Offload Media** page open; you will return to it later in this tutorial\. Continue to the [Step 3: Create an IAM user and policy](#create-iam-user-and-policy-for-wordpress) section of this tutorial\.

## Step 3: Create an IAM user and policy<a name="create-iam-user-and-policy-for-wordpress"></a>

The WP Offload Media plugin requires access to your AWS account to create the Amazon S3 bucket, and to upload your website images and attachments\.

Complete the following steps to create a new AWS Identity and Access Management \(IAM\) user and policy for the WP Offload Media plugin:

1. Open a new browser tab, and sign in to the [IAM console](https://console.aws.amazon.com/iam/)\.

1. In the left navigation menu, choose **Users**\.

1. Choose **Add user**\.

1. In the **User name** text box, enter a name for the new user\. Enter something descriptive, such as `wp_s3_user` or `wp_offload_media_plugin_user`, so that you can easily identify it in the future when performing maintenance\.

1. Under the **Access type** section, choose **Programmatic access**\.  
![\[Access types in the IAM console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-iam-user-programmatic-access.png)

1. Choose **Next: Permissions**\.

1. Choose **Attach existing policies directly**, search for **S3**, and then choose **AmazonS3FullAccess** in the search results\.  
![\[Attach existing policies to a user in the IAM console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-iam-user-attach-existing-policies.png)

1. Choose **Next: Tags**, and then choose **Next: Review**\.

1. Review the user details displayed on the page, then choose **Create user**\.

1. Make note of the **access key ID** and **secret access key** for the user, or choose **Download \.csv** to save a copy of these values to your local drive\. You will need these in the next few steps when editing the `wp-config.php` file on the WordPress instance\.

## Step 4: Edit the WordPress configuration file<a name="edit-the-wp-config-file-for-s3-bucket"></a>

Complete the following steps to connect to your WordPress instance using the browser\-based SSH client in the Lightsail console and edit the `wp-config.php` file\.

The `wp-config.php` file contains your website’s base configuration details, such as database connection information\.

**Note**  
You can also connect to your instance using your own SSH client\. For more information, see [Download and set up PuTTY to connect using SSH in Amazon Lightsail](lightsail-how-to-set-up-putty-to-connect-using-ssh.md)

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Choose the browser\-based SSH client icon for the WordPress instance\.  
![\[The browser-based SSH client icon in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wordpress-browser-based-ssh-client.png)

1. In the SSH client window that appears, enter the following command to create a backup of the `wp-config.php` file in case something goes wrong:

   ```
   sudo cp /opt/bitnami/apps/wordpress/htdocs/wp-config.php /opt/bitnami/apps/wordpress/htdocs/wp-config.php-backup
   ```

1. Enter the following command to open the `wp-config.php` file using `nano`, a text editor:

   ```
   nano /opt/bitnami/apps/wordpress/htdocs/wp-config.php
   ```

1. Enter the following text above the `/* That's all, stop editing! Happy blogging. */` text\.

   Be sure to replace *AccessKeyID* with the access key ID and *SecretAccessKey* with the secret access key of the IAM user you created earlier in these steps\.

   ```
   define( 'AS3CF_SETTINGS', serialize( array(
       'provider' => 'aws',
       'access-key-id' => 'AccessKeyID',
       'secret-access-key' => 'SecretAccessKey',
   ) ) );
   ```

   Example:

   ```
   define( 'AS3CF_SETTINGS', serialize( array(
       'provider' => 'aws',
       'access-key-id' => 'AKIAIOSFODNN7EXAMPLE',
       'secret-access-key' => 'wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY',
   ) ) );
   ```

   The result should look like the following example:  
![\[AWS account credentials in the wp-config.php file.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ssh-wp-config-s3-bucket.png)

1. Press **Ctrl\+X** to exit Nano, then press **Y**, and **Enter** to save your edits to the `wp-config.php` file\.

1. Enter the following command to restart the services on the instance:

   ```
   sudo /opt/bitnami/ctlscript.sh restart
   ```

   You will see a result similar to the following when the services have restarted:  
![\[Restarting the services on the instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ssh-restart-services-bitnami.png)

   Close the SSH window and toggle back to the **Offload Media** page that you left open earlier in this tutorial\. You are now ready to [create the Amazon S3 bucket using the WP Offload Media plugin](#create-the-amazon-s3-bucket)\.

## Step 5: Create the Amazon S3 bucket using the WP Offload Media plugin<a name="create-the-amazon-s3-bucket"></a>

Now that the `wp-config.php` file is configured with the AWS credentials, you can return to the **Offload Media** page to complete the process\.

Complete the following steps to create the Amazon S3 bucket using the WP Offload Media plugin\.

1. Refresh the **Offload Media** page, or choose **Next**\.

   You should now see that the Amazon S3 provider is configured\.

1. Choose **Create new bucket**\.  
![\[Creating a new Amazon S3 bucket using the WP Offload Media plugin.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-offload-media-create-new-bucket.png)

1. In the **Region** drop\-down menu, choose the desired AWS Region\. We recommend that you choose the same region in which your WordPress instance is located\.

1. In the **Bucket** text box, enter a name for the new S3 bucket\.  
![\[Configuring the new Amazon S3 bucket using the WP Offload Media plugin.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-offload-media-bucket-configuration.png)

1. Choose **Create New Bucket**\.

   The page refreshes to confirm that a new bucket was created\. Review the settings that appear and adjust them accordingly to how you want your WordPress website to behave\.  
![\[WP Offload Media plugin settings.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-offload-media-settings-saved.png)

   From now on, images and attachments added to blog posts are automatically uploaded to the Amazon S3 bucket that you created\.

## Step 6: Next steps<a name="connect-wordpress-to-s3-prerequisites-next-steps"></a>

After you’re done connecting your WordPress website to an Amazon S3 bucket, you should create a snapshot of your WordPress instance to back up the changes you made\. For more information, see [Creating a snapshot of your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md)\.