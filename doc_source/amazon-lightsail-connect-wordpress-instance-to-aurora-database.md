# Tutorial: Connecting a WordPress instance in Amazon Lightsail to an Amazon Aurora database<a name="amazon-lightsail-connect-wordpress-instance-to-aurora-database"></a>

 *Last updated: April 22, 2022* 

Website data for posts, pages, and users is stored on a database that is running on your WordPress instance in Amazon Lightsail\. If your instance fails, your data may become unrecoverable\. To prevent this scenario, you should transfer your website data to an Amazon Aurora database in the Amazon Relational Database Service \(Amazon RDS\)\.

Amazon Aurora is a MySQL and PostgreSQL\-compatible relational database built for the cloud\. It combines the performance and availability of traditional enterprise databases with the simplicity and cost\-effectiveness of open\-source databases\. Aurora is offered as part of Amazon RDS\. Amazon RDS is a managed database service that makes it easier to set up, operate, and scale a relational database in the cloud\. For more information, see the [Amazon Relational Database Service User Guide](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/) and the [Amazon Aurora User Guide for Aurora](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/)\.

In this tutorial, we show you how to connect your website database from a WordPress instance in Lightsail to an Aurora managed database in Amazon RDS\.

**Contents**
+ [Step 1: Complete the prerequisites](#connect-mysql-to-aurora-prerequisites)
+ [Step 2: Configure the security group for your Aurora database](#configure-aurora-security-group)
+ [Step 3: Connect to your Aurora database from your Lightsail instance](#connect-to-aurora-database-from-lightsail-instance)
+ [Step 4: Transfer the MySQL database from your WordPress instance to your Aurora database](#transfer-database-from-wordpres-to-aurora)
+ [Step 5: Configure WordPress to connect to your Aurora managed database](#connect-wordpress-to-aurora)

## Step 1: Complete the prerequisites<a name="connect-mysql-to-aurora-prerequisites"></a>

Complete the following prerequisites before you begin:

1. Create a WordPress instance in Lightsail, and configure your application on it\. The instance should be in a running state before you continue\. For more information, see [Tutorial: Launch and configure a WordPress instance in Amazon Lightsail](amazon-lightsail-tutorial-launching-and-configuring-wordpress.md)\.

1. Turn on VPC peering in your Lightsail account\. For more information, see [Set up peering to work with AWS resources outside of Lightsail](lightsail-how-to-set-up-vpc-peering-with-aws-resources.md)\.

1. Create an Aurora managed database in Amazon RDS\. The database must be located in the same AWS Region as your WordPress instance\. It should also be in a running state before you continue\. For more information, see [Getting started with Amazon Aurora](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/CHAP_GettingStartedAurora.html) in the Amazon Aurora User Guide\.

## Step 2: Configure the security group for your Aurora database<a name="configure-aurora-security-group"></a>

An AWS security group acts as a virtual firewall for your AWS resources\. It controls the incoming and outgoing traffic that can connect to your Aurora database in Amazon RDS\. For more information about security groups, see [Control traffic to resources using security groups](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html) in the Amazon Virtual Private Cloud User Guide\.

Complete the following procedure to configure the security group so that your WordPress instance can establish a connection to your Aurora database\.

1. Sign in to the [Amazon RDS console](https://console.aws.amazon.com/rds/)\.

1. Choose **Databases** in the navigation pane\.

1. Choose the **Writer instance** of the Aurora database that your WordPress instance will connect to\.

1. Choose the **Connectivity & security tab**\.

1. In the **Endpoint & port** section, make a note of the **Endpoint name** and **Port** of the **Writer instance**\. You will need these later when configuring your Lightsail instance to connect to the database\.

1. In the **Security** section, choose the active VPC security group link\. You will be redirected to your database’s security group\.  
![\[Connectivity & security tab screenshot of the Amazon RDS console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/wp-aurora-db-select-writer-instance.png)

1. Make sure that the security group for your Aurora database is selected\.

1. Choose the **Inbound rules** tab\.

1. Choose **Edit inbound rules**\.  
![\[Inbound rules tab screenshot of the Amazon RDS console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/wp-aurora-select-security-group.png)

1. In the **Edit inbound rules** page, choose **Add rule**\.

1. Complete one of the following steps:
   + If you are using the default MySQL port 3306, select **MySQL/Aurora** in the **Type** dropdown menu\.
   + If you are using a custom port for your database, select **Custom TCP** in the **Type** dropdown menu and enter the port number in the **Port Range** text box\.

1. In the **Source** text box, add the private IP address of your WordPress instance\. You must enter the IP addresses in CIDR notation, which means that you must append `/32`\. For example, to allow `192.0.2.0`, enter `192.0.2.0/32`\.

1. Choose **Save rules**\.  
![\[Inbound rules detail screenshot of the Amazon RDS console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/wp-aurora-add-security-group-rule.png)

## Step 3: Connect to your Aurora database from your Lightsail instance<a name="connect-to-aurora-database-from-lightsail-instance"></a>

Complete the following procedure to confirm that you can connect to your Aurora database from your Lightsail instance\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Instances** tab\.  
![\[Lightsail homepage.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/wp-aurora-homepage-select-instances-tab.png)

1. Choose the browser\-based SSH client icon for your WordPress instance to connect to it using SSH\.  
![\[Browser-based SSH client icon.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/wp-aurora-browser-based-ssh-client.png)

1. After you're connected to your instance, enter the following command to connect to your Aurora database\. In the command, replace *DatabaseEndpoint* with the endpoint address of your Aurora database and replace *Port* with the port of your database\. Replace *MyUserName* with the name of the user that you entered when creating the database\.

   ```
   mysql -h DatabaseEndpoint -P Port -u MyUserName -p
   ```

   You should see a response similar to the following example, which confirms that your instance can access and connect to your Aurora database\.  
![\[Successful MySQL connection response.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/wp-aurora-mysql-connect-message.png)

   If you don’t see this response, or you get an error message, then you might need to configure the security group of your Aurora database to allow the private IP address of your Lightsail instance to connect to it\. For more information, see the [Configure the security group for your Aurora database](#configure-aurora-security-group) section of this guide\.

## Step 4: Transfer the database from your WordPress instance to your Aurora database<a name="transfer-database-from-wordpres-to-aurora"></a>

Now that you’ve confirmed you can connect to your database from your instance, you should transfer your WordPress website data to your Aurora database\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. In the **Instances** tab, choose the browser\-based SSH client for your WordPress instance\.  
![\[Browser-based SSH client icon.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/wp-aurora-browser-based-ssh-client.png)

1. After the browser\-based SSH client is connected to your WordPress instance, enter the following command\. The command transfers the data from the `bitnami_wordpress` database that is on your instance and moves it to your Aurora database\. In the command, replace *DatabaseUserName* with the name of the primary user that you entered when creating the Aurora database\. Replace *DatabaseEndpoint* with the endpoint address of your Aurora database\.

   ```
   sudo mysqldump -u root --databases bitnami_wordpress --single-transaction --compress --order-by-primary -p$(cat /home/bitnami/bitnami_application_password) | sudo mysql -u DatabaseUserName --host  DatabaseEndpoint --password
   ```

   **Example**

   ```
   sudo mysqldump -u root --databases bitnami_wordpress --single-transaction --compress --order-by-primary -p$(cat /home/bitnami/bitnami_application_password) | sudo mysql -u DBuser --host  abc123exampleE67890.czowadgeezqi.us-west-2.rds.amazonaws.com --password
   ```

1. At the `Enter password` prompt, enter the password for your Aurora database, and press **Enter**\.

   You won't be able to see the password while you type it\.  
![\[Password prompt screenshot.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/wp-aurora-mysql-dump-1.png)

   If the data transfer succeeds, a response similar to the following example is displayed:  
![\[Successful transfer response.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/wp-aurora-mysql-dump-2.png)

   If you get an error, confirm that you’re using the correct database user name, password, and endpoint, and try again\.

## Step 5: Configure WordPress to connect to your Aurora database<a name="connect-wordpress-to-aurora"></a>

After you transfer your application data to your Aurora database, you should configure WordPress to connect to it\. Complete the following procedure to edit the WordPress configuration file \(`wp-config.php`\) so that your website connects to your Aurora database\.

1. In the browser\-based SSH client that is connected to your WordPress instance, enter the following command to create a backup of the `wp-config.php` file:

   ```
   cp /opt/bitnami/wordpress/wp-config.php /opt/bitnami/wordpress/wp-config.php-backup
   ```

1. Enter the following command to make the `wp-config.php` file writable:

   ```
   sudo chmod 664 /opt/bitnami/wordpress/wp-config.php
   ```

1. Edit the database user name in the `config` file to the name of the primary user that you entered when creating the Aurora database\.

   ```
   sudo wp config set DB_USER DatabaseUserName
   ```

1. Edit the database host in the `config` file with the endpoint address and port number of your Aurora database\. For example, `abc123exampleE67890.czowadgeezqi.us-west-2.rds.amazonaws.com:3306`\.

   ```
   sudo wp config set DB_HOST DatabaseEndpoint:Port
   ```

1. Edit the database password in the `config` file with the password for your Aurora database\.

   ```
   sudo wp config set DB_PASSWORD DatabasePassword
   ```

1. Enter the `wp config list` command to verify that the information you entered in the `wp-config.php` file is correct\.

   ```
   sudo wp config list
   ```

   A result similar to the following example appears, displaying your configuration details:  
![\[WordPress configuration file.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/wp-aurora-wpconfig.png)

1. Enter the following command to restart the web services on your instance:

   ```
   sudo /opt/bitnami/ctlscript.sh restart
   ```

   When the services restart, a result similar to the following example is displayed:  
![\[WordPress instances restart confirmation.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/wp-aurora-service-restart.png)

   Congratulations\! Your WordPress site is now configured to use your Aurora database\.
**Note**  
If you need to restore the original `wp-config.php` file, enter the following command to restore it using the backup you created earlier in this tutorial\.  

   ```
   cp /opt/bitnami/wordpress/wp-config.php-backup /opt/bitnami/wordpress/wp-config.php
   ```