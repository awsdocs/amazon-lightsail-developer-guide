# Tutorial: Connecting a LAMP instance in Amazon Lightsail to an Amazon Aurora database<a name="amazon-lightsail-connect-lamp-instance-to-aurora-database"></a>

 *Last updated: April 22, 2022* 

Application data for posts, pages, and users is stored on a MariaDB database that is running on your LAMP instance in Amazon Lightsail\. If your instance fails, your data may become unrecoverable\. To prevent this scenario, you should transfer your application data to a MySQL managed database\.

Amazon Aurora is a MySQL and PostgreSQL\-compatible relational database built for the cloud\. It combines the performance and availability of traditional enterprise databases with the simplicity and cost\-effectiveness of open\-source databases\. Aurora is offered as part of the Amazon Relational Database Service \(Amazon RDS\)\. Amazon RDS is a managed database service that makes it easier to set up, operate, and scale a relational database in the cloud\. For more information, see the [Amazon Relational Database Service User Guide](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/) and the [Amazon Aurora User Guide for Aurora](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/)\.

In this tutorial, we show you how to connect your application database from a LAMP instance in Lightsail to an Aurora managed database in Amazon RDS\.

**Contents**
+ [Step 1: Complete the prerequisites](#connect-lamp-to-aurora-prerequisites)
+ [Step 2: Configure the security group for your Aurora database](#configure-security-group)
+ [Step 3: Connect to your Aurora database from your Lightsail instance](#connect-to-aurora-database-from-lamp-instance)
+ [Step 4: Transfer the MariaDB database from your LAMP instance to your Aurora database](#transfer-database-from-lamp-to-aurora)
+ [Step 5: Configure your application to connect to your Aurora managed database](#connect-application-to-database)

## Step 1: Complete the prerequisites<a name="connect-lamp-to-aurora-prerequisites"></a>

Complete the following prerequisites before you begin:

1. Create a LAMP instance in Lightsail, and configure your application on it\. The instance should be in a running state before you continue\. For more information, see [Tutorial: Launch and configure a LAMP instance in Lightsail](amazon-lightsail-tutorial-launching-and-configuring-lamp.md)\.

1. Turn on VPC peering in your Lightsail account\. For more information, see [Set up Amazon VPC peering to work with AWS resources outside of Lightsail](lightsail-how-to-set-up-vpc-peering-with-aws-resources.md)\.

1. Create an Aurora managed database in Amazon RDS\. The database should be located in the same AWS Region as your LAMP instance\. It should also be in a running state before you continue\. For more information, see [Getting started with Amazon Aurora](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/CHAP_GettingStartedAurora.html) in the *Amazon Aurora User Guide for Aurora*\.

## Step 2: Configure the security group for your Aurora database<a name="configure-security-group"></a>

An AWS security group acts as a virtual firewall for your AWS resources\. It controls the incoming and outgoing traffic that can connect to your Aurora database in Amazon RDS\. For more information about security groups, see [Control traffic to resources using security groups in the Amazon Virtual Private Cloud User Guide](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html)\.

Complete the following procedure to configure the security group to so that your LAMP instance can establish a connection to your Aurora database\.

1. Sign in to the [Amazon RDS console](https://console.aws.amazon.com/rds/)\.

1. Choose **Databases** in the navigation pane\.

1. Choose the **Writer instance** of the Aurora database that your LAMP instance will connect to\.

1. Choose the **Connectivity & security tab**\.

1. In the **Endpoint & port** section, make a note of the **Endpoint name** and **Port** of the **Writer instance**\. You will need these later when configuring your Lightsail instance to connect to the database\.

1. In the **Security** section, choose the active VPC security group link\. You will be redirected to your database’s security group\.  
![\[Connectivity & security tab screenshot of the Amazon RDS console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/lamp-aurora-db-select-writer-instance.png)

1. Make sure that the security group for your Aurora database is selected\.

1. Choose the **Inbound rules** tab\.

1. Choose **Edit inbound rules**\.  
![\[Inbound rules tab screenshot of the Amazon RDS console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/lamp-aurora-select-security-group.png)

1. In the **Edit inbound rules** page, choose **Add rule**\.

1. Complete one of the following steps:
   + If you are using the default MySQL port 3306, select **MySQL/Aurora** in the **Type** dropdown menu\.
   + If you are using a custom port for your database, select **Custom TCP** in the **Type** dropdown menu and enter the port number in the **Port Range** text box\.

1. In the **Source** text box, add the private IP address of your LAMP instance\. You must enter the IP addresses in CIDR notation, which means that you must append `/32`\. For example, to allow `192.0.2.0`, enter `192.0.2.0/32`\.

1. Choose **Save rules**\.  
![\[Inbound rules detail screenshot of the Amazon RDS console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/lamp-aurora-add-security-group-rule.png)

## Step 3: Connect to your Aurora database from your Lightsail instance<a name="connect-to-aurora-database-from-lamp-instance"></a>

Complete the following procedure to confirm that you can connect to your Aurora database from your Lightsail instance\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Instances** tab\.  
![\[Lightsail homepage.\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/lamp-aurora-homepage-select-instances-tab.png)

1. Choose the browser\-based SSH client icon for your LAMP instance to connect to it using SSH\.  
![\[Browser-based SSH client icon.\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/lamp-aurora-browser-based-ssh-client.png)

1. After you're connected to your instance, enter the following command to connect to your Aurora database\. In the command, replace *DatabaseEndpoint* with the endpoint address of your Aurora database, and replace *Port* with the port of your database\. Replace *MyUserName* with the name of the user that you entered when creating the database\.

   ```
   mysql -h DatabaseEndpoint -P Port -u MyUserName -p
   ```

   You should see a response similar to the following example, which confirms that your instance can access and connect to your Aurora database\.  
![\[Successful MySQL connection response.\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/lamp-aurora-mysql-connect-message.png)

   If you don’t see this response, or you get an error message, then you might need to configure the security group of your database to allow the private IP address of your Lightsail instance to connect to it\. For more information, see the [Configure the security group for your Aurora database](#configure-security-group) section of this guide\.

## Step 4: Transfer the MariaDB database from your LAMP instance to your Aurora database<a name="transfer-database-from-lamp-to-aurora"></a>

Now that you’ve confirmed you can connect to your database from your instance, you should migrate the data from your LAMP instance database to your Aurora database\. For more information, see [Migrating data to an Amazon Aurora MySQL DB cluster](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/AuroraMySQL.Migrating.html) in the *Amazon Aurora User Guide for Aurora*\.

## Step 5: Configure your application to connect to your Aurora managed database<a name="connect-application-to-database"></a>

After transferring your application data to your Aurora database, you should configure the application running on your LAMP instance to connect to your Aurora database\. Connect to your LAMP instance using SSH, and access the application’s database configuration file\. In the configuration file, define the endpoint address of your Aurora database, the database user name, and password\. Following is an example configuration file\.

![\[Application configuration file.\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/lamp-aurora-application-config-file.png)