# Viewing container service metrics in Amazon Lightsail<a name="amazon-lightsail-viewing-container-services-metrics"></a>

 *Last updated: November 12, 2020* 

After you create an Amazon Lightsail container service, you can view its metric graphs on the Metrics tab of the service’s management page\. Monitoring metrics is an important part of maintaining the reliability, availability, and performance of your resources\. Monitor and collect metric data from your resources regularly so that you can more readily debug a multi\-point failure, if one occurs\. For more information about metrics, see [Metrics in Amazon Lightsail](understanding-instance-health-metrics-in-amazon-lightsail.md)\.

When monitoring your resources, you should establish a baseline for normal resource performance in your environment\.

**Note**  
Alarms and notifications are currently not supported for container service metrics\.

## Container service metrics available in Lightsail<a name="container-service-metrics-available"></a>

The following container service metrics are available:
+ **CPU utilization** — The average percentage of compute units that are currently in use across all nodes of your container service\. This metric identifies the processing power required to run containers on your container service\.
+ **Memory utilization** — The average percentage of memory that is currently in use across all nodes of your container service\. This metric identifies the memory required to run containers on your container service\.

**Note**  
If you create a new deployment, then the existing utilization metrics of your container service will disappear, and only metrics for the new current deployment will be shown\.

## View container service metrics in the Lightsail console<a name="view-container-service-metrics"></a>

Complete the following procedure to view container service metrics in the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Containers** tab\.

1. Choose the name of the container for which you want to view metrics\.

1. Choose the **Metrics** tab on the container service management page\.

1. Choose the metric that you want to view in the dropdown menu under the **Metrics** graphs heading\.

   The graph displays a visual representation of the data points for the chosen metric\.

1. You can perform the following actions on the metrics graph:
   + Change the view of the graph to show data for 1 hour, 6 hours, 1 day, 1 week, and 2 weeks\.
   + Pause your cursor on a data point to view detailed information about that data point\.
**Note**  
Alarms and notifications are currently not supported for container service metrics\.

## Additional information about container services<a name="view-container-service-metrics-additional-info"></a>

These are the general steps to manage your Lightsail container service after it's up and running:

1. Get familiar with all of the elements of Lightsail container services\. For more information, see [Container services in Amazon Lightsail](amazon-lightsail-container-services.md)\.

1. Create your container service in your Lightsail account\. For more information, see [Creating Amazon Lightsail container services](amazon-lightsail-creating-container-services.md)\.

1. If you plan to use container images from a public registry, find container images that you want to use from a public registry like Docker Hub\. For more information, see [Docker Hub Quickstart](https://docs.docker.com/docker-hub/) in the *Docker documentation*\.

1. If you plan to push container images from your local machine to your service, install software on your local machine that you need to create your own container images and push them to your Lightsail container service\. For more information, see the following guides:
   + [Installing software to manage container images for your Amazon Lightsail container services](amazon-lightsail-install-software.md)
   + [Creating container images for your Amazon Lightsail container services](amazon-lightsail-creating-container-images.md)
   + [Pushing and managing container images on your Amazon Lightsail container services](amazon-lightsail-pushing-container-images.md)

1. Create a deployment in your container service that configures and launches your containers\. For more information, see [Creating and managing deployments for your Amazon Lightsail container services](amazon-lightsail-container-services-deployments.md)\.

1. View previous deployments for your container service\. You can create a new deployment using a previous deployment version\. For more information, see [Viewing and managing deployment versions of your Amazon Lightsail container services](amazon-lightsail-container-services-deployment-versions.md)\.

1. View the logs of containers on your container service\. For more information, see [Viewing the container logs of your Amazon Lightsail container services](amazon-lightsail-viewing-container-service-container-logs.md)\.

1. Create an SSL/TLS certificate for the domains that you want to use with your containers\. For more information, see [Creating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-creating-container-services-certificates.md)\.

1. Validate the SSL/TLS certificate by adding records to the DNS of your domains\. For more information, see [Validating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-validating-container-services-certificates.md)\.

1. Enable custom domains by attaching a valid SSL/TLS certificate to your container service\. For more information, see [Enabling and managing custom domains for your Amazon Lightsail container services](amazon-lightsail-enabling-container-services-custom-domains.md)\.

1. Monitor the utilization metrics of your container service\. For more information, see [Viewing container service metrics in Amazon Lightsail](#amazon-lightsail-viewing-container-services-metrics)\.

1. \(Optional\) Scale the capacity of your container service vertically, by increasing its power specification, and horizontally, by increasing its scale specification\. For more information, see [Changing the capacity of your Amazon Lightsail container services](amazon-lightsail-changing-container-service-capacity.md)\.

1. Delete your container service if you're not using it to avoid incurring monthly charges\. For more information, see [Deleting Amazon Lightsail container services](amazon-lightsail-deleting-container-services.md)\.