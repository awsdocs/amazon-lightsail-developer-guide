# Creating a larger Amazon Lightsail instance, block storage disk, or database from a snapshot using the AWS CLI<a name="lightsail-how-to-create-larger-instance-from-snapshot-using-aws-cli"></a>

 *Last updated: October 16, 2017* 

It happens\. Your cloud project is growing and you need more compute power right away\! We can help you with that\. You can do everything from within the Lightsail console, or you can use the AWS Command Line Interface \(AWS CLI\) to do it\.

We'll show you how to take a *snapshot* of your current Lightsail instance and create a new, larger one with the compute power you need based on that snapshot\.

**Note**  
At this time, we don't support creating a smaller instance size \(or bundle\) from a snapshot\. You can only create the same size instance or a larger instance\.

## Prerequisites<a name="create-larger-instance-from-snapshot-prerequisites"></a>

1. First, if you haven't already, you need to install the AWS CLI\. To learn more, see [Installing the AWS Command Line Interface](http://docs.aws.amazon.com/cli/latest/userguide/installing.html)\. Be sure [you configure the AWS CLI](lightsail-how-to-set-up-access-keys-to-use-sdk-api-cli.md)\.

1. You also need a snapshot of your instance to work from\. To learn more, see [Creating a snapshot of your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md)\.

## Step 1: Get your snapshot name<a name="create-larger-instance-from-snapshot-get-your-snapshot-name"></a>

This might seem obvious, but you need to have your snapshot name before you execute this AWS CLI command to create the larger instance\. The good news is that it's easy to get\.

1. In the AWS CLI, type the following\.

   ```
   aws lightsail get-instance-snapshots
   ```

   You should see output similar to the following\.

   ```
   {
       "instanceSnapshots": [
           {
               "fromInstanceName": "WordPress-512MB-EXAMPLE",
               "name": "WordPress-512MB-EXAMPLE-system-1234567891011",
               "sizeInGb": 20,
               "resourceType": "InstanceSnapshot",
               "fromInstanceArn":
               "arn:aws:lightsail:us-east-1:123456789101:Instance/86f49ee4-26cc-4802-9b0d-12345EXAMPLE",
               "state": "available",
               "arn": "arn:aws:lightsail:us-east-1:123456789101:InstanceSnapshot/c87acb5f-851e-4fbc-94f1-12345EXAMPLE",
               "fromBundleId": "nano_1_0",
               "fromBlueprintId": "wordpress_4_6_1",
               "createdAt": 1480898073.653,
               "location": {
                   "availabilityZone": "all",
                   "regionName": "us-east-2"
               }
           }
       ]
   }
   ```

1. Copy the **name** value to some place where you can get it later\. This is the `--instance-snapshot-name` value you'll use in your AWS CLI command\.

## Step 2: Choose your new Lightsail bundle<a name="create-larger-instance-from-snapshot-get-your-snapshot-name"></a>

A *bundle* is really just a pricing plan and a configuration for your instance\. For example, **Medium** Linux\-based bundles cost $20 USD per month and have 4\.0 GB of RAM, 80 GB SSD storage, and so on\.

If you started out with a smaller bundle and need more compute power, you might want to upgrade to a larger bundle\. For more information, see [Creating a larger instance, block storage disk, or database from a snapshot in Amazon Lightsail](how-to-create-larger-instance-from-snapshot-using-console.md)\.

**Important**  
You cannot resize to a smaller bundle from a snapshot\. If you want to create a smaller bundle, you have to start over\.

1. Type the following AWS CLI command\.

   ```
   aws lightsail get-bundles
   ```

   Your output should be similar to the following\.

   ```
   {
       "bundles": [
           {
               "name": "Nano",
               "power": 300,
               "price": 5.0,
               "ramSizeInGb": 0.5,
               "diskSizeInGb": 20,
               "transferPerMonthInGb": 1024,
               "cpuCount": 1,
               "instanceType": "t2.nano",
               "isActive": true,
               "bundleId": "nano_1_0"
           },
           {
               "name": "Micro",
               "power": 500,
               "price": 10.0,
               "ramSizeInGb": 1.0,
               "diskSizeInGb": 30,
               "transferPerMonthInGb": 2048,
               "cpuCount": 1,
               "instanceType": "t2.micro",
               "isActive": true,
               "bundleId": "micro_1_0"
           },
           {
               "name": "Small",
               "power": 1000,
               "price": 20.0,
               "ramSizeInGb": 2.0,
               "diskSizeInGb": 40,
               "transferPerMonthInGb": 3072,
               "cpuCount": 1,
               "instanceType": "t2.small",
               "isActive": true,
               "bundleId": "small_1_0"
           },
           {
               "name": "Medium",
               "power": 2000,
               "price": 40.0,
               "ramSizeInGb": 4.0,
               "diskSizeInGb": 60,
               "transferPerMonthInGb": 4096,
               "cpuCount": 2,
               "instanceType": "t2.medium",
               "isActive": true,
               "bundleId": "medium_1_0"
           },
           {
               "name": "Large",
               "power": 3000,
               "price": 80.0,
               "ramSizeInGb": 8.0,
               "diskSizeInGb": 80,
               "transferPerMonthInGb": 5120,
               "cpuCount": 2,
               "instanceType": "t2.large",
               "isActive": true,
               "bundleId": "large_1_0"
           }
       ]
   }
   ```

1. Locate the **bundleId** value of the bundle you want\. For more information, see [Lightsail Pricing](https://amazonlightsail.com/pricing/)\.

## Step 3: Write your AWS CLI command and create your new instance<a name="create-larger-instance-from-snapshot-create-your-cli-command"></a>

Now that you have your parameter values, you're ready to write and execute your command to create the instance\!

1. Type the following\.

   ```
   aws lightsail create-instances-from-snapshot --instance-names MyNewInstanceFromSnapshot --availability-zone us-east-1a --instance-snapshot-name WordPress-512MB-EXAMPLE-system-1234567891011 --bundle-id medium_1_0
   ```

   Your output should be similar to the following\.

   ```
   {
       "operations": [
           {
               "status": "Started",
               "resourceType": "Instance",
               "isTerminal": false,
               "statusChangedAt": 1486863990.961,
               "location": {
                   "availabilityZone": "us-east-2a",
                   "regionName": "us-east-2"
               },
               "operationType": "CreateInstance",
               "resourceName": "MyNewInstanceFromSnapshot",
               "id": "30fec45e-e7d7-4e18-96c8-12345EXAMPLE",
               "createdAt": 1486863989.784
           }
       ]
   }
   ```
**Note**  
You can also return a list of regions and Availability Zones using the AWS CLI\. Just type `aws lightsail get-regions --include-availability-zones` to return the list of availability zones with your `get-regions` request\.

1. Now open your new instance in the Lightsail console and start modifying it\.

## Next steps<a name="create-larger-instance-from-snapshot-next-steps"></a>

After you create your new instance from a snapshot, here are some things you can do next:
+ If you're done with the old instance, you might want to delete it\. You can do this by using the Lightsail console or the [delete\-instance CLI command](http://docs.aws.amazon.com/cli/latest/reference/lightsail/delete-instance.html)\.
+ If you don't need the old snapshot, you might want to delete it\. You can do this by using the Lightsail console or the [delete\-instance\-snapshot CLI command](http://docs.aws.amazon.com/cli/latest/reference/lightsail/delete-instance-snapshot.html)\.
+ If you had a static IP address attached to your old instance, you might want to keep it and attach it to the new instance\. You can do this by using the console\. See [Create a static IP and attach it to an instance](lightsail-create-static-ip.md)\.