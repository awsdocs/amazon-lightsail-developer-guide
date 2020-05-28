# Regions and Availability Zones in Amazon Lightsail<a name="understanding-regions-and-availability-zones-in-amazon-lightsail"></a>

**Note**  
In Lightsail, you can create instances \(*virtual private servers*\) and other resources worldwide\. Choose an AWS Region that is closest to your users\. In addition, you can create your resources in one or more Availability Zones\. By creating your instances in separate Availability Zones, you protect your applications from a failure in a single location\.

 *Last updated: May 7, 2018* 

When creating resources in Amazon Lightsail, create them in an AWS Region that is closest to your users\. For example, if your blog traffic comes mostly from Switzerland, choose **Frankfurt** or **Paris**\.

**Note**  
DNS zones are global resources\. They are created only in the US East \(N\. Virginia\) \(us\-east\-1\) region, but they can reference any instance in any AWS Region\.

Lightsail is available in the following AWS Regions:
+ US East \(Ohio\) \(us\-east\-2\)
+ US East \(N\. Virginia\) \(us\-east\-1\)
+ US West \(Oregon\) \(us\-west\-2\)
+ Asia Pacific \(Mumbai\) \(ap\-south\-1\)
+ Asia Pacific \(Seoul\) \(ap\-northeast\-2\)
+ Asia Pacific \(Singapore\) \(ap\-southeast\-1\)
+ Asia Pacific \(Sydney\) \(ap\-southeast\-2\)
+ Asia Pacific \(Tokyo\) \(ap\-northeast\-1\)
+ Canada \(Central\) \(ca\-central\-1\)
+ EU \(Frankfurt\) \(eu\-central\-1\)
+ EU \(Ireland\) \(eu\-west\-1\)
+ EU \(London\) \(eu\-west\-2\)
+ EU \(Paris\) \(eu\-west\-3\)

![\[Supported AWS Regions in Amazon Lightsail\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-regions_720.png)

## SSH keys and Lightsail regions<a name="ssh-keys-and-regions"></a>

In Lightsail, as soon as you create an instance in an AWS Region, we create a **Default** SSH key in that region\. This default key can be used to connect to instances only in that specific region\. To use the same key in all the regions where you have instances, create your own key pair and upload it to each of those regions\. Or upload an existing key pair in those regions\.

For more information, see [SSH and connecting to your Lightsail instance](understanding-ssh-in-amazon-lightsail.md)\.

## Tips for working with Lightsail regions<a name="tips-working-with-regions"></a>

Each AWS Region is designed to be completely isolated from other AWS Regions\. This achieves the greatest possible fault tolerance and stability\.

All communication between regions occurs across the public internet\. Therefore, you should use the appropriate encryption methods to protect your data\. Note that there is a charge for data transfer between regions\. For more information, see [Amazon EC2 Pricing \- Data Transfer](https://aws.amazon.com/ec2/pricing/on-demand/#Data_Transfer)\.

When you work with a Lightsail instance using the AWS Command Line Interface \(AWS CLI\) or API operations, you must specify its regional endpoint\. Use the `--region` option in your AWS CLI command and specify `us-east-1` to return information about DNS zones and network resources\. For more information about using the AWS CLI `--region` option, see [General Options](http://docs.aws.amazon.com/cli/latest/topic/config-vars.html#general-options) in the *AWS CLI Reference*\.

## Lightsail Availability Zones<a name="availability-zones"></a>

Availability Zones are collections of data centers that run on physically distinct, independent infrastructure\. Availability Zones are engineered to be highly reliable\. Common points of failure such as generators and cooling equipment are not shared between Availability Zones\. Availability Zones are also physically separate, so that even an extreme disaster such as a fire, tornado, or flood will affect only the single Availability Zone where it occurred\.

![\[How Availability Zones work in Amazon Lightsail\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-availability-zones-example.png)

Each AWS Region has two to six Availability Zones, which are indicated by a letter following the region name \(e\.g\., `us-east-2a`\)\. You can create Lightsail instances in only one Availability Zone at a time\. You might not see all Availability Zones at the time you create your instance\. If you don't see the list of Availability Zones at all, be sure that you have selected a region in the previous step\.

## Availability Zones and your Lightsail application<a name="why-regions-and-availability-zones"></a>

By launching your instances in separate Availability Zones, you can protect your applications from a failure in a single location\.

To create an instance that is available in multiple Availability Zones, first [create a snapshot of your instance](understanding-instance-snapshots-in-amazon-lightsail.md)\. Next, choose another Availability Zone when you [create a new instance from the snapshot you created](lightsail-how-to-create-instance-from-snapshot.md)\.

For more information, see [AWS Regions and Availability Zones](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html) in the *Amazon EC2 User Guide*\.