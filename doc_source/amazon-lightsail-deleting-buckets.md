# Deleting buckets in Amazon Lightsail<a name="amazon-lightsail-deleting-buckets"></a>

 *Last updated: July 14, 2021* 

Delete your bucket in the Amazon Lightsail object storage service if you're no longer using it\. When you delete your bucket, all objects in the bucket, including stored versions of objects and access keys, are permanently deleted\.

For more information about buckets, see [Object storage in Amazon Lightsail](buckets-in-amazon-lightsail.md)\.

## Force deleting a bucket<a name="force-delete-bucket"></a>

Buckets that have one of the following conditions cannot be deleted unless you acknowledge the deletion:
+ The bucket is the origin of a distribution\.
+ The bucket has instances attached to it\.
+ The bucket has objects\.
+ The bucket has access keys\.

You must acknowledge the deletion to ensure that you don't disrupt an existing workflow that relies on the bucket\. For example, a WordPress website that is storing media on the bucket or a distribution that is caching and serving objects in your bucket\.

To acknowledge deletion of a bucket that has one of the preceding conditions, you must force delete the bucket\. Before you delete the bucket, the Lightsail service prompts you about which of these conditions exist on it\. If you use the Lightsail console to delete your bucket, you are presented with the option to force delete it\. If you use the AWS CLI, you must specify the `--force-delete` flag when making a `delete-bucket` request\. Both of these procedures are covered in the [Delete your bucket using the Lightsail console](#delete-bucket-using-lightsail-console) and [Delete your bucket using the AWS CLI](#delete-bucket-using-aws-cli) sections of this guide\.

## Delete your bucket using the Lightsail console<a name="delete-bucket-using-lightsail-console"></a>

Complete the following procedure to delete your bucket using the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Storage** tab\.

1. Choose the name of the bucket that you want to delete\.

1. Choose the ellipsis \(⋮\) icon in the tab menu, then choose **Delete**\.

1. Choose **Delete bucket**\.

1. In the prompt that appears, confirm if your bucket meets any of the following conditions:
   + Contains an object
   + Has access keys
   + Is attached to an instance
   + Is the origin of a distribution

   If it has any of those conditions, then you must choose to force delete the bucket\.

1. Choose one of the following options:
   + Choose **Force delete** to delete your bucket even if it has any of the conditions listed in step 6 of this procedure\.
   + Choose **Yes, delete** to delete your bucket when it doesn't have any of the conditions listed in step 6 of this procedure\.
   + Choose **No, cancel** to cancel deletion\.

## Delete your bucket using the AWS CLI<a name="delete-bucket-using-aws-cli"></a>

Complete the following procedure to delete your bucket using the AWS Command Line Interface \(AWS CLI\)\. You do this by using the `delete-bucket` command\. For more information, see [delete\-bucket](https://docs.aws.amazon.com/cli/latest/reference/lightsail/delete-bucket.html) in the *AWS CLI Command Reference*\.

**Note**  
You must install the AWS CLI and configure it for Lightsail and Amazon S3 before continuing with this procedure\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a Command Prompt or Terminal window\.

1. In the command prompt or terminal window, enter one of the following commands:
   + Enter the following command to delete a bucket that doesn't have the conditions listed in the [Force deleting a bucket](#force-delete-bucket) section of this guide\.

     ```
     aws lightsail delete-bucket --bucket-name BucketName
     ```
   + Enter the following command to force delete a bucket that has the conditions listed in the [Force deleting a bucket](#force-delete-bucket) section of this guide\.

     ```
     aws lightsail delete-bucket --bucket-name BucketName --force-delete
     ```

   In the commands, replace *BucketName* with the name of the bucket you want to delete\.

   Example:

   ```
   aws lightsail delete-bucket --bucket-name DOC-EXAMPLE-BUCKET
   ```

   You should see a result similar to the following example:  
![\[Result of the delete bucket request\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-delete-bucket-cli.png)

## Managing buckets and objects in Lightsail<a name="deleting-buckets-managing-buckets-and-objects"></a>

These are the general steps to manage your Lightsail object storage bucket:

1. Learn about objects and buckets in the Amazon Lightsail object storage service\. For more information, see [Object storage in Amazon Lightsail](buckets-in-amazon-lightsail.md)\.

1. Learn about the names that you can give your buckets in Amazon Lightsail\. For more information, see [Bucket naming rules in Amazon Lightsail](bucket-naming-rules-in-amazon-lightsail.md)\.

1. Get started with the Lightsail object storage service by creating a bucket\. For more information, see [Creating buckets in Amazon Lightsail](amazon-lightsail-creating-buckets.md)\.

1. Learn about security best practices for buckets and the access permissions that you can configure for your bucket\. You can make all objects in your bucket public or private, or you can choose to make individual objects public\. You can also grant access to your bucket by creating access keys, attaching instances to your bucket, and granting access to other AWS accounts\. For more information, see [Security Best Practices for Amazon Lightsail object storage](amazon-lightsail-bucket-security-best-practices.md) and [Understanding bucket permissions in Amazon Lightsail](amazon-lightsail-understanding-bucket-permissions.md)\.

   After learning about bucket access permissions, see the following guides to grant access to your bucket:
   + [Block public access for buckets in Amazon Lightsail](amazon-lightsail-block-public-access-for-buckets.md)
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
   + [Tutorial: Using an Amazon Lightsail bucket with a Lightsail content delivery network distribution](amazon-lightsail-using-distributions-with-buckets.md)

1. Delete your bucket if you're no longer using it\. For more information, see [Deleting buckets in Amazon Lightsail](#amazon-lightsail-deleting-buckets)\.