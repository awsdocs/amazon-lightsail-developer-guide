# Connecting to your MySQL database in Amazon Lightsail<a name="amazon-lightsail-connecting-to-your-mysql-database"></a>

 *Last updated: March 15, 2019* 

After your MySQL managed database is created in Amazon Lightsail, you can use any standard MySQL client application or utility to connect to it\. You must get the database endpoint, port, user name, and password from your database management page in the Lightsail console\. Specify those values when configuring the database connection in your client or web application\.

This guide shows you how to obtain the required connection information, and how to configure MySQL Workbench to connect to your managed database\.

**Note**  
For more information about connecting to a PostgreSQL database, see [Connecting to your PostgreSQL database in Amazon Lightsail](amazon-lightsail-connecting-to-your-postgres-database.md)\.

## Step 1: Get your MySQL database connection details<a name="get-your-mysql-database-connection-details"></a>

Get your database endpoint and port information from the Lightsail console\. You use these later when configuring your client to connect to your database\.

**To get your database connection details**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Databases** tab\.

1. Choose the name of the database that you want to connect to\.

1. On the **Connect** tab, under the **Endpoint and port** section, note the endpoint and port information\.

   We recommend copying the endpoint to your clipboard to avoid entering it incorrectly\. To do that, highlight the endpoint and press **Ctrl\+C** if you’re using Windows, or **Cmd\+C** if you’re using macOS, to copy it to your clipboard\. Then, press **Ctrl\+V** or **Cmd\+V** as appropriate to paste it\.  
![\[Database endpoint and port in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-mysql-database-endpoint-and-port.png)

1. On the **Connect** tab, under the **User name and passwords** section, make note of the user name, then choose **Show** under the **Password** section to view the current database password\.

   Because managed passwords are complex, we also recommend copying and pasting it to avoid entering it incorrectly\. Highlight the managed password and press **Ctrl\+C** if you’re using Windows, or **Cmd\+C** if you’re using macOS, to copy it to your clipboard\. Then, press **Ctrl\+V** or **Cmd\+V** as appropriate to paste it\.

## Step 2: Configure the public availability of your MySQL database<a name="configure-mysql-database-public-availability"></a>

You must enable public mode for your database to connect to it externally, or from a Lightsail instance in a different AWS Region than your database\. With public mode enabled, anyone with the database user name and password can connect to your database\. To configure the public availability of your database, follow the steps in the [Configuring the public mode for your database in Amazon Lightsail](amazon-lightsail-configuring-database-public-mode.md) guide\.

**Note**  
Skip to step 3 if you plan to connect to your database from one of your Lightsail instances that is in the same Region as your database\.

## Step 3: Configure your database client to connect to your MySQL database<a name="configure-the-mysql-workbench-database-client"></a>

To connect to your MySQL database, configure your database client to use the endpoint and port that you obtained earlier\. The following steps show you how to configure MySQL Workbench, but these steps may be similar for other clients\.

**Note**  
For more information about using MySQL Workbench, see the [MySQL Workbench Manual](https://dev.mysql.com/doc/workbench/en/)\.

**To configure MySQL Workbench to connect to your database**

1. Open **MySQL Workbench**\.

1. Choose the **Database** menu, then choose **Manage connections**\.

1. Enter the following information into the form that displays:  
![\[MySQL Workbench connection configuration\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-mysql-workbench-connection-manager.png)
   + **Connection Name** — We recommend using a name for the connection that is similar to your database\. This helps you identify it in the future\.
   + **Connection Method** — Choose **Standard \(TCP/IP\)**\. 
   + **Port** — Enter the port for your database that you obtained earlier\. The default port for MySQL is 3306\.
   + **Hostname** — Enter the database endpoint that you obtained earlier\. If you copied the database endpoint from the Lightsail console, and it’s still in your clipboard, press **Ctrl\+V** if you’re using Windows, or **Cmd\+V** if you’re using macOS, to paste it\.
   + **Username** — Enter the database user name that you obtained earlier\.
   + **Password** — Choose **Store in vault**\. In the window that appears, enter your database password that you obtained earlier\. If you copied your password from the Lightsail console, and it’s still in your clipboard, press **Ctrl\+V** if you’re using Windows, or **Cmd\+V** if you’re using macOS, to paste it\. Choose **OK** to save your password\.
   + **Default Schema** — Keep this text box blank\.

1. Choose **Test connection** to determine if the client can establish a connection with your database\.

   If the connection is successful, a prompt similar to the following example displays\. After you read the information, choose **OK** to close it\.  
![\[MySQL Workbench successful connection test\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-mysql-workbench-successful-connection.png)

1. Choose **New** to save the new connection details, then choose **Close** to close the connections management window\.

   Your new database connection appears on the home page of the MySQL Workbench application, under the MySQL Connections section\.

1. To connect to your database, choose your new database connection\.

   If the connection is successful, a window similar to the following example displays\.  
![\[MySQL Workbench workspace\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-mysql-workbench-workspace.png)

## Next steps<a name="connecting-to-your-mysql-database-next-steps"></a>

Here is a guide to help you import data into your database in Lightsail:
+ [Importing data into your MySQL database in Amazon Lightsail](amazon-lightsail-importing-data-into-your-mysql-database.md)