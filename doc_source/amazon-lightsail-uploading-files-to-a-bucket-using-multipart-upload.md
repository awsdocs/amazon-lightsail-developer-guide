# Uploading files to a bucket in Amazon Lightsail using multipart upload<a name="amazon-lightsail-uploading-files-to-a-bucket-using-multipart-upload"></a>

 *Last updated: January 10, 2022* 

Multipart upload allows you to upload a single file to your bucket as a set of parts\. Each part is a contiguous portion of the file's data\. You can upload these file parts independently and in any order\. If transmission of any part fails, you can retransmit that part without affecting other parts\. After all parts of your file are uploaded, Amazon S3 assembles these parts and creates the object in your bucket in Amazon Lightsail\. In general, when your object size reaches 100 MB, you should consider using multipart uploads instead of uploading the object in a single operation\. For more information about buckets, see [Object storage in Amazon Lightsail](buckets-in-amazon-lightsail.md)\.

Using multipart upload provides the following advantages:
+ Improved throughput \- You can upload parts in parallel to improve throughput\.
+ Quick recovery from any network issues \- Smaller part size minimizes the impact of restarting a failed upload due to a network error\.
+ Upload over time \- You can upload file parts over time\. After you initiate a multipart upload, you have 24 hours to complete the multipart upload\.
+ Begin an upload before you know the final file size \- You can upload a file as you are creating it\.

We recommend that you use multipart upload in the following ways:
+ If you're uploading large files over a stable high\-bandwidth network, multipart upload maximizes the use of your available bandwidth by uploading file parts in parallel for multi\-threaded performance\.
+ If you're uploading over a spotty network, use multipart upload to increase resiliency to network errors by avoiding upload restarts\. When using multipart upload, you retry uploads only for the interrupted parts\. There's no need to start over or upload the entire file again\.

**Contents:**
+ [Multipart upload process](#mutipart-upload-process)
+ [Concurrent multipart upload operations](#concurrent-multipart-upload-operations)
+ [Multipart upload retention](#multipart-upload-retention)
+ [Amazon S3 multipart upload limits](#multipart-upload-limits)
+ [Split the file to upload](#split-the-file-to-upload)
+ [Initiate a multipart upload using the AWS CLI](#initiate-multipart-upload)
+ [Upload a part using the AWS CLI](#upload-a-part)
+ [List parts of a multipart upload using the AWS CLI](#list-parts-of-multipart-upload)
+ [Create a multipart upload \.json file](#create-multipart-upload-json-file)
+ [Complete a multipart upload using the AWS CLI](#complete-multipart-upload)
+ [List multipart uploads for a bucket using the AWS CLI](#list-multipart-uploads)
+ [Stop a multipart upload using the AWS CLI](#stop-multipart-uploads)

## Multipart upload process<a name="mutipart-upload-process"></a>

Multipart upload is a three\-step process that uses Amazon S3 actions to upload files to your bucket in Lightsail:

1. You initiate the multipart upload using the [CreateMultipartUpload](https://docs.aws.amazon.com/AmazonS3/latest/API/API_CreateMultipartUpload.html) action\.

1. You upload the file parts using the [UploadPart](https://docs.aws.amazon.com/AmazonS3/latest/API/API_UploadPart.html) action\.

1. You complete the multipart upload using the [CompleteMultipartUpload](https://docs.aws.amazon.com/AmazonS3/latest/API/API_CompleteMultipartUpload.html) action\.

**Note**  
You can stop a multipart upload after you've initiated it by using the [AbortMultipartUpload](https://docs.aws.amazon.com/AmazonS3/latest/API/API_AbortMultipartUpload.html) action\.

When the multipart upload request completes, Amazon S3 constructs the object from the uploaded parts\. Then you can access the object in the same way that you would access any other object in your bucket\.

You can list all of your in\-progress multipart uploads or get a list of the parts that you have uploaded for a specific multipart upload\. Each of these operations is explained in this section\.

**Multipart upload initiation**

When you send a request to initiate a multipart upload, Amazon S3 returns a response with an upload ID\. This is a unique identifier for your multipart upload\. You must include the upload ID whenever you upload parts, list the parts, complete an upload, or stop an upload\. If you want to provide any metadata describing the object being uploaded, you must specify the metadata in the request to initiate multipart upload\.

**Parts upload**

When uploading a part, in addition to the upload ID, you must specify a part number\. You can choose any part number between 1 and 10,000\. A part number uniquely identifies a part and its position in the object you are uploading\. The part number that you choose doesn’t need to be in a consecutive sequence \(for example, it can be 1, 5, and 14\)\. If you upload a new part using the same part number as a previously uploaded part, the previously uploaded part is overwritten\.

Whenever you upload a part, Amazon S3 returns an ETag header in its response\. For each part upload, you must record the part number and the ETag value\. You must include these values in the subsequent request to complete the multipart upload\.

**Note**  
All uploaded parts of a multipart upload are stored on your bucket\. They consume your bucket's storage space until you complete the upload, stop the upload, or the upload times\-out\. For more information, see [Multipart upload retention](#multipart-upload-retention) later in this guide\.

**Multipart upload completion**

When you complete a multipart upload, Amazon S3 creates an object by concatenating the parts in ascending order based on the part number\. If any object metadata was provided in the initiate multipart upload request, Amazon S3 associates that metadata with the object\. After a successful complete request, the parts no longer exist\.

Your complete multipart upload request must include the upload ID and a list of both part numbers and corresponding ETag values\. The Amazon S3 response includes an ETag that uniquely identifies the combined object data\. This ETag is not necessarily an MD5 hash of the object data\.

You can optionally stop the multipart upload\. After stopping a multipart upload, you cannot upload any part using that upload ID again\. All storage from any part of the canceled multipart upload is then freed\. If any part uploads were in\-progress, they can still succeed or fail even after you stop\. To free all storage consumed by all parts, you must stop a multipart upload only after all part uploads have completed\.

**Multipart upload listings**

You can list the parts of a specific multipart upload or all in\-progress multipart uploads\. The list parts operation returns the parts information that you have uploaded for a specific multipart upload\. For each list parts request, Amazon S3 returns the parts information for the specified multipart upload, up to a maximum of 1,000 parts\. If there are more than 1,000 parts in the multipart upload, you must send a series of list part requests to retrieve all the parts\. Note that the returned list of parts doesn't include parts that are still in the process of uploading\. Using the list multipart uploads operation, you can obtain a list of multipart uploads in progress\.

An in\-progress multipart upload is an upload that you have initiated, but have not yet completed or stopped\. Each request returns at most 1,000 multipart uploads\. If there are more than 1,000 multipart uploads in progress, you must send additional requests to retrieve the remaining multipart uploads\. Only use the returned listing for verification\. Do not use the result of this listing when sending a complete multipart upload request\. Instead, maintain your own list of the part numbers you specified when uploading parts and the corresponding ETag values that Amazon S3 returns\.

## Concurrent multipart upload operations<a name="concurrent-multipart-upload-operations"></a>

In a distributed development environment, it is possible for your application to initiate several updates on the same object at the same time\. Your application might initiate several multipart uploads using the same object key\. For each of these uploads, your application can then upload parts and send a complete upload request to Amazon S3 to create the object\. When the buckets have versioning enabled, completing a multipart upload always creates a new version\. For buckets that don't have versioning enabled, other request might take precedence, such as requests that are received after a multipart upload is initiated and before it's complete\.

**Note**  
It is possible for other requests to take precedence, such as requests that are received after you initiate a multipart upload and before it is complete\. For example, another operation might delete a key after you initiate a multipart upload with that key, and before the multipart upload is complete\. If this occurs, the complete multipart upload response might indicate a successful object creation without you ever seeing the object\.

## Multipart upload retention<a name="multipart-upload-retention"></a>

All uploaded parts of a multipart upload are stored on your bucket\. They consume your bucket's storage space until you complete the upload, stop the upload, or the upload times out\. A multipart upload times out, and the multipart upload is deleted, after 24 hours from when it was created\. When you stop a multipart upload, or it times out, all uploaded parts are deleted and the storage space they used to consume on your bucket is freed\.

## Amazon S3 multipart upload limits<a name="multipart-upload-limits"></a>

The following table provides multipart upload core specifications\.
+ Maximum object size: 5 TB
+ Maximum number of parts per upload: 10,000
+ Part numbers: 1\-10,000 \(inclusive\)
+ Part size: 5 MB \(minimum\) \- 5 GB \(maximum\)\. There is no size limit on the last part of your multipart upload\.
+ Maximum number of parts returned for a list parts request: 1,000
+ Maximum number of multipart uploads returned in a list multipart uploads request: 1,000

## Split the file to upload<a name="split-the-file-to-upload"></a>

Use the `split` command on the Linux or Unix operating system to split a file into multiple parts that you then upload to your bucket\. There are similar free\-ware applications that you can use on the Windows operating system to split a file\. After you split the file into multiple parts, continue to the [Initiate a multipart upload](#initiate-multipart-upload) section of this guide\.

## Initiate a multipart upload using the AWS CLI<a name="initiate-multipart-upload"></a>

Complete the following procedure to initiate a multipart upload using the AWS Command Line Interface \(AWS CLI\)\. You do this by using the `create-multipart-upload` command\. For more information, see [create\-multipart\-upload](https://docs.aws.amazon.com/cli/latest/reference/s3api/create-multipart-upload.html) in the *AWS CLI Command Reference*\.

**Note**  
You must install the AWS CLI and configure it for Lightsail and Amazon S3 before continuing with this procedure\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to create a multipart upload for your bucket\.

   ```
   aws s3api create-multipart-upload --bucket BucketName --key ObjectKey --acl bucket-owner-full-control
   ```

   In the command, replace the following example text with your own:
   + *BucketName* \- The name of the bucket for which you want to create a multipart upload\.
   + *ObjectKey* \- The object key to use for the file that you will upload\.

   Example:

   ```
   aws s3api create-multipart-upload --bucket DOC-EXAMPLE-BUCKET --key sailbot.mp4 --acl bucket-owner-full-control
   ```

   You should see a result similar to the following example\. The response includes an `UploadID`, which you must specify in subsequent commands to upload parts, and to complete the multipart upload for this object\.  
![\[Result of the create-multipart-upload command\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-s3api-create-multipart-upload-result.png)

   After you have the `UploadID` for your multipart upload, continue to the following [Upload a part using the AWS CLI](#upload-a-part) section of this guide and start uploading parts\.

## Upload a part using the AWS CLI<a name="upload-a-part"></a>

Complete the following procedure to upload a part of a multipart upload using the AWS Command Line Interface \(AWS CLI\)\. You do this by using the `upload-part` command\. For more information, see [upload\-part](https://docs.aws.amazon.com/cli/latest/reference/s3api/upload-part.html) in the *AWS CLI Command Reference*\.

**Note**  
You must install the AWS CLI and configure it for Lightsail and Amazon S3 before continuing with this procedure\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to upload a part to your bucket\.

   ```
   aws s3api upload-part --bucket BucketName --key ObjectKey --part-number Number --body FilePart --upload-id "UploadID"  --acl bucket-owner-full-control
   ```

   In the command, replace the following example text with your own:
   + *BucketName* \- The name of the bucket for which you want to create a multipart upload\.
   + *ObjectKey* \- The object key to use for the file that you will upload\.
   + *Number* \- The part number of the part you are uploading\. A part number uniquely identifies a part and its position in the object you are uploading\. Make sure to incrementally increase the `--part-number` parameter with each part that you upload\. To do so, number them in the order in which Amazon S3 should assemble the object when you complete the multipart upload\.
   + *FilePart* \- The part file to upload from your computer\.
   + *UploadID* \- The upload ID of the multipart upload that you created earlier in this guide\.

   Example:

   ```
   aws s3api upload-part --bucket DOC-EXAMPLE-BUCKET --key sailbot.mp4 --part-number 1 --body sailbot.mp4.001 --upload-id "R4QU.mO.exampleiHWiLOeNw7JtXX7OotRhTLsXXCzF21CZdYlfj5lfjtiMnpzVw2WPj.exampleBTmL_N_.42.DlHYOTsITFsX.tO3XOUTTAHiCxY5VR8jWRGdkVkUG" --acl bucket-owner-full-control
   ```

   You should see a result similar to the following example\. Repeat the `upload-part` command for each part you upload\. The response for each of your upload part requests will include an `ETag` value for the part that you uploaded\. Record the `ETag` values for each of the parts that you upload\. You will need all of the `ETag` values to complete the multipart upload, which is covered later in this guide\.  
![\[Result of the upload-part command\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-s3api-upload-part-result.png)

## List parts of a multipart upload using the AWS CLI<a name="list-parts-of-multipart-upload"></a>

Complete the following procedure to list parts of a multipart upload using the AWS Command Line Interface \(AWS CLI\)\. You do this by using the `list-parts` command\. For more information, see [list\-parts](https://docs.aws.amazon.com/cli/latest/reference/s3api/list-parts.html) in the *AWS CLI Command Reference*\.

Complete this procedure to get the `ETag` values for all of the uploaded parts in a multipart upload\. You will need these values to complete the multipart upload later in this guide\. However, if you recorded all of the `ETag` values from the response of your part uploads, then you can skip this procedure and continue to the [Create a multipart upload \.json](#create-multipart-upload-json-file) file section of this guide\.

**Note**  
You must install the AWS CLI and configure it for Lightsail and Amazon S3 before continuing with this procedure\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to list the parts of a multipart upload on your bucket\.

   ```
   aws s3api list-parts --bucket BucketName --key ObjectKey --upload-id "UploadID"
   ```

   In the command, replace the following example text with your own:
   + *BucketName* \- The name of the bucket for which you want to list the parts of a multipart upload\.
   + *ObjectKey* \- The object key of the multipart upload\.
   + *UploadID* \- The upload ID of the multipart upload that you created earlier in this guide\.

   Example:

   ```
   aws s3api list-parts --bucket DOC-EXAMPLE-BUCKET --key sailbot.mp4 --upload-id "R4QU.mO.exampleiHWiLOeNw7JtXX7OotRhTLsXXCzF21CZdYlfj5lfjtiMnpzVw2WPj.exampleBTmL_N_.42.DlHYOTsITFsX.tO3XOUTTAHiCxY5VR8jWRGdkVkUG"
   ```

   You should see a result similar to the following example\. The response lists all of the part numbers and `ETag` values for the parts that you uploaded in the multipart upload\. Copy these values to your clipboard, and continue to the [Create a multipart upload \.json](#create-multipart-upload-json-file) section of this guide\.  
![\[Result of the list-parts command\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-s3api-list-parts-result.png)

## Create a multipart upload \.json file<a name="create-multipart-upload-json-file"></a>

Complete the following procedure to create a multipart upload \.json file that defines all of the parts you uploaded and their `ETag` values\. This is required later in this guide to complete the multipart upload\.

1. Open a text editor, and paste the response from the `list-parts` command that you requested in the previous section of this guide\.

   The result should look like the following example\.  
![\[asdf\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-multipart-upload-json-file-1.png)

1. Reformat the text file as shown in the following example:  
![\[asdf\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-multipart-upload-json-file-2.png)

1. Save the text file to your computer as `mpstructure.json`, and continue to the [Complete a multipart upload using the AWS CLI](#complete-multipart-upload) section of this guide\.

## Complete a multipart upload using the AWS CLI<a name="complete-multipart-upload"></a>

Complete the following procedure to complete a multipart upload using the AWS Command Line Interface \(AWS CLI\)\. You do this by using the `complete-multipart-upload` command\. For more information, see [complete\-multipart\-upload](https://docs.aws.amazon.com/cli/latest/reference/s3api/complete-multipart-upload.html) in the *AWS CLI Command Reference*\.

**Note**  
You must install the AWS CLI and configure it for Lightsail and Amazon S3 before continuing with this procedure\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to upload a part to your bucket\.

   ```
   aws s3api complete-multipart-upload --multipart-upload file://JSONFileName --bucket BucketName --key ObjectKey --upload-id "UploadID"  --acl bucket-owner-full-control
   ```

   In the command, replace the following example text with your own:
   + *JSONFileName* \- The name of the \.json file that you created earlier in this guide \(for example, `mpstructure.json`\)\.
   + *BucketName* \- The name of the bucket for which you want to complete a multipart upload\.
   + *ObjectKey* \- The object key of the multipart upload\.
   + *UploadID* \- The upload ID of the multipart upload that you created earlier in this guide\.

   ```
   aws s3api complete-multipart-upload --multipart-upload file://mpstructure.json --bucket DOC-EXAMPLE-BUCKET --key sailbot.mp4 --upload-id "R4QU.mO.exampleiHWiLOeNw7JtXX7OotRhTLsXXCzF21CZdYlfj5lfjtiMnpzVw2WPj.exampleBTmL_N_.42.DlHYOTsITFsX.tO3XOUTTAHiCxY5VR8jWRGdkVkUG" --acl bucket-owner-full-control
   ```

   You should see a response similar to the following example\. This confirms that the multipart upload is completed\. The object is now assembled and available in the bucket\.  
![\[Result of the complete-multipart-upload command\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-s3api-complete-multipart-upload-result.png)

## List multipart uploads for a bucket using the AWS CLI<a name="list-multipart-uploads"></a>

Complete the following procedure to list all multipart uploads for a bucket using the AWS Command Line Interface \(AWS CLI\)\. You do this by using the `list-multipart-uploads` command\. For more information, see [list\-multipart\-uploads](https://docs.aws.amazon.com/cli/latest/reference/s3api/list-multipart-uploads.html) in the *AWS CLI Command Reference*\.

**Note**  
You must install the AWS CLI and configure it for Lightsail and Amazon S3 before continuing with this procedure\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to upload a part to your bucket\.

   ```
   aws s3api list-multipart-uploads --bucket BucketName
   ```

   In the command, replace *BucketName* with the name of the bucket for which you want to list all multipart uploads\.

   Example:

   ```
   aws s3api list-multipart-uploads --bucket DOC-EXAMPLE-BUCKET
   ```

   You should see a response similar to the following example\.  
![\[Result of the list-multipart-uploads command\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-s3api-list-multipart-uploads-result.png)

## Stop a multipart upload using the AWS CLI<a name="stop-multipart-uploads"></a>

Complete the following procedure to stop a multipart upload using the AWS Command Line Interface \(AWS CLI\)\. You do this if you started a multipart upload but no longer want to continue it\. You do this by using the `abort-multipart-upload` command\. For more information, see [abort\-multipart\-upload](https://docs.aws.amazon.com/cli/latest/reference/s3api/abort-multipart-upload.html) in the *AWS CLI Command Reference*\.

**Note**  
You must install the AWS CLI and configure it for Lightsail and Amazon S3 before continuing with this procedure\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to upload a part to your bucket\.

   ```
   aws s3api abort-multipart-upload --bucket BucketName --key ObjectKey --upload-id "UploadID" --acl bucket-owner-full-control
   ```

   In the command, replace the following example text with your own:
   + *BucketName* \- The name of the bucket for which you want to stop a multipart upload\.
   + *ObjectKey* \- The object key of the multipart upload\.
   + *UploadID* \- The upload ID of the multipart upload that you want to stop\.

   Example:

   ```
   aws s3api abort-multipart-upload --bucket DOC-EXAMPLE-BUCKET --key sailbot.mp4 --upload-id "R4QU.mO.exampleiHWiLOeNw7JtXX7OotRhTLsXXCzF21CZdYlfj5lfjtiMnpzVw2WPj.exampleBTmL_N_.42.DlHYOTsITFsX.tO3XOUTTAHiCxY5VR8jWRGdkVkUG" --acl bucket-owner-full-control
   ```

   This command does not return a response\. You can run a `list-multipart-uploads` command to confirm that the multipart upload was stopped\.

## Managing buckets and objects in Lightsail<a name="uploading-files-multipart-managing-buckets-and-objects"></a>

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
   + [Uploading files to a bucket in Amazon Lightsail using multipart upload](#amazon-lightsail-uploading-files-to-a-bucket-using-multipart-upload)
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