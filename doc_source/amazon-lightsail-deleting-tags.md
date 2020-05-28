# Deleting tags in Amazon Lightsail<a name="amazon-lightsail-deleting-tags"></a>

 *Last updated: November 28, 2018* 

You can delete tags from an Amazon Lightsail resource\. Deleting a tag from one resource does not delete the same tag from all other resources\. To completely delete a tag from all resources, you must remove that tag from each resource\. This guide provides the steps to delete tags from a resource\.

**Note**  
For more information about tags, what resources can be tagged, and the tag restrictions, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

**To delete tags from a resource**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the tab for the resource type that you want to delete tags from\. For example, to delete tags from a DNS zone, choose the **Networking** tab\. Or choose the **Instances** tab to delete tags from an instance\.
**Note**  
Instances, databases, disks, DNS zones, and load balancers can be tagged using the Lightsail console\. However, more Lightsail resources can be tagged using the [Lightsail API operations](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/Welcome.html), or the [AWS Command Line Interface](https://docs.aws.amazon.com/cli/latest/reference/lightsail/) \(AWS CLI\) or SDKs\. For a full list of Lightsail resources that support tagging, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

1. Choose the resource that you want to delete tags from\.

1. On the management page for the resource you selected, choose the **Tags** tab\.  
![\[Tags tab in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-tags-tab.png)

1. Do one of the following, depending on the type of tag that you want to delete from the resource:

   1. Choose **Edit key\-only tags**, then choose the delete icon \(X\) for the tag that you want to delete from the resource\. Choose **Save** when you’re done deleting tags to remove them from the resource, or choose **Cancel** to not remove them\.  
![\[Deleting a key-only tag in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-delete-key-only-tag.png)

   1. To remove a key\-value tag, choose the delete icon \(X\) for the key\-value tag\. At the prompt, choose **Yes, delete** to remove the key\-value tag, or choose **No, cancel** to not remove it\.  
![\[Deleting a key-value tag in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-delete-key-value-tag.png)