# Using tags to organize costs for your Amazon Lightsail resources<a name="amazon-lightsail-organizing-costs-using-tags"></a>

 *Last updated: November 28, 2018* 

You can use tags in Amazon Lightsail to organize your AWS billing to reflect your own cost structure\. To do this, add key\-value tags to your Lightsail resources\. Then activate those tags in the AWS Billing and Cost Management console\. Finally, sign up to get your AWS account bill with the tag key values included in your cost allocation report\. This guide provides the steps to set this up\.

**Note**  
For more information about tags in Lightsail, what resources can be tagged, and tag restrictions, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

**Important**  
Lightsail database snapshots cannot be tracked in the cost allocation report at this time, even after a cost allocation tag is added to them\.

## Step 1: Add key\-value tags to Lightsail resources<a name="add-key-value-tags"></a>

Add key\-value tags to the Lightsail resources that you want to organize in your billing console\. For more information about key\-value tags, see [Adding tags to a resource in Amazon Lightsail](amazon-lightsail-adding-tags-to-a-resource.md)\.

It's a good idea to devise a set of tag keys that represent how you want to organize your costs\. Your cost allocation report displays the tag keys as additional columns with the applicable values for each row\. Therefore, it's more efficient to track your costs if you use a consistent set of tag keys\. For example, you can tag several Lightsail resources with a specific cost center\. You do this with a “Cost center” key and a numerical value pairing\. Then organize your billing information to see the billing for that cost center across several resources\. The following example shows key\-value tags that could be used to organize cost allocation:

![\[Key-value tags for cost allocation.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-key-value-tags-for-cost-allocation.png)

## Step 2: Activate user\-defined cost allocation tags<a name="activate-user-defined-cost-allocation-tags"></a>

After you add the necessary tags to your Lightsail resources, activate them for cost allocation in the Billing and Cost Management console\. For example, if you created a “Cost center” key tag, then activate that key tag in the Billing and Cost Management console to generate cost\-allocation reports for that tag\. For more information, see [Activating user\-defined cost allocation tags](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/activating-tags.html) in the AWS Billing and Cost Management documentation\.

## Step 3: Set up the cost allocation report, and view it<a name="set-up-cost-allocation-report"></a>

The monthly cost allocation report lists the AWS usage for your account by product category and linked account user\. The report contains the same line items as your detailed billing report and additional columns for your tag keys\. To set up the monthly cost allocation report, see [Setting up a monthly cost allocation report](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/configurecostallocreport.html#allocation-report) in the AWS Billing and Cost Management documentation\.

When you set up the cost allocation report, you defined an Amazon Simple Storage Service \(Amazon S3\) bucket where the report is saved\. Open the Amazon S3 bucket that you defined and open the cost allocation report after it becomes available\. For more information about the contents of the cost allocation report, see [Viewing a cost allocation report](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/configurecostallocreport.html#allocation-viewing) in the AWS Billing and Cost Management documentation\.