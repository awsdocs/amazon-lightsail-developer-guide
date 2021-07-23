# Restoring previous versions of objects in a bucket in Amazon Lightsail<a name="amazon-lightsail-restoring-bucket-object-versions"></a>

 *Last updated: July 14, 2021* 

If your bucket in the Amazon Lightsail object storage service is version\-enabled, then you can restore previous versions of an object\. Restore a previous version of an object recover from unintended user actions or application failures\.

You can restore a previous version of an object using the Lightsail console\. You can also use the AWS Command Line Interface \(AWS CLI\) and AWS SDKs restore a previous version of an object\. To do this, copy a specific version of the object into the same bucket, and use the same object key name\. This replaces the current version with the previous version, making the previous version the current version\. For more information about versioning, see [Enabling and suspending object versioning in a bucket in Amazon Lightsail](amazon-lightsail-managing-bucket-object-versioning.md)\. For more information about buckets, see [Object storage in Amazon Lightsail](buckets-in-amazon-lightsail.md)\.

## Restore a previous version of an object using the Lightsail console<a name="restore-previous-object-version-lightsail-console"></a>

Complete the following procedure to restore a previous version of an object using the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Storage** tab\.

1. Choose the name of the bucket for which you want to restore a previous version of an object\.

1. Use the **Objects browser** pane in the **Objects** tab to browse to the location of the object\.

1. Add a checkmark next to the object for which you want to restore a previous version\.

1. Choose **Manage** under the Versions section of the **Object information** pane\.

1. Choose **Restore**\.

1. In the **Restore object** from a stored version pane that appears, choose the version of the object that you want to restore\.

1. Choose **Continue**\.

1. In the confirmation prompt that appears, choose **Yes, restore** to restore the object version\. Otherwise, choose **No, cancel**\.

## Restore a previous version of an object using the AWS CLI<a name="restore-previous-object-version-aws-cli"></a>

Complete the following procedure to restore a previous version of an object the AWS Command Line Interface \(AWS CLI\)\. You do this by using the `copy-object` command\. You must copy the previous version of the object into the same bucket, using the same object key\. For more information, see [copy\-object](https://docs.aws.amazon.com/cli/latest/reference/s3api/copy-object.html) in the *AWS CLI Command Reference*\.

**Note**  
You must install the AWS CLI and configure it for Lightsail and Amazon S3 before continuing with this procedure\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to restore a previous version of an object\.

   ```
   aws s3api copy-object --copy-source "BucketName/ObjectKey?versionId=VersionId" --key ObjectKey --bucket BucketName
   ```

   In the command, replace the following example text with your own:
   + *BucketName* \- The name of the bucket for which you want to restore a previous version of an object\. You must specify the same bucket name for the `--copy-source` and `--bucket` parameters\.
   + *ObjectKey* \- The name of the object to restore\. You must specify the same object key name for the `--copy-source` and `--key` parameters\.
   + *VersionId* \- The ID of the previous object version that you want to restore to the current version\. Use the `list-object-versions` command to get a list of version IDs for objects in your bucket\.

   Example:

   ```
   aws s3api copy-object --copy-source "DOC-EXAMPLE-BUCKET/sailbot.jpg?versionId=GQWEexample87Mdl8Q_DKdVTiVMi_VyU" –key sailbot.jpg --bucket DOC-EXAMPLE-BUCKET
   ```

   You should see a result similar to the following example:  
![\[Result of the AWS CLI copy-object-version command\]](https://d9yljz1nd5001.cloudfront.net/en_us/cdafd3c2a6d9edfefee89eda217b0068/images/amazon-lightsail-s3api-copy-object-version-result.png)

## Managing buckets and objects in Lightsail<a name="restoring-versions-managing-buckets-and-objects"></a>

These are the general steps to manage your Lightsail object storage bucket:

1. Learn about objects and buckets in the Amazon Lightsail object storage service\. For more information, see [Object storage in Amazon Lightsail](buckets-in-amazon-lightsail.md)\.

1. Learn about the names that you can give your buckets in Amazon Lightsail\. For more information, see [Bucket naming rules in Amazon Lightsail](bucket-naming-rules-in-amazon-lightsail.md)\.

1. Get started with the Lightsail object storage service by creating a bucket\. For more information, see [Creating buckets in Amazon Lightsail](amazon-lightsail-creating-buckets.md)\.

1. Learn about the access permissions that you can configure for your bucket\. You can make all objects in your bucket public or private, or you can choose to make individual objects public\. You can also grant access to your bucket by creating access keys, attaching instances to your bucket, and granting access to other AWS accounts\. For more information, see [Understanding bucket permissions in Amazon Lightsail](amazon-lightsail-understanding-bucket-permissions.md)\.

   After learning about bucket access permissions, see the following guides to grant access to your bucket:
   + [Configuring bucket access permissions in Amazon Lightsail](amazon-lightsail-configuring-bucket-permissions.md)
   + [Configuring access permissions for individual objects in a bucket in Amazon Lightsail](amazon-lightsail-configuring-individual-object-access.md)
   + [Creating access keys for a bucket in Amazon Lightsail](amazon-lightsail-creating-bucket-access-keys.md)
   + [Configuring resource access for a bucket in Amazon Lightsail](amazon-lightsail-configuring-bucket-resource-access.md)
   + [Configuring cross\-account access for a bucket in Amazon Lightsail](amazon-lightsail-configuring-bucket-cross-account-access.md)

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

1. After enabling object versioning, you can restore previous versions of objects in your bucket\. For more information, see [Restoring previous versions of objects in a bucket in Amazon Lightsail](#amazon-lightsail-restoring-bucket-object-versions)\.

1. Monitor the utilization of your bucket\. For more information, see [Viewing metrics for your bucket in Amazon Lightsail](amazon-lightsail-viewing-bucket-metrics.md)\.

1. Configure an alarm for bucket metrics to be notified when the utilization of your bucket crosses a threshold\. For more information, see [Creating bucket metric alarms in Amazon Lightsail](amazon-lightsail-adding-bucket-metric-alarms.md)\.

1. Change the storage plan of your bucket if it's running low on storage and network transfer\. For more information, see [Changing the plan of your bucket in Amazon Lightsail](amazon-lightsail-changing-bucket-plans.md)\.

1. Learn how to connect your bucket to other resources\. For more information, see the following tutorials\.
   + [Tutorial: Connecting a WordPress instance to an Amazon Lightsail bucket](amazon-lightsail-connecting-buckets-to-wordpress.md)
   + [Tutorial: Using an Amazon Lightsail bucket with a Lightsail content delivery network distribution](amazon-lightsail-using-distributions-with-buckets.md)

1. Delete your bucket if you're no longer using it\. For more information, see [Deleting buckets in Amazon Lightsail](amazon-lightsail-deleting-buckets.md)\.