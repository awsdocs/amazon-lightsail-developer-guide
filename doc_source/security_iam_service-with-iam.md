# How Amazon Lightsail Works with IAM<a name="security_iam_service-with-iam"></a>

 *Last updated: September 2, 2021* 

Before you use IAM to manage access to Lightsail, you should understand what IAM features are available to use with Lightsail\. To get a high\-level view of how Lightsail and other AWS services work with IAM, see [AWS Services That Work with IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html) in the *IAM User Guide*\.

## Lightsail Identity\-Based Policies<a name="security_iam_service-with-iam-id-based-policies"></a>

With IAM identity\-based policies, you can specify allowed or denied actions and resources as well as the conditions under which actions are allowed or denied\. Lightsail supports specific actions, resources, and condition keys\. To learn about all of the elements that you use in a JSON policy, see [IAM JSON Policy Elements Reference](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html) in the *IAM User Guide*\.

### Actions<a name="security_iam_service-with-iam-id-based-policies-actions"></a>

Administrators can use AWS JSON policies to specify who has access to what\. That is, which **principal** can perform **actions** on what **resources**, and under what **conditions**\.

The `Action` element of a JSON policy describes the actions that you can use to allow or deny access in a policy\. Policy actions usually have the same name as the associated AWS API operation\. There are some exceptions, such as *permission\-only actions* that don't have a matching API operation\. There are also some operations that require multiple actions in a policy\. These additional actions are called *dependent actions*\.

Include actions in a policy to grant permissions to perform the associated operation\.

Policy actions in Lightsail use the following prefix before the action: `lightsail:`\. For example, to grant someone permission to run a Lightsail instance with the Lightsail `CreateInstances` API operation, you include the `lightsail:CreateInstances` action in their policy\. Policy statements must include either an `Action` or `NotAction` element\. Lightsail defines its own set of actions that describe tasks that you can perform with this service\.

To specify multiple actions in a single statement, separate them with commas as follows:

```
"Action": [
      "lightsail:action1",
      "lightsail:action2"
```

You can specify multiple actions using wildcards \(\*\)\. For example, to specify all actions that begin with the word `Create`, include the following action:

```
"Action": "lightsail:Create*"
```

To see a list of Lightsail actions, see [Actions Defined by Amazon Lightsail](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonlightsail.html#amazonlightsail-actions-as-permissions) in the *IAM User Guide*\.

### Resources<a name="security_iam_service-with-iam-id-based-policies-resources"></a>

Administrators can use AWS JSON policies to specify who has access to what\. That is, which **principal** can perform **actions** on what **resources**, and under what **conditions**\.

The `Resource` JSON policy element specifies the object or objects to which the action applies\. Statements must include either a `Resource` or a `NotResource` element\. As a best practice, specify a resource using its [Amazon Resource Name \(ARN\)](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html)\. You can do this for actions that support a specific resource type, known as *resource\-level permissions*\.

For actions that don't support resource\-level permissions, such as listing operations, use a wildcard \(\*\) to indicate that the statement applies to all resources\.

```
"Resource": "*"
```

**Important**  
Lightsail does not support resource\-level permissions for some API actions\. For more information, see [Support for resource\-level permissions and authorization based on tags in Amazon Lightsail](resource-level-permissions-and-auth-based-on-tags-support.md)\.

The Lightsail instance resource has the following ARN:

```
arn:${Partition}:lightsail:${Region}:${Account}:Instance/${InstanceId}
```

For more information about the format of ARNs, see [Amazon Resource Names \(ARNs\) and AWS Service Namespaces](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html)\.

For example, to specify the `ea123456-e6b9-4f1d-b518-3ad1234567e6` instance in your statement, use the following ARN:

```
"Resource": "arn:aws:lightsail:us-east-1:123456789012:Instance/ea123456-e6b9-4f1d-b518-3ad1234567e6"
```

To specify all instances that belong to a specific account, use the wildcard \(\*\):

```
"Resource": "arn:aws:lightsail:us-east-1:123456789012:Instance/*"
```

Some Lightsail actions, such as those for creating resources, cannot be performed on a specific resource\. In those cases, you must use the wildcard \(\*\)\.

```
"Resource": "*"
```

Many Lightsail API actions involve multiple resources\. For example, `AttachDisk` attaches a Lightsail block storage disk to an instance, so an IAM user must have permissions to use the disk and the instance\. To specify multiple resources in a single statement, separate the ARNs with commas\. 

```
"Resource": [
      "resource1",
      "resource2"
```

To see a list of Lightsail resource types and their ARNs, see [Resources Defined by Amazon Lightsail](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonlightsail.html#amazonlightsail-resources-for-iam-policies) in the *IAM User Guide*\. To learn with which actions you can specify the ARN of each resource, see [Actions Defined by Amazon Lightsail](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonlightsail.html#amazonlightsail-actions-as-permissions)\.

### Condition Keys<a name="security_iam_service-with-iam-id-based-policies-conditionkeys"></a>

Administrators can use AWS JSON policies to specify who has access to what\. That is, which **principal** can perform **actions** on what **resources**, and under what **conditions**\.

The `Condition` element \(or `Condition` *block*\) lets you specify conditions in which a statement is in effect\. The `Condition` element is optional\. You can create conditional expressions that use [condition operators](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_condition_operators.html), such as equals or less than, to match the condition in the policy with values in the request\. 

If you specify multiple `Condition` elements in a statement, or multiple keys in a single `Condition` element, AWS evaluates them using a logical `AND` operation\. If you specify multiple values for a single condition key, AWS evaluates the condition using a logical `OR` operation\. All of the conditions must be met before the statement's permissions are granted\.

 You can also use placeholder variables when you specify conditions\. For example, you can grant an IAM user permission to access a resource only if it is tagged with their IAM user name\. For more information, see [IAM policy elements: variables and tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_variables.html) in the *IAM User Guide*\. 

AWS supports global condition keys and service\-specific condition keys\. To see all AWS global condition keys, see [AWS global condition context keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html) in the *IAM User Guide*\.

Lightsail does not provide any service\-specific condition keys, but it does support using some global condition keys\. To see all AWS global condition keys, see [AWS Global Condition Context Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html) in the *IAM User Guide*\.

To see a list of Lightsail condition keys, see [Condition Keys for Amazon Lightsail](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonlightsail.html#amazonlightsail-policy-keys) in the *IAM User Guide*\. To learn with which actions and resources you can use a condition key, see [Actions Defined by Amazon Lightsail](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonlightsail.html#amazonlightsail-actions-as-permissions)\.

### Examples<a name="security_iam_service-with-iam-id-based-policies-examples"></a>

To view examples of Lightsail identity\-based policies, see [Amazon Lightsail Identity\-Based Policy Examples](security_iam_id-based-policy-examples.md)\.

## Lightsail Resource\-Based Policies<a name="security_iam_service-with-iam-resource-based-policies"></a>

Lightsail does not support resource\-based policies\.

## Access Control Lists \(ACLs\)<a name="security_iam_service-with-iam-acls"></a>

Lightsail does not support Access Control Lists \(ACLs\)\.

## Authorization Based on Lightsail Tags<a name="security_iam_service-with-iam-tags"></a>

You can attach tags to Lightsail resources or pass tags in a request to Lightsail\. To control access based on tags, you provide tag information in the [condition element](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_condition.html) of a policy using the `lightsail:ResourceTag/key-name`, `aws:RequestTag/key-name`, or `aws:TagKeys` condition keys\.

**Important**  
Lightsail does not support authorization based on tags for some API actions\. For more information, see [Support for resource\-level permissions and authorization based on tags in Amazon Lightsail](resource-level-permissions-and-auth-based-on-tags-support.md)\.

For more information about tagging Lightsail resources, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

To view an example identity\-based policy for limiting access to a resource based on the tags on that resource, see [Allowing Creation and Deletion of Lightsail Resources Based on Tags](https://lightsail.aws.amazon.com/ls/docs/en_us/articles/security_iam_id-based-policy-examples#security_iam_id-based-policy-examples-view-widget-tags)\.

## Lightsail IAM Roles<a name="security_iam_service-with-iam-roles"></a>

An [IAM role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html) is an entity within your AWS account that has specific permissions\.

### Using Temporary Credentials with Lightsail<a name="security_iam_service-with-iam-roles-tempcreds"></a>

You can use temporary credentials to sign in with federation, assume an IAM role, or to assume a cross\-account role\. You obtain temporary security credentials by calling AWS STS API operations such as [AssumeRole](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) or [GetFederationToken](https://docs.aws.amazon.com/STS/latest/APIReference/API_GetFederationToken.html)\. 

Lightsail supports using temporary credentials\. 

### Service\-Linked Roles<a name="security_iam_service-with-iam-roles-service-linked"></a>

[Service\-linked roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role) allow AWS services to access resources in other services to complete an action on your behalf\. Service\-linked roles appear in your IAM account and are owned by the service\. An IAM administrator can view but not edit the permissions for service\-linked roles\.

Lightsail supports service\-linked roles\. For details about creating or managing Lightsail service\-linked roles, see [Using Service\-Linked Roles for Amazon Lightsail](amazon-lightsail-using-service-linked-roles.md)\.

### Service Roles<a name="security_iam_service-with-iam-roles-service"></a>

Lightsail does not support service roles\.