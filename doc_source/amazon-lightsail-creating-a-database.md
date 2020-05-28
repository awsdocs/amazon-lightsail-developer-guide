# Creating a database in Amazon Lightsail<a name="amazon-lightsail-creating-a-database"></a>

 *Last updated: January 3, 2020* 

Create a managed database in Amazon Lightsail in minutes\. You can choose between the latest major versions of MySQL or PostgreSQL, and configure your database with a standard or high availability plan\.

**Note**  
For more information about managed databases in Lightsail, see [Choosing an Amazon Lightsail database](amazon-lightsail-choosing-a-database.md)\.

**To create a database**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Databases** tab\.

1. Choose **Create database**\.

1. Choose the AWS Region and Availability Zone for your database\.

   1. Choose **Change AWS Region and Availability Zone**, then choose a Region\.

   1. Choose **Change your Availability Zone**, then choose an Availability Zone\.

1. Choose your database type\. Under one of the database engine options available, choose the drop\-down menu, and then choose one of the latest major database versions supported by Lightsail\.  
![\[Pick a database engine in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-pick-your-database.png)

1. If necessary, choose one of these options:
   + **Specify login credentials** — Specify your own database user name and password\. Otherwise, Lightsail specifies the user name, and creates a strong password for you\. 
     + To specify your own user name, choose **Specify login credentials**, and enter your user name into the text box\.
**Important**  
The user name can't be a word reserved by the selected database engine\. Additionally, the master user name cannot be changed after the database is created\. To learn more about reserved words, refer to the [MySQL 5\.6](https://dev.mysql.com/doc/refman/5.6/en/keywords.html), [MySQL 5\.7](https://dev.mysql.com/doc/refman/5.7/en/keywords.html), or [MySQL 8\.0](https://dev.mysql.com/doc/refman/8.0/en/keywords.html) documentation\. For PostgreSQL, refer to the [PostgreSQL 9\.6](https://www.postgresql.org/docs/9.6/sql-keywords-appendix.html), [PostgreSQL 10](https://www.postgresql.org/docs/10/sql-keywords-appendix.html), or [PostgreSQL 11](https://www.postgresql.org/docs/11/sql-keywords-appendix.html) documentation\.
     + To specify your own password, clear the **Create a strong password for me** check box, and enter your password into the text box\. 
   + **Specify the master database name** — Specify your own master database name, or Lightsail specifies the name for you\. To specify your own master database name, choose **Specify the master database name**, and enter a name into the text box\.

1. Choose a high availability or a standard database plan, and choose a database bundle\.

   A database created with a high availability plan has a primary database and a secondary standby database in another Availability Zone for failover support\. For more information, see [High availability databases in Amazon Lightsail](amazon-lightsail-high-availability-databases.md)\. Differently priced database bundle options are available, each with different levels of memory, processing, storage space, and transfer rates\.

1. Enter a name for your database\.

   Resource names:
   + Must be unique within each AWS Region in your Lightsail account\.
   + Must contain 2 to 255 characters\.
   + Must start and end with an alphanumeric character or number\.
   + Can include alphanumeric characters, numbers, periods, dashes, and underscores\.

1. Choose one of the following options to add tags to your database:
   + **Add key\-only tags** or **Edit key\-only tags** \(if tags have already been added\)\. Enter your new tag into the tag key text box, and press **Enter**\. Choose **Save** when you’re done entering your tags to add them, or choose **Cancel** to not add them\.  
![\[Key-only tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-key-only-tags.png)
   + **Create a key\-value tag**, then enter a key into the **Key** text box, and a value into the **Value** text box\. Choose **Save** when you’re done entering your tags, or choose **Cancel** to not add them\.

     Key\-value tags can only be added one at a time before saving\. To add more than one key\-value tag, repeat the previous steps\.  
![\[Key-value tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-key-value-tag.png)
**Note**  
For more information about key\-only and key\-value tags, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

1. Choose **Create database**\.

   Within minutes, your Lightsail database is ready\. You can begin configuring it for data import, or connect to it by using a database client\.

## Next steps<a name="creating-a-database-next-steps"></a>

Here are a few guides to help you manage your new database in Lightsail after it’s up and running:
+ [Configuring the data import mode for your database in Amazon Lightsail](amazon-lightsail-configuring-database-data-import-mode.md)
+ [Configuring the public mode for your database in Amazon Lightsail](amazon-lightsail-configuring-database-public-mode.md)
+ [Managing your database password in Amazon Lightsail](amazon-lightsail-managing-database-password.md)
+ [Connecting to your MySQL database in Amazon Lightsail](amazon-lightsail-connecting-to-your-mysql-database.md)
+ [Connecting to your PostgreSQL database in Amazon Lightsail](amazon-lightsail-connecting-to-your-postgres-database.md)
+ [Importing data into your MySQL database in Amazon Lightsail](amazon-lightsail-importing-data-into-your-mysql-database.md)
+ [Importing data into your PostgreSQL database in Amazon Lightsail](amazon-lightsail-importing-data-into-your-postgres-database.md)
+ [Creating a snapshot of your database in Amazon Lightsail](amazon-lightsail-creating-a-database-snapshot.md)