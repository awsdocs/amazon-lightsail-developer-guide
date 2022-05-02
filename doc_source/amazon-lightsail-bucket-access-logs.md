# Access logging for buckets in the Amazon Lightsail object storage service<a name="amazon-lightsail-bucket-access-logs"></a>

 *Last updated: November 1, 2021* 

Access logging provides detailed records for the requests that are made to a bucket in the Amazon Lightsail object storage service\. This information can include the request type, the resources that are specified in the request, and the time and date that the request was processed\. Access logs are useful for many applications\. For example, access log information can be useful in security and access audits\. It can also help you learn about your customer base\.

**Contents**
+ [What do I need to enable log delivery](#access-log-delivery)
+ [Log object key format](#log-object-key-format)
+ [How are logs delivered?](#how-are-logs-delivered)
+ [Best effort access log delivery](#best-effort-access-log-delivery)
+ [Bucket logging status changes take effect over time](#bucket-logging-status-changes)
+ [Additional information about access logging](#access-logging-additional-information)
+ [Managing buckets and objects in Lightsail](#bucket-access-logs-managing-buckets-and-objects)

## What do I need to enable log delivery?<a name="access-log-delivery"></a>

Consider the following before enabling log delivery\. For details, see [Enabling access logging for a bucket in the Amazon Lightsail object storage service](amazon-lightsail-enabling-bucket-access-logs.md)\.

1. **Identify the target bucket for the logs\.** This bucket is where you want Lightsail to save the access logs as objects\. Both the source and target buckets must be in the same AWS Region and owned by the same account\.

   You can have logs delivered to any bucket that you own that is in the same Region as the source bucket, including the source bucket itself\. But for simpler log management, we recommend that you save access logs in a different bucket\.

   When your source bucket and target bucket are the same bucket, additional logs are created for the logs that are written to the bucket\. This might not be ideal because it could result in a small increase in your storage consumption\. In addition, the extra logs about logs might make it harder to find the log that you are looking for\. If you choose to save access logs in the source bucket, we recommend that you specify a prefix for the log object keys so that the object names begin with a common string and the log objects are easier to identify\. Key prefixes are also useful to distinguish between source buckets when multiple buckets log to the same target bucket\.

1. **\(Optional\) Identify a prefix for the log object keys\.** The prefix makes it simpler for you to locate the log objects\. For example, if you specify the prefix value `logs/`, each log object that Lightsail creates begins with the `logs/` prefix in its key\. The trailing slash `/` is required to denote the end of the prefix\. Following is an example of a log object key with the `logs/` prefix:

   ```
   logs/2021-11-31-21-32-16-E568B2907131C0C0
   ```

## Log object key format<a name="log-object-key-format"></a>

Lightsail uses the following object key format for the log objects it uploads in the target bucket:

```
TargetPrefix/YYYY-mm-DD-HH-MM-SS-UniqueString
```

In the key, `YYYY`, `mm`, `DD`, `HH`, `MM`, and `SS` are the digits of the year, month, day, hour, minute, and seconds \(respectively\) when the log file was delivered\. These dates and times are in Coordinated Universal Time \(UTC\)\.

A log file delivered at a specific time can contain records written at any point before that time\. There is no way to know whether all log records for a certain time interval have been delivered or not\.

The `UniqueString` component of the key is there to prevent overwriting of files\. It has no meaning, and log processing software should ignore it\.

## How are logs delivered?<a name="how-are-logs-delivered"></a>

Lightsail periodically collects access log records, consolidates the records in log files, and then uploads log files to your target bucket as log objects\. If you enable logging on multiple source buckets that deliver to the same target bucket, the target bucket will have access logs for all those source buckets\. However, each log object reports access log records for a specific source bucket\.

## Best effort access log delivery<a name="best-effort-access-log-delivery"></a>

Access log records are delivered on a best effort basis\. Most requests for a bucket that is properly configured for logging result in a delivered log record\. Most log records are delivered within a few hours of the time that they are recorded, but they can be delivered more frequently\.

The completeness and timeliness of access logging is not guaranteed\. The log record for a particular request might be delivered long after the request was actually processed, or it might not be delivered at all\. The purpose of access logs is to give you an idea of the nature of traffic against your bucket\. It is rare to lose log records, but access logging is not meant to be a complete accounting of all requests\.

## Bucket logging status changes take effect over time<a name="bucket-logging-status-changes"></a>

Changes to the logging status of a bucket take time to actually affect the delivery of log files\. For example, if you enable logging for a bucket, some requests made in the following hour might be logged, while others might not\. If you change the target bucket for logging from bucket A to bucket B, some logs for the next hour might continue to be delivered to bucket A, while others might be delivered to the new target bucket B\. In all cases, the new settings eventually take effect without any further action on your part\.

## Additional information about access logging<a name="access-logging-additional-information"></a>

For more information about logging and log files, see the following guides:
+ [Enabling access logging for a bucket in the Amazon Lightsail object storage service](amazon-lightsail-enabling-bucket-access-logs.md)
+ [Access log format for a bucket in the Amazon Lightsail object storage service](amazon-lightsail-bucket-access-log-format.md)
+ [Using access logs for a bucket in Amazon Lightsail to identify requests](amazon-lightsail-using-bucket-access-logs.md)

## Managing buckets and objects in Lightsail<a name="bucket-access-logs-managing-buckets-and-objects"></a>

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
   + [Access logging for buckets in the Amazon Lightsail object storage service](#amazon-lightsail-bucket-access-logs)
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