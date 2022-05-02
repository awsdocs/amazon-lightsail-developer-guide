# Uploading files to a bucket in Amazon Lightsail<a name="amazon-lightsail-uploading-files-to-a-bucket"></a>

 *Last updated: Januay 10, 2022* 

When you upload a file to your bucket in the Amazon Lightsail object storage service, it is stored as an object\. Objects consist of the file data and metadata that describe the object\. You can have any number of objects in a bucket\.

You can upload any file type—images, backups, data, movies—into a bucket\. The maximum file size that you can upload by using the Lightsail console is 2 GB\. To upload a larger file, use the Lightsail API, AWS Command Line Interface \(AWS CLI\), or AWS SDKs\.

Lightsail offers the following options depending on the size of the file you want to upload:
+ **Upload an object up to 2 GB in size using the Lightsail Console** — With the Lightsail console, you can upload a single object up to 2 GB in size\. For more information, see [Upload files to a bucket using the Lightsail console](#uploading-files-to-a-bucket-lightsail-console) later in this guide\.
+ **Upload an object up to 5 GB in size with a single operation using the AWS SDKs, REST API, or AWS CLI** — With a single PUT operation, you can upload a single object up to 5 GB in size\. For more information, see [Upload files to a bucket using the AWS CLI](#uploading-files-to-a-bucket-aws-cli) later in this guide\.
+ **Upload an object in parts using the AWS SDKs, REST API, or AWS CLI** — Using the multipart upload API, you can upload a single large object, of 5 MB to 5 TB in size\. The multipart upload API is designed to improve the upload experience for larger objects\. You can upload an object in parts\. These object parts can be uploaded independently, in any order, and in parallel\. For more information, see [Uploading files to a bucket in Amazon Lightsail using multipart upload](amazon-lightsail-uploading-files-to-a-bucket-using-multipart-upload.md)\.

For more information about buckets, see [Object storage in Amazon Lightsail](buckets-in-amazon-lightsail.md)\.

## Object key names and versioning<a name="uploading-files-to-a-bucket-object-key-names"></a>

When you upload a file using the Lightsail console, the file name is used as the object key name\. An object key \(or key name\) uniquely identifies an object stored in a bucket\. The folder that the file is uploaded into, if any, is used as the key name prefix\. For example, if you upload a file named `sailbot.jpg` to a folder in your bucket named `images`, the full object key name and prefix will be `images/sailbot.jpg`\. However, the object is displayed in the console as `sailbot.jpg` in the `images` folder\. For more information about object key names, see [Understanding object key names in Amazon Lightsail](understanding-bucket-object-key-names-in-amazon-lightsail.md)\.

When you upload a directory using the Lightsail console, all of the files and subfolders in the directory are uploaded to the bucket\. Lightsail then assigns an object key name that is a combination of each of the uploaded file names and the folder name\. For example, if you upload a folder named `images` that contains two files, `sample1.jpg` and `sample2.jpg`, Lightsail uploads the files and then assigns the corresponding key names, `images/sample1.jpg` and `images/sample2.jpg`\. The objects are displayed in the console as `sample1.jpg` and `sample2.jpg` in the `images` folder\.

If you upload a file with a key name that already exists, and your bucket *does not have versioning enabled*, the new uploaded object replaces the previous object\. However, if your bucket *has versioning enabled*, Lightsail creates a new version of the object instead of replacing the existing object\. For more information, see [Enabling and suspending object versioning in a bucket in Amazon Lightsail](amazon-lightsail-managing-bucket-object-versioning.md)\.

## Upload files to a bucket using the Lightsail console<a name="uploading-files-to-a-bucket-lightsail-console"></a>

Complete the following procedure to upload files and directories using the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Storage** tab\.

1. Choose the name of the bucket that you want to upload files and folders into\.

1. In the **Objects** tab, perform one of the following actions:
   + Drag and drop files and folders to the **Objects** page\.
   + Choose **Upload**, and choose **File** to upload an individual file, or **Directory** to upload a folder and all of its contents\.
**Note**  
You can also create a folder in by choosing **Create new folder**\. You can then browse into the new folder and upload files to it\.

   An **Upload successful** message is displayed when the upload completes\.

## Upload files to a bucket using the AWS CLI<a name="uploading-files-to-a-bucket-aws-cli"></a>

Complete the following procedure to upload files and folders to a bucket using the AWS Command Line Interface \(AWS CLI\)\. You do this by using the `put-object` command\. For more information, see [put\-object](https://docs.aws.amazon.com/cli/latest/reference/s3api/put-object.html) in the *AWS CLI Command Reference*\.

**Note**  
You must install the AWS CLI and configure it for Lightsail and Amazon S3 before continuing with this procedure\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to upload a file to your bucket\.

   ```
   aws s3api put-object --bucket BucketName --key ObjectKey --body LocalDirectory --acl bucket-owner-full-control
   ```

   In the command, replace the following example text with your own:
   + *BucketName* with the name of the bucket to which you want to upload the file\.
   + *ObjectKey* with the full object key of the object in your bucket\.
   + *LocalDirectoryFire* with the local directory folder path on your computer of the file to upload\.

   Example:
   + On a Linux or Unix computer:

     ```
     aws s3api put-object --bucket DOC-EXAMPLE-BUCKET --key images/sailbot.jpg --body home/user/Pictures/sailbot.jpg --acl bucket-owner-full-control
     ```
   + On a Windows computer:

     ```
     aws s3api put-object --bucket DOC-EXAMPLE-BUCKET --key images/sailbot.jpg --body "C:\Users\user\Pictures\sailbot.jpg" --acl bucket-owner-full-control
     ```

   You should see a result similar to the following example:  
![\[Result of the AWS CLI put-object command\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-s3api-put-object-result.png)

## Managing buckets and objects in Lightsail<a name="uploading-files-managing-buckets-and-objects"></a>

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
   + [Uploading files to a bucket in Amazon Lightsail](#amazon-lightsail-uploading-files-to-a-bucket)
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