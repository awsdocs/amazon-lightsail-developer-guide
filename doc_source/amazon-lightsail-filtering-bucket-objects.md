# Filtering objects in a bucket in Amazon Lightsail<a name="amazon-lightsail-filtering-bucket-objects"></a>

 *Last updated: July 14, 2021* 

You can use filtering to find objects in your bucket in the Amazon Lightsail object storage service\. In this guide, we show you how to filter objects using the Lightsail console, and the AWS Command Line Interface \(AWS CLI\)\. For more information about buckets, see [Object storage in Amazon Lightsail](buckets-in-amazon-lightsail.md)\.

## Filtering objects using the Lightsail console<a name="filtering-objects-lightsail-console"></a>

Complete the following procedure to filter objects in a bucket using the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Storage** tab\.

1. Choose the name of the bucket for which you want to find objects\.

1. In the **Objects** tab, type an object prefix in the **Filter by name** text box\.

   The list of objects in the folder that you're currently viewing are filtered to match the text you enter\. The following example shows that if you enter `sail`, the list of objects on the page are filtered to display only those that start with `sail`\.  
![\[Filtering bucket objects in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-filter-bucket-objects-using-console.png)

   To filter the list of objects in a different folder, navigate to that folder\. Then, enter the object prefix into the **Filter by name** text box there\.

## Filtering objects using the AWS CLI<a name="filtering-objects-aws-cli"></a>

Complete the following procedure to filter objects in a bucket using the AWS Command Line Interface \(AWS CLI\)\. You do this by using the `list-objects-v2` command\. For more information, see [list\-objects\-v2](https://docs.aws.amazon.com/cli/latest/reference/s3api/list-objects-v2.html) in the *AWS CLI Command Reference*\.

**Note**  
You must install the AWS CLI and configure it for Lightsail and Amazon S3 before continuing with this procedure\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to list objects that start with a specific object key name prefix\.

   ```
   aws s3api list-objects-v2 --bucket BucketName --prefix ObjectKeyNamePrefix --query "Contents[].{Key: Key, Size: Size}"
   ```

   In the command, replace the following example text with your own:
   + *BucketName* \- The name of the bucket for which you want to list all objects\.
   + *ObjectKeyNamePrefix* \- An object key name prefix to limit the response to keys that begin with the specified prefix\.
**Note**  
This command uses the `--query` parameter to filter the response of the `list-objects-v2` request to the key value and size of each object\.

   Example:

   ```
   aws s3api list-objects-v2 --bucket DOC-EXAMPLE-BUCKET --prefix archived/ --query "Contents[].{Key: Key, Size: Size}"
   ```

   You should see a result similar to the following example\.  
![\[Result of the AWS CLI list-objects-v2 command\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-s3api-list-objects-v2-prefix-result.png)

## Managing buckets and objects in Lightsail<a name="filtering-objects-managing-buckets-and-objects"></a>

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
   + [Filtering objects in a bucket in Amazon Lightsail](#amazon-lightsail-filtering-bucket-objects)
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

1. Delete your bucket if you're no longer using it\. For more information, see [Deleting buckets in Amazon Lightsail](amazon-lightsail-deleting-buckets.md)\.