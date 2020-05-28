# Enabling email on your WordPress instance in Amazon Lightsail<a name="amazon-lightsail-enabling-email-on-wordpress"></a>

 *Last updated: May 31, 2019* 

You can enable email on your WordPress instance in Amazon Lightsail\. Configure the SMTP service in the Amazon Simple Email Service \(Amazon SES\)\. Then activate and configure the WP Mail SMTP plugin on your instance\. After email is enabled, your WordPress administrators can request password resets for their user profiles, and will be sent email notifications for blog posts, website updates, and other plugin messages\. This guide shows you how to enable email on your WordPress instance in Amazon Lightsail using Amazon SES\.

**Contents**
+ [Step 1: Review the restrictions](#enabling-email-on-wordpress-review-the-restrictions)
+ [Step 2: Complete the prerequisites](#enabling-email-on-wordpress-prerequisites)
+ [Step 3: Create SMTP credentials in Amazon SES](#enabling-email-on-wordpress-create-smtp-credentials)
+ [Step 4: Verify your domain in Amazon SES](#enabling-email-on-wordpress-verify-your-domain)
+ [Step 5: Verify email addresses in Amazon SES](#enabling-email-on-wordpress-verify-email-addresses)
+ [Step 6: Configure the WP Mail SMTP plugin on your WordPress instance](#enabling-email-on-wordpress-verify-email-addresses)

For more information, see [Using the Amazon SES SMTP Interface to Send Email](https://docs.aws.amazon.com/ses/latest/DeveloperGuide/send-email-smtp.html) in the Amazon SES documentation\.

## Step 1: Review the restrictions<a name="enabling-email-on-wordpress-review-the-restrictions"></a>

New Amazon Web Services \(AWS\) accounts that are in the Amazon SES sandbox can send email only to verified addresses and domains\. If this is the case for your account, then we recommend that you verify your website’s domain, and verify the email addresses of your WordPress administrators\. To get their email addresses, sign in to your WordPress website’s dashboard, and choose **Users** in the left\-navigation menu\. You’ll see the administrator email addresses listed in the **Email** column as shown in the following example:

![\[Administrator email addresses in the WordPress dashboard.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wordpress-dashboard-administrators.png)

**Note**  
The default `user` profile is configured with the `user@example.com` email address\. You should change this to a working email address\. For more information, see [Users Profile Screen](https://codex.wordpress.org/Users_Your_Profile_Screen) in the WordPress documentation\.

To send email to any address and domain, you must request to have your account taken out of the Amazon SES sandbox\. For more information, see [Moving Out of the Amazon SES Sandbox](https://docs.aws.amazon.com/ses/latest/DeveloperGuide/request-production-access.html) in the Amazon SES documentation\.

## Step 2: Complete the prerequisites<a name="enabling-email-on-wordpress-prerequisites"></a>

You must complete the following tasks before you can enable email on your WordPress instance:
+ Create a WordPress instance in Lightsail\. For more information, see [Tutorial: Launch and configure a WordPress instance in Amazon Lightsail](amazon-lightsail-tutorial-launching-and-configuring-wordpress.md)\.
+ Point your registered domain to your WordPress instance using a Lightsail DNS zone\. For more information, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)\.
+ Sign up for Amazon SES and learn more about the service\. For more information about signing up for Amazon SES, see [Amazon SES Quick Start](https://docs.aws.amazon.com/ses/latest/DeveloperGuide/quick-start.html) in the Amazon SES documentation\. For more information about Amazon SES, see the following guides in the Amazon SES documentation:
  + [Amazon SES Developer Guide](https://docs.aws.amazon.com/ses/latest/DeveloperGuide/Welcome.html)
  + [Amazon SES FAQs](https://aws.amazon.com/ses/faqs/)
  + [Amazon SES Pricing](https://aws.amazon.com/ses/pricing/)
  + [Amazon SES Service Quotas](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html#limits_ses_quota)

## Step 3: Create SMTP credentials in Amazon SES<a name="enabling-email-on-wordpress-create-smtp-credentials"></a>

Creating SMTP credentials in your Amazon SES account is required to configure the WP Mail SMTP plugin that you configure later in this guide\. For more information, see [Obtaining Your Amazon SES SMTP Credentials](https://docs.aws.amazon.com/ses/latest/DeveloperGuide/smtp-credentials.html) in the Amazon SES documentation\.

**To create SMTP credentials in Amazon SES**

1. Sign in to the [Amazon SES console](https://console.aws.amazon.com/ses/)\.

1. From the left\-navigation menu, choose **SMTP settings**\.

   The **SMTP settings** page displays your SMTP server name, ports, and TLS setting\. Note these values because you need them later in this guide when configuring the WP Mail SMTP plugin on your WordPress instance\.  
![\[The SMTP settings displayed in the Amazon SES console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-amazon-ses-smtp-settings-page.png)

1. Choose **Create My SMTP Credentials**\.

1. In the **IAM User Name** text box, leave the default user name, then choose **Create**\.  
![\[IAM user name for SMTP credentials in the Amazon SES console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-amazon-ses-iam-user-name.png)

1. Choose **Show User SMTP Security Credentials** to view the SMTP username and password, or choose **Download Credentials** to download a CSV file containing the same information\. You need these credentials later when configuring the WP Mail SMTP plugin on your WordPress instance\.  
![\[SMTP security credentials in the Amazon SES console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-amazon-ses-smtp-security-credentials.png)
**Note**  
The credentials created in the Amazon SES console are automatically added to AWS Identity and Access Management \(IAM\) for your account\.

## Step 4: Verify your domain in Amazon SES<a name="enabling-email-on-wordpress-verify-your-domain"></a>

Amazon SES requires that you verify your domain to confirm that you own it and to prevent others from using it\. When you verify a domain, you are verifying all email addresses from that domain, so you don't need to verify email addresses from that domain individually\. For example, if you verify the domain `example.com`, you can send email from `user1@example.com`, `user2@example.com`, or any other user at `example.com`\. For more information, see [Verifying Domains in Amazon SES](https://docs.aws.amazon.com/ses/latest/DeveloperGuide/verify-domains.html) in the Amazon SES documentation\. 

**To verify your domain in Amazon SES**

1. In the [Amazon SES console](https://console.aws.amazon.com/ses/), from the left\-navigation menu, choose **Domains**\.

1. Choose **Verify a New Domain**\.

1. Enter the domain that you want to verify, and select the **Generate DKIM Settings** check box\.

   The domain that you verify should be the same domain that you’re using with your WordPress instance in Lightsail\.  
![\[Verify a new domain in the Amazon SES console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-amazon-ses-verify-a-new-domain.png)

1. Choose **Verify This Domain**\.

   The **Verify a New Domain** page displays the DNS records that you must add to your domain’s DNS zone to confirm that you own it\. There is a single text \(TXT\) record, a single mail exchanger \(MX\) record, and three canonical name \(CNAME\) records\.  
![\[Domain verification records in the Amazon SES console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-amazon-ses-domain-verification-records.png)

1. Open a new browser tab and navigate to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Networking** tab, then choose your domain’s DNS zone\.

1. Add the DNS records from the Amazon SES console\. For more information about editing a DNS zone in Lightsail, see the [Edit a DNS zone in Amazon Lightsail](amazon-lightsail-edit-or-delete-a-dns-zone.md)\.

   The result should look like the following example\.  
![\[Lightsail DNS zone records for Amazon SES SMTP.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-amazon-ses-dns-zone-records.png)
**Note**  
Enter an `@` symbol in the **Subdomain** text box to use the apex of your domain for an MX record\. Additionally, the MX record value provided by Amazon SES is `10 inbound-smtp.us-west-2.amazonaws.com`\. Enter `10` as the **Priority** and `inbound-smtp.us-west-2.amazonaws.com` as the **Maps to** domain\.

1. In the [Amazon SES console](https://console.aws.amazon.com/ses/), close the **Verify a New Domain** page\.

   After a few minutes, your domain listed in the Amazon SES console is labeled as verified and enabled for sending, as shown in the following example:  
![\[Verified domains in the Amazon SES console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-amazon-ses-verified-domains-list.png)

   Your SMTP service in Amazon SES is now ready to send emails from your domain\.

## Step 5: Verify email addresses in Amazon SES<a name="enabling-email-on-wordpress-verify-email-addresses"></a>

As a new Amazon SES customer, you must verify the email addresses to which you want to send email\. You do this by adding the email addresses in the Amazon SES console\. For more information, see [Verifying Email Addresses in Amazon SES](https://docs.aws.amazon.com/ses/latest/DeveloperGuide/verify-email-addresses.html) in the Amazon SES documentation\.

We recommend that you add the email addresses of your WordPress website’s administrators\. This lets them request password resets for their user profiles, and receive email notifications for blog posts, website updates, and other plugin messages\.

**Note**  
If you want to send email to any address without verification, then you must request to have your Amazon SES account moved out of the sandbox\. For more information, see [Moving Out of the Amazon SES Sandbox](https://docs.aws.amazon.com/ses/latest/DeveloperGuide/request-production-access.html) in the Amazon SES documentation\.

**To verify email addresses in Amazon SES**

1. In the [Amazon SES console](https://console.aws.amazon.com/ses/), from the left\-navigation menu, choose **Email Addresses**\.

1. Choose **Verify a New Email Address**\.

1. Enter the email address that you want to verify, and choose **Verify This Email Address**\.  
![\[Verify new email address in the Amazon SES console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-amazon-ses-verify-new-email-address.png)

   Repeat the steps 1 through 3 for every email address that you want to verify\. A verification email is sent to the email address that you entered\. The address is added to the list of verified email identities with a status of "pending verification\." It is marked as "verified" when the user opens the email message and completes the verification process\.  
![\[Verified email identities list in the Amazon SES console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-amazon-ses-verified-email-identities-list.png)

## Step 6: Configure the WP Mail SMTP plugin on your WordPress instance<a name="enabling-email-on-wordpress-configure-the-wp-mail-smtp-plugin"></a>

The final step is to configure the WP Mail SMTP plugin on your WordPress instance\. Use the SMTP credentials that you created earlier in this guide in the Amazon SES console\.

**To configure the WP Mail SMTP plugin on your WordPress instance**

1. Sign in to your WordPress website‘s dashboard as an administrator\.

1. From the left\-navigation menu, choose **Plugins**, then choose **Installed Plugins**\.

1. Scroll down to the WP Mail SMTP plugin, then choose **Activate**\. If there is a new version of the plugin, make sure to update it before continuing to the next step\.  
![\[The WP Mail SMTP plugin in the WordPress dashboard.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wordpress-wp-mail-smtp-plugin-activation.png)

1. After the WP Mail SMTP plugin is activated, choose **Settings**\. You may need to scroll back down to find the plugin\.  
![\[The WP Mail SMTP plugin in the WordPress dashboard.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wordpress-wp-mail-smtp-plugin-settings.png)

1. In the **From Email Address** text box, enter the email address that you want emails to originate from\. The email address that you enter must be confirmed in Amazon SES using the steps earlier in this guide\.

1. Choose **Force From Email** to force using the email address that you enter in the **From Email Address** text box, and ignore the “from email address” value set by other plugins\.

1. In the **From Name** text box, enter the name that you want emails to originate from, or leave it as is to use the name of the WordPress blog\.

1. Choose **Force From Name** to force using the name that you entered in the **From Name** text box\. Choosing this option ignores the “from name” value set by other plugins, and forces WordPress to use the name that you enter in the **From Name** text box\.

1. In the mailer section of the page, choose **Other SMTP**\.

1. Choose **Set the return\-path to match the From Email** to have non\-delivery receipts sent to the email address that you enter in the **From Email Address** text box\.  
![\[Configuration settings for the WP Mail SMTP plugin.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wordpress-wp-mail-smtp-plugin-configuration.png)

1. In the **SMTP Host** text box, enter the SMTP server name that you got earlier in this guide from the **SMTP Settings** page in the Amazon SES console\. 

1. Choose **TLS** in the **Encryption** section of the page to specify that the SMTP service in Amazon SES uses TLS encryption\.

1. In the **SMTP Port** text box, leave the default value of **587**\.

1. Switch the **Authentication** toggle to **ON**, then enter the SMTP username and password that you got earlier in this guide from the Amazon SES console\.  
![\[SMTP settings for the WP Mail SMTP plugin.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wordpress-wp-mail-smtp-plugin-smtp-settings.png)

1. Choose **Save Settings**\. A prompt appears confirming that the settings were successfully saved\.

1. Choose the **Email Test** tab\.

   In the next step, you send a test email to confirm that the email service is working\.

1. Enter an email address in the **Send To** text box, then choose **Send Email**\. The email address that you enter must be confirmed in Amazon SES using the steps earlier in this guide\.

   There are two possible results that you should see\.
   + If you see a success confirmation, then your WordPress website is enabled for email\. Confirm that the following test email arrives at the specified mailbox:  
![\[Test email success confirmation.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wordpress-wp-mail-smtp-plugin-success-confirmation.png)

     You can now choose **Lost your password?** on the sign\-in page for your WordPress website’s dashboard\. A new password is emailed to you if the email address on your WordPress user profile is confirmed in Amazon SES\.
   + If you see a failure notice, confirm that the SMTP settings that you entered into the WP Mail SMTP plugin match those of the SMTP service in your Amazon SES account\. Also confirm that you are using an email address that you verified in Amazon SES\.