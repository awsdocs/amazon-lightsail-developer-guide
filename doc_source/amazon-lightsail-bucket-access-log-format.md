# Access log format for a bucket in the Amazon Lightsail object storage service<a name="amazon-lightsail-bucket-access-log-format"></a>

 *Last updated: November 1, 2021* 

Access logging provides detailed records for the requests that are made to a bucket in the Amazon Lightsail object storage service\. You can use access logs for security and access audits, or learn about your customer base\. This section describes the format and other details about access log files\. For more information about logging basics, see [Access logging for buckets in the Amazon Lightsail object storage service](amazon-lightsail-bucket-access-logs.md)\.

Access log files consist of a sequence of newline\-delimited log records\. Each log record represents one request and consists of space\-delimited fields\.

The following is an example log consisting of five log records\.

```
79a59df900b949e55d96a1e698fbacedfd6e09d98eacf8f8d5218e7cd47ef2be awsexamplebucket1 [06/Feb/2019:00:00:38 +0000] 192.0.2.3 79a59df900b949e55d96a1e698fbacedfd6e09d98eacf8f8d5218e7cd47ef2be 3E57427F3EXAMPLE REST.GET.VERSIONING - "GET /awsexamplebucket1?versioning HTTP/1.1" 200 - 113 - 7 - "-" "S3Console/0.4" - s9lzHYrFp76ZVxRcpX9+5cjAnEH2ROuNkd2BHfIa6UkFVdtjf5mKR3/eTPFvsiP/XV/VLi31234= SigV2 ECDHE-RSA-AES128-GCM-SHA256 AuthHeader awsexamplebucket1.s3.us-west-1.amazonaws.com TLSV1.1
```

```
79a59df900b949e55d96a1e698fbacedfd6e09d98eacf8f8d5218e7cd47ef2be awsexamplebucket1 [06/Feb/2019:00:00:38 +0000] 192.0.2.3 79a59df900b949e55d96a1e698fbacedfd6e09d98eacf8f8d5218e7cd47ef2be 891CE47D2EXAMPLE REST.GET.LOGGING_STATUS - "GET /awsexamplebucket1?logging HTTP/1.1" 200 - 242 - 11 - "-" "S3Console/0.4" - 9vKBE6vMhrNiWHZmb2L0mXOcqPGzQOI5XLnCtZNPxev+Hf+7tpT6sxDwDty4LHBUOZJG96N1234= SigV2 ECDHE-RSA-AES128-GCM-SHA256 AuthHeader awsexamplebucket1.s3.us-west-1.amazonaws.com TLSV1.1
```

```
79a59df900b949e55d96a1e698fbacedfd6e09d98eacf8f8d5218e7cd47ef2be awsexamplebucket1 [06/Feb/2019:00:00:38 +0000] 192.0.2.3 79a59df900b949e55d96a1e698fbacedfd6e09d98eacf8f8d5218e7cd47ef2be A1206F460EXAMPLE REST.GET.BUCKETPOLICY - "GET /awsexamplebucket1?policy HTTP/1.1" 404 NoSuchBucketPolicy 297 - 38 - "-" "S3Console/0.4" - BNaBsXZQQDbssi6xMBdBU2sLt+Yf5kZDmeBUP35sFoKa3sLLeMC78iwEIWxs99CRUrbS4n11234= SigV2 ECDHE-RSA-AES128-GCM-SHA256 AuthHeader awsexamplebucket1.s3.us-west-1.amazonaws.com TLSV1.1
```

```
79a59df900b949e55d96a1e698fbacedfd6e09d98eacf8f8d5218e7cd47ef2be awsexamplebucket1 [06/Feb/2019:00:01:00 +0000] 192.0.2.3 79a59df900b949e55d96a1e698fbacedfd6e09d98eacf8f8d5218e7cd47ef2be 7B4A0FABBEXAMPLE REST.GET.VERSIONING - "GET /awsexamplebucket1?versioning HTTP/1.1" 200 - 113 - 33 - "-" "S3Console/0.4" - Ke1bUcazaN1jWuUlPJaxF64cQVpUEhoZKEG/hmy/gijN/I1DeWqDfFvnpybfEseEME/u7ME1234= SigV2 ECDHE-RSA-AES128-GCM-SHA256 AuthHeader awsexamplebucket1.s3.us-west-1.amazonaws.com TLSV1.1
```

```
79a59df900b949e55d96a1e698fbacedfd6e09d98eacf8f8d5218e7cd47ef2be awsexamplebucket1 [06/Feb/2019:00:01:57 +0000] 192.0.2.3 79a59df900b949e55d96a1e698fbacedfd6e09d98eacf8f8d5218e7cd47ef2be DD6CC733AEXAMPLE REST.PUT.OBJECT s3-dg.pdf "PUT /awsexamplebucket1/s3-dg.pdf HTTP/1.1" 200 - - 4406583 41754 28 "-" "S3Console/0.4" - 10S62Zv81kBW7BB6SX4XJ48o6kpcl6LPwEoizZQQxJd5qDSCTLX0TgS37kYUBKQW3+bPdrg1234= SigV4 ECDHE-RSA-AES128-SHA AuthHeader awsexamplebucket1.s3.us-west-1.amazonaws.com TLSV1.1
```

**Note**  
Any log record field can be set to `–` \(dash\) to indicate that the data was unknown or unavailable, or that the field was not applicable to the request\.

**Contents**
+ [Log record fields](#log-record-fields)
+ [Additional logging for copy operations](#additional-logging-for-copy-operations)
+ [Custom access log information](#custom-access-log-information)
+ [Programming considerations for extensible access log format](#programing-considerations)
+ [Managing buckets and objects in Lightsail](#bucket-access-log-format-managing-buckets-and-objects)

## Log record fields<a name="log-record-fields"></a>

The following list describes the log record fields\.

**Access Point ARN \(Amazon Resource Name\)**

The Amazon Resource Name \(ARN\) of the access point of the request\. If access point ARN is malformed or not used, the field will contain a '\-'\. For more information on access points, see [Using access points](https://docs.aws.amazon.com/AmazonS3/latest/userguide/using-access-points.html)\. For more information on ARNs, see the topic on [Amazon Resource Name \(ARN\)](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) in the *AWS General Reference*\.

Example entry

```
arn:aws:s3:us-east-1:123456789012:accesspoint/example-AP
```

**Bucket Owner**

The canonical user ID of the owner of the source bucket\. The canonical user ID is another form of the AWS account ID\. For more information about the canonical user ID, see [AWS account identifiers](https://docs.aws.amazon.com/general/latest/gr/acct-identifiers.html) in the *AWS General Reference*\. For information about how to find the canonical user ID for your account, see [Finding the canonical user ID for your AWS account](https://docs.aws.amazon.com/general/latest/gr/acct-identifiers.html#FindingCanonicalId)\.

Example entry

```
79a59df900b949e55d96a1e698fbacedfd6e09d98eacf8f8d5218e7cd47ef2be
```

**Bucket**

The name of the bucket that the request was processed against\. If the system receives a malformed request and cannot determine the bucket, the request will not appear in any access log\.

Example entry

```
awsexamplebucket1
```

**Time**

The time at which the request was received; these dates and times are in Coordinated Universal Time \(UTC\)\. The format, using *strftime\(\)* terminology, is as follows: *\[%d/%b/%Y:%H:%M:%S %z\]*

Example entry

```
[06/Feb/2019:00:00:38 +0000]
```

**Remote IP**

The apparent internet address of the requester\. Intermediate proxies and firewalls might obscure the actual address of the machine making the request\.

Example entry

```
192.0.2.3
```

**Requester**

The canonical user ID of the requester, or a `-` for unauthenticated requests\. If the requester was an IAM user, this field returns the requester's IAM user name along with the AWS root account that the IAM user belongs to\. This identifier is the same one used for access control purposes\.

Example entry

```
79a59df900b949e55d96a1e698fbacedfd6e09d98eacf8f8d5218e7cd47ef2be
```

**Request ID**

A string generated by Lightsail to uniquely identify each request\.

Example entry

```
3E57427F33A59F07
```

**Operation**

The operation listed here is declared as `SOAP.operation`, `REST.HTTP_method.resource_type`, `WEBSITE.HTTP_method.resource_type`, or `BATCH.DELETE.OBJECT`\.

Example entry

```
REST.PUT.OBJECT
```

**Key**

The "key" part of the request, URL encoded, or "\-" if the operation does not take a key parameter\.

Example entry

```
/photos/2019/08/puppy.jpg
```

**Request\-URI**

The Request\-URI part of the HTTP request message\.

Example Entry

```
"GET /awsexamplebucket1/photos/2019/08/puppy.jpg?x-foo=bar HTTP/1.1"
```

**HTTP status**

The numeric HTTP status code of the response\.

Example entry

```
200
```

**Error Code**

The Amazon S3 [Error code](https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingRESTError.html#ErrorCode), or "\-" if no error occurred\.

Example entry

```
NoSuchBucket
```

**Bytes Sent**

The number of response bytes sent, excluding HTTP protocol overhead, or "\-" if zero\.

Example entry

```
2662992
```

**Object Size**

The total size of the object in question\.

Example entry

```
3462992
```

**Total Time**

The number of milliseconds the request was in flight from the bucket's perspective\. This value is measured from the time your request is received to the time that the last byte of the response is sent\. Measurements made from the client's perspective might be longer due to network latency\.

Example entry

```
70
```

**Turn\-Around Time**

The number of milliseconds that Lightsail spent processing your request\. This value is measured from the time the last byte of your request was received until the time the first byte of the response was sent\.

Example entry

```
10
```

**Referer**

The value of the HTTP Referer header, if present\. HTTP user\-agents \(for example, browsers\) typically set this header to the URL of the linking or embedding page when making a request\.

Example entry

```
"http://www.amazon.com/webservices"
```

**User\-Agent**

The value of the HTTP User\-Agent header\.

Example entry

```
"curl/7.15.1"
```

**Version Id**

The version ID in the request, or `-` if the operation does not take a `versionId` parameter\.

Example entry

```
3HL4kqtJvjVBH40Nrjfkd
```

**Host Id**

The x\-amz\-id\-2 or Lightsail extended request ID\.

Example entry

```
s9lzHYrFp76ZVxRcpX9+5cjAnEH2ROuNkd2BHfIa6UkFVdtjf5mKR3/eTPFvsiP/XV/VLi31234=
```

**Signature Version**

The signature version, `SigV2` or `SigV4`, that was used to authenticate the request or a `-` for unauthenticated requests\.

Example entry

```
SigV2
```

**Cipher Suite**

The Secure Sockets Layer \(SSL\) cipher that was negotiated for HTTPS request or a `-` for HTTP\.

Example entry

```
ECDHE-RSA-AES128-GCM-SHA256
```

**Authentication Type**

The type of request authentication used, `AuthHeader` for authentication headers, `QueryString` for query string \(pre\-signed URL\) or a `-` for unauthenticated requests\.

Example entry

```
AuthHeader
```

**Host Header**

The endpoint used to connect to Lightsail\.

Example entry

```
s3.us-west-2.amazonaws.com
```

**TLS version**

The Transport Layer Security \(TLS\) version negotiated by the client\. The value is one of following: `TLSv1`, `TLSv1.1`, `TLSv1.2`; or `-` if TLS wasn't used\.

Example entry

```
TLSv1.2
```

## Additional logging for copy operations<a name="additional-logging-for-copy-operations"></a>

A copy operation involves a `GET` and a `PUT`\. For that reason, we log two records when performing a copy operation\. The previous section describes the fields related to the `PUT` part of the operation\. The following list describes the fields in the record that relate to the `GET` part of the copy operation\.

**Bucket Owner**

The canonical user ID of the bucket that stores the object being copied\. The canonical user ID is another form of the AWS account ID\. For more information about the canonical user ID, see [AWS account identifiers](https://docs.aws.amazon.com/general/latest/gr/acct-identifiers.html) in the *AWS General Reference*\. For information about how to find the canonical user ID for your account, see [Finding the canonical user ID for your AWS account](https://docs.aws.amazon.com/general/latest/gr/acct-identifiers.html#FindingCanonicalId)\.

Example entry

```
79a59df900b949e55d96a1e698fbacedfd6e09d98eacf8f8d5218e7cd47ef2be
```

**Bucket**

The name of the bucket that stores the object being copied\.

Example entry

```
awsexamplebucket1
```

**Time**

The time at which the request was received; these dates and times are in Coordinated Universal time \(UTC\)\. The format, using `strftime()` terminology, is as follows: `[%d/%B/%Y:%H:%M:%S %z]`

Example entry

```
[06/Feb/2019:00:00:38 +0000]
```

**Remote IP**

The apparent internet address of the requester\. Intermediate proxies and firewalls might obscure the actual address of the machine making the request\.

Example entry

```
192.0.2.3
```

**Requester**

The canonical user ID of the requester, or a `-` for unauthenticated requests\. If the requester was an IAM user, this field will return the requester's IAM user name along with the AWS root account that the IAM user belongs to\. This identifier is the same one used for access control purposes\.

Example entry

```
79a59df900b949e55d96a1e698fbacedfd6e09d98eacf8f8d5218e7cd47ef2be
```

**Request ID**

A string generated by Lightsail to uniquely identify each request\.

Example entry

```
3E57427F33A59F07
```

**Operation**

The operation listed here is declared as `SOAP.operation`, `REST.HTTP_method.resource_type`, `WEBSITE.HTTP_method.resource_type`, or `BATCH.DELETE.OBJECT`\.

Example entry

```
REST.COPY.OBJECT_GET
```

**Key**

The "key" of the object being copied or "\-" if the operation does not take a key parameter\.

Example entry

```
/photos/2019/08/puppy.jpg
```

**Request\-URI**

The Request\-URI part of the HTTP request message\.

Example entry

```
"GET /awsexamplebucket1/photos/2019/08/puppy.jpg?x-foo=bar"
```

**HTTP status**

The numeric HTTP status code of the `GET` portion of the copy operation\.

Example entry

```
200
```

**Error Code**

The Amazon S3 Error code, of the `GET` portion of the copy operation or `-` if no error occurred\.

Example entry

```
NoSuchBucket
```

**Bytes Sent**

The number of response bytes sent, excluding HTTP protocol overhead, or "\-" if zero\.

Example entry

```
2662992
```

**Object Size**

The total size of the object in question\.

Example entry

```
3462992
```

**Total Time**

The number of milliseconds the request was in flight from the bucket's perspective\. This value is measured from the time your request is received to the time that the last byte of the response is sent\. Measurements made from the client's perspective might be longer due to network latency\.

Example entry

```
70
```

**Turn\-Around Time**

The number of milliseconds that Lightsail spent processing your request\. This value is measured from the time the last byte of your request was received until the time the first byte of the response was sent\.

Example entry

```
10
```

**Referer**

The value of the HTTP Referer header, if present\. HTTP user\-agents \(for example, browsers\) typically set this header to the URL of the linking or embedding page when making a request\.

Example entry

```
"http://www.amazon.com/webservices"
```

**User\-Agent**

The value of the HTTP User\-Agent header\.

Example entry

```
"curl/7.15.1"
```

**Version Id**

The version ID of the object being copied or `-` if the `x-amz-copy-source` header didn’t specify a `versionId` parameter as part of the copy source\.

Example entry

```
3HL4kqtJvjVBH40Nrjfkd
```

**Host Id**

The x\-amz\-id\-2 or Lightsail extended request ID\.

Example entry

```
s9lzHYrFp76ZVxRcpX9+5cjAnEH2ROuNkd2BHfIa6UkFVdtjf5mKR3/eTPFvsiP/XV/VLi31234=
```

**Signature Version**

The signature version, `SigV2` or `SigV4`, that was used to authenticate the request or a `-` for unauthenticated requests\.

Example entry

```
SigV2
```

**Cipher Suite**

The Secure Sockets Layer \(SSL\) cipher that was negotiated for HTTPS request or a `-` for HTTP\.

Example entry

```
ECDHE-RSA-AES128-GCM-SHA256
```

**Authentication Type**

The type of request authentication used, `AuthHeader` for authentication headers, `QueryString` for query string \(presigned URL\) or a `-` for unauthenticated requests\.

Example entry

```
AuthHeader
```

**Host Header**

The endpoint used to connect to Lightsail\.

Example entry

```
s3.us-west-2.amazonaws.com
```

**TLS version**

The Transport Layer Security \(TLS\) version negotiated by the client\. The value is one of following: `TLSv1`, `TLSv1.1`, `TLSv1.2`; or `-` if TLS wasn't used\.

Example entry

```
TLSv1.2
```

## Custom access log information<a name="custom-access-log-information"></a>

You can include custom information to be stored in the access log record for a request\. To do this, add a custom query\-string parameter to the URL for the request\. Lightsail ignores query\-string parameters that begin with "x\-", but includes those parameters in the access log record for the request, as part of the `Request-URI` field of the log record\.

For example, a `GET` request for `"s3.amazonaws.com/awsexamplebucket1/photos/2019/08/puppy.jpg?x-user=johndoe"` works the same as the request for `"s3.amazonaws.com/awsexamplebucket1/photos/2019/08/puppy.jpg"`, except that the `"x-user=johndoe"` string is included in the `Request-URI` field for the associated log record\. This functionality is available in the REST interface only\.

## Programming considerations for extensible access log format<a name="programing-considerations"></a>

Occasionally we might extend the access log record format by adding new fields to the end of each line\. Therefore, you should write any code that parses access logs to handle trailing fields that it might not understand\.

## Managing buckets and objects in Lightsail<a name="bucket-access-log-format-managing-buckets-and-objects"></a>

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
   + [Access log format for a bucket in the Amazon Lightsail object storage service](#amazon-lightsail-bucket-access-log-format)
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