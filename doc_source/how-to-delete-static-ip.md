# Delete a static IP in Amazon Lightsail<a name="how-to-delete-static-ip"></a>

 *Last updated: March 18, 2017* 

If you no longer need a static IP, you can delete it using the Lightsail console\. You can delete a static IP using the Lightsail console or the AWS Command Line Interface \(AWS CLI\)\. There are two places in the Lightsail console where you can delete a static IP: from the Lightsail home page or the manage static IP page of the Lightsail console\.

**Note**  
Static IP addresses are free while attached to an instance\. You can manage five at no additional cost\.  
[Learn more about static IP addresses in Lightsail](understanding-static-ip-addresses-in-amazon-lightsail.md)\.

## Delete a static IP from the Lightsail console home page<a name="delete-static-ip-from-home-page-of-console"></a>

You can get to the Lightsail home page by choosing the **Amazon Lightsail** logo in the upper left\. [Go to the home page now](https://lightsail.aws.amazon.com/ls/webapp/home)\.

**Important**  
Deleting a static IP will completely remove the static IP\. Other resources that rely on this static IP may be impacted\.

1. From the Lightsail home page, choose **Delete** from the manage static IP menu\.  
![\[Delete a static IP from the manage static IP menu on the Lightsail home page\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-delete-static-ip-from-manage-static-ip-menu.png)

1. Choose **Yes** when Lightsail asks you to confirm\.

## Delete a static IP from the manage static IP page in the Lightsail console<a name="delete-static-ip-from-manage-static-ip-page-of-console"></a>

You can get to the manage static IP page by choosing any static IP resource in Lightsail\.

**Important**  
Deleting a static IP will completely remove the static IP\. Other resources that rely on this static IP may be impacted\.

1. From the manage static IP page, choose the **Delete** tab\.  
![\[Delete a static IP from the manage static IP page (Delete tab)\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-manage-static-ip.png)

1. Choose **Delete this static IP**  
![\[Delete a static IP from the manage static IP page (not attached to an instance)\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-delete-static-ip-from-manage-static-ip-page-not-attached.png)

   If your static IP is attached to an instance, you'll see a slightly different screen\.  
![\[Delete a static IP from the manage static IP page (attached to an instance)\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-delete-static-ip-from-manage-static-ip-page-attached.png)

1. Choose **Yes** when Lightsail asks you to confirm\.

## Delete a static IP using the AWS CLI<a name="delete-static-ip-using-aws-cli"></a>

The API operation for deleting a static IP is actually called [ReleaseStaticIp](http://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_ReleaseStaticIp.html)\. When you create a static IP, you're actually *allocating* it\. So, instead of deleting the static IP, you're actually *releasing* it\. The following example shows you how to use the `release-static-ip` AWS CLI command to delete a static IP from your Lightsail account\.

 **Prerequisites** 

First, if you haven't already, you need to install the AWS CLI\. To learn more, see [Installing the AWS Command Line Interface](http://docs.aws.amazon.com/cli/latest/userguide/installing.html)\. Be sure [you configure the AWS CLI](lightsail-how-to-set-up-access-keys-to-use-sdk-api-cli.md)\.

You'll need the name of your static IP to release it\. You can get that by using the `get-static-ips` AWS CLI command\.

1. Type the following command:

   ```
   aws lightsail get-static-ips
   ```

   You should see output similar to the following\.

   ```
   {
       "staticIps": [
           {
               "name": "Example-StaticIP",
               "resourceType": "StaticIp",
               "attachedTo": "MyInstance",
               "arn": "arn:aws:lightsail:us-east-2:123456789101:StaticIp/5282f35e-c720-4e5a-1234-12345EXAMPLE",
               "isAttached": true,
               "ipAddress": "192.0.2.0",
               "createdAt": 1489750629.026,
               "location": {
                   "availabilityZone": "all",
                   "regionName": "us-east-2"
               }
           },
           {
               "name": "my-other-static-ip",
               "resourceType": "StaticIp",
               "arn": "arn:aws:lightsail:us-east-2:123456789101:StaticIp/f5885e14-8984-49e5-1234-12345EXAMPLE",
               "isAttached": false,
               "ipAddress": "192.0.2.2",
               "createdAt": 1483653597.815,
               "location": {
                   "availabilityZone": "all",
                   "regionName": "us-east-2"
               }
           }
       ]
   }
   ```

1. Select the **name** value of the static IP you wish to release and make a note of it so you can use it in the next step\.

   For example, you can copy the value to the clipboard\.

1. Type the following command\.

   ```
   aws lightsail release-static-ip --static-ip-name StaticIpName
   ```

   In the command, replace *StaticIpName* with the name of your static IP\.

   If successful, you should see output similar to the following\.

   ```
   {
       "operations": [
           {
               "status": "Succeeded",
               "resourceType": "StaticIp",
               "isTerminal": true,
               "statusChangedAt": 1489860944.19,
               "location": {
                   "availabilityZone": "all",
                   "regionName": "us-east-2"
               },
               "operationType": "ReleaseStaticIp",
               "resourceName": "Example-StaticIP",
               "id": "92a2f0d2-eef2-4e6f-1234-12345EXAMPLE",
               "createdAt": 1489860944.19
           }
       ]
   }
   ```