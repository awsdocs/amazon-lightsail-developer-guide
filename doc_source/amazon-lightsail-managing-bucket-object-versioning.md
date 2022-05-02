# Enabling and suspending object versioning in a bucket in Amazon Lightsail<a name="amazon-lightsail-managing-bucket-object-versioning"></a>

 *Last updated: July 14, 2021* 

Versioning in Amazon Lightsail object storage service is a means of keeping multiple variants of an object in the same bucket\. You can use the versioning feature to preserve, retrieve, and restore every version of every object stored in your buckets\. With versioning, you can recover more easily from both unintended user actions and application failures\. When you enable versioning for a bucket, if the Lightsail object storage service receives multiple write requests for the same object simultaneously, it stores all of those objects\. Versioning is disabled by default on buckets in the Lightsail object storage service, so you must explicitly enable it\. For more information about buckets, see [Object storage in Amazon Lightsail](buckets-in-amazon-lightsail.md)\.

**Important**  
When you enable or suspend versioning on a bucket that has the **Individual objects can be made public \(read\-only\)** access permission configured, the permission resets to **All objects are private**\. If you want to continue having the option to make individual objects public, you must manually change the bucket access permission back to **Individual objects can be made public \(read\-only\)**\. For more information, see [Configuring bucket access permissions in Amazon Lightsail](amazon-lightsail-configuring-bucket-permissions.md)\.

## Version disabled, enabled, and suspended buckets<a name="version-disabled-enabled-suspended-buckets"></a>

Bucket versioning can be in one of three states in the Lightsail console:
+ Disabled \(`NeverEnabled` in the API and SDKs\)
+ Enabled \(`Enabled` in the API and SDKs\)
+ Suspended \(`Suspended` in the API and SDKs\)

After you enable versioning in a bucket, it cannot return to a disabled state\. But you can suspend versioning\. You enable and suspend versioning at the bucket level\.

The versioning state applies to all \(not some\) of the objects in that bucket\. When you enable versioning in a bucket, all new objects are versioned and given a unique version ID\. Objects that already exist in the bucket when versioning is enabled are always versioned going forward\. They are given a unique version ID when they are modified by future requests\.

## Version IDs<a name="bucket-object-version-ids"></a>

If you enable versioning for a bucket, the Lightsail object storage service automatically generates a unique version ID for the object that is being stored\. For example, in one bucket you can have two objects with the same key but different version IDs, such as `photo.gif` \(version 111111\) and `photo.gif` \(version 121212\)\.

![\[Bucket versioning enabled\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-bucket-versioning-versioning-enabled.png)

Version IDs cannot be edited\. They are Unicode, UTF\-8 encoded, URL\-ready, opaque strings that are no more than 1,024 bytes long\. The following is an example of a version ID:

```
3sL4kqtJlcpXroDTDmJ+rmSpXd3dIbrHY+MTRCxf3vjVBH40Nr8X8gdRQBpUMLUo
```

## Enable or suspend object versioning using the Lightsail console<a name="enable-dsable-bucket-object-versioning-lightsail-console"></a>

Complete the following procedure to enable or suspend object versioning using the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Storage** tab\.

1. Choose the name of the bucket for which you want to enable or suspend versioning\.

1. Choose the Versioning tab\.

1. Complete one of the following actions depending on the current versioning state of your bucket:
   + If versioning is currently suspended or has not been enabled, choose the toggle under the **Object versioning** section of the page to enable versioning\.
   + If versioning is currently enabled, choose the toggle under the **Object versioning** section of the page to suspend versioning\.

## Enable or suspend object versioning using the AWS CLI<a name="enable-dsable-bucket-object-versioning-aws-cli"></a>

Complete the following procedure to enable or suspend object versioning using the AWS Command Line Interface \(AWS CLI\)\. You do this by using the `update-bucket` command\. For more information, see [update\-bucket](https://docs.aws.amazon.com/cli/latest/reference/lightsail/update-bucket.html) in the *AWS CLI Command Reference*\.

**Note**  
You must install the AWS CLI and configure it for Lightsail and Amazon S3 before continuing with this procedure\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to enable or suspend object versioning\.

   ```
   aws lightsail update-bucket --bucket-name BucketName --versioning VersioningState
   ```

   In the command, replace the following example text with your own:
   + *BucketName* \- The name of the bucket for which you want to enable object versioning\.
   + *VersioningState* \- One of the following:
     + `Enabled` \- Enables object versioning\.
     + `Suspended` \- Suspends object versioning if it was previously enabled\.

   Example:

   ```
   aws lightsail update-bucket --bucket-name DOC-EXAMPLE-BUCKET --versioning Enabled
   ```

   You should see a result similar to the following example:  
![\[Response to the update bucket request\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-update-bucket-objects-versioning-cli.png)

## Managing buckets and objects in Lightsail<a name="versioning-managing-buckets-and-objects"></a>

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

1. Enable object versioning to preserve, retrieve, and restore every version of every object stored in your bucket\. For more information, see [Enabling and suspending object versioning in a bucket in Amazon Lightsail](#amazon-lightsail-managing-bucket-object-versioning)\.

1. After enabling object versioning, you can restore previous versions of objects in your bucket\. For more information, see [Restoring previous versions of objects in a bucket in Amazon Lightsail](amazon-lightsail-restoring-bucket-object-versions.md)\.

1. Monitor the utilization of your bucket\. For more information, see [Viewing metrics for your bucket in Amazon Lightsail](amazon-lightsail-viewing-bucket-metrics.md)\.

1. Configure an alarm for bucket metrics to be notified when the utilization of your bucket crosses a threshold\. For more information, see [Creating bucket metric alarms in Amazon Lightsail](amazon-lightsail-adding-bucket-metric-alarms.md)\.

1. Change the storage plan of your bucket if it's running low on storage and network transfer\. For more information, see [Changing the plan of your bucket in Amazon Lightsail](amazon-lightsail-changing-bucket-plans.md)\.

1. Learn how to connect your bucket to other resources\. For more information, see the following tutorials\.
   + [Tutorial: Connecting a WordPress instance to an Amazon Lightsail bucket](amazon-lightsail-connecting-buckets-to-wordpress.md)
   + [Tutorial: Using an Amazon Lightsail bucket with a Lightsail content delivery network distribution](amazon-lightsail-using-distributions-with-buckets.md)

1. Delete your bucket if you're no longer using it\. For more information, see [Deleting buckets in Amazon Lightsail](amazon-lightsail-deleting-buckets.md)\.