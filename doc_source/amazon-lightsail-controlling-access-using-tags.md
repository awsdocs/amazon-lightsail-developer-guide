# Using tags to control access to your Amazon Lightsail resources<a name="amazon-lightsail-controlling-access-using-tags"></a>

 *Last updated: November 28, 2018* 

You can use tags in Amazon Lightsail to control access to resources, control access to requests, and control access to tag keys\. In this guide, you’ll learn how to create an AWS Identity and Access Management \(IAM\) policy that specifies a key\-value tag required to create or delete Lightsail resources, and attach the policy to users or groups who need to make those requests\.

**Note**  
To learn more about tags in Lightsail, what resources can be tagged, and the restrictions, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

## Step 1: Create an IAM policy<a name="create-an-iam-policy"></a>

First, create the following IAM policies in the IAM console\. For more information about creating IAM policies, see [Creating IAM Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html) in the IAM documentation\.

The following policy restricts users from creating new Lightsail resources unless a key tag of `allow` and a value of `true` is defined with the create request\. This policy also restricts users from deleting resources unless they have the `allow/true` key\-value tag\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "lightsail:Create*",
                "lightsail:TagResource",
                "lightsail:UntagResource"
            ],
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "aws:RequestTag/allow": "true"
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": [
                "lightsail:Delete*",
                "lightsail:TagResource",
                "lightsail:UntagResource"
            ],
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "aws:ResourceTag/allow": "true"
                }
            }
        }
    ]
}
```

The following policy restricts users from changing the tag for resources that have a key\-value tag that is not `allow/false`\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Deny",
            "Action": [
                "lightsail:TagResource"
            ],
            "Resource": "*",
            "Condition": {
                "StringNotEquals": {
                    "aws:ResourceTag/allow": "false"
                }
            }
        }
    ]
}
```

## Step 2: Attach the policy to users or groups<a name="attach-the-policy"></a>

After you’ve created the IAM policies, attach them to the users or groups who need to create Lightsail resources using the key\-value pair\. For more information about attaching IAM policies to users or groups, see [Adding and Removing IAM Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_manage-attach-detach.html) in the IAM documentation\.