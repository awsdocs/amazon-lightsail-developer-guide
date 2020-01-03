# Modifying your managed database in Amazon Lightsail to use a specific certificate<a name="amazon-lightsail-modifying-database-to-use-a-specific-certificate"></a>

 *Last updated: January 2, 2020* 

Amazon Lightsail has published new Certificate Authority \(CA\) certificates for connecting to your managed database using SSL/TLS\. The new certificates are referred to as `rds-ca-2019`, and the old certificates are referred to as `rds-ca-2015`\. We provide the CA certificates as an AWS security best practice\. For information about the CA certificates for your managed database, and the supported AWS Regions, see [Downloading an SSL certificate for your managed database in Amazon Lightsail](amazon-lightsail-download-ssl-certificate-for-managed-database.md)\.

The old CA certificate \(`rds-ca-2015`\) on your managed database expires on March 5, 2020\. Therefore, we strongly recommend completing the steps in this guide as soon as possible to modify your managed database to use the new certificate\. If your applications are not connecting to your Lightsail managed database using SSL/TLS, no action is required\. If these steps are not completed, your applications will fail to connect to your managed database using SSL/TLS after March 5, 2020\.

New managed databases created after January 14, 2020 will use the new certificates by default\. If you want to temporarily modify new managed databases to use the old certificates \(`rds-ca-2015`\), you can do so using the AWS Command Line Interface \(AWS CLI\)\. Any managed databases created prior to January 14, 2020 use the `rds-ca-2015` certificates until you update them to the `rds-ca-2019` certificates\.

**Note**  
Test the steps in this guide on a development or staging environment before using them on your production environments\.

**Contents**
+ [Prerequisites](#modifying-database-prerequisites)
+ [Modifying your managed database to use the new CA certificate](#modifying-database-new-certificate)
+ [Modifying your managed database to use the old CA certificate](#modifying-database-old-certificate)

## Prerequisites<a name="modifying-database-prerequisites"></a>
+ If you haven't done so already, install and configure the AWS Command Line Interface \(AWS CLI\)\. For more information, see [Configuring the AWS CLI to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.
+ Before completing the following steps, make sure to update your database applications to use the new SSL/TLS certificate\. The methods for updating applications for new SSL/TLS certificates depend on your specific applications\. Work with your application developers to update the SSL/TLS certificates for your applications\. To learn more about updating applications for new SSL/TLS certificates, see [Updating Applications to Connect to MySQL DB Instances Using New SSL/TLS Certificates](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/ssl-certificate-rotation-mysql.html) or [Updating Applications to Connect to PostgreSQL DB Instances Using New SSL/TLS Certificates](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/ssl-certificate-rotation-postgresql.html) in the *Amazon Relational Database Service User Guide*\.

## Modifying your managed database to use the new CA certificate<a name="modifying-database-new-certificate"></a>

Complete the following steps to modify your managed database in Lightsail to use the new CA certificate \(`rds-ca-2019`\)\.

1. Open a Terminal or Command Prompt window\.

1. Enter the following command to use the `rds-ca-2019` certificate on your managed database\.

   ```
   aws lightsail update-relational-database --relational-database-name DatabaseName --ca-certificate-identifier rds-ca-2019 --no-apply-immediately
   ```

   In the command, replace *DatabaseName* with the name of the database you want to modify\.

   **Example**

   ```
   aws lightsail update-relational-database --relational-database-name Database-1 --ca-certificate-identifier rds-ca-2019 --no-apply-immediately
   ```

   The CA certificate used by your managed database will be updated during your database’s next maintenance window\.

## Modifying your managed database to use the old CA certificate<a name="modifying-database-old-certificate"></a>

Complete the following steps to modify your managed database in Lightsail to use the old CA certificate \(`rds-ca-2015`\)\. You may want to do this in case you experience a critical issue with the new certificate \(`rds-ca-2019`\) and need to temporarily revert the old one\.

1. Open a Terminal or Command Prompt window\.

1. Enter the following command to use the `rds-ca-2015` on your managed database\.

   ```
   aws lightsail update-relational-database --relational-database-name DatabaseName --ca-certificate-identifier rds-ca-2015 --no-apply-immediately
   ```

   In the command, replace *DatabaseName* with the name of the database you want to modify\.

   **Example**

   ```
   aws lightsail update-relational-database --relational-database-name Database-1 --ca-certificate-identifier rds-ca-2015 --no-apply-immediately
   ```

   The CA certificate used by your managed database will be updated during your database’s next maintenance window\.