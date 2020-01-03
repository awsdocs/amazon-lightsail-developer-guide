# Choosing an Amazon Lightsail database<a name="amazon-lightsail-choosing-a-database"></a>

 *Last updated: January 3, 2020* 

Amazon Lightsail provides the latest major versions of the MySQL and PostgreSQL databases\. This guide helps you decide which database is right for your project\.

## Compare managed databases in Lightsail<a name="lightsail-compare-databases"></a>

**MySQL**

MySQL 5\.6, 5\.7, and 8\.0 are available in Lightsail\. MySQL is the most widely adopted open source relational database\. It serves as the primary relational data store for many popular websites, applications, and commercial products\. MySQL is a reliable, stable, and secure SQL\-based database management system, with more than 20 years of community\-backed development and support\. The MySQL database is suitable for a wide variety of use cases, including mission\-critical apps and dynamic websites\. It also functions as an embedded database for software, hardware, and appliances\.

For more information, see the following MySQL documentation:
+ [MySQL 5\.6 documentation](https://dev.mysql.com/doc/refman/5.6/en/)
+ [MySQL 5\.7 documentation](https://dev.mysql.com/doc/refman/5.7/en/)
+ [MySQL 8\.0 documentation](https://dev.mysql.com/doc/refman/8.0/en/)

**PostgreSQL**

PostgreSQL 9\.6, 10\.10, and 11\.5 are available in Lightsail\. PostgreSQL is a powerful, open source object\-relational database system with over 30 years of active development that has earned it a strong reputation for reliability, feature robustness, and performance\.

There is a wealth of information to be found describing how to install and use PostgreSQL through the [official documentation](https://www.postgresql.org/docs/)\. The [PostgreSQL community](https://www.postgresql.org/community/) provides many helpful places to become familiar with the technology, discover how it works, and find career opportunities\.

For more information, see the following PostgreSQL documentation:
+ [PostgreSQL 9\.6 documentation](https://www.postgresql.org/docs/9.6/index.html)
+ [PostgreSQL 10 documentation](https://www.postgresql.org/docs/10/index.html)
+ [PostgreSQL 11 documentation](https://www.postgresql.org/docs/11/index.html)

**Note**  
Lightsail also offers a Windows Server 2016 instance with SQL Server 2016 Express\. For more information, see [Choose an Amazon Lightsail instance image](compare-options-choose-lightsail-instance-image.md)\.

## Optimizing data import<a name="optimizing-your-data-import"></a>

Several database plans are available in Lightsail, each with specific memory, vCPU, storage, and data transfer allowance specifications\. Because each database plan has these specifications, it is important that you choose an appropriately\-sized database plan for the amount of data that you want to import into your new Lightsail database\. Your data import may be slowed if you choose a plan that is under your size requirements\. Use the following guidelines to select the appropriate database plan for your data import requirement:
+ **Micro $15 USD/month database plan** — Data import may be slowed if you transfer more than 10 GB of data\.
+ **Small $30 USD/month database plan** — Data import may be slowed if you transfer more than 20 GB of data\.
+ **Medium $60 USD/month database plan** — Data import may be slowed if you transfer more than 85 GB of data\.
+ **Large $115 USD/month database plan** — Data import may be slowed if you transfer more than 156 GB of data\.

**Note**  
For more information about importing data into your database, see [Importing data into your MySQL database in Amazon Lightsail](amazon-lightsail-importing-data-into-your-mysql-database.md) or [Importing data into your PostgreSQL database in Amazon Lightsail](amazon-lightsail-importing-data-into-your-postgres-database.md)\.