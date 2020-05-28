# Organizing your Amazon Lightsail resources using tags<a name="amazon-lightsail-organizing-resources-using-tags"></a>

 *Last updated: November 28, 2018* 

After you tag your Amazon Lightsail resources, you can filter your resources by the tags you have added\. You do this in the Lightsail console by choosing or searching for a tag\. This guide shows you how to view and filter your Lightsail resources by tags\.

**Note**  
For more information about tags, what resources can be tagged, and tag restrictions, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

## Viewing tags for a resource<a name="viewing-tags-for-a-resource"></a>

Instances, databases, disks, DNS zones, and load balancers can be tagged using the Lightsail console and therefore contain a **Tags** tab\. That tab is accessible through the resource’s management page, as shown in the following example for an instance resource\. On the **Tags** tab, you can add, edit, or delete tags\. For more information, see [Adding tags to a resource in Amazon Lightsail](amazon-lightsail-adding-tags-to-a-resource.md), and [Deleting tags in Amazon Lightsail](amazon-lightsail-deleting-tags.md)\.

![\[Viewing tags for a resource in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-viewing-tags-for-a-resource.png)

**Note**  
Instances, databases, disks, DNS zones, and load balancers can be tagged using the Lightsail console\. However, more Lightsail resources can be tagged using the [Lightsail API operations](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/Welcome.html), or the [AWS Command Line Interface](https://docs.aws.amazon.com/cli/latest/reference/lightsail/) \(AWS CLI\) or SDKs\. For a full list of Lightsail resources that support tagging, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

## Filtering Lightsail resources using tags<a name="filtering-lightsail-resources-using-tags"></a>

The following options are available in the Lightsail console to filter your resources using tags\. All of these options refresh the Lightsail home page to display only the tag that you searched for or selected\.

**Note**  
These filtering options are persistent\. If you filter by a tag, and then navigate between sections of the Lightsail home page, the filter is still applied\.
+ On the Lightsail home page, enter the key\-only tag or the value that you want to filter by into the **Search** text box, and press **Enter**\.  
![\[Searching for a tag in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-searching-for-a-tag.png)
+ Choose a tag that is displayed under a resource on the Lightsail home page\.  
![\[Choosing a tag in the Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-choosing-a-tag.png)
+ Choose a tag that is displayed in the heading of a resource\.  
![\[Choosing a tag in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-choosing-a-heading-tag.png)