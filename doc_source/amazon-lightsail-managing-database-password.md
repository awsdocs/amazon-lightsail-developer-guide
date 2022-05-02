# Managing your database password in Amazon Lightsail<a name="amazon-lightsail-managing-database-password"></a>

 *Last updated: March 12, 2021* 

When you create a new database in Amazon Lightsail, you can let Lightsail create a strong password for you or specify your own\. You can view or change the current database password at any time in the Lightsail console\.

**To manage your database password**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Databases** tab\.

1. Choose the name of the database for which you want to manage the password\.

1. On the **Connect** tab, under the **User name and passwords** section, choose **Show** to view the current database password\.  
![\[Show database password\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-database-show-password.png)

1. To change the database password, choose **Change password**\.

   You can opt to have Lightsail create a strong password for you, or you can enter your own password into the text box\.The password can include any printable ASCII character except "/", """, or "@"\. For MySQL databases, the password must contain from 8 to 41 characters\. For PostgreSQL, the password must contain from 8 to 128 characters\.  
![\[Changing your database password\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-database-change-password.png)

1. Choose **Save** when you’re done\.

   A database password change is applied immediately\. If you entered your own password, the password is saved immediately\. If Lightsail created the password for you, it is generated within a few seconds\. Choose **Show** to view the new password\.

## Next steps<a name="managing-database-password-next-steps"></a>

Here are a few guides to help you manage your database in Lightsail:
+ [Configuring the public mode for your database in Amazon Lightsail](amazon-lightsail-configuring-database-public-mode.md)
+ [Configuring the data import mode for your database in Amazon Lightsail](amazon-lightsail-configuring-database-data-import-mode.md)
+ [Connecting to your MySQL database in Amazon Lightsail](amazon-lightsail-connecting-to-your-mysql-database.md)
+ [Connecting to your PostgreSQL database in Amazon Lightsail](amazon-lightsail-connecting-to-your-postgres-database.md)
+ [Importing data into your MySQL database in Amazon Lightsail](amazon-lightsail-importing-data-into-your-mysql-database.md)
+ [Importing data into your PostgreSQL database in Amazon Lightsail](amazon-lightsail-importing-data-into-your-postgres-database.md)
+ [Creating a snapshot of your database in Amazon Lightsail](amazon-lightsail-creating-a-database-snapshot.md)
+ [Changing the preferred maintenance and backup windows for your database in Amazon Lightsail](amazon-lightsail-changing-preferred-maintenance-and-backup-windows.md)