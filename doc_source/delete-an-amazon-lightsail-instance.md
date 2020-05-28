# Deleting an Amazon Lightsail instance<a name="delete-an-amazon-lightsail-instance"></a>

*Last updated: May 31, 2018*

If you no longer need an instance, you can delete it using the Amazon Lightsail console or the AWS Command Line Interface \(AWS CLI\)\. You stop incurring charges for the instance as soon as it’s deleted\. However, resources attached to the deleted instance, such as static IPs and snapshots, continue to incur charges until you delete them\.

**Note**  
Deleted instances cannot be recovered\. Create a snapshot of an instance before deleting if you might need the data in the instance at a later time\. For more information, see [Creating a snapshot of your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md) or [Creating a snapshot of your Windows Server instance in Amazon Lightsail](prepare-windows-based-instance-and-create-snapshot.md)\.

## Delete an instance from the Lightsail console home page<a name="delete-instance-in-lightsail-home-page"></a>

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. For the instance you want to delete, choose the actions menu icon \(⋮\), then choose **Delete**\.  
![\[Delete an instance from the Lightsail console home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/animation_delete_instance.gif)

1. Choose **Yes** to confirm the deletion\.

## Delete an instance from the Lightsail console instance management page<a name="delete-instance-in-instance-management-page"></a>

1. In the Lightsail console on the home page, choose the instance you want to delete\.

1. Choose the **Delete** tab, then choose **Delete instance**\.  
![\[Delete an instance from the Lightsail console instance management page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-delete-instance-button.png)

1. Choose **Yes** to confirm the deletion\.

## Delete an instance using the AWS CLI<a name="delete-instance-using-aws-cli"></a>

1. Complete the following prerequisites if you haven't already:

   1. Install the AWS CLI\. For more information, see [Installing the AWS CLI](http://docs.aws.amazon.com/cli/latest/userguide/installing.html) \.

   1. Configure the AWS CLI\. For more information, see [Configuring the AWS CLI](lightsail-how-to-set-up-access-keys-to-use-sdk-api-cli.md)\.

1. Open a Terminal or Command Prompt window, then type the following command to get the name of the instance you want to delete:

   ```
   aws lightsail get-instances
   ```

   You should see results similar to the following:  
![\[AWS CLI output for Lightsail get-instances operation.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-get-instance-output.png)

1. Select and copy the name of the instance you want to delete so you can use it in the next step\.
**Note**  
If the instance you want to delete does not appear, confirm that your AWS CLI is configured for the AWS Region where the instance is located\. For more information, see [Configuring the AWS CLI](lightsail-how-to-set-up-access-keys-to-use-sdk-api-cli.md)\.

1. Type the following command to delete the instance\.

   ```
   aws lightsail delete-instance --instance-name InstanceName
   ```

   In the command, replace *InstanceName* with the name of the instance\.

   If the deletion is successful, you should see a confirmation similar to the following:  
![\[AWS CLI output for Lightsail delete-instance operation.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-delete-instance-output.png)
**Note**  
If the deletion isn’t successful, you should see an error message\. Confirm that you copied and pasted the exact name of the instance and try again\.

## Next steps<a name="delete-instance-next-steps"></a>

After you delete an instance, a static IP, snapshots, block storage disks, and load balancer associated to an instance remain in Lightsail, and incur additional charges\. For more information about how to delete those resources, see the following articles:
+ [Delete a static IP in Amazon Lightsail](how-to-delete-static-ip.md)
+ [Deleting snapshots in Amazon Lightsail](amazon-lightsail-deleting-snapshots.md)
+ [Detach and delete a block storage disk in Amazon Lightsail](detach-and-delete-block-storage-disks.md)
+ [Delete a load balancer in Amazon Lightsail](delete-lightsail-load-balancer.md)