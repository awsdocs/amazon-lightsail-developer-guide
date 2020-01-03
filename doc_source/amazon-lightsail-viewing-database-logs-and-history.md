# Viewing your database logs and history in Amazon Lightsail<a name="amazon-lightsail-viewing-database-logs-and-history"></a>

 *Last updated: January 3, 2020* 

View your database logs and history of changes in the Amazon Lightsail console\. Database logs provide useful information that could help you diagnose issues with your database\. Likewise, database history shows you changes made to your database, which allows you to associate problems with a recent change\.

**To view your database logs**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Databases** tab\.

1. Choose the name of the database for which you want to view logs\.

1. Choose the **Logs and history** tab\.

   The page displays the database logs and history of changes made to your database\.

1. Choose a database log\. The following database logs are available:

   **MySQL database logs**
   + **Error log** — A record of mysqld startup and shutdown times\. It also contains diagnostic messages such as errors, warnings, and notes that occur during server startup and shutdown, and while the server is running\. For more information, see the error log article in the [MySQL 5\.6](https://dev.mysql.com/doc/refman/5.6/en/keywords.html), [MySQL 5\.7](https://dev.mysql.com/doc/refman/5.7/en/keywords.html), or [MySQL 8\.0](https://dev.mysql.com/doc/refman/8.0/en/keywords.html) documentation\.
   + **General log** — A general record of what mysqld is doing\. The server writes information to this log when clients connect or disconnect, and logs each SQL statement received from clients\. For more information, see the general query log article in the [MySQL 5\.6](https://dev.mysql.com/doc/refman/5.6/en/keywords.html), [MySQL 5\.7](https://dev.mysql.com/doc/refman/5.7/en/keywords.html), or [MySQL 8\.0](https://dev.mysql.com/doc/refman/8.0/en/keywords.html) documentation\.
   + **Slow query log** — A record of SQL statements that took more than long\_query\_time seconds to run, and required at least min\_examined\_row\_limit rows to be examined\. For more information, see the slow query log article in the [MySQL 5\.6](https://dev.mysql.com/doc/refman/5.6/en/keywords.html), [MySQL 5\.7](https://dev.mysql.com/doc/refman/5.7/en/keywords.html), or [MySQL 8\.0](https://dev.mysql.com/doc/refman/8.0/en/keywords.html) documentation\.
**Note**  
The general and slow query logs are disabled by default for MySQL databases\. You can enable these logs, and begin collecting data, by updating a few database parameters\. For more information, see [Enabling the MySQL database general and slow query logs in Amazon Lightsail](amazon-lightsail-enabling-mysql-general-and-slow-query-logs)\.

   **PostgreSQL database logs**
   + **Postgres log** — A record of database startup and shutdown times\. It can also contain diagnostics, such as errors, warnings, notices, and debug messages that occur during database startup, shutdown, and while the database is running\. For more information, see the error reporting and logging article in the [PostgreSQL 9\.6](https://www.postgresql.org/docs/9.6/runtime-config-logging.html), [PostgreSQL 10](https://www.postgresql.org/docs/10/runtime-config-logging.html), or [PostgreSQL 11](https://www.postgresql.org/docs/11/runtime-config-logging.html) documentation\.