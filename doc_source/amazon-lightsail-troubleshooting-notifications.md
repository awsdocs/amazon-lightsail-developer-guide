# Troubleshooting notifications in Amazon Lightsail<a name="amazon-lightsail-troubleshooting-notifications"></a>

 *Last updated: February 27, 2020* 

If don't receive notifications when you expect to be notified, then there are a few things you should check to confirm that your notification contacts are configured correctly\. To learn more about notifications, see [Notifications in Amazon Lightsail](amazon-lightsail-notifications.md)\.

The following list describes common notification contact issues that you may experience, along with what causes them, and how to resolve them\. If you encounter an issue that's not in the list, use the **Questions? Comments?** link at the bottom of this page to submit feedback or contact AWS Customer Support\.

**I added my email address as a notification contact but I'm not receiving email notifications**  
When you add an email address as a notification contact in Lightsail, a verification request is sent to that address\. The verification request email contains a link that the recipient must click to confirm that they want to receive Lightsail notifications\. Notifications are not sent to the email address until after it is verified\. The verification comes from *AWS Notifications <no\-reply@sns\.amazonaws\.com>*, with a subject of *AWS Notification \- Subscription Confirmation*\. SMS messaging does not require verification\.  
Check the mailbox's spam and junk folders if the verification request is not in the inbox folder\. If the verification request got lost, or was deleted, choose **Resend verification** in the notification banner that is displayed in the Lightsail console, and in the **Account** page\.  

![\[Resend email verification in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-email-verification-banner-resend.png)

**I see **null** listed as my email notification contact\.**  
Email addresses must be verified within 24 hours after they are added\. If you fail to verify an email within 24 hours, that email is automatically given a status of `invalid` and it is removed from Lightsail\. That is why you might see a value of **null** for one or more of your email notification contacts\.  

![\[Null email notification contact in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-null-email-notification-contact.png)
To fix this issue, remove the **null** email notification contact, and add the correct email address again\. Ensure that you verify the email address immediately after adding it to Lightsail\. For more information, see [Notifications in Amazon Lightsail](amazon-lightsail-notifications.md)\.

**I have not received SMS text message notifications, or I stopped receiving them recently**  
You may have opted out of receiving SMS text message notifications\. You can opt out by responding to an SMS text message notification with `ARRET` \(French\), `CANCEL`, `END`, `OPT-OUT`, `OPTOUT`, `QUIT`, `REMOVE`, `STOP`, `TD`, or `UNSUBSCRIBE`\. If you opt out a mobile phone number, you must wait 30 days before you are able to add that mobile phone number again as a notification contact in Lightsail\.