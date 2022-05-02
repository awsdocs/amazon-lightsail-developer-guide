# Enabling access logging for a bucket in the Amazon Lightsail object storage service<a name="amazon-lightsail-enabling-bucket-access-logs"></a>

 *Last updated: January 7, 2022* 

Access logging provides detailed records for the requests that are made to a bucket in the Amazon Lightsail object storage service\. Access logs are useful for many applications\. For example, access log information can be useful in security and access audits\. It can also help you learn about your customer base\.

By default, Lightsail doesn't collect access logs for your buckets\. When you enable logging, Lightsail delivers access logs for a source bucket to a target bucket that you choose\. Both the source and target buckets must be in the same AWS Region and owned by the same account\.

An access log record contains details about the requests that are made to a bucket\. This information can include the request type, the resources that are specified in the request, and the time and date that the request was processed\. In this guide, we show you how to enable or disable access logging for your buckets by using the Lightsail API, the AWS Command Line Interface \(AWS CLI\), or AWS SDKs\.

For more information about logging basics, see [Access logging for buckets in the Amazon Lightsail object storage service](amazon-lightsail-bucket-access-logs.md)\.

**Contents**
+ [Costs for access logging](#costs-for-access-logging)
+ [Enabling access logging using the AWS CLI](#enabling-access-logging)
+ [Disabling access logging using the AWS CLI](#disabling-access-logging)
+ [Managing buckets and objects in Lightsail](#enabling-bucket-access-log-managing-buckets-and-objects)

## Costs for access logging<a name="costs-for-access-logging"></a>

There is no extra charge for enabling access logging on a bucket\. However, log files that the system delivers to a bucket will use up storage space\. You can delete the log files at any time\. We do not assess data transfer charges for log file delivery when the log bucket's data transfer is within its configured monthly allowance\.

Your target bucket should not have access logging enabled\. You can have logs delivered to any bucket that you own that is in the same Region as the source bucket, including the source bucket itself\. However, for simpler log management, we recommend that you save access logs in a different bucket\.

## Enabling access logging using the AWS CLI<a name="enabling-access-logging"></a>

To enable access logging for your buckets, we recommend that you create a dedicated logging bucket in each AWS Region that you have buckets\. Then have the access log delivered to that dedicated logging bucket\.

Complete the following procedure to enable access logging using the AWS CLI\.

**Note**  
You must install the AWS CLI and configure it for Lightsail before continuing with this procedure\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a Command Prompt or Terminal window on your local computer\.

1. Enter the following command to enable access logging\.

   ```
   aws lightsail update-bucket --bucket-name SourceBucketName --access-log-config "{\"enabled\": true, \"destination\": \"TargetBucketName\", \"prefix\": \"ObjectKeyNamePrefix/\"}"
   ```

   In the command, replace the following example text with your own:
   + *SourceBucketName* \- The name of the source bucket for which the access logs will be created\.
   + *TargetBucketName* – The name of the target bucket where the access logs will be saved\.
   + *ObjectKeyNamePrefix/* \- The optional object key name prefix for the access logs\. Note that the prefix must end with a forward slash \(`/`\)\.

   **Example**

   ```
   aws lightsail update-bucket --bucket-name MyExampleBucket --access-log-config "{\"enabled\": true, \"destination\": \"MyExampleLogDestinationBucket\", \"prefix\": \"logs/MyExampleBucket/\"}"
   ```

   In the example, *MyExampleBucket* is the source bucket for which access logs will be created, *MyExampleLogDestinationBucket* is the destination bucket where the access logs will be saved, and *logs/MyExampleBucket/* is the object key name prefix for the access logs\.

   You should see a result similar to the following example after running the command\. The source bucket is updated, and the access logs should begin generating and being stored on the destination bucket\.  
![\[Access logging for a bucket enabled\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-enable-access-logging-for-a-bucket.png)

## Disabling access logging using the AWS CLI<a name="disabling-access-logging"></a>

Complete the following procedure to disable access logging using the AWS CLI\.

**Note**  
You must install the AWS CLI and configure it for Lightsail before continuing with this procedure\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a Command Prompt or Terminal window on your local computer\.

1. Enter the following command to disable access logging\.

   ```
   aws lightsail update-bucket --bucket-name SourceBucketName --access-log-config "{\"enabled\": false}"
   ```

   In the command, replace *SourceBucketName* with the name of the source bucket for which to disable access logging\.

   **Example**

   ```
   aws lightsail update-bucket --bucket-name MyExampleBucket --access-log-config "{\"enabled\": false}"
   ```

   You should see a result similar to the following example after running the command\.  
![\[Access logging for a bucket disabled\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-disable-access-logging-for-a-bucket.png)

## Managing buckets and objects in Lightsail<a name="enabling-bucket-access-log-managing-buckets-and-objects"></a>

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
   + [Enabling access logging for a bucket in the Amazon Lightsail object storage service](#amazon-lightsail-enabling-bucket-access-logs)
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