# Troubleshooting a 403 \(unauthorized\) error and getting back into Amazon Lightsail<a name="create-policy-that-grants-access-to-amazon-lightsail"></a>

 *Last updated: March 24, 2017* 

When you're trying to access Lightsail, you might see the following 403 error\. Don't panic\! We'll help you sort this out\.

![\[403 error in Amazon Lightsail - unauthorized\]](https://d9yljz1nd5001.cloudfront.net/en_us/b380b072d417d05346bbc87239d4fd76/images/403-not-authorized-access-error-in-amazon-lightsail.png)

## Troubleshooting: Try these things first<a name="troubleshooting-try-these-things-first"></a>

If you're logged into AWS with your root credentials and you just created your account, you might need to wait a few minutes\. If you still can't log in, contact [AWS Customer Support](https://console.aws.amazon.com/support/home#/)\.

Try refreshing your browser first in case it's been a while since you last authenticated\. If you're prompted to sign in again, be sure you sign in using an account that has Lightsail access\.

Another common scenario is that you might be logged in to Lightsail using an account that doesn't have Lightsail access\.

If you have an account with Lightsail access, do the following to sign out of the account that doesn't have access to Lightsail, and then log back in with the account that does have access\. 

1. On the **Account** menu, choose **Sign out**\.

1. Sign in again using your account that has Lightsail access\.

## Create an IAM policy to allow your account to access Lightsail<a name="setting-up-an-iam-policy-that-has-access-to-amazon-lightsail"></a>

If you don't have an account that has Lightsail access, follow these steps to create an AWS Identity and Access Management policy to allow access\.

1. [Open the IAM console](https://console.aws.amazon.com/iam/)\.

1. Choose **Policies**\.

1. Choose **Get Started**\.

1. Choose **Create Policy**\.

1. Select **Create Your Own Policy**

1. On the **Review Policy** page, provide a **Policy Name** and a **Description** for your new policy\.

   For example, `lightsail-policy`\.

1. Paste the following **Policy Document** into the editor\.

   ```
   {
       "Version": "2012-10-17",
       "Statement": [
           {
               "Effect": "Allow",
               "Action": [
                   "lightsail:*"
               ],
               "Resource": "*"
           }
       ]
   }
   ```

1. Choose **Create Policy**\.

## Create a new user or attach your new policy to an existing user<a name="creating-a-user-with-this-iam-policy"></a>

1. Go back to the [IAM console](https://console.aws.amazon.com/iam/)\.

1. Choose **Users**\.

1. Choose **Add user**\.

1. Provide a **User name**\. For example, **lightsail\-user**\.

1. If you're creating a console user, choose **AWS Management Console access**\.

   You can also create **Programmatic access** at the same time if your user needs to access Lightsail using the AWS Command Line Interface \(AWS CLI\) or the Lightsail API\.

1. Choose **Next: Permissions**\.

1. Choose **Attach existing policies directly**\.

1. Choose the policy you created in the previous step, and then choose **Next: Review**\.

1. Choose **Create user**\.

   If you're successful, your screen should look like this\.  
![\[Successful creation of an IAM user with the attached policy.\]](https://d9yljz1nd5001.cloudfront.net/en_us/b380b072d417d05346bbc87239d4fd76/images/iam-console-add-user-success.png)

1. If you created the user for yourself, then show the password and copy it to a safe location\.

   If you created the user for someone else, choose **Send email** and follow the instructions to send the new user name to that user\.

   You should now be able to log out of Lightsail and log back in using these new credentials\.

For more information, see [Creating an IAM User in Your AWS Account](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html)\.

If you still have trouble, please contact [AWS Customer Support](https://console.aws.amazon.com/support/home#/)\.