# Configuring the data import mode for your database in Amazon Lightsail<a name="amazon-lightsail-configuring-database-data-import-mode"></a>

 *Last updated: March 15, 2019* 

Regular database backup operations can cause substantial delays, or slowdowns, when importing large amounts of data all at once\. Enable the data import mode for your Amazon Lightsail managed database to suspend these operations while you import large amounts of data\.

**Important**  
All emergency restore backups are deleted when data import mode is enabled\. Create a snapshot of your database if you would like to have a backup before data import mode is enabled\. For more information, see [Creating a snapshot of your database in Amazon Lightsail](amazon-lightsail-creating-a-database-snapshot.md)\.

**To configure the data import mode for your database**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Databases** tab\.

1. Choose the name of the database for which you want to configure data import mode\.

1. On the **Connect** tab, under the **Data import mode** section, use the toggle to turn on the data import mode\. Likewise, after the import is complete, use the toggle to turn it off\.  
![\[The data import mode toggle in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-database-data-import-mode-toggle.png)

   Now that the data import mode is enabled, database backup operations are suspended\. We recommend that you enable data import mode temporarily\. Use it only when it’s necessary for you to import large amounts of data into your database\. Disable data import mode as soon as you’re done to restore backup operations\.
**Note**  
Your import may be slowed depending on the amount of data that you're importing\. For more information, see [Optimizing data import](https://lightsail.aws.amazon.com/ls/docs/en/articles/amazon-lightsail-choosing-a-database#optimizing-your-data-import)\.

## Next steps<a name="configuring-database-data-import-mode-next-steps"></a>

Here are a few guides to help you manage your database in Lightsail:
+ [Configuring the public mode for your database in Amazon Lightsail](amazon-lightsail-configuring-database-public-mode.md)
+ [Managing your database password in Amazon Lightsail](amazon-lightsail-managing-database-password.md)
+ [Connecting to your MySQL database in Amazon Lightsail](amazon-lightsail-connecting-to-your-mysql-database.md)
+ [Connecting to your PostgreSQL database in Amazon Lightsail](amazon-lightsail-connecting-to-your-postgres-database.md)
+ [Importing data into your MySQL database in Amazon Lightsail](amazon-lightsail-importing-data-into-your-mysql-database.md)
+ [Importing data into your PostgreSQL database in Amazon Lightsail](amazon-lightsail-importing-data-into-your-postgres-database.md)
+ [Creating a snapshot of your database in Amazon Lightsail](amazon-lightsail-creating-a-database-snapshot.md)