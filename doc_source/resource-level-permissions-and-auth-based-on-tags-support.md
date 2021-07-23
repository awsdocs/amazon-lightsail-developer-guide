# Support for resource\-level permissions and authorization based on tags in Amazon Lightsail<a name="resource-level-permissions-and-auth-based-on-tags-support"></a>

 *Last updated: July 20, 2021* 

Lightsail supports resource\-level permissions and authorization based on tags for some of its API actions\. In this guide, we describe the API actions for which resource\-level permissions and authorization based on tags is not supported\. For more information about how Lightsail works with AWS Identity and Access Management \(IAM\), see [IAM for Amazon Lightsail](security_iam.md) and [How Amazon Lightsail Works with IAM](security_iam_service-with-iam.md)\.

**Contents**
+ [API actions that support resource\-level permissions](#resource-level-permissions)
+ [API actions that support authorization based on tags](#auth-based-on-tags)

## API actions that support resource\-level permissions<a name="resource-level-permissions"></a>

The following list describes which Lightsail API actions support resource\-level permissions:
+ The following API actions **support** resource\-level permissions:
  + **[AllocateStaticIp](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_AllocateStaticIp.html)** \- Supports resource\-level permissions\.
  + **[AttachDisk](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_AttachDisk.html)** \- Supports resource\-level permissions\.
  + **[AttachInstancesToLoadBalancer](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_AttachInstancesToLoadBalancer.html)** \- Supports resource\-level permissions\.
  + **[AttachLoadBalancerTlsCertificate](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_AttachLoadBalancerTlsCertificate.html)** \- Supports resource\-level permissions\.
  + **[AttachStaticIp](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_AttachStaticIp.html)** \- Supports resource\-level permissions\.
  + **[CloseInstancePublicPorts](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CloseInstancePublicPorts.html)** \- Supports resource\-level permissions\.
  + **[CopySnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CopySnapshot.html)** \- Supports resource\-level permissions\.
  + **[CreateBucketAccessKey](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateBucketAccessKey.html)** \- Supports resource\-level permissions\.
  + **[CreateDiskFromSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateDiskFromSnapshot.html)** \- Supports resource\-level permissions\.
  + **[CreateDiskSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateDiskSnapshot.html)** \- Supports resource\-level permissions\.
  + **[CreateDomainEntry](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateDomainEntry.html)** \- Supports resource\-level permissions\.
  + **[CreateInstancesFromSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateInstancesFromSnapshot.html)** \- Supports resource\-level permissions\.
  + **[CreateInstanceSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateInstanceSnapshot.html)** \- Supports resource\-level permissions\.
  + **[CreateLoadBalancerTlsCertificate](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateLoadBalancerTlsCertificate.html)** \- Supports resource\-level permissions\.
  + **[CreateRelationalDatabaseFromSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateRelationalDatabaseFromSnapshot.html)** \- Supports resource\-level permissions\.
  + **[CreateRelationalDatabaseSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateRelationalDatabaseSnapshot.html)** \- Supports resource\-level permissions\.
  + **[DeleteBucket](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteBucket.html)** \- Supports resource\-level permissions\.
  + **[DeleteBucketAccessKey](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteBucketAccessKey.html)** \- Supports resource\-level permissions\.
  + **[DeleteDisk](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteDisk.html)** \- Supports resource\-level permissions\.
  + **[DeleteDiskSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteDiskSnapshot.html)** \- Supports resource\-level permissions\.
  + **[DeleteDomain](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteDomain.html)** \- Supports resource\-level permissions\.
  + **[DeleteDomainEntry](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteDomainEntry.html)** \- Supports resource\-level permissions\.
  + **[DeleteInstance](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteInstance.html)** \- Supports resource\-level permissions\.
  + **[DeleteInstanceSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteInstanceSnapshot.html)** \- Supports resource\-level permissions\.
  + **[DeleteKeyPair](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteKeyPair.html)** \- Supports resource\-level permissions\.
  + **[DeleteKnownHostKeys](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteKnownHostKeys.html)** \- Supports resource\-level permissions\.
  + **[DeleteLoadBalancer](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteLoadBalancer.html)** \- Supports resource\-level permissions\.
  + **[DeleteLoadBalancerTlsCertificate](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteLoadBalancerTlsCertificate.html)** \- Supports resource\-level permissions\.
  + **[DeleteRelationalDatabase](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteRelationalDatabase.html)** \- Supports resource\-level permissions\.
  + **[DeleteRelationalDatabaseSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteRelationalDatabaseSnapshot.html)** \- Supports resource\-level permissions\.
  + **[DetachDisk](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DetachDisk.html)** \- Supports resource\-level permissions\.
  + **[DetachInstancesFromLoadBalancer](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DetachInstancesFromLoadBalancer.html)** \- Supports resource\-level permissions\.
  + **[DetachStaticIp](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DetachStaticIp.html)** \- Supports resource\-level permissions\.
  + **[DownloadDefaultKeyPair](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DownloadDefaultKeyPair.html)** \- Supports resource\-level permissions\.
  + **[ExportSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_ExportSnapshot.html)** \- Supports resource\-level permissions\.
  + **[IsVpcPeered](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_IsVpcPeered.html)** \- Supports resource\-level permissions\.
  + **[OpenInstancePublicPorts](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_OpenInstancePublicPorts.html)** \- Supports resource\-level permissions\.
  + **[PeerVpc](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_PeerVpc.html)** \- Supports resource\-level permissions\.
  + **[PutInstancePublicPorts](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_PutInstancePublicPorts.html)** \- Supports resource\-level permissions\.
  + **[RebootInstance](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_RebootInstance.html)** \- Supports resource\-level permissions\.
  + **[RebootRelationalDatabase](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_RebootRelationalDatabase.html)** \- Supports resource\-level permissions\.
  + **[ReleaseStaticIp](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_ReleaseStaticIp.html)** \- Supports resource\-level permissions\.
  + **[SetIpAddressType](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_SetIpAddressType.html)** \- Supports resource\-level permissions\.
  + **[SetResourceAccessForBucket](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_SetResourceAccessForBucket.html)** \- Supports resource\-level permissions\.
  + **[StartInstance](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_StartInstance.html)** \- Supports resource\-level permissions\.
  + **[StartRelationalDatabase](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_StartRelationalDatabase.html)** \- Supports resource\-level permissions\.
  + **[StopInstance](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_StopInstance.html)** \- Supports resource\-level permissions\.
  + **[StopRelationalDatabase](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_StopRelationalDatabase.html)** \- Supports resource\-level permissions\.
  + **[TagResource](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_TagResource.html)** \- Supports resource\-level permissions\.
  + **[UnpeerVpc](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UnpeerVpc.html)** \- Supports resource\-level permissions\.
  + **[UntagResource](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UntagResource.html)** \- Supports resource\-level permissions\.
  + **[UpdateBucket](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UpdateBucket.html)** \- Supports resource\-level permissions\.
  + **[UpdateBucketBundle](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UpdateBucketBundle.html)** \- Supports resource\-level permissions\.
  + **[UpdateDomainEntry](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UpdateDomainEntry.html)** \- Supports resource\-level permissions\.
  + **[UpdateLoadBalancerAttribute](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UpdateLoadBalancerAttribute.html)** \- Supports resource\-level permissions\.
  + **[UpdateRelationalDatabase](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UpdateRelationalDatabase.html)** \- Supports resource\-level permissions\.
  + **[UpdateRelationalDatabaseParameters](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UpdateRelationalDatabaseParameters.html)** \- Supports resource\-level permissions\.
+ The following API actions **don't support** resource\-level permissions:
  + **[AttachCertificateToDistribution](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_AttachCertificateToDistribution.html)** \- Does not support resource\-level permissions\.
  + **[CreateBucket](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateBucket.html)** \- Does not support resource\-level permissions\.
  + **[CreateCertificate](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateCertificate.html)** \- Does not support resource\-level permissions\.
  + **[CreateCloudFormationStack](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateCloudFormationStack.html)** \- Does not support resource\-level permissions\.
  + **[CreateContactMethod](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateContactMethod.html)** \- Does not support resource\-level permissions\.
  + **[CreateContainerService](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateContainerService.html)** \- Does not support resource\-level permissions\.
  + **[CreateContainerServiceDeployment](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateContainerServiceDeployment.html)** \- Does not support resource\-level permissions\.
  + **[CreateContainerServiceRegistryLogin](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateContainerServiceRegistryLogin.html)** \- Does not support resource\-level permissions\.
  + **[CreateDisk](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateDisk.html)** \- Does not support resource\-level permissions\.
  + **[CreateDistribution](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateDistribution.html)** \- Does not support resource\-level permissions\.
  + **[CreateDomain](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateDomain.html)** \- Does not support resource\-level permissions\.
  + **[CreateInstances](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateInstances.html)** \- Does not support resource\-level permissions\.
  + **[CreateKeyPair](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateKeyPair.html)** \- Does not support resource\-level permissions\.
  + **[CreateLoadBalancer](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateLoadBalancer.html)** \- Does not support resource\-level permissions\.
  + **[CreateRelationalDatabase](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateRelationalDatabase.html)** \- Does not support resource\-level permissions\.
  + **[DeleteAlarm](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteAlarm.html)** \- Does not support resource\-level permissions\.
  + **[DeleteAutoSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteAutoSnapshot.html)** \- Does not support resource\-level permissions\.
  + **[DeleteCertificate](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteCertificate.html)** \- Does not support resource\-level permissions\.
  + **[DeleteContactMethod](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteContactMethod.html)** \- Does not support resource\-level permissions\.
  + **[DeleteContainerImage](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteContainerImage.html)** \- Does not support resource\-level permissions\.
  + **[DeleteContainerService](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteContainerService.html)** \- Does not support resource\-level permissions\.
  + **[DeleteDistribution](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteDistribution.html)** \- Does not support resource\-level permissions\.
  + **[DetachCertificateFromDistribution](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DetachCertificateFromDistribution.html)** \- Does not support resource\-level permissions\.
  + **[DisableAddOn](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DisableAddOn.html)** \- Does not support resource\-level permissions\.
  + **[EnableAddOn](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_EnableAddOn.html)** \- Does not support resource\-level permissions\.
  + **[GetActiveNames](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetActiveNames.html)** \- Does not support resource\-level permissions\.
  + **[GetAlarms](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetAlarms.html)** \- Does not support resource\-level permissions\.
  + **[GetAutoSnapshots](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetAutoSnapshots.html)** \- Does not support resource\-level permissions\.
  + **[GetBlueprints](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetBlueprints.html)** \- Does not support resource\-level permissions\.
  + **[GetBucketAccessKeys](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetBucketAccessKeys.html)** \- Does not support resource\-level permissions\.
  + **[GetBucketBundles](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetBucketBundles.html)** \- Does not support resource\-level permissions\.
  + **[GetBucketMetricData](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetBucketMetricData.html)** \- Does not support resource\-level permissions\.
  + **[GetBuckets](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetBuckets.html)** \- Does not support resource\-level permissions\.
  + **[GetBundles](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetBundles.html)** \- Does not support resource\-level permissions\.
  + **[GetCertificates](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetCertificates.html)** \- Does not support resource\-level permissions\.
  + **[GetCloudFormationStackRecords](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetCloudFormationStackRecords.html)** \- Does not support resource\-level permissions\.
  + **[GetContactMethods](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetContactMethods.html)** \- Does not support resource\-level permissions\.
  + **[GetContainerAPIMetadata](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetContainerAPIMetadata.html)** \- Does not support resource\-level permissions\.
  + **[GetContainerImages](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetContainerImages.html)** \- Does not support resource\-level permissions\.
  + **[GetContainerLog](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetContainerLog.html)** \- Does not support resource\-level permissions\.
  + **[GetContainerServiceDeployments](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetContainerServiceDeployments.html)** \- Does not support resource\-level permissions\.
  + **[GetContainerServiceMetricData](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetContainerServiceMetricData.html)** \- Does not support resource\-level permissions\.
  + **[GetContainerServicePowers](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetContainerServicePowers.html)** \- Does not support resource\-level permissions\.
  + **[GetContainerServices](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetContainerServices.html)** \- Does not support resource\-level permissions\.
  + **[GetDisk](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetDisk.html)** \- Does not support resource\-level permissions\.
  + **[GetDisks](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetDisks.html)** \- Does not support resource\-level permissions\.
  + **[GetDiskSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetDiskSnapshot.html)** \- Does not support resource\-level permissions\.
  + **[GetDiskSnapshots](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetDiskSnapshots.html)** \- Does not support resource\-level permissions\.
  + **[GetDistributionBundles](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetDistributionBundles.html)** \- Does not support resource\-level permissions\.
  + **[GetDistributionLatestCacheReset](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetDistributionLatestCacheReset.html)** \- Does not support resource\-level permissions\.
  + **[GetDistributionMetricData](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetDistributionMetricData.html)** \- Does not support resource\-level permissions\.
  + **[GetDistributions](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetDistributions.html)** \- Does not support resource\-level permissions\.
  + **[GetDomain](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetDomain.html)** \- Does not support resource\-level permissions\.
  + **[GetDomains](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetDomains.html)** \- Does not support resource\-level permissions\.
  + **[GetExportSnapshotRecords](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetExportSnapshotRecords.html)** \- Does not support resource\-level permissions\.
  + **[GetInstance](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetInstance.html)** \- Does not support resource\-level permissions\.
  + **[GetInstanceAccessDetails](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetInstanceAccessDetails.html)** \- Does not support resource\-level permissions\.
  + **[GetInstanceMetricData](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetInstanceMetricData.html)** \- Does not support resource\-level permissions\.
  + **[GetInstancePortStates](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetInstancePortStates.html)** \- Does not support resource\-level permissions\.
  + **[GetInstances](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetInstances.html)** \- Does not support resource\-level permissions\.
  + **[GetInstanceSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetInstanceSnapshot.html)** \- Does not support resource\-level permissions\.
  + **[GetInstanceSnapshots](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetInstanceSnapshots.html)** \- Does not support resource\-level permissions\.
  + **[GetInstanceState](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetInstanceState.html)** \- Does not support resource\-level permissions\.
  + **[GetKeyPair](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetKeyPair.html)** \- Does not support resource\-level permissions\.
  + **[GetKeyPairs](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetKeyPairs.html)** \- Does not support resource\-level permissions\.
  + **[GetLoadBalancer](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetLoadBalancer.html)** \- Does not support resource\-level permissions\.
  + **[GetLoadBalancerMetricData](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetLoadBalancerMetricData.html)** \- Does not support resource\-level permissions\.
  + **[GetLoadBalancers](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetLoadBalancers.html)** \- Does not support resource\-level permissions\.
  + **[GetLoadBalancerTlsCertificates](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetLoadBalancerTlsCertificates.html)** \- Does not support resource\-level permissions\.
  + **[GetOperation](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetOperation.html)** \- Does not support resource\-level permissions\.
  + **[GetOperations](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetOperations.html)** \- Does not support resource\-level permissions\.
  + **[GetOperationsForResource](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetOperationsForResource.html)** \- Does not support resource\-level permissions\.
  + **[GetRegions](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRegions.html)** \- Does not support resource\-level permissions\.
  + **[GetRelationalDatabase](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabase.html)** \- Does not support resource\-level permissions\.
  + **[GetRelationalDatabaseBlueprints](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseBlueprints.html)** \- Does not support resource\-level permissions\.
  + **[GetRelationalDatabaseBundles](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseBundles.html)** \- Does not support resource\-level permissions\.
  + **[GetRelationalDatabaseEvents](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseEvents.html)** \- Does not support resource\-level permissions\.
  + **[GetRelationalDatabaseLogEvents](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseLogEvents.html)** \- Does not support resource\-level permissions\.
  + **[GetRelationalDatabaseLogStreams](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseLogStreams.html)** \- Does not support resource\-level permissions\.
  + **[GetRelationalDatabaseMasterUserPassword](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseMasterUserPassword.html)** \- Does not support resource\-level permissions\.
  + **[GetRelationalDatabaseMetricData](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseMetricData.html)** \- Does not support resource\-level permissions\.
  + **[GetRelationalDatabaseParameters](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseParameters.html)** \- Does not support resource\-level permissions\.
  + **[GetRelationalDatabases](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabases.html)** \- Does not support resource\-level permissions\.
  + **[GetRelationalDatabaseSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseSnapshot.html)** \- Does not support resource\-level permissions\.
  + **[GetRelationalDatabaseSnapshots](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseSnapshots.html)** \- Does not support resource\-level permissions\.
  + **[GetStaticIp](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetStaticIp.html)** \- Does not support resource\-level permissions\.
  + **[GetStaticIps](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetStaticIps.html)** \- Does not support resource\-level permissions\.
  + **[PutAlarm](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_PutAlarm.html)** \- Does not support resource\-level permissions\.
  + **[ImportKeyPair](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_ImportKeyPair.html)** \- Does not support resource\-level permissions\.
  + **[RegisterContainerImage](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_RegisterContainerImage.html)** \- Does not support resource\-level permissions\.
  + **[ResetDistributionCache](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_ResetDistributionCache.html)** \- Does not support resource\-level permissions\.
  + **[SendContactMethodVerification](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_SendContactMethodVerification.html)** \- Does not support resource\-level permissions\.
  + **[TestAlarm](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_TestAlarm.html)** \- Does not support resource\-level permissions\.
  + **[UpdateContainerService](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UpdateContainerService.html)** \- Does not support resource\-level permissions\.
  + **[UpdateDistribution](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UpdateDistribution.html)** \- Does not support resource\-level permissions\.
  + **[UpdateDistributionBundle](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UpdateDistributionBundle.html)** \- Does not support resource\-level permissions\.

## API actions that support authorization based on tags<a name="auth-based-on-tags"></a>

The following list describes which Lightsail API actions support authorization based on tags:
+ The following API actions **support** authorization based on tags:
  + **[AllocateStaticIp](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_AllocateStaticIp.html)** \- Supports authorization based on tags\.
  + **[AttachDisk](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_AttachDisk.html)** \- Supports authorization based on tags\.
  + **[AttachInstancesToLoadBalancer](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_AttachInstancesToLoadBalancer.html)** \- Supports authorization based on tags\.
  + **[AttachLoadBalancerTlsCertificate](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_AttachLoadBalancerTlsCertificate.html)** \- Supports authorization based on tags\.
  + **[AttachStaticIp](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_AttachStaticIp.html)** \- Supports authorization based on tags\.
  + **[CloseInstancePublicPorts](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CloseInstancePublicPorts.html)** \- Supports authorization based on tags\.
  + **[CopySnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CopySnapshot.html)** \- Supports authorization based on tags\.
  + **[CreateBucket](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateBucket.html)** \- Supports authorization based on tags\.
  + **[CreateBucketAccessKey](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateBucketAccessKey.html)** \- Supports authorization based on tags\.
  + **[CreateCloudFormationStack](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateCloudFormationStack.html)** \- Supports authorization based on tags\.
  + **[CreateDisk](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateDisk.html)** \- Supports authorization based on tags\.
  + **[CreateDiskFromSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateDiskFromSnapshot.html)** \- Supports authorization based on tags\.
  + **[CreateDiskSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateDiskSnapshot.html)** \- Supports authorization based on tags\.
  + **[CreateDomain](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateDomain.html)** \- Supports authorization based on tags\.
  + **[CreateDomainEntry](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateDomainEntry.html)** \- Supports authorization based on tags\.
  + **[CreateInstances](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateInstances.html)** \- Supports authorization based on tags\.
  + **[CreateInstancesFromSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateInstancesFromSnapshot.html)** \- Supports authorization based on tags\.
  + **[CreateInstanceSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateInstanceSnapshot.html)** \- Supports authorization based on tags\.
  + **[CreateKeyPair](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateKeyPair.html)** \- Supports authorization based on tags\.
  + **[CreateLoadBalancer](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateLoadBalancer.html)** \- Supports authorization based on tags\.
  + **[CreateLoadBalancerTlsCertificate](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateLoadBalancerTlsCertificate.html)** \- Supports authorization based on tags\.
  + **[CreateRelationalDatabase](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateRelationalDatabase.html)** \- Supports authorization based on tags\.
  + **[CreateRelationalDatabaseFromSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateRelationalDatabaseFromSnapshot.html)** \- Supports authorization based on tags\.
  + **[CreateRelationalDatabaseSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateRelationalDatabaseSnapshot.html)** \- Supports authorization based on tags\.
  + **[DeleteBucket](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteBucket.html)** \- Supports authorization based on tags\.
  + **[DeleteBucketAccessKey](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteBucketAccessKey.html)** \- Supports authorization based on tags\.
  + **[DeleteDisk](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteDisk.html)** \- Supports authorization based on tags\.
  + **[DeleteDiskSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteDiskSnapshot.html)** \- Supports authorization based on tags\.
  + **[DeleteDomain](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteDomain.html)** \- Supports authorization based on tags\.
  + **[DeleteDomainEntry](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteDomainEntry.html)** \- Supports authorization based on tags\.
  + **[DeleteInstance](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteInstance.html)** \- Supports authorization based on tags\.
  + **[DeleteInstanceSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteInstanceSnapshot.html)** \- Supports authorization based on tags\.
  + **[DeleteKeyPair](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteKeyPair.html)** \- Supports authorization based on tags\.
  + **[DeleteKnownHostKeys](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteKnownHostKeys.html)** \- Supports authorization based on tags\.
  + **[DeleteLoadBalancer](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteLoadBalancer.html)** \- Supports authorization based on tags\.
  + **[DeleteLoadBalancerTlsCertificate](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteLoadBalancerTlsCertificate.html)** \- Supports authorization based on tags\.
  + **[DeleteRelationalDatabase](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteRelationalDatabase.html)** \- Supports authorization based on tags\.
  + **[DeleteRelationalDatabaseSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteRelationalDatabaseSnapshot.html)** \- Supports authorization based on tags\.
  + **[DetachDisk](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DetachDisk.html)** \- Supports authorization based on tags\.
  + **[DetachInstancesFromLoadBalancer](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DetachInstancesFromLoadBalancer.html)** \- Supports authorization based on tags\.
  + **[DetachStaticIp](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DetachStaticIp.html)** \- Supports authorization based on tags\.
  + **[DownloadDefaultKeyPair](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DownloadDefaultKeyPair.html)** \- Supports authorization based on tags\.
  + **[ExportSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_ExportSnapshot.html)** \- Supports authorization based on tags\.
  + **[GetActiveNames](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetActiveNames.html)** \- Supports authorization based on tags\.
  + **[GetBlueprints](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetBlueprints.html)** \- Supports authorization based on tags\.
  + **[GetBundles](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetBundles.html)** \- Supports authorization based on tags\.
  + **[GetCloudFormationStackRecords](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetCloudFormationStackRecords.html)** \- Supports authorization based on tags\.
  + **[GetDisk](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetDisk.html)** \- Supports authorization based on tags\.
  + **[GetDisks](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetDisks.html)** \- Supports authorization based on tags\.
  + **[GetDiskSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetDiskSnapshot.html)** \- Supports authorization based on tags\.
  + **[GetDiskSnapshots](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetDiskSnapshots.html)** \- Supports authorization based on tags\.
  + **[GetDomain](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetDomain.html)** \- Supports authorization based on tags\.
  + **[GetDomains](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetDomains.html)** \- Supports authorization based on tags\.
  + **[GetExportSnapshotRecords](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetExportSnapshotRecords.html)** \- Supports authorization based on tags\.
  + **[GetInstance](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetInstance.html)** \- Supports authorization based on tags\.
  + **[GetInstanceAccessDetails](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetInstanceAccessDetails.html)** \- Supports authorization based on tags\.
  + **[GetInstanceMetricData](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetInstanceMetricData.html)** \- Supports authorization based on tags\.
  + **[GetInstancePortStates](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetInstancePortStates.html)** \- Supports authorization based on tags\.
  + **[GetInstances](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetInstances.html)** \- Supports authorization based on tags\.
  + **[GetInstanceSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetInstanceSnapshot.html)** \- Supports authorization based on tags\.
  + **[GetInstanceSnapshots](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetInstanceSnapshots.html)** \- Supports authorization based on tags\.
  + **[GetInstanceState](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetInstanceState.html)** \- Supports authorization based on tags\.
  + **[GetKeyPair](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetKeyPair.html)** \- Supports authorization based on tags\.
  + **[GetKeyPairs](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetKeyPairs.html)** \- Supports authorization based on tags\.
  + **[GetLoadBalancer](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetLoadBalancer.html)** \- Supports authorization based on tags\.
  + **[GetLoadBalancerMetricData](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetLoadBalancerMetricData.html)** \- Supports authorization based on tags\.
  + **[GetLoadBalancers](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetLoadBalancers.html)** \- Supports authorization based on tags\.
  + **[GetLoadBalancerTlsCertificates](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetLoadBalancerTlsCertificates.html)** \- Supports authorization based on tags\.
  + **[GetOperation](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetOperation.html)** \- Supports authorization based on tags\.
  + **[GetOperations](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetOperations.html)** \- Supports authorization based on tags\.
  + **[GetOperationsForResource](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetOperationsForResource.html)** \- Supports authorization based on tags\.
  + **[GetRegions](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRegions.html)** \- Supports authorization based on tags\.
  + **[GetRelationalDatabase](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabase.html)** \- Supports authorization based on tags\.
  + **[GetRelationalDatabaseBlueprints](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseBlueprints.html)** \- Supports authorization based on tags\.
  + **[GetRelationalDatabaseBundles](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseBundles.html)** \- Supports authorization based on tags\.
  + **[GetRelationalDatabaseEvents](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseEvents.html)** \- Supports authorization based on tags\.
  + **[GetRelationalDatabaseLogEvents](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseLogEvents.html)** \- Supports authorization based on tags\.
  + **[GetRelationalDatabaseLogStreams](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseLogStreams.html)** \- Supports authorization based on tags\.
  + **[GetRelationalDatabaseMasterUserPassword](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseMasterUserPassword.html)** \- Supports authorization based on tags\.
  + **[GetRelationalDatabaseMetricData](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseMetricData.html)** \- Supports authorization based on tags\.
  + **[GetRelationalDatabaseParameters](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseParameters.html)** \- Supports authorization based on tags\.
  + **[GetRelationalDatabases](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabases.html)** \- Supports authorization based on tags\.
  + **[GetRelationalDatabaseSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseSnapshot.html)** \- Supports authorization based on tags\.
  + **[GetRelationalDatabaseSnapshots](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetRelationalDatabaseSnapshots.html)** \- Supports authorization based on tags\.
  + **[GetStaticIp](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetStaticIp.html)** \- Supports authorization based on tags\.
  + **[GetStaticIps](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetStaticIps.html)** \- Supports authorization based on tags\.
  + **[ImportKeyPair](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_ImportKeyPair.html)** \- Supports authorization based on tags\.
  + **[IsVpcPeered](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_IsVpcPeered.html)** \- Supports authorization based on tags\.
  + **[OpenInstancePublicPorts](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_OpenInstancePublicPorts.html)** \- Supports authorization based on tags\.
  + **[PeerVpc](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_PeerVpc.html)** \- Supports authorization based on tags\.
  + **[PutInstancePublicPorts](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_PutInstancePublicPorts.html)** \- Supports authorization based on tags\.
  + **[RebootInstance](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_RebootInstance.html)** \- Supports authorization based on tags\.
  + **[RebootRelationalDatabase](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_RebootRelationalDatabase.html)** \- Supports authorization based on tags\.
  + **[ReleaseStaticIp](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_ReleaseStaticIp.html)** \- Supports authorization based on tags\.
  + **[SetIpAddressType](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_SetIpAddressType.html)** \- Supports authorization based on tags\.
  + **[SetResourceAccessForBucket](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_SetResourceAccessForBucket.html)** \- Supports authorization based on tags\.
  + **[StartInstance](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_StartInstance.html)** \- Supports authorization based on tags\.
  + **[StartRelationalDatabase](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_StartRelationalDatabase.html)** \- Supports authorization based on tags\.
  + **[StopInstance](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_StopInstance.html)** \- Supports authorization based on tags\.
  + **[StopRelationalDatabase](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_StopRelationalDatabase.html)** \- Supports authorization based on tags\.
  + **[TagResource](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_TagResource.html)** \- Supports authorization based on tags\.
  + **[UnpeerVpc](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UnpeerVpc.html)** \- Supports authorization based on tags\.
  + **[UntagResource](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UntagResource.html)** \- Supports authorization based on tags\.
  + **[UpdateBucket](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UpdateBucket.html)** \- Supports authorization based on tags\.
  + **[UpdateBucketBundle](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UpdateBucketBundle.html)** \- Supports authorization based on tags\.
  + **[UpdateDomainEntry](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UpdateDomainEntry.html)** \- Supports authorization based on tags\.
  + **[UpdateLoadBalancerAttribute](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UpdateLoadBalancerAttribute.html)** \- Supports authorization based on tags\.
  + **[UpdateRelationalDatabase](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UpdateRelationalDatabase.html)** \- Supports authorization based on tags\.
  + **[UpdateRelationalDatabaseParameters](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UpdateRelationalDatabaseParameters.html)** \- Supports authorization based on tags\.
+ The following API actions **don't support** authorization based on tags:
  + **[AttachCertificateToDistribution](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_AttachCertificateToDistribution.html)** \- Does not support authorization based on tags\.
  + **[CreateCertificate](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateCertificate.html)** \- Does not support authorization based on tags\.
  + **[CreateContactMethod](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateContactMethod.html)** \- Does not support authorization based on tags\.
  + **[CreateContainerService](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateContainerService.html)** \- Does not support authorization based on tags\.
  + **[CreateContainerServiceDeployment](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateContainerServiceDeployment.html)** \- Does not support authorization based on tags\.
  + **[CreateContainerServiceRegistryLogin](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateContainerServiceRegistryLogin.html)** \- Does not support authorization based on tags\.
  + **[CreateDistribution](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_CreateDistribution.html)** \- Does not support authorization based on tags\.
  + **[DeleteAlarm](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteAlarm.html)** \- Does not support authorization based on tags\.
  + **[DeleteAutoSnapshot](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteAutoSnapshot.html)** \- Does not support authorization based on tags\.
  + **[DeleteCertificate](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteCertificate.html)** \- Does not support authorization based on tags\.
  + **[DeleteContactMethod](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteContactMethod.html)** \- Does not support authorization based on tags\.
  + **[DeleteContainerImage](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteContainerImage.html)** \- Does not support authorization based on tags\.
  + **[DeleteContainerService](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteContainerService.html)** \- Does not support authorization based on tags\.
  + **[DeleteDistribution](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DeleteDistribution.html)** \- Does not support authorization based on tags\.
  + **[DetachCertificateFromDistribution](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DetachCertificateFromDistribution.html)** \- Does not support authorization based on tags\.
  + **[DisableAddOn](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_DisableAddOn.html)** \- Does not support authorization based on tags\.
  + **[EnableAddOn](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_EnableAddOn.html)** \- Does not support authorization based on tags\.
  + **[GetBucketAccessKeys](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetBucketAccessKeys.html)** \- Does not support authorization based on tags\.
  + **[GetBucketBundles](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetBucketBundles.html)** \- Does not support authorization based on tags\.
  + **[GetBucketMetricData](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetBucketMetricData.html)** \- Does not support authorization based on tags\.
  + **[GetBuckets](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetBuckets.html)** \- Does not support authorization based on tags\.
  + **[GetAlarms](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetAlarms.html)** \- Does not support authorization based on tags\.
  + **[GetAutoSnapshots](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetAutoSnapshots.html)** \- Does not support authorization based on tags\.
  + **[GetCertificates](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetCertificates.html)** \- Does not support authorization based on tags\.
  + **[GetContactMethods](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetContactMethods.html)** \- Does not support authorization based on tags\.
  + **[GetContainerAPIMetadata](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetContainerAPIMetadata.html)** \- Does not support authorization based on tags\.
  + **[GetContainerImages](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetContainerImages.html)** \- Does not support authorization based on tags\.
  + **[GetContainerLog](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetContainerLog.html)** \- Does not support authorization based on tags\.
  + **[GetContainerServiceDeployments](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetContainerServiceDeployments.html)** \- Does not support authorization based on tags\.
  + **[GetContainerServiceMetricData](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetContainerServiceMetricData.html)** \- Does not support authorization based on tags\.
  + **[GetContainerServicePowers](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetContainerServicePowers.html)** \- Does not support authorization based on tags\.
  + **[GetContainerServices](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetContainerServices.html)** \- Does not support authorization based on tags\.
  + **[GetDistributionBundles](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetDistributionBundles.html)** \- Does not support authorization based on tags\.
  + **[GetDistributionLatestCacheReset](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetDistributionLatestCacheReset.html)** \- Does not support authorization based on tags\.
  + **[GetDistributionMetricData](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetDistributionMetricData.html)** \- Does not support authorization based on tags\.
  + **[GetDistributions](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_GetDistributions.html)** \- Does not support authorization based on tags\.
  + **[PutAlarm](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_PutAlarm.html)** \- Does not support authorization based on tags\.
  + **[RegisterContainerImage](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_RegisterContainerImage.html)** \- Does not support authorization based on tags\.
  + **[ResetDistributionCache](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_ResetDistributionCache.html)** \- Does not support authorization based on tags\.
  + **[SendContactMethodVerification](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_SendContactMethodVerification.html)** \- Does not support authorization based on tags\.
  + **[TestAlarm](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_TestAlarm.html)** \- Does not support authorization based on tags\.
  + **[UpdateContainerService](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UpdateContainerService.html)** \- Does not support authorization based on tags\.
  + **[UpdateDistribution](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UpdateDistribution.html)** \- Does not support authorization based on tags\.
  + **[UpdateDistributionBundle](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/API_UpdateDistributionBundle.html)** \- Does not support authorization based on tags\.