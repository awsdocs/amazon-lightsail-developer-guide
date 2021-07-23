# Object storage in Amazon Lightsail<a name="buckets-in-amazon-lightsail"></a>

 *Last updated: July 14, 2021* 

Use the Amazon Lightsail object storage service to store and retrieve objects, at any time, from anywhere on the internet\. It is designed to make web\-scale computing easier for developers, and is built using the Amazon Simple Storage Service \(Amazon S3\)\. Lightsail object storage gives you access to the same highly scalable, reliable, fast, inexpensive data storage infrastructure that Amazon uses to run its own global network of websites\. The service aims to maximize benefits of scale and to pass those benefits on to you\.

## Object storage concepts<a name="object-storage-concepts"></a>

The following concepts and terminology apply to Lightsail object storage\.

**Buckets**

A bucket is a container for objects stored in the Lightsail object storage service\. Every object is contained in a bucket, which has its own URL\. For example, if the object named `media/sailbot.jpg` is stored in the `DOC-EXAMPLE-BUCKET` bucket in the US East \(N\. Virginia\) Region \(`us-east-1`\), then it is addressable using a URL that is similar to `https://DOC-EXAMPLE-BUCKET.us-east-1.amazonaws.com/media/sailbot.jpg`\.

You can create buckets in AWS Regions where Lightsail is available\. For more information about which AWS Regions Lightsail is available in, see [Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/lightsail.html) in the *AWS General Reference*\.

**Bucket storage plans**

A storage plan, referred to as a *bundle* in the AWS API, specifies the monthly cost, storage space, and data transfer quota for your bucket\. You must choose a storage plan when you first create your bucket\. You can change it later after your bucket is up and running\.

You can change your bucket's plan only one time within your monthly AWS billing cycle\. Change your bucket's plan if it's consistently going over its storage space or data transfer quota, or if your bucket's usage is consistently in the lower range of its storage space or data transfer quota\. Because your bucket might experience unpredictable usage fluctuations, we strongly recommend that you change your bucket's plan only as a long\-term strategy, instead of as a short\-term, monthly cost\-cutting measure\. Choose a storage plan that will provide your bucket with ample an storage space and data transfer quotas for a long time to come\. 

**Objects**

Objects are the fundamental entities stored in buckets\. A file that you upload to your bucket is referred to as an object while it is being stored\. Objects consist of *data* and *metadata*\. The *data* portion is opaque to the Lightsail object storage service\. The *metadata* is a set of name\-value pairs that describe the object\. These include some default metadata \(such as the last modified date\), and standard HTTP metadata \(such as Content\-Type\)\.

An object is uniquely identified within a bucket by a key name and a version ID\.

**Object key names**

A key name is the unique identifier for an object in a bucket\. Every object in a bucket has exactly one key\. The combination of a bucket, key, and version ID uniquely identifies each object\. So you can think of Lightsail object storage as a basic data map between "bucket \+ key \+ version" and the object itself\. Every object in Lightsail object storage can be uniquely addressed through the combination of the web service endpoint, bucket name, key, and optionally, a version\. For example, in the URL `https://DOC-EXAMPLE-BUCKET.us-east-1.amazonaws.com/media/sailbot.jpg`, `DOC-EXAMPLE-BUCKET` is the name of the bucket and `media/sailbot.jpg` is the object key name\. 

**Object versioning**

Versioning is a feature that allows you to keep multiple variants of an object in the same bucket\. Enable versioning to preserve, retrieve, and restore every version of every object stored in your bucket\. With versioning, you can recover more easily from both unintended user actions and application failures\.

Versioning is disabled by default when you create a bucket\. After you enable versioning, every version of every object that you store in your bucket is retained until you manually delete the stored version\. For example, if you store the `media/sailbot.jpg` object, and later you store a larger file with the same object key name, then the original smaller object is retained as a *previous version*\. The new, larger object becomes the *current version*\. If you decide that you don't need the previous version of the object, you can delete it\. All stored previous versions of an object are deleted when you delete the current version of the object\.

Stored object versions consume your bucket's storage space in the same way as stored current versions of an object\. After you enable versioning, you can suspend it to stop storing object versions\. This also consumes less of your bucket's storage space when you upload new object versions\. When you suspend versioning, stored object versions are retained, but new object versions that you upload while versioning is suspended are not retained\.

**Bucket and object access**

By default, all object storage resources—buckets and objects—are private\. This means only the bucket owner, the Lightsail account that created it, can access the bucket and its objects\. The bucket owner can optionally grant access permissions to others\. This can be done by setting all objects or individual objects to public, which makes them readable to anyone in the world\. You can also grant full programmatic access by attaching Lightsail instances to your bucket, or by creating access keys for your bucket\. Finally, you can grant other AWS accounts programmatic read\-only access to your bucket\.

**AWS Regions**

You can create Lightsail object storage buckets in all of the AWS Regions in which Lightsail is available\. You might choose a Region to optimize latency, minimize costs, or address regulatory requirements\. Objects stored in an AWS Region do not leave the Region unless you explicitly transfer them to another Region\. For example, objects stored in the US West \(Oregon\) Region do not leave it\. 

## Managing buckets and objects<a name="managing-buckets-and-objects"></a>

Lightsail object storage is intentionally built with a minimal feature set that focuses on simplicity and robustness\. Following are some of the elements of managing buckets and objects:
+ **Create buckets** – Create a bucket that stores data\. Buckets are the fundamental containers in the Lightsail object storage service\. For more information, see [Creating buckets in Amazon Lightsail](amazon-lightsail-creating-buckets.md)\.
+ **Store data** – Upload files to your bucket using the Lightsail console, AWS Command Line Interface \(AWS CLI\), and AWS APIs\. For more information about uploading files, see [Uploading files to a bucket in Amazon Lightsail](amazon-lightsail-uploading-files-to-a-bucket.md)\.
+ **Download data** – Download your stored objects anytime you want\. For more information, see [Downloading objects from a bucket in Amazon Lightsail](amazon-lightsail-downloading-bucket-objects.md)\.
+ **Grant access** – Grant or deny access to others \(such as software or individuals\), who want to upload data or download data that is in your bucket\. Authentication mechanisms can help keep data secure from unauthorized access\. For more information, see [Understanding bucket permissions in Amazon Lightsail](amazon-lightsail-understanding-bucket-permissions.md)\.
+ **Manage versioning** – Enable versioning to retain every version of every object stored in your bucket\. For more information, see [Enabling and suspending object versioning in a bucket in Amazon Lightsail](amazon-lightsail-managing-bucket-object-versioning.md)\.
+ **Monitor usage** – Monitor the number of objects stored in your bucket, and the amount of storage space being used\. For more information, see [Viewing metrics for your bucket in Amazon Lightsail](amazon-lightsail-viewing-bucket-metrics.md)\.
+ **Change the storage plan** – Upsize your bucket if it's being over\-utilized, or downsize it if it's being under\-utilized\. For more information, see [Changing the plan of your bucket in Amazon Lightsail](amazon-lightsail-changing-bucket-plans.md)\.
+ **Connect your bucket** – Connect your Lightsail bucket to your WordPress website to store website images and attachments\. You can also specify your bucket as the origin of a Lightsail content delivery network \(CDN\) distribution\. This speeds up the delivery of objects in your bucket to your users around the world\. For more information, see [Tutorial: Connecting a WordPress instance to an Amazon Lightsail bucket](amazon-lightsail-connecting-buckets-to-wordpress.md) and [Tutorial: Using an Amazon Lightsail bucket with a Lightsail content delivery network distribution](amazon-lightsail-using-distributions-with-buckets.md)\.
+ **Delete your bucket** – Delete your bucket if you are no longer using it\. For more information, see [Deleting buckets in Amazon Lightsail](amazon-lightsail-deleting-buckets.md)\.