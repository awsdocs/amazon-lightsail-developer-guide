# Changing the plan of your bucket in Amazon Lightsail<a name="amazon-lightsail-changing-bucket-plans"></a>

 *Last updated: July 14, 2021* 

In the Amazon Lightsail object storage service, a bucket's storage plan specifies its monthly cost, storage space quota, and data transfer quota\. You can update your bucket's storage plan only one time within a monthly AWS billing cycle\. When you change your bucket's storage plan, the storage space and network transfer quotas are reset\. However, the excess storage space and data transfer charges you might have incurred from using the previous storage plan are not covered\.

Update your bucket's storage plan if it's consistently going over its storage space or data transfer quota, or if your bucket's usage is consistently in the lower range of these quotas\. Because your bucket might experience unpredictable usage fluctuations, we strongly recommend that you update your bucket's storage plan only as a long\-term strategy, instead of as a short\-term, monthly cost\-cutting measure\. Choose a storage plan that will provide your bucket with an ample storage space and data transfer quota for a long time to come\.

For more information about buckets, see [Object storage in Amazon Lightsail](buckets-in-amazon-lightsail.md)\.

## Change your bucket's storage plan using the Lightsail console<a name="change-bucket-storage-plan-lightsail-console"></a>

Complete the following procedure to change your bucket's storage plan using the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Storage** tab\.

1. Choose the name of the bucket for which you want to change the plan\.

1. Choose the **Metrics** tab in the bucket management page\.

1. Choose **Change storage plan**\.

1. In the confirmation prompt that appears, choose **Yes, change** to continue to change your bucket storage plan\. Otherwise, choose **No, cancel**\.

1. Choose the plan that you want to use, and then choose **Select plan**\.

1. In the confirmation prompt that appears, choose **Yes, apply** to apply the change to your bucket, or choose **No, go back** to not apply it\.

## Change your bucket's storage plan using the AWS CLI<a name="change-bucket-storage-plan-aws-cli"></a>

Complete the following procedure to change the plan of your bucket using the AWS Command Line Interface \(AWS CLI\)\. You do this by using the `update-bucket-bundle` command\. Note that a bucket storage plan is referred to as a bucket bundle in the API\. For more information, see [update\-bucket\-bundle](https://docs.aws.amazon.com/cli/latest/reference/lightsail/update-bucket-bundle.html) in the *AWS CLI Command Reference*\.

**Note**  
You must install the AWS CLI and configure it for Lightsail and Amazon S3 before continuing with this procedure\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to change the plan of your bucket\.

   ```
   aws lightsail update-bucket-bundle --bucket-name BucketName --bundle-id BundleID
   ```

   In the command, replace the following example text with your own:
   + *BucketName* \- The name of the bucket for which you want to update the storage plan\.
   + *BundleID* \- The ID of the new bucket bundle you want to apply to the bucket\. Use the `get-bucket-bundles` command to see a list of available bucket bundles and their IDs\. For more information, see [get\-bucket\-bundles](https://docs.aws.amazon.com/cli/latest/reference/lightsail/get-bucket-bundle.html) in the *AWS CLI Command Reference*\.

   Example:

   ```
   aws lightsail update-bucket-bundle --bucket-name DOC-EXAMPLE-BUCKET --bundle-id medium_1_0
   ```

   You should see a result similar to the following example:  
![\[Result of the update bucket bundle request\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-update-bucket-bundle-cli.png)

## Managing buckets and objects in Lightsail<a name="changing-plan-managing-buckets-and-objects"></a>

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

1. Change the storage plan of your bucket if it's running low on storage and network transfer\. For more information, see [Changing the plan of your bucket in Amazon Lightsail](#amazon-lightsail-changing-bucket-plans)\.

1. Learn how to connect your bucket to other resources\. For more information, see the following tutorials\.
   + [Tutorial: Connecting a WordPress instance to an Amazon Lightsail bucket](amazon-lightsail-connecting-buckets-to-wordpress.md)
   + [Tutorial: Using an Amazon Lightsail bucket with a Lightsail content delivery network distribution](amazon-lightsail-using-distributions-with-buckets.md)

1. Delete your bucket if you're no longer using it\. For more information, see [Deleting buckets in Amazon Lightsail](amazon-lightsail-deleting-buckets.md)\.