# Create a static IP and attach it to an instance in Amazon Lightsail<a name="lightsail-create-static-ip"></a>

 *Last updated: June 28, 2018* 

The default dynamic public IP address attached to your Amazon Lightsail instance changes every time you stop and restart the instance\. Create a static IP address and attach it to your instance to keep the public IP address from changing\. Later, when you point a registered domain name to your instance, you don’t have to update your domain’s DNS records every time you stop and restart your instance\. For more information, see [Static IP addresses in Amazon Lightsail](understanding-static-ip-addresses-in-amazon-lightsail.md)

## Prerequisites<a name="lightsail-create-static-ip-prerequisites"></a>

You need at least one instance running in Lightsail\. To create one, see [Create an instance in Lightsail](getting-started-with-amazon-lightsail.md)\.

## Create and assign a Static IP address to an instance<a name="create-static-ip-procedure"></a>

Follow these steps to create a new static IP address and attach it to an instance in Lightsail\.

1. Sign in to the Lightsail console at [https://lightsail\.aws\.amazon\.com/](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose **Networking**\.

1. Choose **Create static IP**\.

1. Select the AWS Region where you want to create your static IP\.
**Note**  
Static IP addresses can only be attached to instances in the same Region\.

1. Choose the Lightsail resource to which you want to attach the static IP\.

1. Enter a name for your static IP\.

   Resource names:
   + Must be unique within each AWS Region in your Lightsail account\.
   + Must contain 2 to 255 characters\.
   + Must start and end with an alphanumeric character or number\.
   + Can include alphanumeric characters, numbers, periods, dashes, and underscores\.

1. Choose **Create**\.

   Now when you go to the home page, you see a static IP address that you can manage\.  
![\[Static IP address attached to an instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-static-ip-attached-to-an-instance.png)

   Also, on the **Networking** tab of your instance's management page, you'll see a blue pushpin next to your public IP address\. This indicates that the IP address is now static\.  
![\[The Networking tab of the manage instance page\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-static-ip-pushpin.png)

**Important**  
Static IP addresses are free while attached to a resource\. You can manage up to five at a time\.

For more information, see [Public IP addresses and private IP addresses in Amazon Lightsail](understanding-public-ip-and-private-ip-addresses-in-amazon-lightsail.md)\.