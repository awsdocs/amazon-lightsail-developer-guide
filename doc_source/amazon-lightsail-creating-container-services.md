# Creating Amazon Lightsail container services<a name="amazon-lightsail-creating-container-services"></a>

 *Last updated: April 1, 2021* 

In this guide, we show you how to create an Amazon Lightsail container service using the Lightsail console, and describe the container service settings that you can configure\.

Before getting started, we recommend that you familiarize yourself with the elements of a Lightsail container service\. For more information, see [Container services in Amazon Lightsail](amazon-lightsail-container-services.md)\.

## Container service capacity \(scale and power\)<a name="create-container-service-capacity"></a>

You must choose the capacity of your container service when you first create it\. The capacity is made up of a combination of the following parameters:
+ **Scale** \- The number of compute nodes that you want your container workload to run in\. Your container workload is copied across the compute nodes of your service\. You can specify up to 20 compute nodes for a container service\. You pick the scale based on the number of nodes you want powering your service for better availability and higher capacity\. Traffic to your containers will be load\-balanced across all nodes\.
+ **Power** \- The memory and vCPUs of each node in your container service\. The powers that you can choose are Nano \(Na\), Micro \(Mi\), Small \(Sm\), Medium \(Md\), Large \(Lg\), and Xlarge \(Xl\); each with a progressively greater amount of memory and vCPUs\.

The incoming traffic is load balanced across the scale \(the number of compute nodes\) of your container service\. For example, a service with a Nano power and a scale of 3 will have 3 copies of your container workload running\. Each node will have 512 MB of RAM and 0\.25 vCPUs\. The incoming traffic will be load\-balanced across the 3 nodes\. The greater the capacity you choose for your container service, the more traffic it is able to handle\.

You can dynamically increase the power and scale of your container service at any time without any down\-time if you find that it's under\-provisioned, or decrease it if you find that it's over\-provisioned\. Lightsail automatically manages the capacity change along with your current deployment\. For more information, see [Changing the capacity of your Amazon Lightsail container services](amazon-lightsail-changing-container-service-capacity.md)\.

## Pricing<a name="create-container-service-pricing"></a>

The monthly price of your container service is calculated by multiplying the base price of its power with the scale \(the number of compute nodes\)\. For example, a service with the $40 USD medium power and a scale of 3, will cost $120 USD per month\.

Each container service, regardless of its configured capacity, includes a monthly data transfer quota of 500 GB\. The data transfer quota does not change regardless of the power and scale that you choose for your service\. Data transfer out to the internet in excess of the quota will result in an overage charge that varies by AWS Region and starts at $0\.09 USD per GB\. Data transfer in from the internet in excess of the quota does not incur an overage charge\. For more information, see the [Lightsail pricing page](https://aws.amazon.com/lightsail/pricing/)\.

You are charged for your container service whether it's enabled or disabled, and whether it has a deployment or not\. You must delete your container service to stop being charged for it\. For more information, see [Deleting Amazon Lightsail container services](amazon-lightsail-deleting-container-services.md)\.

## Container service status<a name="container-service-status"></a>

Your container service can be in one of the following states:
+ **Pending** – Your container service is being created\.
+ **Ready** – Your container service is running but it does not have an active container deployment\.
+ **Deploying** – Your deployment is being launched to your container service\.
+ **Running** – Your container service is running and it has an active container deployment\.
+ **Updating** – Your container service capacity or its custom domains are being updated\.
+ **Deleting** – Your container service is being deleted\. Your container service is in this state after you choose to delete, and it's in this state only for a brief moment\.
+ **Disabled** – Your container service is disabled, and its active deployment and containers, if any, are shut down\.

**Container service sub\-status**

If your container service is in a **Deploying** or **Updating** state, then one of the following additional sub\-states is displayed below the container service stte:
+ **Creating system resources** \- The system resources for your container service are being created\.
+ **Creating network infrastructure** \- The network infrastructure for your container service are being created\.
+ **Provisioning certificate** \- The SSL/TLS certificate for your container service is being created\.
+ **Provisioning service** \- Your container service is being provisioned\.
+ **Creating deployment** \- Your deployment is being created on your container service\.
+ **Evaluating health check** \- The health of your deployment is being evaluated\.
+ **Activating deployment** \- Your deployment is being activated\.

If your container service is in a **Pending** state, then one of the following additional sub\-states is displayed below the container service state:
+ **Certificate limit exceeded** \- The SSL/TLS certificate required for your container service exceeds the maximum number of certificates allowed for your account\.
+ **Unknown error** \- An error was experienced when your container service was being created\.

## Create a container service<a name="create-container-service"></a>

Complete the following procedure to create a Lightsail container service\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Containers** tab\.

1. Choose **Create container service**\.

1. In the **Create a container service** page, choose **Change AWS Region**, then choose an AWS Region for your container service\.

1. Choose a capacity for your container service\. For more information, see the [Container service capacity \(scale and power\)](#create-container-service-capacity) section of this guide\.

1. Complete the following steps to create a deployment that will be launched at the same time as your container service is created\. Otherwise, skip to step 7 to create a container service without a deployment\.

   Create a container service with a deployment if you plan to use a container image from a public registry\. Otherwise, create your service without a deployment if you plan to use a container image that is on your local machine\. You can push the container image from your local machine to your container service after your service is up and running\. Then you can create a deployment using the pushed container image that is registered to your container service\.

   1. Choose **Create a deployment**\.

   1. Choose one of the following options:
      + **Choose an example deployment** – Choose this option to create a deployment using a container image that's been curated by the Lightsail team with a set of preconfigured deployment parameters\. This option provides the fastest and easiest way to get a popular container up and running on your container service\.
      + **Specify a custom deployment** – Choose this option to create a deployment by specifying containers of your choosing\.

      The deployment form view opens, where you can enter new deployment parameters\.

   1. Enter the parameters of your deployment\. For more information about the deployment parameters that you can specify, see the **Deployment parameters** section in the [Creating and managing deployments for your Amazon Lightsail container services](amazon-lightsail-container-services-deployments.md) guide\.

   1. Choose **Add container entry** to add more than one container entry to your deployment\. You can have up to 10 container entries in your deployment\.

   1. When you're done entering the parameters of your deployment, choose **Save and deploy** to create the deployment on your container service\.

1. Enter a name for your container service\.

   Container service names must be:
   + Must be unique within each AWS Region in your Lightsail account\.
   + Must contain 2 to 63 characters\.
   + Must contain only alphanumeric characters and hyphens\.
   + A hyphen \(\-\) can separate words but cannot be at the start or end of the name\.
**Note**  
The name that you specify will be part of the default domain name of your container service, and it will be visible to the public\.

1. Choose one of the following options to add tags to your container service:
   + **Add key\-only tags** or **Edit key\-only tags** \(if tags have already been added\)\. Enter your new tag into the tag key text box, and press **Enter**\. Choose **Save** when you’re done entering your tags to add them, or choose **Cancel** to not add them\.  
![\[Key-only tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-key-only-tags.png)
   + **Create a key\-value tag**, then enter a key into the **Key** text box, and a value into the **Value** text box\. Choose **Save** when you’re done entering your tags, or choose **Cancel** to not add them\.

     Key\-value tags can only be added one at a time before saving\. To add more than one key\-value tag, repeat the previous steps\.  
![\[Key-value tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-key-value-tag.png)
**Note**  
For more information about key\-only and key\-value tags, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

1. Choose **Create container service**\.

   You are redirected to the management page of your new container service\. The status of your new container service is **Pending** while it's being created\. After a few moments, the status of your service changes to **Ready**, if it doesn't have a current deployment, or **Running**, if you created a deployment\.

## Additional information about container services<a name="create-container-additional-information"></a>

These are the general steps to manage your Lightsail container service after it's up and running:

1. Get familiar with all of the elements of Lightsail container services\. For more information, see [Container services in Amazon Lightsail](amazon-lightsail-container-services.md)\.

1. Create your container service in your Lightsail account\. For more information, see [Creating Amazon Lightsail container services](#amazon-lightsail-creating-container-services)\.

1. If you plan to use container images from a public registry, find container images from a public registry such as the Amazon ECR Public Gallery\. For more information about Amazon ECR Public, see [What Is Amazon Elastic Container Registry Public?](https://docs.aws.amazon.com/AmazonECR/latest/public/what-is-ecr.html) in the *Amazon ECR Public User Guide*\.

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

1. Monitor the utilization metrics of your container service\. For more information, see [Viewing container service metrics in Amazon Lightsail](amazon-lightsail-viewing-container-services-metrics.md)\.

1. \(Optional\) Scale the capacity of your container service vertically, by increasing its power specification, and horizontally, by increasing its scale specification\. For more information, see [Changing the capacity of your Amazon Lightsail container services](amazon-lightsail-changing-container-service-capacity.md)\.

1. Delete your container service if you're not using it to avoid incurring monthly charges\. For more information, see [Deleting Amazon Lightsail container services](amazon-lightsail-deleting-container-services.md)\.