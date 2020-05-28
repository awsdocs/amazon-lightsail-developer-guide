# Creating a database from a snapshot in Amazon Lightsail<a name="amazon-lightsail-creating-a-database-from-snapshot"></a>

 *Last updated: March 15, 2019* 

You can create a new managed database from a snapshot in Amazon Lightsail if something goes wrong with your original database\. You can also change your database to a different plan, such as a high availability or standard plan\. You can also create a new database from a point\-in\-time backup of your original database\. For more information, see [Creating a database from a point\-in\-time backup in Amazon Lightsail](amazon-lightsail-creating-a-database-from-point-in-time-backup.md)\.

When you create the duplicate database, you can choose a different or larger plan than the original database\. However, you can’t choose a smaller plan than the original database\.

**Note**  
A database created with a high availability plan has a primary database and a secondary standby database in another Availability Zone for failover support\. For more information, see [High availability databases in Amazon Lightsail](amazon-lightsail-high-availability-databases.md)\.

**To create a database from a snapshot**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Databases** tab\.

1. Choose the name of the database that you want to duplicate by creating a new database from a snapshot\.

1. Choose the **Snapshots & restore** tab\.

1. Under the **Manual snapshots** section of the page, choose the actions menu icon \(⋮\) next to the snapshot from which you want to create a new database, and choose **Create new database**\.
**Note**  
You need a snapshot of your database to work from\. If you haven’t created a snapshot yet, see [Creating a snapshot of your database in Amazon Lightsail](amazon-lightsail-creating-a-database-snapshot.md)\.  
![\[Creating a new database from a snapshot\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-create-new-database-from-snapshot.png)

1. Choose **Create new database**\.

1. On the **Create a new database** page, choose **Change zone** to select a different Availablity Zone\. Your new database is created in the same AWS Region as the snapshot that you selected earlier\.

1. Choose your new database plan\.

   Select a high availability or a standard database plan\. A database created with a high availability plan has a primary database and a secondary standby database in another Availability Zone for failover support\. For more information, see [High availability databases in Amazon Lightsail](amazon-lightsail-high-availability-databases.md)\.
**Note**  
You cannot choose a database plan that is smaller than the plan of the original database used to create the snapshot\.

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

   Within minutes, your new Lightsail database is ready with the new database plan or bundle\.

## Next steps<a name="creating-a-database-from-snapshot-next-steps"></a>

Complete the following actions after your new database is up and running:
+ If you’re creating a new database to replace an existing database, and you have an application that depends on the existing database, then make sure to update your application dependencies to your new database\.
+ Delete the original database if you no longer need it\. For more information, see [Deleting your database in Amazon Lightsail](amazon-lightsail-deleting-your-database.md)\.
+ Databases created from a snapshot are configured to use a strong password created by Lightsail\. For more information, see [Managing your database password in Amazon Lightsail](amazon-lightsail-managing-database-password.md)\.