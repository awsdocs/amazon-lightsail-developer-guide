# Updating database parameters in Amazon Lightsail<a name="amazon-lightsail-updating-database-parameters"></a>

 *Last updated: March 15, 2019* 

Database parameters, also known as database system variables, define fundamental properties of a managed database in Amazon Lightsail\. For example, you can define a database parameter to limit the number of database connections, or define another parameter to limit the database buffer pool size\. This guide shows you how to get a list of the parameters for your managed database, and how to update them using the AWS Command Line Interface \(AWS CLI\)\.

**Note**  
For more information about MySQL system variables, refer to the [MySQL 5\.6](https://dev.mysql.com/doc/refman/5.6/en/server-system-variables.html), [MySQL 5\.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html), or [MySQL 8\.0](https://dev.mysql.com/doc/refman/8.0/en/server-system-variables.html) documentation\. For more information about PostgreSQL system variables, refer to the [PostgreSQL 9\.6](https://www.postgresql.org/docs/9.6/index.html), [PostgreSQL 10](https://www.postgresql.org/docs/10/index.html), or [PostgreSQL 11\.1](https://www.postgresql.org/docs/11/index.html) documentation\.

## Prerequisites<a name="prerequisites-to-update-database-parameters"></a>
+ If you haven't done so already, install and configure the AWS CLI\. For more information, see [Set up and configure the AWS CLI to work with Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

## Get a list of available database parameters<a name="get-database-parameters"></a>

The database parameters differ depending on the database engine; therefore, you should get a list of the parameters available for your managed database\. This will allow you to decide which parameter you want to modify, and the way in which that parameter becomes effective\.

**To get a list of available database parameters**

1. Open a Terminal or Command Prompt window\.

1. Enter the following command to get a list of parameters for your database\. Be sure to enter the name of your database in place of *DatabaseName*\.

   ```
   aws lightsail get-relational-database-parameters --relational-database-name DatabaseName
   ```

   You should see a result similar to the following example:  
![\[Get relational database parameters result\]](https://d9yljz1nd5001.cloudfront.net/en_us/1cade0c7e07039bf59652df47a09d228/images/amazon-lightsail-get-database-parameters-result.png)
**Note**  
A next page token ID is listed if the parameter results are paginated\. Make note of the next page token ID and use it as shown in the next step to view the next page of parameter results\.

1. If your results are paginated, use the following command to view the additional set of parameters\. Otherwise, skip to the next step\. Be sure to enter the name of your database in place of *DatabaseName*, and the token ID in place of *NextPageTokenID*\.

   ```
   aws lightsail get-relational-database-parameters --relational-database-name DatabaseName --page-token NextPageTokenID
   ```

   The result displays the following information for each database parameter:
   + **Allowed values** — Specifies the valid range of values for the parameter\.
   + **Apply method** — Specifies when the parameter change is applied\. Allowed options are `immediate` or `pending-reboot`\. See the following apply type for more information about how to define the apply method\.
   + **Apply type** — Specifies the engine\-specific submission type\. If `dynamic` is listed, the parameter can be applied with an `immediate` apply method and the database will begin using the new parameter value immediately\. If `static` is listed, the parameter can only be applied with a `pending-reboot` apply method and the database will begin using the new parameter only after it’s restarted\.
   + **Data type** — Specifies the valid data type for the parameter\.
   + **Description** — Provides a description of the parameter\.
   + **Is modifiable** — A Boolean value indicating whether the parameter can be modified\. If `true` is listed, then the parameter can be modified\.
   + **Parameter name** — Specifies the name of the parameter\. Use this value together with the `update relational database` operation and the `parameter name` parameter\.

1. Find the parameter you want to change, and make note of the parameter name, allowed values, and apply method\. We recommend copying the parameter name to your clipboard to avoid entering it incorrectly\. To do that, highlight the parameter name and press **Ctrl\+C** if you’re using Windows, or **Cmd\+C** if you’re using macOS, to copy it to your clipboard\. Then, press **Ctrl\+V** or **Cmd\+V** as appropriate to paste it\.

   After you identify the name of the parameter that you want to modify, continue to the next section of this guide to change the parameter to your desired value\.

## Update your database parameters<a name="update-database-parameters"></a>

After you have the name of the parameter you want to change, perform the following steps to modify the parameter for your managed database in Lightsail:

**To update your database parameters**
+ Enter the following command into a terminal or command prompt window to update a parameter for your managed database\. Be sure to enter the name of your database in place of *DatabaseName*, the name of the parameter you want to modify in place of *ParameterName*, the new value of the parameter in place of *NewParameterValue*, and the apply method in place of *ApplyMethod*\.

  ```
  aws lightsail update-relational-database-parameters --relational-database-name DatabaseName --parameters "parameterName=ParameterName,parameterValue=NewParameterValue,applyMethod=ApplyMethod"
  ```

  You should see a result similar to the following example:  
![\[Change relational database parameters result\]](https://d9yljz1nd5001.cloudfront.net/en_us/1cade0c7e07039bf59652df47a09d228/images/amazon-lightsail-update-database-parameters-result.png)

  The database parameter is updated depending on the apply method used\.
**Note**  
If the parameter's apply type is `dynamic`, the parameter can be applied with an `immediate` apply method and the database will begin using the new parameter value immediately\. However, if the parameter apply type is `static`, the parameter can only be applied with a `pending-reboot` apply method and the database will begin using the new parameter only after it’s restarted\.