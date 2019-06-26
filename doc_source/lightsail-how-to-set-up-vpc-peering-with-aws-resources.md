# Set up Amazon VPC peering to work with AWS resources outside of Amazon Lightsail<a name="lightsail-how-to-set-up-vpc-peering-with-aws-resources"></a>

 *Last updated: May 17, 2017* 

Lightsail lets you connect to AWS resources, such as an Amazon RDS database, through virtual private cloud \(VPC\) peering\. This lets you separate your data tier from the rest of your application\.

A VPC is a virtual network dedicated to your AWS account\. Everything you create inside Lightsail is inside a VPC, and you can connect your Lightsail VPC to an Amazon VPC\.

Some AWS resources, such as Amazon S3, Amazon CloudFront, and Amazon DynamoDB don't require VPC peering to be enabled\.

**Note**  
To enable VPC peering in Lightsail, you need to have a default Amazon VPC\. If you don't have a default Amazon VPC, you can create yours again \(or create one for the first time, if you have an older AWS account\) by following the instructions here: [Get a default Amazon VPC](https://aws.amazon.com/premiumsupport/knowledge-center/deleted-default-vpc/)\.  
Since AWS Regions are isolated from one another, a VPC is also isolated in the Region where you created it\. You'll need to enable VPC peering in each Region where you have Lightsail resources\.

Once you have a default Amazon VPC, follow these instructions to peer your Lightsail VPC with your Amazon VPC\.

1. In Lightsail, choose **Account**\.

1. Choose **Advanced**\.

1. Choose **Enable VPC peering**\.  
![\[Enable VPC peering on the Account page\]](https://d9yljz1nd5001.cloudfront.net/en_us/839d5f6fb9fda85efe16b0c03ccc5f0f/images/amazon-lightsail-enable-vpc-peering.png)

   If the peering connection fails, try to enable VPC peering again\. If it doesn't work, contact [AWS Customer Support](https://console.aws.amazon.com/support/home/)\.

1. To find your Lightsail VPC in the AWS Management Console, go to your [Amazon VPC Dashboard](https://console.aws.amazon.com/vpc/)\.

For more information about Amazon VPC, see [Your VPC and Subnets](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Subnets.html) in the *Amazon VPC User Guide*\.