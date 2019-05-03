# High availability databases in Amazon Lightsail<a name="amazon-lightsail-high-availability-databases"></a>

**Note**  
High availability databases in Amazon Lightsail provide failover support by having a primary database in one Availability Zone, and a secondary standby database in another Availability Zone\.

 *Last updated: March 15, 2019* 

Do you need failover support for your Amazon Lightsail database? A Lightsail high availability managed database provides this support with a primary database in one Availability Zone, and a secondary standby database in another\. We recommend high availability databases for production workloads that experience heavy use and require data redundancy\. For development and test purposes, you can use a standard database that isn't high availability\.

To create a high availability database, select one of the high availability database plans available in Lightsail when creating your managed database\. For more information, see [Creating a database in Amazon Lightsail](amazon-lightsail-creating-a-database.md) \. You can also change your standard database to a high availability database\. Create a snapshot of your standard database, create a new database from the snapshot, and choose a high availability plan\. For more information, see [Creating a database from a snapshot in Amazon Lightsail](amazon-lightsail-creating-a-database-from-snapshot.md)\.