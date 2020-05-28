# Tags in Amazon Lightsail<a name="amazon-lightsail-tags"></a>

**Note**  
Amazon Lightsail allows you to assign labels to your resources as tags\. Each tag is a label consisting of a key and an optional value that can make it more efficient to manage, search for, and filter resources\.

 *Last updated: November 28, 2018* 

Amazon Lightsail allows you to assign labels to your resources as tags\. Each tag is a label consisting of a key and an optional value that can make it efficient to manage, search for, and filter resources\. Although there are no inherent types of tags, they let you categorize Lightsail resources by purpose, owner, environment, or other criteria\. This is useful when you have many resources of the same type\. You can quickly identify a specific resource based on the tags you've assigned to it\. For example, define a set of tags for your resources that helps you track each resource’s project, or priority\.

A key without a value is referred to as a key\-only tag in Lightsail\. A key with a value is referred to as a key\-value tag\. The following diagram illustrates how tagging works\. In this example, each resource has a set of key\-value and key\-only tags\. The key\-value tags identify projects and priorities, and key\-only tags identify customers and application versions\.

![\[Tagging in Amazon Lightsail\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-tags.png)

## Organize billing and control access using tags<a name="organize-billing-and-control-access-using-tags"></a>

You can also use tags to organize your billing, control access to resources and requests in Lightsail, and control access to tag keys\. For more information, see one the following guides:
+ [Using tags to organize costs for your Amazon Lightsail resources](amazon-lightsail-organizing-costs-using-tags.md)
+ [Using tags to control access to your Amazon Lightsail resources](amazon-lightsail-controlling-access-using-tags.md)

## Lightsail resources that support tagging<a name="lightsail-resources-that-support-tagging"></a>

You can tag most Lightsail resources when you create them, or after they are created\. If tags cannot be applied during resource creation, Lightsail rolls back the resource creation process\. This helps to ensure that resources are either created with tags or not created at all, and that no resources that should be tagged are left untagged at any time\.

The following Lightsail resources can be tagged in the Lightsail console:
+ Instances
+ Databases
+ Disks
+ DNS zones
+ Load balancers

**Important**  
Snapshots created using the Lightsail console automatically inherit tags from the source resource\. A Lightsail resource created from that snapshot will have the same tags that were present on the source resource when the snapshot was created\.

The following resources can be tagged using the [Lightsail API](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_TagResource.html), [AWS Command Line Interface \(AWS CLI\)](https://docs.aws.amazon.com/cli/latest/reference/lightsail/tag-resource.html), or SDKs:
+ Database snapshots
+ Databases
+ Disk snapshots
+ Disks
+ Domains \(DNS zones\)
+ Instance snapshots
+ Instances
+ Key pairs
+ Load balancer TLS certificates \(TLS certificates created using Lightsail\)
+ Load balancers

**Important**  
Snapshots created using the Lightsail API, AWS CLI, or SDKs do not automatically inherit tags from the source resource\. Instead, you must manually specify the tags from the source resource using the `tags` parameter\.

## Tag restrictions<a name="tag-restrictions"></a>

The following basic restrictions apply to tags:
+ Maximum number of tags per resource – 50\.
+ For each resource, each tag key must be unique\. Each tag key can have only one value\.
+ Maximum key length – 128 Unicode characters in UTF\-8\.
+ Maximum value length – 256 Unicode characters in UTF\-8\.
+ If your tagging schema is used across multiple services and resources, remember that other services may have restrictions on allowed characters\. Generally allowed characters are: letters, numbers, and spaces, and the following characters: \+ \- = \. \_ : / @
+ Tag keys and values are case\-sensitive\.
+ Don't use the `aws:` prefix for either keys or values\. That prefix is reserved for AWS use\.

## Working with tags in Lightsail<a name="working-with-tags-in-lightsail"></a>

To get started with tags in Lightsail, see the following guides:
+ [Adding tags to a resource in Amazon Lightsail](amazon-lightsail-adding-tags-to-a-resource.md)
+ [Organizing your Amazon Lightsail resources using tags](amazon-lightsail-organizing-resources-using-tags.md)
+ [Using tags to organize costs for your Amazon Lightsail resources](amazon-lightsail-organizing-costs-using-tags.md)
+ [Using tags to control access to your Amazon Lightsail resources](amazon-lightsail-controlling-access-using-tags.md)
+ [Deleting tags in Amazon Lightsail](amazon-lightsail-deleting-tags.md)