# Block public access for buckets in Amazon Lightsail<a name="amazon-lightsail-block-public-access-for-buckets"></a>

 *Last updated: June 22, 2022* 

Amazon Simple Storage Service \(Amazon S3\) is an object storage service on which customers can store and protect data\. The Amazon Lightsail object storage service is built on Amazon S3 technology\. Amazon S3 offers *account\-level block public access*, which you can use to limit public access to all S3 buckets in an AWS account\. Account\-level block public access can make all S3 buckets in an AWS account private, regardless of existing individual bucket and object permissions\.

When allowing or denying public access, Lightsail object storage buckets take into account the following:
+ Lightsail bucket access permissions\. For more information see [Understanding bucket permissions in Amazon Lightsail](amazon-lightsail-understanding-bucket-permissions.md)\.
+ Amazon S3 account\-level block public access configurations, which override the Lightsail bucket access permissions\.

If you turn on account\-level **Block *all* public access** in Amazon S3, your public Lightsail buckets and objects become private and are no longer publicly accessible\.

## Configuring block public access settings for your account<a name="configuring-block-public-access"></a>

You can use the Amazon S3 console, AWS Command Line Interface \(AWS CLI\), AWS SDKs, and REST API to configure block public access settings\. You can access the account\-level block public access feature in the navigation pane of the Amazon S3 console as shown in the following example\.

![\[Block public access navigation pane option in the Amazon S3 console\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-s3-block-public-access-navigation-pane.png)

The Amazon S3 console offers settings to block all public access, block public access granted through new or any access control lists, and block public access to buckets and objects granted through new or any public bucket or access point policies\.

![\[Block public access options in the Amazon S3 console\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-s3-block-public-access-in-s3-console.png)

You can turn each setting **On** or **Off** in the Amazon S3 console\. In the API, the corresponding setting is `TRUE` \(On\) or `FALSE` Off\)\. The following sections describe each setting's effects on S3 buckets and Lightsail buckets\.

**Note**  
The following sections mention access control lists \(ACLs\)\. An ACL defines the users who own or have access to a bucket or individual objects\. For more information, see [Access control list overview](https://docs.aws.amazon.com/AmazonS3/latest/userguide/acl-overview.html) in the *Amazon S3 User Guide\.*
+ **Block *all* public access** — Turn on this setting to block all public access to your S3 buckets, Lightsail buckets, and their corresponding objects\. This setting incorporates all of the following settings\. When you turn on this setting, only you \(the bucket owner\) and authorized users are allowed to access your buckets and their objects\. You can only turn this setting on in the Amazon S3 console\. It is not available in the AWS CLI, Amazon S3 API, or AWS SDKs\.
  + **Block public access to buckets and objects granted through *new* access control lists \(ACLs\)** — Turn on this setting to block putting public ACLs on buckets and objects\. This setting does not impact existing ACLs\. Therefore, an object that already has a public ACL remains public\. This setting also has no impact on objects that are public due to a bucket access permission being set to **All objects are public and read\-only**\. This setting is labeled as `BlockPublicAcls` in the Amazon S3 API\.
**Note**  
WordPress plugins that put media in Lightsail buckets, such as the Offload Media Light plugin, might stop working when this setting is turned on\. This is because most WordPress plugins configure the public\-read ACL on objects\. WordPress plugins that toggle object ACLs might also stop working\.
  + **Block public access to buckets and objects granted through *any* access control lists \(ACLs\)** — Turn on this setting to ignore public ACLs and block public access to buckets and objects\. This setting allows public ACLs to be put on buckets and objects, but ignores them when granting access\. For Lightsail buckets, setting a bucket's access permission to **All objects are public and read\-only** or setting an individual object's permission to **Public \(read\-only\)** is the equivalent of putting a public ACL on either\. This setting is labeled as `IgnorePublicAcls` in the Amazon S3 API\.
  + **Block public access to buckets and objects granted through *new* public bucket or access point policies** — Turn on this setting to block the **All objects are public and read\-only** bucket access permission from being configured on your Lightsail buckets\. This setting does not impact buckets that are already configured with the **All objects are public and read\-only** bucket access permission\. This setting is labeled as `BlockPublicPolicy` in the Amazon S3 API\.
  + **Block public and cross\-account access to buckets and objects through *any* public bucket or access point policies** — Turn on this setting to make all of your Lightsail buckets private\. This makes all Lightsail buckets private, even if they are configured with the **All objects are public and read\-only** bucket access permission\. This setting is labeled as `RestrictPublicBuckets` in the Amazon S3 API\.
**Important**  
This setting also blocks cross\-account access that is configured on a Lightsail bucket that is also configured with the **All objects are public and read\-only** bucket access permission in Lightsail\. To continue allowing cross\-account access, make sure to configure the Lightsail bucket with the **All objects are private** bucket access permission in Lightsail before turning on the **Block public and cross\-account access to buckets and objects through *any* public bucket or access point policies** setting in Amazon S3\.

For more information about block public access and how to configure it, see the following resources in the *Amazon S3 User Guide*:
+ [Blocking public access to your Amazon S3 storage](https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-control-block-public-access.html)
+ [Configuring block public access settings for your account](https://docs.aws.amazon.com/AmazonS3/latest/userguide/configuring-block-public-access-account.html)

Use the Lightsail console, AWS CLI, AWS SDKs, and REST API to configure access permissions for your Lightsail buckets\. For more information, see [Understanding bucket permissions in Amazon Lightsail](amazon-lightsail-understanding-bucket-permissions.md)\.

**Note**  
Lightsail uses a service\-linked role to get the current account\-level block public access configuration from Amazon S3 and apply it to Lightsail object storage resources\. After configuring block public access in Amazon S3, wait at least one hour for it to take effect in Lightsail\. For more information, see [Using Service\-Linked Roles for Amazon Lightsail](amazon-lightsail-using-service-linked-roles.md)\.

## Managing buckets and objects in Lightsail<a name="block-public-access-managing-buckets-and-objects"></a>

These are the general steps to manage your Lightsail object storage bucket:

1. Learn about objects and buckets in the Amazon Lightsail object storage service\. For more information, see [Object storage in Amazon Lightsail](buckets-in-amazon-lightsail.md)\.

1. Learn about the names that you can give your buckets in Amazon Lightsail\. For more information, see [Bucket naming rules in Amazon Lightsail](bucket-naming-rules-in-amazon-lightsail.md)\.

1. Get started with the Lightsail object storage service by creating a bucket\. For more information, see [Creating buckets in Amazon Lightsail](amazon-lightsail-creating-buckets.md)\.

1. Learn about security best practices for buckets and the access permissions that you can configure for your bucket\. You can make all objects in your bucket public or private, or you can choose to make individual objects public\. You can also grant access to your bucket by creating access keys, attaching instances to your bucket, and granting access to other AWS accounts\. For more information, see [Security Best Practices for Amazon Lightsail object storage](amazon-lightsail-bucket-security-best-practices.md) and [Understanding bucket permissions in Amazon Lightsail](amazon-lightsail-understanding-bucket-permissions.md)\.

   After learning about bucket access permissions, see the following guides to grant access to your bucket:
   + [Block public access for buckets in Amazon Lightsail](#amazon-lightsail-block-public-access-for-buckets)
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

1. Delete your bucket if you're no longer using it\. For more information, see [Deleting buckets in Amazon Lightsail](amazon-lightsail-deleting-buckets.md)\.