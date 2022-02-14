# Understanding bucket permissions in Amazon Lightsail<a name="amazon-lightsail-understanding-bucket-permissions"></a>

 *Last updated: July 14, 2021* 

By default, all Amazon Lightsail object storage resources—buckets and objects—are private\. This means that only the bucket owner, the Lightsail account that created it, can access the bucket and its objects\. The bucket owner can optionally grant access to others\. You can grant access to a bucket and its objects in the following ways:
+ **Read\-only access** – The following options control read\-only access to a bucket and its objects through the bucket's URL \(for example, `https://DOC-EXAMPLE-BUCKET.us-east-1.amazonaws.com/media/sailbot.jpg`\)\.
  + **Bucket access permissions** – Use bucket access permissions to grant access to all objects in a bucket for anyone on the internet\. For more information, see [Bucket access permissions](#bucket-access-permissions) later in this guide\.
  + **Individual object access permissions** – Use individual object access permissions to grant access to an individual object in a bucket for anyone on the internet\. For more information, see [Individual object access permissions](#individual-bucket-object-access-permissions) later in this guide\.
  + **Cross\-account access** – Use cross\-account access to grant access to all objects in a bucket for other AWS accounts\. For more information, see [Cross\-account access](#cross-account-access) later in this guide\.
+ **Read and write access** – The following options control full read and write access to a bucket and its objects\. Use these options with the AWS Command Line Interface \(AWS CLI\), AWS APIs, and AWS SDKs\.
  + **Access keys** – Use access keys to grant access to applications or plugins\. For more information, see [Access keys](#bucket-access-keys) later in this guide\.
  + **Resource access** – Use resource access to grant access to a Lightsail instance\. For more information, see [Resource access](#bucket-resource-access) later in this guide\.

For more information about buckets, see [Object storage in Amazon Lightsail](buckets-in-amazon-lightsail.md)\. For more information about security best practices, see [Security Best Practices for Amazon Lightsail object storage](amazon-lightsail-bucket-security-best-practices.md)\.

## Bucket access permissions<a name="bucket-access-permissions"></a>

Use bucket access permissions to control public \(unauthenticated\) read\-only access to objects in a bucket\. You can choose one of the following options when configuring bucket access permissions:
+ **All objects are private** – All objects in the bucket are readable only by you or anyone you give access to\. This option does not allow for individual objects to be made public \(read\-only\)\.
+ **Individual objects can be made public \(read\-only\)** – Objects in the bucket are readable only by you or anyone you give access to, unless you specify an individual object as public \(read\-only\)\. This option allows for individual objects to be made public \(read\-only\)\. For more information, see [Individual object access permissions](#individual-bucket-object-access-permissions) later in this guide\.
+ **All objects are public \(read\-only\)** – All objects in the bucket are readable by anyone on the internet\. All objects in the bucket become readable by anyone on the internet through the URL of the bucket \(for example, `https://DOC-EXAMPLE-BUCKET.us-east-1.amazonaws.com/media/sailbot.jpg`\) when you choose this option\.

For more information about configuring bucket access permissions, see [Configuring bucket access permissions](amazon-lightsail-configuring-bucket-permissions.md)\.

## Individual object access permissions<a name="individual-bucket-object-access-permissions"></a>

Use individual object access permissions to control public \(unauthenticated\) read\-only access to individual objects in a bucket\. Individual object access permissions can be configured only when the [Bucket access permissions](#bucket-access-permissions) of a bucket allow for individual objects to be made public \(read\-only\)\. You can choose one of the following options when configuring access permissions for an individual object:
+ **Private** – The object is readable only by you or anyone you give access to\.
+ **Public \(read\-only\)** – The object is readable by anyone on the internet\. The individual object becomes readable by anyone on the internet through the URL of the bucket \(for example, `https://DOC-EXAMPLE-BUCKET.us-east-1.amazonaws.com/media/sailbot.jpg`\)\.

For more information about configuring individual object access permissions, see [Configuring access permissions for individual objects in a bucket in Amazon Lightsail](amazon-lightsail-configuring-individual-object-access.md)\.

## Cross\-account access<a name="cross-account-access"></a>

Use cross\-account access to grant authenticated read\-only access to all objects in a bucket for other AWS accounts and their users\. Cross\-account access is ideal if you want to share objects with another AWS account\. When you grant cross\-account access to another AWS account, users in that account have read\-only access to objects in a bucket through the URL of the bucket \(for example, `https://DOC-EXAMPLE-BUCKET.us-east-1.amazonaws.com/media/sailbot.jpg`\)\. You can give access to a maximum of 10 AWS accounts\.

For more information about configuring cross\-account access, see [Configuring cross\-account access for a bucket](amazon-lightsail-configuring-bucket-cross-account-access.md)\.

## Access keys<a name="bucket-access-keys"></a>

Use access keys to create a set of credentials that grant full read and write access to a bucket and its objects\. Access keys consist of an access key ID and a secret access key as a set\. You can have a maximum of two access keys per bucket\. You can configure access keys on your application so that it can access your bucket and its objects using the AWS APIs, and AWS SDKs\. You can also configure access keys on the AWS CLI\.

For more information about creating access keys, see [Creating access keys for a bucket](amazon-lightsail-creating-bucket-access-keys.md)\.

## Resource access<a name="bucket-resource-access"></a>

Use resource access to grant full read and write access to a bucket and its objects for Lightsail instances\. With resource access, you don't have to manage credentials like access keys\. To grant access to an instance, attach the instance to a bucket in the same AWS Region\. To deny access, detach the instance from the bucket\. Resource access is ideal if you're configuring an application on your instance to programmatically upload and access files on your bucket\. One such use\-case is to configure a WordPress instance to store media files on a bucket\. For more information, see [Tutorial: Connecting a WordPress instance to an Amazon Lightsail bucket](amazon-lightsail-connecting-buckets-to-wordpress.md) and [Tutorial: Using an Amazon Lightsail bucket with a Lightsail content delivery network distribution](amazon-lightsail-using-distributions-with-buckets.md)\.

For more information about configuring resource access, see [Configuring resource access for a bucket](amazon-lightsail-configuring-bucket-resource-access.md)\.

## Managing buckets and objects in Lightsail<a name="bucket-permissions-managing-buckets-and-objects"></a>

These are the general steps to manage your Lightsail object storage bucket:

1. Learn about objects and buckets in the Amazon Lightsail object storage service\. For more information, see [Object storage in Amazon Lightsail](buckets-in-amazon-lightsail.md)\.

1. Learn about the names that you can give your buckets in Amazon Lightsail\. For more information, see [Bucket naming rules in Amazon Lightsail](bucket-naming-rules-in-amazon-lightsail.md)\.

1. Get started with the Lightsail object storage service by creating a bucket\. For more information, see [Creating buckets in Amazon Lightsail](amazon-lightsail-creating-buckets.md)\.

1. Learn about security best practices for buckets and the access permissions that you can configure for your bucket\. You can make all objects in your bucket public or private, or you can choose to make individual objects public\. You can also grant access to your bucket by creating access keys, attaching instances to your bucket, and granting access to other AWS accounts\. For more information, see [Security Best Practices for Amazon Lightsail object storage](amazon-lightsail-bucket-security-best-practices.md) and [Understanding bucket permissions in Amazon Lightsail](#amazon-lightsail-understanding-bucket-permissions)\.

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
   + [Tutorial: Using an Amazon Lightsail bucket with a Lightsail content delivery network distribution](amazon-lightsail-using-distributions-with-buckets.md)

1. Delete your bucket if you're no longer using it\. For more information, see [Deleting buckets in Amazon Lightsail](amazon-lightsail-deleting-buckets.md)\.