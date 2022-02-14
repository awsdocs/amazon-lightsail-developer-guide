# Tutorial: Using an Amazon Lightsail bucket with a Lightsail content delivery network distribution<a name="amazon-lightsail-using-distributions-with-buckets"></a>

 *Last updated: July 14, 2021* 

This tutorial describes the steps required to configure your Amazon Lightsail bucket as the origin of a Lightsail content delivery network \(CDN\) distribution\. It also describes how to configure your WordPress website to upload and store media \(such as images and movies files\) on your bucket, and deliver media from your distribution\. One example of how to do this is with the [WP Offload Media Lite plugin](https://deliciousbrains.com/wp-offload-media/)\. The following diagram illustrates this configuration\.

![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-wordpress-bucket-cdn.png)

Storing website media in a Lightsail bucket takes the load off your instance from having to store and serve those files\. Caching and serving media from a Lightsail distribution speeds up the delivery of those files to your website visitors, and can improve overall website performance\. For more information about distributions, see [Content delivery network distributions in Amazon Lightsail](amazon-lightsail-content-delivery-network-distributions.md)\. For more information about buckets, see [Object storage in Amazon Lightsail](buckets-in-amazon-lightsail.md)\.

**Contents**
+ [Step 1: Complete the prerequisites](#cdn-bucket-prerequisites)
+ [Step 2: Modify your bucket permissions](#cdn-bucket-modify-bucket-permissions)
+ [Step 3: Create a distribution with a bucket as the origin](#cdn-bucket-create-distribution)
+ [Step 4: Enable a custom subdomain for your distribution](#cdn-bucket-enable-custom-subdomain)
+ [Step 5: Install the WP Offload Media Lite plugin on your WordPress website](#cdn-bucket-install-wp-offload-media)
+ [Step 6: Test the connection between your WordPress website and your Lightsail bucket and distribution](#cdn-bucket-test-connection)

## Step 1: Complete the prerequisites<a name="cdn-bucket-prerequisites"></a>

Complete the following prerequisites if you haven't already:
+ Create and configure a WordPress instance in Lightsail, and get the password to sign in to the administration dashboard\. For more information, see [Tutorial: Launch and configure a WordPress instance in Amazon Lightsail](amazon-lightsail-tutorial-launching-and-configuring-wordpress.md)\.
+ Create a bucket in the Lightsail object storage service\. For more information, see [Creating buckets in Lightsail](amazon-lightsail-creating-buckets.md)\.

## Step 2: Modify your bucket permissions<a name="cdn-bucket-modify-bucket-permissions"></a>

Complete the following procedure to give your WordPress instance and the WP Offload Media Lite plugin access to your bucket\. The permissions of your bucket must be set to **Individual objects can be made public \(read only\)**\. You must also attach your WordPress instance to your bucket\. For more information about bucket permissions, see [Understanding bucket permissions in Amazon Lightsail](amazon-lightsail-understanding-bucket-permissions.md)\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Storage** tab\.

1. Choose the name of the bucket that you want to use with your WordPress website\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-bucket-name-storage-tab.png)

1. Choose the **Permissions** tab on the **Bucket management** page\.

1. Choose **Change permissions** under the **Bucket access permissions** section of the page\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-bucket-access-permissions.png)

1. Choose **Individual objects can be made public and read only**\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-bucket-access-permissions-options.png)

1. Choose **Save**\.

1. Choose **Yes, save** in the confirmation prompt that appears\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-bucket-access-permissions-confirmation.png)

   After a few moments, your bucket will be configured to allow for individual object access\. This ensures that objects uploaded to your bucket from your WordPress website using the Offload Media Lite plugin are readable to your customers\.

1. Scroll to the **Resource access** section of the page, and choose **Attach instance**\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-bucket-resource-access.png)

1. Choose the name of your WordPress instance in the drop\-down that appears, and then choose **Attach**\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-bucket-attach-resource-access.png)

   After a few moments, your WordPress instance is attached to your bucket\. This gives your WordPress instance access to manage your bucket and its objects\.

## Step 3: Create a distribution with a bucket as the origin<a name="cdn-bucket-create-distribution"></a>

Complete the following procedure to create a Lightsail distribution and choose your Lightsail bucket as the origin\.

1. Choose **Home** on the top navigation menu of the Lightsail console\.

1. On the Lightsail home page, choose the **Networking** tab\.

1. Choose **Create distribution**\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-create-distribution.png)

1. In the **Choose your origin** section of the page, choose the AWS Region in which you created your bucket\.

   Distributions are global resources\. They can reference a bucket in any AWS Region, and distribute its content globally\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-choose-origin-region.png)

1. Choose your bucket as the origin\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-choose-origin.png)
**Note**  
The permissions of your bucket must be set to **Individual objects can be made public \(read only\)**\. Only individual objects that are public will be cached and served by the distribution\. When you choose a bucket as the origin of a distribution, the options to specify the origin protocol policy, caching behavior, default behavior, and directory and file overrides become unavailable and cannot be edited\. The origin protocol policy defaults to **HTTP only** for buckets, and the caching behavior defaults to **Cache everything**\. You can change the advanced cache settings of the distribution after it's created\.

1. Choose your distribution plan\.

1. Enter a name for your distribution\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-name-distribution.png)

   Distribution names:
   + Must be unique within each AWS Region in your Lightsail account\.
   + Must contain 2\-255 characters\.
   + Must start and end with an alphanumeric character or number\.
   + Can include alphanumeric characters, numbers, periods, dashes, and underscores\.

1. Choose **Create distribution**\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-create-distribution-button.png)

   Your distribution is created after a few moments\. When your new distribution reaches an **Enabled** state, it is ready to serve and cache objects that are in your bucket\.

## Step 4: Enable a custom subdomain for your distribution<a name="cdn-bucket-enable-custom-subdomain"></a>

When you create your distribution, it is configured with a default domain that is similar to `123abc.cloudfront.net`\. You can specify that default domain as the source of your media files when you configure the WP Offload Media Lite plugin\. But we highly recommend that you enable a custom domain for your distribution\. The custom domain that you enable for your distribution should be a subdomain of the domain that you're using with your WordPress website\. For example, if you're using `mycustomdomain.com` with your WordPress website, then you might choose to use the custom domain `media.mycustomdomain.com` with your distribution\. Using the same domain and subdomain combination between your WordPress website and your distribution helps improve the search engine optimization score of your website\.

Complete the following steps to configure a custom domain for your distribution:

1. Create a Lightsail SSL/TLS certificate for your domain to use it with your distribution\. Lightsail distributions require HTTPS, so you must request an SSL/TLS certificate for your domain before you can use it with your distribution\. For more information, see [Creating SSL/TLS certificates for your distribution in Amazon Lightsail](amazon-lightsail-create-a-distribution-certificate.md)\.

1. Enable custom domains for your distribution to use your domain with your distribution\. Enabling custom domains requires that you specify the Lightsail SSL/TLS certificate that you created for your domain\. This adds your domain to your distribution and enables HTTPS\. For more information, see [Enabling custom domains for your Amazon Lightsail distributions](amazon-lightsail-enabling-distribution-custom-domains.md)\.

1. Add an alias record to your domain's DNS\. After you add the alias record, users who visit your domain are routed through your distribution\. For more information, see [Pointing your domains to your Amazon Lightsail distributions](amazon-lightsail-point-domain-to-distribution.md)\.

## Step 5: Install the WP Offload Media Lite plugin on your WordPress website<a name="cdn-bucket-install-wp-offload-media"></a>

Complete the following procedure to install the WP Offload Media Lite plugin on your WordPress website\. This plugin automatically copies images, videos, documents, and any other media added through WordPress' media uploader to your Lightsail bucket\. It can also be configured to serve media from your bucket through your Lightsail distribution\. For more information, see [WP Offload Media Lite](https://wordpress.org/plugins/amazon-s3-and-cloudfront/) in the *WordPress website*\.

1. Sign in to the dashboard of your WordPress website as an administrator\.

   For more information, see [Getting the application user name and password for your 'Certified by Bitnami' instance in Amazon Lightsail](log-in-to-your-bitnami-application-running-on-amazon-lightsail.md)\.

1. Pause on **Plugins** in the left navigation menu, and choose **Add New**\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-plugin-add-new.png)

1. Search for **WP Offload Media Lite**\.

1. In the search results, choose **Install Now** next to the **WP Offload Media Lite** plugin\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-plugin-install-now.png)

1. Choose **Activate** after the plugin is done installing\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-plugin-activate.png)

1. In the left navigation menu, choose **Settings**, then choose **Offload Media**\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-offload-media-settings-menu.png)

1. In the **Offload Media Lite** page, choose **Amazon S3** as the storage provider\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-offload-media-storage-provider.png)

1. Choose **My server is on Amazon Web Services and I'd like to use IAM Roles**\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-offload-media-iam-roles.png)

1. Choose **Next**\.

1. Choose **Browse existing buckets** in the **What bucket would you like to use?** page that appears\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-offload-media-browse-buckets.png)

1. Choose the name of the bucket that you created to use with your WordPress instance\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-offload-media-existing-buckets.png)

1. In the **Offload Media Lite Settings** page that appears, turn on **Force HTTPS** and **Remove Files From Server**\.
   + The **Force HTTPS** setting must be turned on because Lightsail buckets use HTTPS by default to serve media files\. If you don't turn this feature on, media files that are uploaded to your Lightsail bucket from your WordPress website won't be served correctly to your website visitors\.

     The **Remove Files From Server** setting ensures that media that is uploaded to your Lightsail bucket isn't also stored on your instance's disk\. If you don't turn this feature on, media files that are uploaded to your Lightsail bucket are also stored on the local storage of your WordPress instance\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-offload-media-options.png)

1. Under the **Delivery** section of the page, choose **Change** next to the Amazon S3 label\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-offload-media-change-delivery.png)

1. In the **How would you like to deliver your media?** page that appears, select **Amazon Cloudfront**\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-offload-media-amazon-cloudfront.png)

1. Choose **Save Delivery Provider**\.

1. In the **Offload Media Lite Settings** page that appears, turn on **Custom Domain \(CNAME\)**\. Then, enter the domain of your Lightsail distribution into the text box\. This could be the default domain of your distribution \(for example, `123abc.cloudfront.net`\) or the custom domain for your distribution \(for example, `media.mycustomdomain.com`\), if you enabled it\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-offload-media-custom-domain.png)

1. Choose **Save Changes**\.
**Note**  
To return to the **Offload Media Lite Settings** page later, pause on **Settings** in the left navigation menu, and choose **Offload Media**\.

   Your WordPress website is now configured to use the Media Lite Plugin\. The next time you upload a media file through WordPress, that file is automatically uploaded to your Lightsail bucket, and is served by the distribution\. To test the configuration, continue to the next section of this tutorial\.

## Step 6: Test the connection between your WordPress website and your Lightsail bucket and distribution<a name="cdn-bucket-test-connection"></a>

Complete the following procedure to upload a media file to your WordPress instance and confirm that it is uploaded to your Lightsail bucket and is served from your distribution\.

1. Pause on **Media** in the left navigation menu of the WordPress dashboard, and choose **Add New**\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-wordpress-media-add-new.png)

1. Choose **Select Files** on the **Upload New Media** page that appears\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-wordpress-select-files.png)

1. Choose a media file to upload from your local computer, and choose **Open**\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-wordpress-open-file.png)

1. When the file is done uploading, choose **Library** under **Media** in the left navigation menu\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-wordpress-library.png)

1. Choose the file that you recently uploaded\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-wordpress-media-library.png)

1. In the details panel of the file, the name of your bucket appears in the **Bucket** field\. The URL of your distribution appears in the **File URL** field\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-cdn-bucket-wordpress-media-details.png)

1. If you go to the **Objects** tab of the Lightsail bucket management page, you should see a **wp\-content** folder\. This folder is created by the Offload Media Lite plugin, and is used to store your uploaded media files\.  
![\[\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-bucket-objects-wp-content-folder.png)

## Managing buckets and objects in Lightsail<a name="connecting-to-distribution-managing-buckets-and-objects"></a>

These are the general steps to manage your Lightsail object storage bucket:

1. Learn about objects and buckets in the Amazon Lightsail object storage service\. For more information, see [Object storage in Amazon Lightsail](buckets-in-amazon-lightsail.md)\.

1. Learn about the names that you can give your buckets in Amazon Lightsail\. For more information, see [Bucket naming rules in Amazon Lightsail](bucket-naming-rules-in-amazon-lightsail.md)\.

1. Get started with the Lightsail object storage service by creating a bucket\. For more information, see [Creating buckets in Amazon Lightsail](amazon-lightsail-creating-buckets.md)\.

1. Learn about security best practices for buckets and the access permissions that you can configure for your bucket\. You can make all objects in your bucket public or private, or you can choose to make individual objects public\. You can also grant access to your bucket by creating access keys, attaching instances to your bucket, and granting access to other AWS accounts\. For more information, see [Security Best Practices for Amazon Lightsail object storage](amazon-lightsail-bucket-security-best-practices.md) and [Understanding bucket permissions in Amazon Lightsail](amazon-lightsail-understanding-bucket-permissions.md)\.

   After learning about bucket access permissions, see the following guides to grant access to your bucket:
   + [Configuring bucket access permissions in Amazon Lightsail](amazon-lightsail-configuring-bucket-permissions.md)
   + [Configuring access permissions for individual objects in a bucket in Amazon Lightsail](amazon-lightsail-configuring-individual-object-access.md)
   + [Creating access keys for a bucket in Amazon Lightsail](amazon-lightsail-creating-bucket-access-keys.md)
   + [Configuring resource access for a bucket in Amazon Lightsail](amazon-lightsail-configuring-bucket-resource-access.md)
   + [Configuring cross\-account access for a bucket in Amazon Lightsail](amazon-lightsail-configuring-bucket-cross-account-access.md)

1. Learn how to enable access logging for your bucket, and how to use access logs to audit the security of your bucket\. For more information, see the following guides\.
   + [Access logging for buckets in the Amazon Lightsail object storage service](amazon-lightsail-bucket-access-logs.md)
   + [Access log format for a bucket in the Amazon Lightsail object storage service](amazon-lightsail-bucket-access-log-format.md)
   + [Enabling access logging for a bucket in the Amazon Lightsail object storage service](amazon-lightsail-enabling-bucket-access-logs.md)
   + [Using access logs for a bucket in Amazon Lightsail to identify requests](amazon-lightsail-using-bucket-access-logs.md)

1. Create an IAM policy that grants a user the ability to manage a bucket in Lightsail\. For more information, see [IAM policy to manage buckets in Amazon Lightsail](amazon-lightsail-bucket-management-policies.md)\.

1. Learn about the way that objects in your bucket are labeled and identified\. For more information, see [Understanding object key names in Amazon Lightsail](understanding-bucket-object-key-names-in-amazon-lightsail.md)\.

1. Learn how to upload files and manage objects in your buckets\. For more information, see the following guides\.
   + [Uploading files to a bucket in Amazon Lightsail](amazon-lightsail-uploading-files-to-a-bucket.md)
   + [Uploading files to a bucket in Amazon Lightsail using multipart upload](amazon-lightsail-uploading-files-to-a-bucket-using-multipart-upload.md)
   + [Viewing objects in a bucket in Amazon Lightsail](amazon-lightsail-viewing-objects-in-a-bucket.md)
   + [Copying or moving objects in a bucket in Amazon Lightsail](amazon-lightsail-copying-moving-bucket-objects.md)
   + [Downloading objects from a bucket in Amazon Lightsail](amazon-lightsail-downloading-bucket-objects.md)
   + [Filtering objects in a bucket in Amazon Lightsail](amazon-lightsail-filtering-bucket-objects.md)
   + [Tagging objects in a bucket in Amazon Lightsail](amazon-lightsail-tagging-bucket-objects.md)
   + [Deleting objects in a bucket in Amazon Lightsail](amazon-lightsail-deleting-bucket-objects.md)

1. Enable object versioning to preserve, retrieve, and restore every version of every object stored in your bucket\. For more information, see [Enabling and suspending object versioning in a bucket in Amazon Lightsail](amazon-lightsail-managing-bucket-object-versioning.md)\.

1. After enabling object versioning, you can restore previous versions of objects in your bucket\. For more information, see [Restoring previous versions of objects in a bucket in Amazon Lightsail](amazon-lightsail-restoring-bucket-object-versions.md)\.

1. Monitor the utilization of your bucket\. For more information, see [Viewing metrics for your bucket in Amazon Lightsail](amazon-lightsail-viewing-bucket-metrics.md)\.

1. Configure an alarm for bucket metrics to be notified when the utilization of your bucket crosses a threshold\. For more information, see [Creating bucket metric alarms in Amazon Lightsail](amazon-lightsail-adding-bucket-metric-alarms.md)\.

1. Change the storage plan of your bucket if it's running low on storage and network transfer\. For more information, see [Changing the plan of your bucket in Amazon Lightsail](amazon-lightsail-changing-bucket-plans.md)\.

1. Learn how to connect your bucket to other resources\. For more information, see the following tutorials\.
   + [Tutorial: Connecting a WordPress instance to an Amazon Lightsail bucket](amazon-lightsail-connecting-buckets-to-wordpress.md)
   + [Tutorial: Using an Amazon Lightsail bucket with a Lightsail content delivery network distribution](#amazon-lightsail-using-distributions-with-buckets)

1. Delete your bucket if you're no longer using it\. For more information, see [Deleting buckets in Amazon Lightsail](amazon-lightsail-deleting-buckets.md)\.