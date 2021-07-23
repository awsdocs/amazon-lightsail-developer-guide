# Viewing and managing deployment versions of your Amazon Lightsail container services<a name="amazon-lightsail-container-services-deployment-versions"></a>

 *Last updated: November 12, 2020* 

Every deployment that you create in your Amazon Lightsail container service is saved as a deployment version\. If you modify the parameters of an existing deployment, the containers are re\-deployed to your service and the modified deployment results in a new deployment version\. The latest 50 deployment versions for each container service are saved\. You can use any of the 50 deployment versions to create a new deployment in the same container service\. In this guide, we show you how to view and manage the deployment versions of your container service\.

For more information about container services, see [Container services in Amazon Lightsail](amazon-lightsail-container-services.md)\.

## Deployment version status<a name="deployment-versions-status"></a>

Each of your deployment versions can be in one of the following states after it's created:
+ **Deploying \(Activing\)** – The deployment is being launched\.
+ **Active** – Your deployment was successfully created, and it's currently running on your container service\. Your container service can have only one deployment in an active state at a time\.
+ **Inactive** – Your previously successfully created deployment is no longer running on your container\.
+ **Failed** – Your deployment failed because one or more of the containers specified in the deployment failed to launch\.

## Prerequisites<a name="deployment-versions-prerequisites"></a>

Before you get started, you need to create a Lightsail container service\. For more information, see [Creating Amazon Lightsail container services](amazon-lightsail-creating-container-services.md)\.

You also should create a deployment in your container service that configures and launches your containers\. For more information, see [Creating and managing deployments for your Amazon Lightsail container services](amazon-lightsail-container-services-deployments.md)\.

## View the deployment versions of a container service<a name="view-deployment-versions"></a>

Complete the following procedure to view the deployment versions of your Lightsail container service\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Containers** tab\.

1. Choose the name of the container service for which you want to view the deployment versions\.

1. On the container service management page, choose the **Deployments** tab\.

   The **Deployments** page lists your current deployment and deployment versions, if any\.

1. The deployment versions of your container service are listed under the **Deployment versions** section of the page\.

   Each deployment has a date, in which it was created, a status, and an actions menu\.

1. Choose one of the following options through the actions menu of a deployment version:
   + **Create new deployment** – Choose this option to create a new deployment from the selected deployment version\. For more information about creating a deployment, see [Create or modify your container service deployment](https://lightsail.aws.amazon.com/ls/docs/en_us/articles/amazon-lightsail-container-services-deployments#creating-container-service-deployment)\.
**Note**  
If you choose to create a new deployment from a version that has a **Failed** status, then you must correct the cause of the failure before creating the deployment\. Otherwise, the deployment will likely fail again\.
   + **View details** – Choose this option to view the container entry and public endpoint parameters of the selected deployment version\. You can also view the container logs for the deployment in case you need to diagnose a failed deployment\. For more information, see [Viewing the container logs of your Amazon Lightsail container services](amazon-lightsail-viewing-container-service-container-logs.md)\.

## Additional information about container services<a name="deployment-versions-additional-info"></a>

These are the general steps to manage your Lightsail container service after it's up and running:

1. Get familiar with all of the elements of Lightsail container services\. For more information, see [Container services in Amazon Lightsail](amazon-lightsail-container-services.md)\.

1. Create your container service in your Lightsail account\. For more information, see [Creating Amazon Lightsail container services](amazon-lightsail-creating-container-services.md)\.

1. If you plan to use container images from a public registry, find container images that you want to use from a public registry like the Amazon ECR Public Gallery or Docker Hub\. For more information about Amazon ECR Public, see [What Is Amazon Elastic Container Registry Public?](https://docs.aws.amazon.com/AmazonECR/latest/public/what-is-ecr.html) in the *Amazon ECR Public User Guide*\. For more information about Docker Hub, see [Docker Hub Quickstart](https://docs.docker.com/docker-hub/) in the *Docker documentation*\.

1. If you plan to push container images from your local machine to your service, install software on your local machine that you need to create your own container images and push them to your Lightsail container service\. For more information, see the following guides:
   + [Installing software to manage container images for your Amazon Lightsail container services](amazon-lightsail-install-software.md)
   + [Creating container images for your Amazon Lightsail container services](amazon-lightsail-creating-container-images.md)
   + [Pushing and managing container images on your Amazon Lightsail container services](amazon-lightsail-pushing-container-images.md)

1. Create a deployment in your container service that configures and launches your containers\. For more information, see [Creating and managing deployments for your Amazon Lightsail container services](amazon-lightsail-container-services-deployments.md)\.

1. View previous deployments for your container service\. You can create a new deployment using a previous deployment version\. For more information, see [Viewing and managing deployment versions of your Amazon Lightsail container services](#amazon-lightsail-container-services-deployment-versions)\.

1. View the logs of containers on your container service\. For more information, see [Viewing the container logs of your Amazon Lightsail container services](amazon-lightsail-viewing-container-service-container-logs.md)\.

1. Create an SSL/TLS certificate for the domains that you want to use with your containers\. For more information, see [Creating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-creating-container-services-certificates.md)\.

1. Validate the SSL/TLS certificate by adding records to the DNS of your domains\. For more information, see [Validating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-validating-container-services-certificates.md)\.

1. Enable custom domains by attaching a valid SSL/TLS certificate to your container service\. For more information, see [Enabling and managing custom domains for your Amazon Lightsail container services](amazon-lightsail-enabling-container-services-custom-domains.md)\.

1. Monitor the utilization metrics of your container service\. For more information, see [Viewing container service metrics in Amazon Lightsail](amazon-lightsail-viewing-container-services-metrics.md)\.

1. \(Optional\) Scale the capacity of your container service vertically, by increasing its power specification, and horizontally, by increasing its scale specification\. For more information, see [Changing the capacity of your Amazon Lightsail container services](amazon-lightsail-changing-container-service-capacity.md)\.

1. Delete your container service if you're not using it to avoid incurring monthly charges\. For more information, see [Deleting Amazon Lightsail container services](amazon-lightsail-deleting-container-services.md)\.