# Adding tags to a resource in Amazon Lightsail<a name="amazon-lightsail-adding-tags-to-a-resource"></a>

 *Last updated: November 28, 2018* 

Use tags in Amazon Lightsail to categorize your resources by purpose, owner, environment, or other criteria\. Tags can be added to resources at or after they are created\. Follow these steps to add tags to a resource after it’s been created\.

**Note**  
For more information about tags, what resources can be tagged, and the restrictions, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

**To add tags to a resource**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the tab for the resource type that you want to tag\. For example, to add a tag to a DNS zone, choose the **Networking** tab\. Or choose the **Instances** tab to add a tag to an instance\.
**Note**  
Instances, databases, disks, DNS zones, and load balancers can be tagged using the Lightsail console\. However, more Lightsail resources can be tagged using the [Lightsail API operations](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/Welcome.html), or the [AWS Command Line Interface](https://docs.aws.amazon.com/cli/latest/reference/lightsail/) \(AWS CLI\) or SDKs\. For a full list of Lightsail resources that support tagging, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

1. Choose the resource that you want to tag\.

1. On the management page for the resource that you selected, choose the **Tags** tab\.  
![\[Tags tab in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-tags-tab.png)

1. Choose one of the following options, depending on the type of tag that you want to add:
   + **Add key\-only tags** or **Edit key\-only tags** \(if tags have already been added\)\. Enter your new tag into the tag key text box, and press **Enter**\. Choose **Save** when you’re done entering your tags to add them, or choose **Cancel** to not add them\.  
![\[Key-only tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-key-only-tags.png)
   + **Create a key\-value tag**, then enter a key into the **Key** text box, and a value into the **Value** text box\. Choose **Save** when you’re done entering your tags, or choose **Cancel** to not add them\.

     Key\-value tags can only be added one at a time before saving\. To add more than one key\-value tag, repeat the previous steps\.  
![\[Key-value tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-key-value-tag.png)

## Next steps<a name="adding-tags-to-a-resource-next-steps"></a>

For more information about tasks that you can perform after adding tags to a resource, see the following guides:
+ [Organizing your Amazon Lightsail resources using tags](amazon-lightsail-organizing-resources-using-tags.md)
+ [Using tags to organize costs for your Amazon Lightsail resources](amazon-lightsail-organizing-costs-using-tags.md)
+ [Using tags to control access to your Amazon Lightsail resources](amazon-lightsail-controlling-access-using-tags.md)
+ [Deleting tags in Amazon Lightsail](amazon-lightsail-deleting-tags.md)