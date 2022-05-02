# Viewing the container logs of your Amazon Lightsail container services<a name="amazon-lightsail-viewing-container-service-container-logs"></a>

 *Last updated: November 12, 2020* 

Every container in your Amazon Lightsail container service deployment generates a log\. The container logs provide the stdout and stderr streams of processes that run inside your containers\. Access your containers' logs periodically to diagnose their operations\. The latest three days of log entries are stored before the oldest ones are replaced by the newest entries\.

## Filtering container logs<a name="filtering-log"></a>

Container logs can have hundreds of entries per day\. Use the filtering options to reduce the number of entries displayed in your log window, and make it easier to find what you're looking for\. You can filter container logs by a start and end date \(in local time\), and by a specific term\. When filtering by a term, you can choose to include or exclude log entries for the term you specify\.

![\[Container service log filters in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/container-service-container-log-filter.png)

The *include* or *exclude* filter term looks for an exact match that is case\-sensitive\. For example, if you specify to include only log events that have `HTTP` in the message, then you will see all log events that include `HTTP` in the message, but none that include `http` in the message\. If you specify to exclude `Error`, then you will see all log events that don't include `Error` in the message, and you will also see log events that include `ERROR` in the message\.

## Prerequisites<a name="view-contgainer-logs-prerequisites"></a>

Before you get started, you need to create a Lightsail container service\. For more information, see [Creating Amazon Lightsail container services](amazon-lightsail-creating-container-services.md)\.

You also should create a deployment in your container service that configures and launches your containers\. For more information, see [Creating and managing deployments for your Amazon Lightsail container services](amazon-lightsail-container-services-deployments.md)\.

## Viewing the container logs of a container service<a name="view-contgainer-logs"></a>

Complete the following procedure to view the container logs of your Lightsail container service\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Containers** tab\.

1. Choose the name of the container service for which you want to view the container logs\.

1. On the container service management page, choose the **Deployments** tab\.

   The **Deployments** page lists your current deployment and deployment versions, if any\.

1. Choose one of the following options to view container logs:
   + To access the container logs of the current deployment, choose **Open log** for the container entries under the **Current deployment** section of the page\.
   + To access the container logs of a previous deployment, choose the actions menu icon \(⋮\) for a previous deployment under the **Deployment versions** section of the page, and then choose **Show details**\. In the **Version details** page that appears, choose Open log for the container entries that are listed\.

   The container log opens in a new browser window\. You can scroll down to view more log entries, and refresh the page to load the newest set of entries\. The filtering options are displayed at the bottom of the page\.
**Note**  
Log entries are displayed in ascending order, and in Coordinated Universal Time \(UTC\)\. That is, the oldest log entries are at the top, and you must scroll down to see newer log entries\.  
![\[Container log in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/container-service-container-log.png)

## Additional information about container services<a name="view-contgainer-logs-additional-info"></a>

These are the general steps to manage your Lightsail container service after it's up and running:

1. Get familiar with all of the elements of Lightsail container services\. For more information, see [Container services in Amazon Lightsail](amazon-lightsail-container-services.md)\.

1. Create your container service in your Lightsail account\. For more information, see [Creating Amazon Lightsail container services](amazon-lightsail-creating-container-services.md)\.

1. If you plan to use container images from a public registry, find container images from a public registry such as the Amazon ECR Public Gallery\. For more information about Amazon ECR Public, see [What Is Amazon Elastic Container Registry Public?](https://docs.aws.amazon.com/AmazonECR/latest/public/what-is-ecr.html) in the *Amazon ECR Public User Guide*\.

1. If you plan to push container images from your local machine to your service, install software on your local machine that you need to create your own container images and push them to your Lightsail container service\. For more information, see the following guides:
   + [Installing software to manage container images for your Amazon Lightsail container services](amazon-lightsail-install-software.md)
   + [Creating container images for your Amazon Lightsail container services](amazon-lightsail-creating-container-images.md)
   + [Pushing and managing container images on your Amazon Lightsail container services](amazon-lightsail-pushing-container-images.md)

1. Create a deployment in your container service that configures and launches your containers\. For more information, see [Creating and managing deployments for your Amazon Lightsail container services](amazon-lightsail-container-services-deployments.md)\.

1. View previous deployments for your container service\. You can create a new deployment using a previous deployment version\. For more information, see [Viewing and managing deployment versions of your Amazon Lightsail container services](amazon-lightsail-container-services-deployment-versions.md)\.

1. View the logs of containers on your container service\. For more information, see [Viewing the container logs of your Amazon Lightsail container services](#amazon-lightsail-viewing-container-service-container-logs)\.

1. Create an SSL/TLS certificate for the domains that you want to use with your containers\. For more information, see [Creating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-creating-container-services-certificates.md)\.

1. Validate the SSL/TLS certificate by adding records to the DNS of your domains\. For more information, see [Validating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-validating-container-services-certificates.md)\.

1. Enable custom domains by attaching a valid SSL/TLS certificate to your container service\. For more information, see [Enabling and managing custom domains for your Amazon Lightsail container services](amazon-lightsail-enabling-container-services-custom-domains.md)\.

1. Monitor the utilization metrics of your container service\. For more information, see [Viewing container service metrics in Amazon Lightsail](amazon-lightsail-viewing-container-services-metrics.md)\.

1. \(Optional\) Scale the capacity of your container service vertically, by increasing its power specification, and horizontally, by increasing its scale specification\. For more information, see [Changing the capacity of your Amazon Lightsail container services](amazon-lightsail-changing-container-service-capacity.md)\.

1. Delete your container service if you're not using it to avoid incurring monthly charges\. For more information, see [Deleting Amazon Lightsail container services](amazon-lightsail-deleting-container-services.md)\.