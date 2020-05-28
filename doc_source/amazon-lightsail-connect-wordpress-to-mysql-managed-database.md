# Tutorial: Connecting your WordPress website to a MySQL managed database in Amazon Lightsail<a name="amazon-lightsail-connect-wordpress-to-mysql-managed-database"></a>

 *Last updated: June 27, 2019* 

Crucial WordPress website data for posts, pages, and users, is stored on the MySQL database that is running on the instance in Amazon Lightsail\. If the WordPress instance fails, your data may become unrecoverable\. To avoid this scenario, you should transfer your website data to a MySQL managed database in Amazon Lightsail\.

This tutorial shows you how to transfer your WordPress website data for posts, pages, and users, to a MySQL managed database in Lightsail\. It also shows you how to edit the WordPress configuration file so that your WordPress website connects to the new managed database, and stops using the database running on the instance\.

**Contents**
+ [Step 1: Complete the prerequisites](#connect-wordpress-to-mysql-managed-database-prerequisites)
+ [Step 2: Transfer the WordPress database to a MySQL managed database in Lightsail](#transfer-wordpress-database-to-mysql-managed-database)
+ [Step 3: Configure WordPress to connect to your MySQL managed database](#configure-wordpress-to-connect-to-mysql-managed-database)
+ [Step 4: Complete the next steps](#connect-wordpress-to-mysql-managed-database-next-steps)

## Step 1: Complete the prerequisites<a name="connect-wordpress-to-mysql-managed-database-prerequisites"></a>

Complete the following prerequisites if you haven't already:
+ Create a WordPress instance in Lightsail, and make sure that it’s in a running state\. For more information, see [Tutorial: Launch and configure a WordPress instance in Amazon Lightsail](amazon-lightsail-tutorial-launching-and-configuring-wordpress.md)\.
+ Create a MySQL managed database in Lightsail in the same AWS Region as your WordPress instance, and make sure it's in a running state\. WordPress works with all of the MySQL database options available in Lightsail\. For more information, see [Creating a database in Amazon Lightsail](amazon-lightsail-creating-a-database.md)\.
+ Enable public and data import modes for your MySQL managed database\. You can disable these modes after completing the steps in this tutorial\. For more information, see [Configuring the public mode for your database in Amazon Lightsail](amazon-lightsail-configuring-database-public-mode.md) and [Configuring the data import mode for your database in Amazon Lightsail](amazon-lightsail-configuring-database-data-import-mode.md)\.

## Step 2: Transfer the WordPress database to a MySQL managed database in Lightsail<a name="transfer-wordpress-database-to-mysql-managed-database"></a>

Complete these steps to transfer your WordPress website data for posts, pages, and users, to your MySQL managed database in Lightsail\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. In the **Instances** tab, choose the browser\-based SSH client icon for your WordPress instance\.  
![\[The browser-based SSH client icon in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wordpress-quick-connect.png)

1. After the browser\-based SSH client is connected to your WordPress instance, enter the following command to transfer the `bitnami_wordpress` database on the instance to your MySQL managed database\. Be sure to replace *DbUserName* with the user name for your managed database, and replace *DbEndpoint* with the endpoint address for your managed database\.

   ```
   mysqldump -u root --databases bitnami_wordpress --single-transaction --compress --order-by-primary  -p$(cat /home/bitnami/bitnami_application_password) | mysql -u DbUserName --host DbEndpoint --password
   ```

   Example:

   ```
   mysqldump -u root --databases bitnami_wordpress --single-transaction
             --compress --order-by-primary -p$(cat /home/bitnami/bitnami_application_password) | mysql
             -u dbmasteruser --host
               http://ls-a3420cc0b7a6c82a21d611e6e58198cf01c.czowadgeezqi.us-west-2.rds.amazonaws.com
             --password
   ```

1. At the prompt, enter the password for your MySQL managed database, and press **Enter**\.  
![\[Password prompt to transfer WordPress database to a MySQL managed database in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-transfer-wordpress-database-to-mysql-managed-database.png)
**Note**  
You will not be able to see the password as it is being typed\. You should copy and paste the password into the SSH client window so that you don’t mistype it\.

1. A result similar to the following displays if the data was successfully transferred\.  
![\[Successfully transfered WordPress database to a MySQL mananaged database in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-transfer-wordpress-database-to-mysql-managed-database-success.png)

   If you get an error, confirm that you’re using the correct database user name, password, or endpoint, and try again\.

## Step 3: Configure WordPress to connect to your MySQL managed database<a name="configure-wordpress-to-connect-to-mysql-managed-database"></a>

Complete these steps to edit the WordPress configuration file so that your website connects to your MySQL managed database\.

1. In the browser\-based SSH client that is connected to your WordPress instance, enter the following command to create a backup of the WordPress configuration file in case something goes wrong:

   ```
   cp /opt/bitnami/apps/wordpress/htdocs/wp-config.php /opt/bitnami/apps/wordpress/htdocs/wp-config.php-backup
   ```

1. Enter the following command to open the WordPress configuration file using the Nano text editor:

   ```
   nano /opt/bitnami/apps/wordpress/htdocs/wp-config.php
   ```

1. Press the down arrow on your keyboard to scroll down until you find the values for **DB\_USER**, **DB\_PASSWORD**, and **DB\_HOST** as shown in the following example\.  
![\[Wordpress configuration file before modifications.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wordpress-wpconfig-file-original.png)

1. Modify the following values:
   + **DB\_USER** — Edit this to match the master user name for the MySQL managed database\. The default master user name for Lightsail managed databases is dbmasteruser\.
   + **DB\_PASSWORD** — Edit this to match the strong password for the MySQL managed database\. For more information, see [Managing your database password in Amazon Lightsail](amazon-lightsail-managing-database-password.md)\.
   + **DB\_HOST** — Edit this to match the endpoint for the MySQL managed database\. Be sure to add the `:3306` port number at the end of the host address\. For example: `ls-c6d76d20d6s6d7a695e26.csodadgdeaqi.us-west-2.rds.amazonaws.com:3306`\.

     The result should look like the following:  
![\[Modifications to the WordPress configuration file.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wordpress-wpconfig-file-modifications.png)

1. Press **Ctrl\+X** to exit Nano, then press **Y** and **Enter** to save your edits to the WordPress configuration file\.
**Note**  
If for any reason you need to restore the original `wp-config.php` file, enter the following command to restore it using the backup you created earlier in this tutorial:  

   ```
   cp /opt/bitnami/apps/wordpress/htdocs/wp-config.php-backup /opt/bitnami/apps/wordpress/htdocs/wp-config.php
   ```

1. Enter the following command to restart the web services:

   ```
   sudo /opt/bitnami/ctlscript.sh restart
   ```

   A result similar to the following displays when the services have restarted:  
![\[Restarting server services on the WordPress instances.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-restart-wordpress-services.png)

   Congratulations\! Your WordPress site is now configured to use the MySQL managed database\.

## Step 4: Complete the next steps<a name="connect-wordpress-to-mysql-managed-database-next-steps"></a>

Complete these steps after you’re done connecting your WordPress website to a MySQL managed database\.
+ Create a snapshot of your WordPress instance\. For more information, see [Creating a snapshot of your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md)\.
+ You should also create a snapshot of the MySQL managed database\. For more information, see [Creating a snapshot of your database in Amazon Lightsail](amazon-lightsail-creating-a-database-snapshot.md)\.
+ Disable public and data import modes for the MySQL managed database\. For more information, see [Configuring the public mode for your database in Amazon Lightsail](amazon-lightsail-configuring-database-public-mode.md) and [Configuring the data import mode for your database in Amazon Lightsail](amazon-lightsail-configuring-database-data-import-mode.md)\.