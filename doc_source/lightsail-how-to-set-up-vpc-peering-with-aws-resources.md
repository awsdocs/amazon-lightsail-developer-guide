# Set up Amazon VPC peering to work with AWS resources outside of Amazon Lightsail<a name="lightsail-how-to-set-up-vpc-peering-with-aws-resources"></a>

 *Last updated: June 13, 2019* 

Lightsail lets you connect to AWS resources, such as an Amazon RDS database, through virtual private cloud \(VPC\) peering\. A VPC is a virtual network dedicated to your AWS account\. Everything you create inside Lightsail is inside a VPC, and you can connect your Lightsail VPC to an Amazon VPC\.

Some AWS resources, such as Amazon S3, Amazon CloudFront, and Amazon DynamoDB don't require VPC peering to be enabled\.

**Note**  
To enable VPC peering in Lightsail, you need to have a default Amazon VPC\. If you don't have a default Amazon VPC, you can create yours again \(or create one for the first time, if you have an older AWS account\)\. To learn more, see [Creating a Default VPC ](https://docs.aws.amazon.com/vpc/latest/userguide/default-vpc.html#create-default-vpc) in the Amazon VPC documentation\.  
Since AWS Regions are isolated from one another, a VPC is also isolated in the region where you created it\. You'll need to enable VPC peering in each region where you have Lightsail resources\.

Once you have a default Amazon VPC, follow these instructions to peer your Lightsail VPC with your Amazon VPC\.

1. In the [Lightsail console](https://lightsail.aws.amazon.com/), choose **Account** on the top navigation menu\. 

1. Choose **Account** from the drop\-down\.

1. Choose the **Advanced** tab\.

1. Choose **Enable VPC peering** under the AWS Region where you want to enable it\.  
![\[Enable VPC peering on the Account page\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-enable-vpc-peering.png)

   If the peering connection fails, try to enable VPC peering again\. If it doesn't work, contact [AWS Customer Support](https://console.aws.amazon.com/support/home/)\.

To find your Lightsail VPC in the AWS Management Console, go to your [Amazon VPC Dashboard](https://console.aws.amazon.com/vpc/)\.

For more information about Amazon VPC, see [Your VPC and Subnets](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Subnets.html) in the *Amazon VPC User Guide*\.