# Amazon Lightsail Resource\-Based Policy Examples<a name="security_iam_resource-based-policy-examples"></a>

 *Last updated: October 8, 2020* 

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
                "lightsail:GetActiveNames",
                "lightsail:GetAlarms",
                "lightsail:GetAutoSnapshots",
                "lightsail:GetBlueprints",
                "lightsail:GetBundles",
                "lightsail:GetCertificates",
                "lightsail:GetCloudFormationStackRecords",
                "lightsail:GetContactMethods",
                "lightsail:GetDisk",
                "lightsail:GetDisks",
                "lightsail:GetDiskSnapshot",
                "lightsail:GetDiskSnapshots",
                "lightsail:GetDistributionBundles",
                "lightsail:GetDistributionLatestCacheReset",
                "lightsail:GetDistributionMetricData",
                "lightsail:GetDistributions",
                "lightsail:GetDomain",
                "lightsail:GetDomains",
                "lightsail:GetExportSnapshotRecords",
                "lightsail:GetInstance",
                "lightsail:GetInstanceAccessDetails",
                "lightsail:GetInstanceMetricData",
                "lightsail:GetInstancePortStates",
                "lightsail:GetInstances",
                "lightsail:GetInstanceSnapshot",
                "lightsail:GetInstanceSnapshots",
                "lightsail:GetInstanceState",
                "lightsail:GetKeyPair",
                "lightsail:GetKeyPairs",
                "lightsail:GetLoadBalancer",
                "lightsail:GetLoadBalancerMetricData",
                "lightsail:GetLoadBalancers",
                "lightsail:GetLoadBalancerTlsCertificates",
                "lightsail:GetOperation",
                "lightsail:GetOperations",
                "lightsail:GetOperationsForResource",
                "lightsail:GetRegions",
                "lightsail:GetRelationalDatabase",
                "lightsail:GetRelationalDatabaseBlueprints",
                "lightsail:GetRelationalDatabaseBundles",
                "lightsail:GetRelationalDatabaseEvents",
                "lightsail:GetRelationalDatabaseLogEvents",
                "lightsail:GetRelationalDatabaseLogStreams",
                "lightsail:GetRelationalDatabaseMetricData",
                "lightsail:GetRelationalDatabaseParameters",
                "lightsail:GetRelationalDatabases",
                "lightsail:GetRelationalDatabaseSnapshot",
                "lightsail:GetRelationalDatabaseSnapshots",
                "lightsail:GetStaticIp",
                "lightsail:GetStaticIps",
                "lightsail:IsVpcPeered"
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

![\[An instance ARN in the GetInstance results.\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/amazon-lightsail-instance-arn.png)

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
                "lightsail:GetActiveNames",
                "lightsail:GetAlarms",
                "lightsail:GetAutoSnapshots",
                "lightsail:GetBlueprints",
                "lightsail:GetBundles",
                "lightsail:GetCertificates",
                "lightsail:GetCloudFormationStackRecords",
                "lightsail:GetContactMethods",
                "lightsail:GetDisk",
                "lightsail:GetDisks",
                "lightsail:GetDiskSnapshot",
                "lightsail:GetDiskSnapshots",
                "lightsail:GetDistributionBundles",
                "lightsail:GetDistributionLatestCacheReset",
                "lightsail:GetDistributionMetricData",
                "lightsail:GetDistributions",
                "lightsail:GetDomain",
                "lightsail:GetDomains",
                "lightsail:GetExportSnapshotRecords",
                "lightsail:GetInstance",
                "lightsail:GetInstanceAccessDetails",
                "lightsail:GetInstanceMetricData",
                "lightsail:GetInstancePortStates",
                "lightsail:GetInstances",
                "lightsail:GetInstanceSnapshot",
                "lightsail:GetInstanceSnapshots",
                "lightsail:GetInstanceState",
                "lightsail:GetKeyPair",
                "lightsail:GetKeyPairs",
                "lightsail:GetLoadBalancer",
                "lightsail:GetLoadBalancerMetricData",
                "lightsail:GetLoadBalancers",
                "lightsail:GetLoadBalancerTlsCertificates",
                "lightsail:GetOperation",
                "lightsail:GetOperations",
                "lightsail:GetOperationsForResource",
                "lightsail:GetRegions",
                "lightsail:GetRelationalDatabase",
                "lightsail:GetRelationalDatabaseBlueprints",
                "lightsail:GetRelationalDatabaseBundles",
                "lightsail:GetRelationalDatabaseEvents",
                "lightsail:GetRelationalDatabaseLogEvents",
                "lightsail:GetRelationalDatabaseLogStreams",
                "lightsail:GetRelationalDatabaseMetricData",
                "lightsail:GetRelationalDatabaseParameters",
                "lightsail:GetRelationalDatabases",
                "lightsail:GetRelationalDatabaseSnapshot",
                "lightsail:GetRelationalDatabaseSnapshots",
                "lightsail:GetStaticIp",
                "lightsail:GetStaticIps",
                "lightsail:IsVpcPeered"
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

![\[A database ARN in the GetRelationalDatabase results.\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/amazon-lightsail-database-arn.png)