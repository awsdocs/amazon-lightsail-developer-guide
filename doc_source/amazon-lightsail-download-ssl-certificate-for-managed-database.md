# Download an SSL certificate for your managed database in Amazon Lightsail<a name="amazon-lightsail-download-ssl-certificate-for-managed-database"></a>

 *Last updated: May 20, 2021* 

**Important**  
The certificates labeled as `rds-ca-2015` expire on March 5, 2020\. We strongly recommend that you start using the certificates labeled as `rds-ca-2019` as soon as possible\. For more information, see [Modifying your managed database in Amazon Lightsail to use a specific certificate](amazon-lightsail-modifying-database-to-use-a-specific-certificate.md)\.

You can use Secure Socket Layer \(SSL\) or Transport Layer Security \(TLS\) from your application to encrypt a connection to a managed database in Amazon Lightsail running MySQL, or PostgreSQL\. Each DB engine has its own process for implementing SSL/TLS\. For more information, see [Using SSL to connect to your MySQL database in Amazon Lightsail](amazon-lightsail-connecting-to-mysql-database-using-ssl.md) or [Using SSL to connect to your PostgreSQL database in Amazon Lightsail](amazon-lightsail-connecting-to-postgres-database-using-ssl.md)\.

**Note**  
The certificates available for download are labeled for Amazon Relational Database Service \(Amazon RDS\), but also work for managed databases in Lightsail\.

To get a certificate bundle that contains both the intermediate and root certificates, download from [https://s3\.amazonaws\.com/rds\-downloads/rds\-combined\-ca\-bundle\.pem](https://s3.amazonaws.com/rds-downloads/rds-combined-ca-bundle.pem)\.

To get a root certificate that works for all AWS Regions, download from one of these locations:
+ [https://s3\.amazonaws\.com/rds\-downloads/rds\-ca\-2019\-root\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2019-root.pem)
+ [https://s3\.amazonaws\.com/rds\-downloads/rds\-ca\-2015\-root\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2015-root.pem)

This root certificate is a trusted root entity and should work in most cases but might fail if your application doesn't accept certificate chains\. If your application doesn't accept certificate chains, download the AWS Region–specific certificate from the list of intermediate certificates found later in this section\.

If your application is on Microsoft Windows and requires a PKCS7 file, you can download the PKCS7 certificate bundle\. This bundle contains both the intermediate and root certificates at [https://s3\.amazonaws\.com/rds\-downloads/rds\-combined\-ca\-bundle\.p7b](https://s3.amazonaws.com/rds-downloads/rds-combined-ca-bundle.p7b)\.

## Intermediate certificates<a name="intermediate-certificates"></a>

You might need to use an intermediate certificate to connect to your AWS Region\. If you need an intermediate certificate for a particular AWS Region, download the certificate from the following list\.
+ US East \(Ohio\) \(us\-east\-2\)
  + CA\-2019: [rds\-ca\-2019\-us\-east\-2\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2019-us-east-2.pem)
  + CA\-2015: [rds\-ca\-2015\-us\-east\-2\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2015-us-east-2.pem)
+ US East \(N\. Virginia\) \(us\-east\-1\)
  + CA\-2019: [rds\-ca\-2019\-us\-east\-1\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2019-us-east-1.pem)
  + CA\-2015: [rds\-ca\-2015\-us\-east\-1\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2015-us-east-1.pem)
+ US West \(Oregon\) \(us\-west\-2\)
  + CA\-2019: [rds\-ca\-2019\-us\-west\-2\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2019-us-west-2.pem)
  + CA\-2015: [rds\-ca\-2015\-us\-west\-2\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2015-us-west-2.pem)
+ Asia Pacific \(Mumbai\) \(ap\-south\-1\)
  + CA\-2019: [rds\-ca\-2019\-ap\-south\-1\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2019-ap-south-1.pem)
  + CA\-2015: [rds\-ca\-2015\-ap\-south\-1\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2015-ap-south-1.pem)
+ Asia Pacific \(Seoul\) \(ap\-northeast\-2\)
  + CA\-2019: [rds\-ca\-2019\-ap\-northeast\-2\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2019-ap-northeast-2.pem)
  + CA\-2015: [rds\-ca\-2015\-ap\-northeast\-2\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2015-ap-northeast-2.pem)
+ Asia Pacific \(Singapore\) \(ap\-southeast\-1\)
  + CA\-2019: [rds\-ca\-2019\-ap\-southeast\-1\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2019-ap-southeast-1.pem)
  + CA\-2015: [rds\-ca\-2015\-ap\-southeast\-1\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2015-ap-southeast-1.pem)
+ Asia Pacific \(Sydney\) \(ap\-southeast\-2\)
  + CA\-2019: [rds\-ca\-2019\-ap\-southeast\-2\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2019-ap-southeast-2.pem)
  + CA\-2015: [rds\-ca\-2015\-ap\-southeast\-2\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2015-ap-southeast-2.pem)
+ Asia Pacific \(Tokyo\) \(ap\-northeast\-1\)
  + CA\-2019: [rds\-ca\-2019\-ap\-northeast\-1\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2019-ap-northeast-1.pem)
  + CA\-2015: [rds\-ca\-2015\-ap\-northeast\-1\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2015-ap-northeast-1.pem)
+ Canada \(Central\) \(ca\-central\-1\)
  + CA\-2019: [rds\-ca\-2019\-ca\-central\-1\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2019-ca-central-1.pem)
  + CA\-2015: [rds\-ca\-2015\-ca\-central\-1\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2015-ca-central-1.pem)
+ EU \(Frankfurt\) \(eu\-central\-1\)
  + CA\-2019: [rds\-ca\-2019\-eu\-central\-1\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2019-eu-central-1.pem)
  + CA\-2015: [rds\-ca\-2015\-eu\-central\-1\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2015-eu-central-1.pem)
+ EU \(Ireland\) \(eu\-west\-1\)
  + CA\-2019: [rds\-ca\-2019\-eu\-west\-1\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2019-eu-west-1.pem)
  + CA\-2015: [rds\-ca\-2015\-eu\-west\-1\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2015-eu-west-1.pem)
+ EU \(London\) \(eu\-west\-2\)
  + CA\-2019: [rds\-ca\-2019\-eu\-west\-2\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2019-eu-west-2.pem)
  + CA\-2015: [rds\-ca\-2015\-eu\-west\-2\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2015-eu-west-2.pem)
+ EU \(Paris\) \(eu\-west\-3\)
  + CA\-2019: [rds\-ca\-2019\-eu\-west\-3\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2019-eu-west-3.pem)
  + CA\-2015: [rds\-ca\-2015\-eu\-west\-3\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2015-eu-west-3.pem)
+ EU \(Stockholm\) \(eu\-north\-1\)
  + CA\-2019: [rds\-ca\-2019\-eu\-north\-1\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2019-eu-north-1.pem)
  + CA\-2015: [rds\-ca\-2015\-eu\-north\-1\.pem](https://s3.amazonaws.com/rds-downloads/rds-ca-2015-eu-north-1.pem)