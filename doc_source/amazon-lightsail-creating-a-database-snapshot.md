# Creating a snapshot of your database in Amazon Lightsail<a name="amazon-lightsail-creating-a-database-snapshot"></a>

 *Last updated: March 15, 2019* 

You can create a snapshot of your managed database in Amazon Lightsail\. A snapshot is a copy of your database that you can use to restore it if something goes wrong\. You can also use a snapshot to create a new database using a different plan, such as a high availability or standard plan\.

When you create a snapshot of a standard database, the database becomes unavailable from a few seconds to a few minutes, depending on the size\. High availability databases are not affected by snapshot operations because the snapshot is created using the standby database\.

**To create a snapshot of your database**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Databases** tab\.

1. Choose the name of the database for which you want to create a snapshot\.

1. Choose the **Snapshots & restore** tab\.

1. Under the **Manual snapshots** section of the page, choose **Create snapshot**, then enter a name for your snapshot\.

   Resource names:
   + Must be unique within each AWS Region in your Lightsail account\.
   + Must contain 2 to 255 characters\.
   + Must start and end with an alphanumeric character or number\.
   + Can include alphanumeric characters, numbers, periods, dashes, and underscores\.

1. Choose **Create**\.

   The snapshot creation process begins and a status of **Snapshot in progress** is shown\.  
![\[Database snapshot in progress\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-database-snapshot-in-progress.png)

   After the snapshot creation process is complete, the new snapshot is listed under the **Recent snapshots** section\. You can also view all of the snapshots for your account in the Lightsail home page, under the **Snapshots** tab\.  
![\[Recent database snapshots in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-database-recent-snapshots.png)

## Next steps<a name="creating-a-database-snapshot-next-steps"></a>

After your snapshot is ready, you can create a new database from the snapshot, which is a duplicate of the original database\. For more information, see [Creating a database from a snapshot in Amazon Lightsail](amazon-lightsail-creating-a-database-from-snapshot.md)\.