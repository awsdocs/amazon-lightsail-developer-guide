# Troubleshooting a 403 \(unauthorized\) error and getting back into Amazon Lightsail<a name="create-policy-that-grants-access-to-amazon-lightsail"></a>

 *Last updated: May 20, 2019* 

If you get a 403 error when trying to access the [Lightsail console](https://lightsail.aws.amazon.com/), don’t panic\. Try these steps to troubleshoot the problem:
+ If your AWS account or your AWS Identity and Access Management \(IAM\) user was recently created, wait a few minutes, and then refresh your browser\.
+ If it’s been a while since you last signed in, refresh your browser\. If you're prompted to sign in again, be sure to use an IAM user that has access to Lightsail\.
+ If your IAM user doesn’t have access to Lightsail, then contact the [AWS account root user](https://docs.aws.amazon.com/general/latest/gr/root-vs-iam.html) or an IAM user with administrator access to request access to Lightsail\. To learn more, see [Manage access to Amazon Lightsail for an IAM user](amazon-lightsail-managing-access-for-an-iam-user.md)\.
+ If you continue to get the 403 error after trying the above steps, contact [AWS Customer Support](https://console.aws.amazon.com/support/home#/)\. In some rare cases for AWS accounts created before 2011, support will have to manually subscribe your account to Lightsail\.