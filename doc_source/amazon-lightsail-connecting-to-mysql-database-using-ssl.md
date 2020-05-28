# Connecting to your MySQL database in Amazon Lightsail using SSL<a name="amazon-lightsail-connecting-to-mysql-database-using-ssl"></a>

 *Last updated: January 2, 2020* 

Amazon Lightsail creates an SSL certificate, and installs it on your MySQL managed database when it’s provisioned\. The certificate is signed by a certificate authority \(CA\), and it includes the database endpoint as the Common Name \(CN\) for the SSL certificate to guard against spoofing attacks\.

An SSL certificate created by Lightsail is the trusted root entity and should work in most cases but might fail if your application does not accept certificate chains\. If your application does not accept certificate chains, you might need to use an intermediate certificate to connect to your AWS Region\.

For more information about the CA certificates for your managed database, supported AWS Regions, and how you can download intermediate certificates for your applications, see [Downloading an SSL certificate for your managed database in Amazon Lightsail](amazon-lightsail-download-ssl-certificate-for-managed-database.md)\.

## Supported connections<a name="mysql-ssl-supported-connections"></a>

MySQL uses yaSSL for secure connections in the following versions:
+ MySQL version 5\.7\.19 and earlier 5\.7 versions
+ MySQL version 5\.6\.37 and earlier 5\.6 versions
+ MySQL version 5\.5\.57 and earlier 5\.5 versions

MySQL uses OpenSSL for secure connections in the following versions:
+ MySQL version 8\.0
+ MySQL version 5\.7\.21 and later 5\.7 versions
+ MySQL version 5\.6\.39 and later 5\.6 versions
+ MySQL version 5\.5\.59 and later 5\.5 versions

MySQL managed databases support Transport Layer Security \(TLS\) versions 1\.0, 1\.1, and 1\.2\. The following list shows the TLS support for MySQL versions:
+ MySQL 8\.0—TLS1\.0, TLS 1\.1, and TLS 1\.2
+ MySQL 5\.7—TLS1\.0, and TLS 1\.1\. TLS 1\.2 is supported only for MySQL 5\.7\.21 and later\.
+ MySQL 5\.6—TLS1\.0
+ MySQL 5\.5—TLS1\.0

## Prerequisites<a name="connecting-to-mysql-ssl-prerequisites"></a>
+ Install MySQL server on the computer you will use to connect to your database\. For more information, see [MySQL Community Server download](https://dev.mysql.com/downloads/mysql/) in the MySQL website\.
+ Download the appropriate certificate for your database\. For information, see [Downloading an SSL certificate for your managed database in Amazon Lightsail](amazon-lightsail-download-ssl-certificate-for-managed-database.md)\.

## Connect to your MySQL database using SSL<a name="connect-to-your-mysql-database-using-ssl"></a>

Complete the following steps to connect to your MySQL database using SSL\.

1. Open a Terminal or Command Prompt window\.

1. Enter one of the following commands depending on the version of your MySQL database:
   + Enter the following command to connect to a database that is MySQL 5\.7 or later\.

     ```
     mysql -h DatabaseEndpoint --ssl-ca=/path/to/certificate/rds-combined-ca-bundle.pem --ssl-mode=VERIFY_IDENTITY -u UserName -p
     ```

     In the command, replace:
     + *DatabaseEndpoint* with the endpoint of your database\.
     + */path/to/certificate/rds\-combined\-ca\-bundle\.pem* with the local path where you downloaded and saved the certificate for your database\.
     + *UserName* with the user name of your database\.

     **Example:**

     ```
     mysql -h ls-1c51a7c70a4fb55e542829a4e4e0d735ba42.czowadgeezqi.us-west-2.rds.amazonaws.com --ssl-ca=/home/ec2-user/rds-combined-ca-bundle.pem --ssl-mode=VERIFY_IDENTITY -u dbmasteruser -p
     ```
   + Enter the following command to connect to a database that is MySQL 6\.7 or earlier\.

     ```
     mysql -h DatabaseEndpoint --ssl-ca=/path/to/certificate/rds-combined-ca-bundle.pem --ssl-verify-server-cert -u UserName -p
     ```

     In the command, replace:
     + *DatabaseEndpoint* with the endpoint of your database\.
     + */path/to/certificate/rds\-combined\-ca\-bundle\.pem* with the local path where you downloaded and saved the certificate for your database\.
     + *UserName* with the user name of your database\.

     **Example:**

     ```
     mysql -h ls-1c51a7c70a4fb55e542829a4e4e0d735ba42.czowadgeezqi.us-west-2.rds.amazonaws.com --ssl-ca=/home/ec2-user/rds-combined-ca-bundle.pem --ssl-verify-server-cert -u dbmasteruser -p
     ```

1. Type the password for the database user you specified in the previous command when prompted, and press **Enter**\.

   You should see a result similar to the following example:  
![\[MySQL database connection.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-mysql-ssl-connection.png)

1. Type **status**, and press **Enter** to view the status of your connection\.

   Your connection is encrypted if you see a value of “Cipher in use is” next to SSL\.  
![\[MySQL database connection status.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-mysql-ssl-status.png)