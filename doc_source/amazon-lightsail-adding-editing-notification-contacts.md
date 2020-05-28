# Adding notification contacts in Amazon Lightsail<a name="amazon-lightsail-adding-editing-notification-contacts"></a>

 *Last updated: February 27, 2020* 

You can configure Amazon Lightsail to notify you when a metric for one of your instances, databases, or load balancers crosses a specified threshold\. Notifications can be in the form of a banner displayed in the Lightsail console, an email sent to an address you specify, or an SMS text message sent to a mobile phone number you specify\. To be notified by email and SMS text message, you must add your email address and mobile phone number as notification contacts in each AWS Region where you want to monitor your resources\. For more information about notifications, see [Notifications in Amazon Lightsail](amazon-lightsail-notifications.md)\.

**Note**  
SMS text messaging is not supported in all AWS Regions in which you can create Lightsail resources, and text messages cannot be sent to some countries and regions of the world\. For more information, see [SMS text messaging support](#sms-support)\.

**Contents**
+ [Regional notification contact limits](#contact-limits)
+ [SMS text messaging support](#sms-support)
+ [Email contact verification](#contact-verification)
+ [Adding notification contacts using the Lightsail console](#adding-notification-contacts-console)
+ [Adding notification contacts using the AWS CLI](#adding-notification-contacts-cli)
+ [Next steps after adding your notification contacts](#next-steps-adding-notification-contacts)

## Regional notification contact limits<a name="contact-limits"></a>

You can add only one email address and one mobile phone number in each AWS Region\. If you add an email address or mobile phone number in a Region where those were already added, you will be asked if you would like to replace the existing notification contact with the new contact\.

If you require multiple email recipients in an AWS Region, you can configure a distribution list that forwards to multiple recipients, and add the distribution list's email address as the notification contact\.

## SMS text messaging support<a name="sms-support"></a>

SMS text messaging is not supported in all AWS Regions in which you can create Lightsail resources\. Also, SMS text messages cannot be sent to some countries and regions of the world\. For AWS Regions in which SMS messaging is not supported, you can configure only an email notification contact\.

SMS messaging is supported in the following AWS Regions\. These are Regions where SMS text messaging is supported by the Amazon Simple Notification Service \(Amazon SNS\), which is used by Lightsail to send you notifications:
+ US East \(N\. Virginia\) \(us\-east\-1\)
+ US West \(Oregon\) \(us\-west\-2\)
+ Europe \(Ireland\) \(eu\-west\-1\)
+ Asia Pacific \(Tokyo\) \(ap\-northeast\-1\)
+ Asia Pacific \(Singapore\) \(ap\-southeast\-1\)
+ Asia Pacific \(Sydney\) \(ap\-southeast\-2\)

For a list of countries and regions of the world where SMS text messages can be sent, and the latest AWS Regions in which SMS text messaging is supported, see [Supported Regions and Countries](https://docs.aws.amazon.com/sns/latest/dg/sns-supported-regions-countries.html) in the *Amazon SNS Developer Guide*\.

## Email contact verification<a name="contact-verification"></a>

When you add an email address as a notification contact in Lightsail, a verification request is sent to that address\. The verification request email contains a link that the recipient must click to confirm that they want to receive Lightsail notifications\. Notifications are not sent to the email address until after it is verified\. The verification comes from *AWS Notifications <no\-reply@sns\.amazonaws\.com>*, with a subject of *AWS Notification \- Subscription Confirmation*\. SMS messaging does not require verification\.

![\[Verification request email.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-email-verification.png)

Check the mailbox's spam and junk folders if the verification request is not in the inbox folder\. If the verification request got lost, or was deleted, choose **Resend verification** in the notification banner that is displayed in the Lightsail console, and in the **Account** page\.

![\[Email waiting verification banner in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-email-verification-banner.png)

## Adding notification contacts using the Lightsail console<a name="adding-notification-contacts-console"></a>

Complete the following steps to add notification contacts using the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose **Account** on the top navigation menu\.

1. Choose **Account** in the drop\-down menu\.  
![\[Account menu in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-account-drop-down.png)

1. Choose **Add email address** or **Add SMS number** in the **Notification contacts** section on the **Profile & contacts** tab\.  
![\[Notification contacts in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-notification-contacts.png)

1. Complete one of the following steps:
   + If you are adding an email address, choose the AWS Region where you want to add the notification contact\. Enter your email address into the text box\.  
![\[Select an AWS Region when adding a notification contact.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-email-notification-contact-region-menu.png)
   + If you are adding an SMS number, choose the AWS Region where you want to add the notification contact\. Choose the country of your mobile number, and enter it into the text box\. The country code is already entered for you\.
**Note**  
SMS text messaging is not supported in all AWS Regions in which you can create Lightsail resources, and text messages cannot be sent to some countries and regions of the world\. For more information, see [SMS text messaging support](#sms-support)\.  
![\[Select an AWS Region when adding a notification contact.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-sms-notification-contact-region-menu.png)

1. Choose **Add contact**\.

   When you add an email address as a notification contact, a verification request is sent to that address\. The verification request email contains a link that the recipient must click to confirm that they want to receive Lightsail notifications\. SMS messaging does not require verification\.  
![\[Email verification prompt after adding an email notification contacts in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-email-verification-modal.png)

1. Choose **I understand**\.

   Your email address or mobile phone number is added to the **Notification contacts** section\. Email addresses are not verified until you complete the verification process in the following steps\. Notifications are not sent to the email address until after you verify it\. Choose **Resend** next to one of your regional email addresses to send another verification request if the verification request got lost, or was deleted\.
**Note**  
SMS messaging does not require verification\. Therefore, you don’t need to complete steps 8 through 10 in this procedure after you add an SMS notification contact\.  
![\[Notification contacts added in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-added-notification-contacts.png)

1. Open the inbox for the email address that you added as a notification contact in Lightsail\.

1. Open the **AWS Notification \- Subscription Confirmation** email from **no\-reply@sns\.amazonaws\.com**\.
**Note**  
Check the mailbox's spam and junk folders if the verification request is not in the inbox folder\.  
![\[Verification email request.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-email-verification-request.png)

1. Choose **Confirm subscription** in the email to confirm that you want to receive Lightsail notifications\.

   A browser window opens to the following page confirming your subscription\. To unsubscribe, choose **click here to unsubscribe** on the page\. Or, if you have closed the page, complete the steps to [delete your notification contacts](amazon-lightsail-deleting-notification-contacts.md)\.  
![\[Email verification subscription.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-email-verification-subscribe.png)

## Adding notification contacts using the AWS CLI<a name="adding-notification-contacts-cli"></a>

Complete the following steps to add notification contacts for Lightsail using the AWS Command Line Interface \(AWS CLI\)\.

1. Open a Terminal or Command Prompt window\.

   If you haven't already, [install the AWS CLI](lightsail-how-to-set-up-and-configure-aws-cli.md) and [configure it to work with Lightsail](lightsail-how-to-set-up-access-keys-to-use-sdk-api-cli.md)\.

1. Enter the following command to add a notification contact:

   ```
   aws lightsail create-contact-method --region Region --notificationProtocol Protocol --contact-endpoint Destination
   ```

   In the command, replace:
   + *Region* with the AWS Region in which the notification contact should be added\.
   + *Protocol* with the notification protocol for the contact, which should be Email or SMS\.
   + *Destination* with your email address or mobile phone number\.
**Note**  
Use the E\.164 format when specifying a mobile phone number\. E\.164 is a standard for the phone number structure used for international telecommunication\. Phone numbers that follow this format can have a maximum of 15 digits, and are prefixed with the plus character \(\+\) and the country code\. For example, a U\.S\. phone number in [E\.164](https://en.wikipedia.org/wiki/E.164) format is specified as \+1XXX5550100\. For more information, see E\.164 in Wikipedia\.

   **Examples:**

   ```
   aws lightsail create-contact-method --region us-west-2 --notificationProtocol Email --contact-endpoint example@example.com
   ```

   ```
   aws lightsail create-contact-method --region us-east-1 --notificationProtocol SMS --contact-endpoint +14445556666
   ```

   When you press enter, you'll see an operation response with details about your request\.

   A verification request is sent to the email address that you specified as a notification contact\. This confirms that the recipient wants to subscribe to Lightsail notifications\. Email addresses are not verified until after the verification process in the following steps is completed\. Notifications are not sent to the email address until after the email address is verified\. Choose **Resend** next to one of your regional email addresses to send another verification request if the original notification is misplaced\.
**Note**  
SMS messaging does not require verification\. Therefore, you don’t need to complete steps 8 through 10 in this procedure when you add an SMS notification contact\.

1. Open the inbox for the email address that you added as a notification contact\.

1. Open the **AWS Notification \- Subscription Confirmation** email from **no\-reply@sns\.amazonaws\.com**\.

1. Choose **Confirm subscription** in the email to confirm that you want to receive email notifications from Lightsail\.

   A browser window opens to the following page confirming your subscription\. To unsubscribe, choose **click here to unsubscribe** on the page\. Or, if you have closed the page, complete the steps to [delete your notification contacts](amazon-lightsail-deleting-notification-contacts.md)\.

## Next steps after adding your notification contacts<a name="next-steps-adding-notification-contacts"></a>

There are a couple of additional tasks that you can perform for your notification contacts:
+ Add an alarm in the AWS Region where you added your notification contacts\. You can choose to be notified by email and SMS text message when the alarm starts\. For more information, see [Alarms in Amazon Lightsail](amazon-lightsail-alarms.md)\.
+ If don't receive notifications when you expect to be notified, then there are a few things you should check to confirm that your notification contacts are configured correctly\. To learn more, see [Troubleshooting notifications in Amazon Lightsail](amazon-lightsail-troubleshooting-notifications.md)\.
+ To stop receiving notifications, you can remove your email and mobile phone from Lightsail\. For more information, see [Deleting or disabling metric alarms in Amazon Lightsail](amazon-lightsail-deleting-notification-contacts.md)\. You can also disable or delete an alarm to stop receiving notifications for a specific alarm\. For more information, see [Deleting or disabling metric alarms in Amazon Lightsail](amazon-lightsail-deleting-health-metric-alarms.md)\.