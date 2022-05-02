# Understanding object key names in Amazon Lightsail<a name="understanding-bucket-object-key-names-in-amazon-lightsail"></a>

 *Last updated: July 14, 2021* 

Files that you upload to your bucket are stored as objects in the Amazon Lightsail object storage service\. An object key \(or key name\) uniquely identifies an object stored in a bucket\. This guide explains the concept of key names and key name prefixes that make up the folder structure of buckets viewed through the Lightsail console\. For more information about buckets, see [Object storage in Amazon Lightsail](buckets-in-amazon-lightsail.md)\.

## Object key names<a name="bucket-object-key-names"></a>

The Lightsail object storage service data model uses a flat structure instead of a hierarchical structure like you would see in a file system\. There is no hierarchy of folders and subfolders\. However, you can infer logical hierarchy using key name prefixes and delimiters\. The Lightsail console uses the key name prefixes to display your objects in a folder structure\.

Suppose that your bucket has four objects with the following object keys:
+ `Development/Projects.xls`
+ `Finance/statement1.pdf`
+ `Private/taxdocument.pdf`
+ `to-dos.doc`

The Lightsail console uses the key name prefixes \(`Development/`, `Finance/`, and `Private/`\) and the delimiter \(`/`\) to present a folder structure\. The `to-dos.doc` key name does not have a prefix, so its object appears directly at the root level of your bucket\. If you browse to the `Development/` folder in the Lightsail console, you see the `Projects.xls` object\. In the `Finance/` folder, you see the `statement1.pdf` object, and in the `Private/` folder, you see the `taxdocument.pdf` object\.

The Lightsail console allows for folder creation by creating a zero\-byte object with the key name prefix and delimiter value as the key name\. These folder objects don't appear in the console\. However, they behave like any other objects\. You can view and manipulate them using the Amazon S3 API, AWS Command Line Interface \(AWS CLI\), or AWS SDKs\.

## Object key naming guidelines<a name="object-key-naming-guidelines"></a>

You can use any UTF\-8 character in an object key name\. However, using certain characters in key names can cause problems with some applications and protocols\. The following guidelines help you maximize compliance with DNS, web\-safe characters, XML parsers, and other APIs\.

### Safe characters<a name="w13aab7d113b9b5"></a>

The following character sets are generally safe for use in key names\.
+ Alphanumeric characters
  + 0\-9
  + a\-z
  + A\-Z
+ Special characters
  + Forward slash \(`/`\)
  + Exclamation point \(`!`\)
  + Hyphen \(`-`\)
  + Underscore \(`_`\)
  + Period \(`.`\)
  + Asterisk \(`*`\)
  + Single quote \(`'`\)
  + Open parenthesis \(`(`\)
  + Close parenthesis \(`)`\)

The following are examples of valid object key names:
+ `4my-organization`
+ `my.great_photos-2014/jan/myvacation.jpg`
+ `videos/2014/birthday/video1.wmv`

**Important**  
If an object key name ends with a single period \(\.\), or two periods \(\.\.\), you can’t download the object using the Lightsail console\. To download an object with a key name ending with one or two periods, you must use the Amazon S3 API, AWS CLI, and AWS SDKs\. For more information, see [Downloading objects from a bucket in Amazon Lightsail](amazon-lightsail-downloading-bucket-objects.md)\.

### Characters that might require special handling<a name="asdf"></a>

The following characters in a key name might require additional code handling and likely need to be URL encoded or referenced as HEX\. Some of these are non\-printable characters that your browser might not handle, which also requires special handling:
+ Ampersand \("`&`"\)
+ Dollar \("`$`"\)
+ ASCII character ranges 00–1F hex \(0–31 decimal\) and 7F \(127 decimal\)
+ 'At' symbol \("`@`"\)
+ Equals \("`=`"\)
+ Semicolon \("`;`"\)
+ Colon \("`:`"\)
+ Plus \("`+`"\)
+ Space – Significant sequences of spaces might be lost in some uses \(especially multiple spaces\)
+ Comma \("`,`"\)
+ Question mark \("`?`"\)

### Characters to avoid<a name="key-name-characters-to-avoid"></a>

Avoid the following characters in a key name because of significant special handling for consistency across all applications\.
+ Backslash \("`\`"\)
+ Left curly brace \("`{`"\)
+ Non\-printable ASCII characters \(128–255 decimal characters\)
+ Caret \("`^`"\)
+ Right curly brace \("`}`"\)
+ Percent character \("`%`"\)
+ Grave accent / back tick \("```"\)
+ Right square bracket \("`]`"\)
+ Quotation marks
+ 'Greater than' symbol \("`>`"\)
+ Left square bracket \("`[`"\)
+ Tilde \("`~`"\)
+ 'Less than' symbol \("`<`"\)
+ 'Pound' character \("`#`"\)
+ Vertical bar / pipe \("`|`"\)

## XML related object key constraints<a name="xml-object-key-constraints"></a>

As specified by the [XML standard on end\-of\-line handling](https://www.w3.org/TR/REC-xml/#sec-line-ends), all XML text is normalized so that single carriage returns \(ASCII code 13\) and carriage returns immediately followed by a line feed \(ASCII code 10\) are replaced by a single line feed character\. To ensure the correct parsing of object keys in XML requests, carriage returns and [other special characters must be replaced with their equivalent XML entity code](https://www.w3.org/TR/xml/#syntax) when they are inserted within XML tags\. The following is a list of such special characters and their equivalent entity codes:
+ `'` as `&apos;`
+ `”` as `&quot;`
+ `&` as `&amp;`
+ `<` as `&lt;`
+ `<` as `&gt;`
+ `\r` as `&#13;` or `&#x0D;`
+ `\n` as `&#10;` or `&#x0A;`

The following example illustrates the use of an XML entity code as a substitution for a carriage return\. This `DeleteObjects` request deletes an object with the key parameter `/some/prefix/objectwith\rcarriagereturn` \(where the \\r is the carriage return\)\.

```
<Delete xmlns="http://s3.amazonaws.com/doc/2006-03-01/">
      <Object>
        <Key>/some/prefix/objectwith&#13;carriagereturn</Key>
      </Object>
    </Delete>
```

## Managing buckets and objects in Lightsail<a name="object-key-names-managing-buckets-and-objects"></a>

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

1. Learn about the way that objects in your bucket are labeled and identified\. For more information, see [Understanding object key names in Amazon Lightsail](#understanding-bucket-object-key-names-in-amazon-lightsail)\.

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