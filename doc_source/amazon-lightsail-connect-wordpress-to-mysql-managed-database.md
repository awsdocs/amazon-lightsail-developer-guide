# Tutorial: Connecting your WordPress website to a MySQL managed database in Amazon Lightsail<a name="amazon-lightsail-connect-wordpress-to-mysql-managed-database"></a>

 *Last updated: January 27, 2020* 

Crucial WordPress website data for posts, pages, and users, is stored on the MySQL database that is running on your instance in Amazon Lightsail\. If your instance fails, your data may become unrecoverable\. To prevent this scenario, you should transfer your website data to a MySQL managed database\.

In this tutorial, we show you how to transfer your WordPress website data to a MySQL managed database in Lightsail\. We also show you how to edit the WordPress configuration \(`wp-config.php`\) file on your instance so that your website connects to the managed database, and stops connecting to the database running on the instance\.

**Contents**
+ [Step 1: Complete the prerequisites](#connect-wordpress-to-mysql-managed-database-prerequisites)
+ [Step 2: Transfer the WordPress database to your MySQL managed database](#transfer-wordpress-database-to-mysql-managed-database)
+ [Step 3: Configure WordPress to connect to your MySQL managed database](#configure-wordpress-to-connect-to-mysql-managed-database)
+ [Step 4: Complete the next steps](#connect-wordpress-to-mysql-managed-database-next-steps)

## Step 1: Complete the prerequisites<a name="connect-wordpress-to-mysql-managed-database-prerequisites"></a>

Complete the following prerequisites before getting started:
+ Create a WordPress instance in Lightsail, and make sure that it’s in a running state\. For more information, see [Tutorial: Launch and configure a WordPress instance in Amazon Lightsail](amazon-lightsail-tutorial-launching-and-configuring-wordpress.md)\.
+ Create a MySQL managed database in Lightsail in the same AWS Region as your WordPress instance, and make sure it's in a running state\. WordPress works with all of the MySQL database options available in Lightsail\. For more information, see [Creating a database in Amazon Lightsail](amazon-lightsail-creating-a-database.md)\.
+ Enable the public mode and data import mode of your MySQL managed database\. You can disable these modes after completing the steps in this tutorial\. For more information, see [Configuring the public mode for your database in Amazon Lightsail](amazon-lightsail-configuring-database-public-mode.md) and [Configuring the data import mode for your database in Amazon Lightsail](amazon-lightsail-configuring-database-data-import-mode.md)\.

## Step 2: Transfer the WordPress database to your MySQL managed database<a name="transfer-wordpress-database-to-mysql-managed-database"></a>

Complete the following procedure to transfer your WordPress website data to your MySQL managed database in Lightsail\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. In the **Instances** tab, choose the browser\-based SSH client icon for your WordPress instance\.  
![\[The browser-based SSH client icon in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/amazon-lightsail-wordpress-quick-connect.png)

1. After the browser\-based SSH client is connected to your WordPress instance, enter the following command to transfer the data in the `bitnami_wordpress` database that is on your instance to your MySQL managed database\. Be sure to replace *DbUserName* with the user name of your managed database, and replace *DbEndpoint* with the endpoint address of your managed database\.

   ```
   mysqldump -u root --databases bitnami_wordpress --single-transaction --compress --order-by-primary  -p$(cat /home/bitnami/bitnami_application_password) | mysql -u DbUserName --host DbEndpoint --password
   ```

   **Example**

   ```
   mysqldump -u root --databases bitnami_wordpress --single-transaction --compress --order-by-primary -p$(cat /home/bitnami/bitnami_application_password) | mysql -u dbmasteruser --host http://ls-a3420cc0b7a6c82a21d611e6e58198cf01c.czowadgeezqi.us-west-2.rds.amazonaws.com --password
   ```

1. At the prompt, enter the password for your MySQL managed database, and press **Enter**\.

   You will not be able to see the password as it is being typed\.  
![\[Password prompt to transfer WordPress database to a MySQL managed database in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/amazon-lightsail-transfer-wordpress-database-to-mysql-managed-database.png)

1. A response similar to the following example is displayed if the data was successfully transferred\.

   If you get an error, confirm that you’re using the correct database user name, password, or endpoint, and try again\.  
![\[Successfully transfered WordPress database to a MySQL mananaged database in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/amazon-lightsail-transfer-wordpress-database-to-mysql-managed-database-success.png)

## Step 3: Configure WordPress to connect to your MySQL managed database<a name="configure-wordpress-to-connect-to-mysql-managed-database"></a>

Complete the following procedure to edit the WordPress configuration file \(`wp-config.php`\) so that your website connects to your MySQL managed database\.

1. In the browser\-based SSH client that is connected to your WordPress instance, enter the following command to create a backup of the `wp-config.php` file in case something goes wrong\.

   ```
   cp /opt/bitnami/apps/wordpress/htdocs/wp-config.php /opt/bitnami/apps/wordpress/htdocs/wp-config.php-backup
   ```

1. Enter the following command to open the `wp-config.php` file using the Nano text editor\.

   ```
   nano /opt/bitnami/apps/wordpress/htdocs/wp-config.php
   ```

1. Scroll down until you find the values for `DB_USER`, `DB_PASSWORD`, and `DB_HOST` as shown in the following example\.  
![\[Wordpress configuration file before modifications.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/amazon-lightsail-wordpress-wpconfig-file-original.png)

1. Modify the following values:
   + **DB\_USER** — Edit this to match the user name of your MySQL managed database\. The default master user name for Lightsail managed databases is `dbmasteruser`\.
   + **DB\_PASSWORD** — Edit this to match the strong password of your MySQL managed database\. For more information, see [Managing your database password in Amazon Lightsail](amazon-lightsail-managing-database-password.md)\.
   + **DB\_HOST** — Edit this to match the endpoint of your MySQL managed database\. Be sure to add the `:3306` port number at the end of the host address\. For example `ls-c6d76d20d6s6d7a695e26.csodadgdeaqi.us-west-2.rds.amazonaws.com:3306`\.

   The result should look like the following example\.  
![\[Modifications to the WordPress configuration file.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/amazon-lightsail-wordpress-wpconfig-file-modifications.png)

1. Press **Ctrl\+X** to exit Nano, then press **Y** and **Enter** to save your edits\.

1. Enter the following command to restart the web services on your instance\.

   ```
   sudo /opt/bitnami/ctlscript.sh restart
   ```

   A result similar to the following example is displayed when the services have restarted\.  
![\[Restarting server services on the WordPress instances.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/amazon-lightsail-restart-wordpress-services.png)

   Congratulations\! Your WordPress site is now configured to use the MySQL managed database\.
**Note**  
If for any reason you need to restore the original `wp-config.php` file, enter the following command to restore it using the backup you created earlier in this tutorial\.  

   ```
   cp /opt/bitnami/apps/wordpress/htdocs/wp-config.php-backup /opt/bitnami/apps/wordpress/htdocs/wp-config.php
   ```

## Step 4: Complete the next steps<a name="connect-wordpress-to-mysql-managed-database-next-steps"></a>

You should complete these additional steps after you’re done connecting your WordPress website to a MySQL managed database:
+ Create a snapshot of your WordPress instance\. For more information, see [Creating a snapshot of your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md)\.
+ Create a snapshot of the MySQL managed database\. For more information, see [Creating a snapshot of your database in Amazon Lightsail](amazon-lightsail-creating-a-database-snapshot.md)\.
+ Disable the public mode and data import mode of your MySQL managed database\. For more information, see [Configuring the public mode for your database in Amazon Lightsail](amazon-lightsail-configuring-database-public-mode.md) and [Configuring the data import mode for your database in Amazon Lightsail](amazon-lightsail-configuring-database-data-import-mode.md)\.