# Deleting objects in a bucket in Amazon Lightsail<a name="amazon-lightsail-deleting-bucket-objects"></a>

 *Last updated: July 14, 2021* 

You can delete objects from your bucket in the Amazon Lightsail object storage service\. To free\-up storage space, delete objects that you no longer need \. For example, if you're collecting log files, it's a good idea to delete them when you don't need them anymore\.

For more information about buckets, see [Object storage in Amazon Lightsail](buckets-in-amazon-lightsail.md)\.

**Contents**
+ [Deleting objects from a version\-enabled bucket](#deleting-objects-from-version-enabled-buckets)
+ [Delete objects using the Lightsail console](#deleting-objects-lightsail-console)
+ [Delete object versions using the Lightsail console](#deleting-object-versions-lightsail-console)
+ [Delete a single object or object version using the AWS CLI](#deleting-single-object-aws-cli)
+ [Delete multiple objects or object versions using the AWS CLI](#delete-objects-aws-cli)

## Deleting objects from a version\-enabled bucket<a name="deleting-objects-from-version-enabled-buckets"></a>

If versioning is enabled on your bucket, multiple versions of the same object can exist in it\. You can delete any version of an object using the Lightsail console, AWS CLI\), AWS APIs, or AWS SDKS\. However, you should consider the following options\.

**Deleting objects and object versions using the Lightsail console**

When you delete the current version of an object in the **Objects browser pane** of the **Objects** tab in the Lightsail console, this also deletes all previous versions of the object\. To delete a specific version of an object, you must do so from the **Manage versions** pane\. If you use the **Manage versions** pane to delete the current version of an object, then the most recent previous version is restored as the current version\. For more information, see [Delete object versions using the Lightsail console](#deleting-object-versions-lightsail-console) later in this guide\.

**Deleting objects and object versions using the Lightsail API, AWS CLI, or AWS SDKs**

To delete a single object and all of its stored versions, specify only the object's key in your delete request\. To delete a specific version of an object, specify both the object key and also a version ID\. For more information, see [Delete a single object or object version using the AWS CLI](#deleting-single-object-aws-cli) later in this guide\.

## Delete objects using the Lightsail console<a name="deleting-objects-lightsail-console"></a>

Complete the following procedure to delete an object, including its stored previous versions, using the Lightsail console\. You can delete only one object at a time using the Lightsail console\. Use the AWS CLI to delete multiple objects at once\. For more information, see [Delete multiple objects or object versions using the AWS CLI](#delete-objects-aws-cli) later in this guide\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Storage** tab\.

1. Choose the name of the bucket for which you want to delete objects\.

1. Use the **Objects browser** pane in the **Objects** tab to browse to the location of the object that you want to delete\.

1. Add a checkmark next to the object that you want to delete\.

1. In the **Object information** pane, choose the actions \(⋮\) menu, and then choose **Delete**\.

1. In the confirmation pane that appears, confirm that you want to permanently delete the object by choosing **Yes, delete**\.

   If you delete the only object in the folder that you're in, this also deletes the folder\. This happens because the folder is part of the object key name, and deleting the object also deletes the preceding folders when no other objects in the bucket share the same object prefix\. For more information, see [Understanding object key names in Amazon Lightsail](understanding-bucket-object-key-names-in-amazon-lightsail.md)\.

## Delete object versions using the Lightsail console<a name="deleting-object-versions-lightsail-console"></a>

Complete the following procedure to delete stored versions of an object\. This is only possible for version\-enabled buckets\. For more information, see [Enabling and suspending object versioning in a bucket in Amazon Lightsail](amazon-lightsail-managing-bucket-object-versioning.md)\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Storage** tab\.

1. Choose the name of the bucket for which you want to delete objects\.

1. Use the **Objects browser** pane to browse to the location of the object that you want to delete\.

1. Add a checkmark next to the object for which you want to delete stored previous versions\.

1. Choose **Manage** in the **Versions** section of the **Object information** pane, and then choose Manage\.

1. In the **Manage stored object versions** pane that appears, add a checkmark next to the versions of the object that you want to delete\.

   You can also choose to delete the current version of an object\.

1. Choose **Delete selected** to delete the selected versions\.

   If you delete:
   + The current version of an object \- The most recent previous version of the object is restored as the current version\.
   + The only version of an object \- The object is deleted from the bucket\. If the version you deleted is the only object in the current folder, then the folder is deleted also\. This happens because the folder is part of the object key name, and deleting the object also deletes the preceding folders when no other objects in the bucket share the same object key prefix\. For more information, see [Enabling and suspending object versioning in a bucket in Amazon Lightsail](amazon-lightsail-managing-bucket-object-versioning.md)\.

## Delete a single object or object version using the AWS CLI<a name="deleting-single-object-aws-cli"></a>

Complete the following procedure to delete a single object or object version in your bucket using the AWS Command Line Interface \(AWS CLI\)\. You do this by using the `delete-object` command\. For more information, see [delete\-object](https://docs.aws.amazon.com/cli/latest/reference/s3api/delete-object.html) in the *AWS CLI Command Reference*\.

**Note**  
You must install the AWS CLI and configure it for Lightsail and Amazon S3 before continuing with this procedure\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to delete an object or an object version in your bucket\.

   To delete an object:

   ```
   aws s3api delete-object --bucket BucketName --key ObjectKey
   ```

   To delete an object version:
**Note**  
Deleting object versions is only possible for version\-enabled buckets\. For more information, see [Enabling and suspending object versioning in a bucket in Amazon Lightsail](amazon-lightsail-managing-bucket-object-versioning.md)\.

   ```
   aws s3api delete-object --bucket BucketName --key ObjectKey --version-id VersionID
   ```

   In the command, replace the following example text with your own:
   + *BucketName* \- The name of the bucket from which you want to delete an object\.
   + *ObjectKey* \- The full object key of the object you want to delete\.
   + *VersionID* \- The ID of the object version you want to delete\.

   Examples:

   Deleting an object:

   ```
   aws s3api delete-object --bucket DOC-EXAMPLE-BUCKET --key images/sailbot.jpg
   ```

   Deleting an object version:

   ```
   aws s3api delete-object --bucket DOC-EXAMPLE-BUCKET --key images/sailbot.jpg --version-id YF0YMBlUvexampleO07l2vJi9hRz4ujX
   ```

   You should see a result similar to the following example:  
![\[Result of the AWS CLI delete-object command\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-s3api-delete-object-version-result.png)

## Delete multiple objects or object versions using the AWS CLI<a name="delete-objects-aws-cli"></a>

Complete the following procedure to delete multiple objects in your bucket using the AWS Command Line Interface \(AWS CLI\)\. You do this by using the `delete-objects` command\. For more information, see [delete\-objects](https://docs.aws.amazon.com/cli/latest/reference/s3api/delete-objects.html) in the AWS CLI Command Reference\.

**Note**  
You must install the AWS CLI and configure it for Lightsail and Amazon S3 before continuing with this procedure\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to delete multiple objects or multiple object versions in your bucket\.

   ```
   aws s3api delete-objects --bucket BucketName --delete file://LocalDirectory
   ```

   In the command, replace the following example text with your own:
   + *BucketName* \- The name of the bucket from which you want to delete multiple objects or multiple object versions\.
   + *LocalDirectory* \- The directory path on your computer of the \.json document that specifies the objects or versions to delete\. The \.json document can be formatted as follows\.

     To delete objects, enter the following text in the \.json file and replace *ObjectKey* with the object key of the objects you want to delete\.

     ```
     {
       "Objects": [
         {
           "Key": "ObjectKey1"
         },
         {
           "Key": "ObjectKey2"
         }
       ],
       "Quiet": false
     }
     ```

     To delete object versions, enter the following text in the \.json file\. Replace *ObjectKey* and *VersionID* with the object key and IDs of the object versions that you want to delete\.
**Note**  
Deleting object versions is only possible for version\-enabled buckets\. For more information, see [Enabling and suspending object versioning in a bucket in Amazon Lightsail](amazon-lightsail-managing-bucket-object-versioning.md)\.

     ```
     {
       "Objects": [
         {
           "Key": "ObjectKey1",
           "VersionId": "VersionID1"
         },
         {
           "Key": "ObjectKey2",
           "VersionId": "VersionID2"
         }
       ],
       "Quiet": false
     }
     ```

   Examples:
   + On a Linux or Unix computer:

     ```
     aws s3api delete-objects --bucket DOC-EXAMPLE-BUCKET --delete file://home/user/Documents/delete-objects.json
     ```
   + On a Windows computer:

     ```
     aws s3api delete-objects --bucket DOC-EXAMPLE-BUCKET --delete file://C:\Users\user\Documents\delete-objects.json
     ```

   You should see a result similar to the following example:  
![\[Result of the AWS CLI delete-objects command\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-s3api-delete-objects-version-result.png)

## Managing buckets and objects in Lightsail<a name="deleting-objects-managing-buckets-and-objects"></a>

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
   + [Deleting objects in a bucket in Amazon Lightsail](#amazon-lightsail-deleting-bucket-objects)

1. Enable object versioning to preserve, retrieve, and restore every version of every object stored in your bucket\. For more information, see [Enabling and suspending object versioning in a bucket in Amazon Lightsail](amazon-lightsail-managing-bucket-object-versioning.md)\.

1. After enabling object versioning, you can restore previous versions of objects in your bucket\. For more information, see [Restoring previous versions of objects in a bucket in Amazon Lightsail](amazon-lightsail-restoring-bucket-object-versions.md)\.

1. Monitor the utilization of your bucket\. For more information, see [Viewing metrics for your bucket in Amazon Lightsail](amazon-lightsail-viewing-bucket-metrics.md)\.

1. Configure an alarm for bucket metrics to be notified when the utilization of your bucket crosses a threshold\. For more information, see [Creating bucket metric alarms in Amazon Lightsail](amazon-lightsail-adding-bucket-metric-alarms.md)\.

1. Change the storage plan of your bucket if it's running low on storage and network transfer\. For more information, see [Changing the plan of your bucket in Amazon Lightsail](amazon-lightsail-changing-bucket-plans.md)\.

1. Learn how to connect your bucket to other resources\. For more information, see the following tutorials\.
   + [Tutorial: Connecting a WordPress instance to an Amazon Lightsail bucket](amazon-lightsail-connecting-buckets-to-wordpress.md)
   + [Tutorial: Using an Amazon Lightsail bucket with a Lightsail content delivery network distribution](amazon-lightsail-using-distributions-with-buckets.md)

1. Delete your bucket if you're no longer using it\. For more information, see [Deleting buckets in Amazon Lightsail](amazon-lightsail-deleting-buckets.md)\.