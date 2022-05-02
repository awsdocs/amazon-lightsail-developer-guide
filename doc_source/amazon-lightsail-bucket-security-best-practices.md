# Security Best Practices for Amazon Lightsail object storage<a name="amazon-lightsail-bucket-security-best-practices"></a>

 *Last updated: March 9, 2022* 

Amazon Lightsail object storage provides a number of security features to consider as you develop and implement your own security policies\. The following best practices are general guidelines and don’t represent a complete security solution\. Because these best practices might not be appropriate or sufficient for your environment, treat them as helpful considerations rather than prescriptions\.

**Contents**
+ [Preventative security best practices](#bucket-security-best-practices-preventative-practices)
  + [Implement least privilege access](#bucket-security-best-practices-least-privilege-access)
  + [Verify that your Lightsail buckets are not publicly accessible](#bucket-security-best-practices-verify-bucket-permissions)
  + [Enable block public access in Amazon S3](#bucket-security-best-practices-block-public-access)
  + [Attach instances to buckets to grant full programmatic access](#bucket-security-best-practices-attach-instances)
  + [Use cross\-account access to give other AWS accounts access to objects in your bucket](#bucket-security-best-practices-cross-account-access)
  + [Encryption of data](#bucket-security-best-practices-data-encryption)
  + [Enable versioning](#bucket-security-best-practices-enable-versioning)
+ [Monitoring and auditing best practices](#bucket-security-best-practices-monitoring-auditing)
  + [Enable access logging and perform periodic security and access audits](#bucket-security-best-practices-enable-access-logging)
  + [Identify, tag, and audit your Lightsail buckets](#bucket-security-best-practices-identify-tag)
  + [Implement monitoring using AWS monitoring tools](#bucket-security-best-practices-monitoring-tools)
  + [Use AWS CloudTrail](#bucket-security-best-practices-cloudtrail)
  + [Monitor AWS security advisories](#bucket-security-best-practices-security-advisories)

## Preventative security best practices<a name="bucket-security-best-practices-preventative-practices"></a>

The following best practices can help prevent security incidents with Lightsail buckets\.

### Implement least privilege access<a name="bucket-security-best-practices-least-privilege-access"></a>

When granting permissions, you decide who is getting what permissions to which Lightsail resources\. You enable specific actions that you want to allow on those resources\. Therefore, you should grant only the permissions that are required to perform a task\. Implementing least privilege access is fundamental in reducing security risk and the impact that could result from errors or malicious intent\.

For more information about creating an IAM policy to manage buckets, see [IAM policy to manage buckets in Amazon Lightsail](amazon-lightsail-bucket-management-policies.md)\. For more information about the Amazon S3 actions supported by Lightsail buckets, see [Actions for object storage](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_Amazon_S3.html) in the *Amazon Lightsail API reference*\.

### Verify that your Lightsail buckets are not publicly accessible<a name="bucket-security-best-practices-verify-bucket-permissions"></a>

Buckets and objects are private by default\. Keep your bucket private by having the bucket access permission set to **All objects are private**\. For the majority of use\-cases, you don't need to make your bucket or individual objects public\. For more information, see [Configuring access permissions for individual objects in a bucket in Amazon Lightsail](amazon-lightsail-configuring-individual-object-access.md)\.

![\[Bucket access permissions in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-bucket-access-permission-all-objects-private.png)

However, if you are using your bucket to host media for your website or application, under certain scenarios, you might need to make your bucket or individual objects public\. You can configure one of the following options to make your bucket or individual objects public:
+ If only some of the objects in a bucket need to be public \(read\-only\) to anyone on the internet, then change the bucket access permission to **Individual objects can be made public and read\-only**, and change only the objects that need to be public to **Public \(read\-only\)**\. This option keeps the bucket private, but gives you the option to make individual objects public\. Don't make an individual object public if it contains sensitive or confidential information that you don't want to be publicly accessible\. If you make individual objects public, you should periodically validate the public accessibility of each individual object\.   
![\[Bucket access permissions in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-bucket-access-permission-individual-objects-public.png)
+ If all objects in the bucket need to be public \(read\-only\) to anyone on the internet, then change the bucket access permission to **All objects are public and read\-only**\. Don't use this option if any of your objects in the bucket contain sensitive or confidential information\.  
![\[Bucket access permissions in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-bucket-access-permission-all-objects-public.png)
+ If you previously changed a bucket to be public, or changed individual objects to be public, you can quickly change the bucket and all its objects to be private by changing the bucket access permission to **All objects are private**\.  
![\[Bucket access permissions in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-bucket-access-permission-all-objects-private.png)

### Enable block public access in Amazon S3<a name="bucket-security-best-practices-block-public-access"></a>

Lightsail object storage resources take into account both Lightsail bucket access permissions and Amazon S3 account\-level block public access configurations when allowing or denying public access\. With Amazon S3 account\-level block public access, account administrators and bucket owners can centrally limit public access to their Amazon S3 and Lightsail buckets\. Block public access can make all Amazon S3 and Lightsail buckets private regardless of how the resources are created, and regardless of the individual bucket and object permissions that might have been configured\. For more information, see [Block public access for buckets in Amazon Lightsail](amazon-lightsail-block-public-access-for-buckets.md)\.

### Attach instances to buckets to grant full programmatic access<a name="bucket-security-best-practices-attach-instances"></a>

Attaching an instance to a Lightsail object storage bucket is the most secure way to provide access to the bucket\. The **Resource access** functionality, which is how you attach an instance to a bucket, grants the instance full programmatic access to the bucket\. With this method, you don't have to store bucket credentials directly in the instance or application, and you don't have to periodically rotate the credentials\. For example, some WordPress plugins can access a bucket that the instance has access to\. For more information, see [Configuring resource access for a bucket in Amazon Lightsail](amazon-lightsail-configuring-bucket-resource-access.md) and [Tutorial: Connecting a WordPress instance to an Amazon Lightsail bucket](amazon-lightsail-connecting-buckets-to-wordpress.md)\.

![\[Bucket resource access in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-bucket-resource-access-attached.png)

However, if the application is not on a Lightsail instance, then you can create and configure bucket access keys\. Bucket access keys are long term credentials that are not automatically rotated\.

![\[Bucket access keys in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-bucket-access-keys.png)

You can create and use access keys to grant applications or plugins full programmatic access to objects in your bucket\. If you use an access key with your bucket, you should periodically rotate your keys and take inventory of the existing keys\. Confirm the date an access key was last used, and the AWS Region in which it was used, correspond with your expectations of how the key should be used\. The date an access key was last used is displayed in the Lightsail console; in the **Access keys** section of the **Permissions** tab of a bucket's management page\. Delete access keys that are not being used\.

If you accidentally share your secret access key with the public, you should delete it and create a new one\. You can have a maximum of two access keys per bucket\. Even though you can have two different access keys at the same time, having one access key unused in your bucket is helpful for when you need to rotate a key with minimal downtime\. To rotate an access key, create a new one, configure it on your software and test it, and then delete the earlier key\. After you delete an access key, it's gone forever and can't be restored\. It can only be replaced with a new access key\. For more information, see [Creating access keys for a bucket in Amazon Lightsail](amazon-lightsail-creating-bucket-access-keys.md)\. 

### Use cross\-account access to give other AWS accounts access to objects in your bucket<a name="bucket-security-best-practices-cross-account-access"></a>

You can use cross\-account access to make objects in a bucket accessible to a specific individual who has an AWS account without making the bucket and its objects public\. If you've configured cross account access, make sure that the account IDs listed are the correct accounts that you want to give access to objects in your bucket\. For more information, see [Configuring cross\-account access for a bucket in Amazon Lightsail](amazon-lightsail-configuring-bucket-cross-account-access.md)\.

![\[Bucket cross-account access in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-bucket-cross-account-access.png)

### Encryption of data<a name="bucket-security-best-practices-data-encryption"></a>

Lightsail performs server\-side encryption with Amazon managed keys and encryption of data in transit by enforcing HTTPS \(TLS\)\. Server\-side encryption helps reduce risk to your data by encrypting the data with a key that is stored in a separate service\. In addition, encryption of data in transit helps prevent potential attackers from eavesdropping on or manipulating network traffic using person\-in\-the\-middle or similar attacks\.

### Enable versioning<a name="bucket-security-best-practices-enable-versioning"></a>

Versioning is a means of keeping multiple variants of an object in the same bucket\. You can use versioning to preserve, retrieve, and restore every version of every object stored in your Lightsail bucket\. With versioning, you can easily recover from both unintended user actions and application failures\. For more information, see [Enabling and suspending object versioning in a bucket in Amazon Lightsail](amazon-lightsail-managing-bucket-object-versioning.md)\.

## Monitoring and auditing best practices<a name="bucket-security-best-practices-monitoring-auditing"></a>

The following best practices can help detect potential security weaknesses and incidents for Lightsail buckets\.

### Enable access logging and perform periodic security and access audits<a name="bucket-security-best-practices-enable-access-logging"></a>

Access logging provides detailed records for the requests that are made to a bucket\. This information can include the request type \(`GET`, `PUT`\), the resources that are specified in the request, and the time and date that the request was processed\. Enable access logging for a bucket, and periodically perform a security and access audit to identify the entities that are accessing your bucket\. By default, Lightsail doesn't collect access logs for your buckets\. You must manually enable access logging\. For more information, see [Access logging for buckets in the Amazon Lightsail object storage service](amazon-lightsail-enabling-bucket-access-logs.md) and [Enabling access logging for a bucket in the Amazon Lightsail object storage service](amazon-lightsail-enabling-bucket-access-logs.md)\.

### Identify, tag, and audit your Lightsail buckets<a name="bucket-security-best-practices-identify-tag"></a>

Identification of your IT assets is a crucial aspect of governance and security\. You need to have visibility of all your Lightsail buckets to assess their security posture and take action on potential areas of weakness\.

Use tagging to identify security\-sensitive or audit\-sensitive resources, then use those tags when you need to search for these resources\. For more information, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

### Implement monitoring using AWS monitoring tools<a name="bucket-security-best-practices-monitoring-tools"></a>

Monitoring is an important part of maintaining the reliability, security, availability, and performance of Lightsail buckets and other resources\. You can monitor and create notification alarms for the **Bucket size** \(`BucketSizeBytes`\) and `Number of objects` \(**NumberOfObjects**\) bucket metrics in Lightsail\. For example, you might want to be notified when the size of your bucket increases or decreases to a specific size, or when the number of objects in your bucket goes up to or down to a specific number\. For more information, see [Creating bucket metric alarms in Amazon Lightsail](amazon-lightsail-adding-bucket-metric-alarms.md)\. 

### Use AWS CloudTrail<a name="bucket-security-best-practices-cloudtrail"></a>

AWS CloudTrail provides a record of actions taken by a user, a role, or an AWS service in Lightsail\. You can use information collected by CloudTrail to determine the request that was made to Lightsail, the IP address from which the request was made, who made the request, when it was made, and additional details\. For example, you can identify CloudTrail entries for actions that impact data access, in particular `CreateBucketAccessKey`, `GetBucketAccessKeys`, `DeleteBucketAccessKey`, `SetResourceAccessForBucket`, and `UpdateBucket`\. When you set up your AWS account, CloudTrail is enabled by default\. You can view recent events in the CloudTrail console\. To create an ongoing record of activity and events for your Lightsail buckets, you can create a trail in the CloudTrail console\. For more information, see [Logging Data Events for Trails](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/logging-data-events-with-cloudtrail.html) in the *AWS CloudTrail User Guide*\.

### Monitor AWS security advisories<a name="bucket-security-best-practices-security-advisories"></a>

Actively monitor the primary email address registered to AWS account\. AWS will contact you, using this email address, about emerging security issues that might affect you\.

AWS operational issues with broad impact are posted on the [AWS Service Health Dashboard](https://status.aws.amazon.com/)\. Operational issues are also posted to individual accounts via the Personal Health Dashboard\. For more information, see the [AWS Health Documentation](https://docs.aws.amazon.com/health/)\.

## Managing buckets and objects in Lightsail<a name="bucket-security-best-practices-managing-buckets-and-objects"></a>

These are the general steps to manage your Lightsail object storage bucket:

1. Learn about objects and buckets in the Amazon Lightsail object storage service\. For more information, see [Object storage in Amazon Lightsail](buckets-in-amazon-lightsail.md)\.

1. Learn about the names that you can give your buckets in Amazon Lightsail\. For more information, see [Bucket naming rules in Amazon Lightsail](bucket-naming-rules-in-amazon-lightsail.md)\.

1. Get started with the Lightsail object storage service by creating a bucket\. For more information, see [Creating buckets in Amazon Lightsail](amazon-lightsail-creating-buckets.md)\.

1. Learn about security best practices for buckets and the access permissions that you can configure for your bucket\. You can make all objects in your bucket public or private, or you can choose to make individual objects public\. You can also grant access to your bucket by creating access keys, attaching instances to your bucket, and granting access to other AWS accounts\. For more information, see [Security Best Practices for Amazon Lightsail object storage](#amazon-lightsail-bucket-security-best-practices) and [Understanding bucket permissions in Amazon Lightsail](amazon-lightsail-understanding-bucket-permissions.md)\.

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

1. Delete your bucket if you're no longer using it\. For more information, see [Deleting buckets in Amazon Lightsail](amazon-lightsail-deleting-buckets.md)\.