# Instance snapshots in Amazon Lightsail<a name="understanding-instance-snapshots-in-amazon-lightsail"></a>

**Note**  
A snapshot is a way to create a backup image of your Lightsail instance \(a virtual private server\) for reference, if you might need it later\. For example, before you delete an instance, you create a snapshot of it so that if you change your mind, you have a backup to help you redo that instance as it was\.

*Last updated: April 11, 2017*

The snapshot we create is a copy of the system disk and also stores the original machine configuration \(memory, CPU, disk size, and data transfer rate\)\. If you choose to create a new instance from this snapshot, you can create the same size or larger instance\. You cannot create a smaller instance\.

**Important**  
When you create a new instance from a snapshot, Lightsail lets you create an instance bundle that is either the same size or larger size\. We do not currently support creating a *smaller* instance size from a snapshot\. The smaller options will be grayed out when you create a new instance from a snapshot\.

To create a larger instance size from a snapshot, you can use the Lightsail console, the **create\-instances\-from\-snapshot** CLI command\. or the **CreateInstancesFromSnapshot** API operation\. [Learn how to create an instance from a snapshot](lightsail-how-to-create-instance-from-snapshot.md)\.

For more information about Lightsail bundles, see [Lightsail Pricing](https://amazonlightsail.com/pricing/)\.

Here are some ways you can use snapshots:
+ [Create a snapshot of your Lightsail instance](lightsail-how-to-create-a-snapshot-of-your-instance.md)
+ [Create a Lightsail instance from a snapshot](lightsail-how-to-create-instance-from-snapshot.md)
+ [Create a larger Amazon Lightsail instance from a snapshot using the AWS CLI](lightsail-how-to-create-larger-instance-from-snapshot-using-aws-cli.md)