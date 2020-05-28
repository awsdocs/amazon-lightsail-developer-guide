# Configuring the public mode for your database in Amazon Lightsail<a name="amazon-lightsail-configuring-database-public-mode"></a>

 *Last updated: March 15, 2019* 

Your managed database in Amazon Lightsail is accessible only by your Lightsail resources \(instances, load balancers, etc\.\) that are in the same Lightsail account\. One common scenario is to create both a Lightsail instance with a public\-facing web application and a Lightsail database that is not publicly accessible, and then connect the two\.

Enable the public mode feature to make your database publicly accessible\. This way, anyone with the database endpoint, port, user name, and password can connect to your database\. For more information, see [Connecting to your MySQL database in Amazon Lightsail](amazon-lightsail-connecting-to-your-mysql-database.md) or [Connecting to your PostgreSQL database in Amazon Lightsail](amazon-lightsail-connecting-to-your-postgres-database.md)\.

**To configure the public mode for your database**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Databases** tab\.

1. Choose the name of the database for which you want to configure public mode\.

1. Choose the **Networking** tab\.

1. Under the **Public mode** section, use the toggle to turn it on\. Likewise, use the toggle to turn it off\.  
![\[The database public mode toggle in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-database-public-mode-toggle.png)

   The public accessibility setting begins applying immediately but may require a few minutes to complete\. During this time, the status of your database changes to **Modifying**\. The status of your database changes to **Available** after the public accessibility setting is applied\.

## Next steps<a name="configuring-database-public-mode-next-steps"></a>

Here are a few guides to help you manage your database in Lightsail:
+ [Configuring the data import mode for your database in Amazon Lightsail](amazon-lightsail-configuring-database-data-import-mode.md)
+ [Managing your database password in Amazon Lightsail](amazon-lightsail-managing-database-password.md)
+ [Connecting to your MySQL database in Amazon Lightsail](amazon-lightsail-connecting-to-your-mysql-database.md)
+ [Connecting to your PostgreSQL database in Amazon Lightsail](amazon-lightsail-connecting-to-your-postgres-database.md)
+ [Importing data into your MySQL database in Amazon Lightsail](amazon-lightsail-importing-data-into-your-mysql-database.md)
+ [Importing data into your PostgreSQL database in Amazon Lightsail](amazon-lightsail-importing-data-into-your-postgres-database.md)
+ [Creating a snapshot of your database in Amazon Lightsail](amazon-lightsail-creating-a-database-snapshot.md)