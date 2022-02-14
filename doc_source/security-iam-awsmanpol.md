# AWS managed policies for Amazon Lightsail<a name="security-iam-awsmanpol"></a>

*Last updated: January 14, 2022*

To add permissions to users, groups, and roles, it is easier to use AWS managed policies than to write policies yourself\. It takes time and expertise to [create IAM customer managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html) that provide your team with only the permissions they need\. To get started quickly, you can use our AWS managed policies\. These policies cover common use cases and are available in your AWS account\. For more information about AWS managed policies, see [AWS managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) in the *IAM User Guide*\.

AWS services maintain and update AWS managed policies\. You can't change the permissions in AWS managed policies\. Services occasionally add additional permissions to an AWS managed policy to support new features\. This type of update affects all identities \(users, groups, and roles\) where the policy is attached\. Services are most likely to update an AWS managed policy when a new feature is launched or when new operations become available\. Services do not remove permissions from an AWS managed policy, so policy updates won't break your existing permissions\.

Additionally, AWS supports managed policies for job functions that span multiple services\. For example, the **ReadOnlyAccess** AWS managed policy provides read\-only access to all AWS services and resources\. When a service launches a new feature, AWS adds read\-only permissions for new operations and resources\. For a list and descriptions of job function policies, see [AWS managed policies for job functions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_job-functions.html) in the *IAM User Guide*\.

## AWS managed policy: LightsailExportAccess<a name="security-iam-awsmanpol-LightsailExportAccess"></a>

You can't attach LightsailExportAccess to your IAM entities\. This policy is attached to a service\-linked role that allows Lightsail to perform actions on your behalf\. For more information, see [Using Service\-Linked Roles for Amazon Lightsail](amazon-lightsail-using-service-linked-roles.md)\.

This policy grants permissions that allow Lightsail to export your instance and disk snapshots to Amazon Elastic Compute Cloud, and get the current account\-level Block Public Access configuration from Amazon Simple Storage Service \(Amazon S3\)\.

**Permissions details**

This policy includes the following permissions\.
+ `ec2` – Allows access to list and copy instance images and disk snapshots\.
+ `iam` – Allows access to delete service\-linked roles and retrieve the status of your service\-linked role deletion\.
+ `s3` – Allows access to retrieve the `PublicAccessBlock` configuration for an AWS account\.

```
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Effect": "Allow",
			"Action": [
				"iam:DeleteServiceLinkedRole",
				"iam:GetServiceLinkedRoleDeletionStatus"
			],
			"Resource": "arn:aws:iam::*:role/aws-service-role/lightsail.amazonaws.com/AWSServiceRoleForLightsail*"
		},
		{
			"Effect": "Allow",
			"Action": [
				"ec2:CopySnapshot",
				"ec2:DescribeSnapshots",
				"ec2:CopyImage",
				"ec2:DescribeImages"
			],
			"Resource": "*"
		},
		{
			"Effect": "Allow",
			"Action": [
				"s3:GetAccountPublicAccessBlock"
			],
			"Resource": "*"
		}
	]
}
```

## Lightsail updates to AWS managed policies<a name="security-iam-awsmanpol-updates"></a>
+ Edit to the `LightsailExportAccess` managed policy

  Added the `s3:GetAccountPublicAccessBlock` action to the `LightsailExportAccess` managed policy\. It allows Lightsail to get the current account\-level Block Public Access configuration from Amazon S3\.

  January 14, 2022
+ Lightsail started tracking changes

  Lightsail started tracking changes for its AWS managed policies\.

  January 14, 2022