# Amazon Lightsail Resource\-Based Policy Examples<a name="security_iam_resource-based-policy-examples"></a>

 *Last updated: February 18, 2020* 

The term *resource\-based permissions* refers to the ability to specify which resources users are allowed to perform actions on\. Amazon Lightsail supports resource\-level permissions\. This means that for certain Lightsail actions, you can control when users are allowed to use those actions based on conditions that have to be fulfilled, or specific resources that users are allowed to use or edit\. For example, you can also grant users permissions to manage an instance or database with a specific Amazon Resource Name \(ARN\)\.

For more information about the resources that are created or modified by the Lightsail actions, and the ARNs and Lightsail condition keys that you can use in an IAM policy statement, see [Actions, Resources, and Condition Keys for Amazon Lightsail](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonlightsail.html) in the *IAM User Guide*\.

## Allow management of a specific instance<a name="security_iam_resource-based-policy-examples-manage-specific-instance"></a>

The following policy grants access to reboot/start/stop an instance, manage instance ports, and create instance snapshots for a specific instance\. It also provides read\-only access to other instance\-related information and resources in the Lightsail account\. In the policy, replace *InstanceARN* with the Amazon Resource Name \(ARN\) of your instance\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "lightsail:GetLoadBalancer",
                "lightsail:GetKeyPair",
                "lightsail:GetLoadBalancerTlsCertificates",
                "lightsail:GetCloudFormationStackRecords",
                "lightsail:GetInstance",
                "lightsail:GetDiskSnapshots",
                "lightsail:GetStaticIps",
                "lightsail:GetDomains",
                "lightsail:GetDomain",
                "lightsail:GetInstanceMetricData",
                "lightsail:GetInstanceState",
                "lightsail:GetOperationsForResource",
                "lightsail:GetInstanceSnapshot",
                "lightsail:GetInstances",
                "lightsail:GetLoadBalancers",
                "lightsail:GetExportSnapshotRecords",
                "lightsail:GetLoadBalancerMetricData",
                "lightsail:GetStaticIp",
                "lightsail:GetDiskSnapshot",
                "lightsail:GetDisk",
                "lightsail:GetInstancePortStates",
                "lightsail:GetInstanceSnapshots",
                "lightsail:GetKeyPairs",
                "lightsail:GetActiveNames",
                "lightsail:GetOperations",
                "lightsail:GetBlueprints",
                "lightsail:IsVpcPeered",
                "lightsail:GetRegions",
                "lightsail:GetDisks",
                "lightsail:GetOperation",
                "lightsail:GetBundles",
                "lightsail:GetAutoSnapshots"
            ],
            "Resource": "*"
        },
        {
            "Sid": "VisualEditor2",
            "Effect": "Allow",
            "Action": [
                "lightsail:CloseInstancePublicPorts",
                "lightsail:CreateInstanceSnapshot",
                "lightsail:OpenInstancePublicPorts",
                "lightsail:PutInstancePublicPorts",
                "lightsail:RebootInstance",
                "lightsail:StartInstance",
                "lightsail:StopInstance"
            ],
            "Resource": "InstanceARN"
        }
    ]
}
```

To get the ARN for your instance, use the `GetInstance` Lightsail API action, and specify the name of the instance using the `instanceName` parameter\. Your instance ARN will be listed in the results of that action as shown in the following example\. For more information, see [GetInstance](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetInstance.html) in the *Amazon Lightsail API Reference*\.

![\[An instance ARN in the GetInstance results.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-instance-arn.png)

## Allow management of a specific database<a name="security_iam_resource-based-policy-examples-manage-specific-database"></a>

The following policy grants access to reboot/start/stop and update a specific database\. It also provides read\-only access to other database\-related information and resources in the Lightsail account\. In the policy, replace *DatabaseARN* with the Amazon Resource Name \(ARN\) of your database\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "lightsail:GetRelationalDatabaseSnapshots",
                "lightsail:GetOperationsForResource",
                "lightsail:GetRelationalDatabase",
                "lightsail:GetRelationalDatabases",
                "lightsail:GetRelationalDatabaseSnapshot",
                "lightsail:GetActiveNames",
                "lightsail:GetOperations",
                "lightsail:GetRelationalDatabaseEvents",
                "lightsail:GetRelationalDatabaseBlueprints",
                "lightsail:GetRelationalDatabaseBundles",
                "lightsail:GetRelationalDatabaseLogEvents",
                "lightsail:GetRelationalDatabaseMetricData",
                "lightsail:IsVpcPeered",
                "lightsail:GetRegions",
                "lightsail:GetOperation",
                "lightsail:GetRelationalDatabaseParameters",
                "lightsail:GetRelationalDatabaseLogStreams"
            ],
            "Resource": "*"
        },
        {
            "Sid": "VisualEditor2",
            "Effect": "Allow",
            "Action": [
                "lightsail:RebootRelationalDatabase",
                "lightsail:StartRelationalDatabase",
                "lightsail:StopRelationalDatabase",
                "lightsail:UpdateRelationalDatabase"
            ],
            "Resource": "DatabaseARN"
        }
    ]
}
```

To get the ARN for your database, use the `GetRelationalDatabase` Lightsail API action, and specify the name of the database using the `relationalDatabaseName` parameter\. Your database ARN will be listed in the results of that action as shown in the following example\. For more information, see [GetRelationalDatabase](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabase.html) in the *Amazon Lightsail API Reference*\.

![\[A database ARN in the GetRelationalDatabase results.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-database-arn.png)