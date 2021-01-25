# Container services in Amazon Lightsail<a name="amazon-lightsail-container-services"></a>

**Note**  
An Amazon Lightsail container service is a compute resource to which you can deploy your Docker images\. When you deploy your images to your Lightsail container service, the service automatically launches and runs your containers in the AWS infrastructure\. Containers are standard units of software that package code and dependencies so the applications run quickly and reliably from one computing environment to another\.

 *Last updated: November 12, 2020* 

An Amazon Lightsail container service is a highly scalable compute and networking resource on which you can deploy, run, and manage containers\. A container is a standard unit of software that packages code and its dependencies together so the application runs quickly and reliably from one computing environment to another\.

You can think of your Lightsail container service as a computing environment that lets you run containers in the AWS infrastructure by using images that you create on your local machine and push to your service, or images from an online repository, like Docker Hub\.

You can also run containers locally, on your local machine, by installing software such as Docker\. Amazon Elastic Container Service \(Amazon ECS\) and Amazon Elastic Compute Cloud \(Amazon EC2\) are other resources within the AWS infrastructure on which you can run containers\. For more information, see the [Amazon ECS Developer Guide](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html)\.

**Contents:**
+ [Understanding containers](#understanding-containers)
+ [Understanding Lightsail container services](#understanding-lightsail-container-services)
  + [Lightsail container services](#lightsail-container-services)
  + [Container service capacity \(scale and power\)](#container-services-capacity)
  + [Pricing](#container-services-pricing)
  + [Deployments](#container-services-deployments)
  + [Deployment versions](#container-services-deployment-versions)
  + [Container image sources](#container-services-image-sources)
  + [Public endpoints and default domains](#container-services-endpoints-domains)
  + [Custom domains and SSL/TLS certificates](#container-services-custom-domains-certificates)
  + [Container logs](#container-services-container-logs)
  + [Metrics](#container-services-metrics)
+ [Using Lightsail container services](#using-lightsail-container-services)

## Understanding containers<a name="understanding-containers"></a>

A container is a standard unit of software that packages code and its dependencies together so the application runs quickly and reliably from one computing environment to another\. You could run a container on your development environment, deploy it to your pre\-production environment, and then deploy it to your production environment\. Your containers will run reliably regardless of whether your development environment is your local machine, your pre\-production environment is a physical server in a data center, or your production environment is a virtual private server in the cloud\.

A container image is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries and settings\. Container images become containers at runtime\. By containerizing the application and its dependencies, you no longer have to worry about whether your software runs correctly on the operating system and infrastructure that you deploy it on – you can spend more time focusing on the code\.

For more information about containers, and container images, see [What is a Container?](https://www.docker.com/resources/what-container) in the *Docker documentation*\.

## Understanding Lightsail container services<a name="understanding-lightsail-container-services"></a>

The following are the key elements of Lightsail container services that you should understand before getting started\.

### Lightsail container services<a name="lightsail-container-services"></a>

A container service is the Lightsail compute resource that you can create in any AWS Region in which Lightsail is available\. You can create and delete container services at any time\. For more information, see [Creating Amazon Lightsail container services](amazon-lightsail-creating-container-services.md) and [Deleting Amazon Lightsail container services](amazon-lightsail-deleting-container-services.md)\.

![\[Lighstail container service diagram\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/amazon-lightsail-container-service-diagram.png)

### Container service capacity \(scale and power\)<a name="container-services-capacity"></a>

You must choose the following capacity parameters when you first create your container service:
+ **Scale** — The number of compute nodes that you want your container workload to run in\. Your container workload is copied across the compute nodes of your service\. You can specify up to 20 compute nodes for a container service\. You pick the scale based on the number of nodes you want powering your service for better availability and higher capacity\. Traffic to your containers will be load\-balanced across all nodes\.
+ **Power** — The memory and vCPUs of each node in your container service\. The powers that you can choose are Nano \(Na\), Micro \(Mi\), Small \(Sm\), Medium \(Md\), Large \(Lg\), and Xlarge \(Xl\), each with a progressively greater amount of memory and vCPUs\.

If you specify the scale of your container service as more than 1, then your container workload is copied across the multiple compute nodes of your service\. For example, if the scale of your service is 3 and the power is Nano, then there are three copies of your container workload running on three compute resources each with 512 MB of RAM and 0\.25 vCPUs\. The incoming traffic is load\-balanced between the three resources\. The greater the capacity you specify for your container service, the more traffic it is able to handle\.

You can dynamically increase the power and scale of your container service at any time without any down\-time if you find that it's under\-provisioned, or decrease it if you find that it's over\-provisioned\. Lightsail automatically manages the capacity change along with your current deployment\. For more information, see [Changing the capacity of your Amazon Lightsail container services](amazon-lightsail-changing-container-service-capacity.md)\.

### Pricing<a name="container-services-pricing"></a>

The monthly price of your container service is calculated by multiplying the price of its power with the number of its compute nodes \(the scale of your service\)\. For example, a service with a medium power, which has a price of $40 USD, and a scale of 3 compute nodes, will cost $120 USD per month\. You are charged for your container service whether it's enabled or disabled, and whether it has a deployment or not\. You must delete your container service to stop being charged for it\.

Each container service, regardless of its configured capacity, includes a monthly data transfer quota of 500 GB\. The data transfer quota does not change regardless of the power and scale that you choose for your service\. Data transfer out to the internet in excess of the quota will result in an overage charge that varies by AWS Region and starts at $0\.09 USD per GB\. Data transfer in from the internet in excess of the quota does not incur an overage charge\. For more information, see the [Lightsail pricing page](https://aws.amazon.com/lightsail/pricing/)\.

### Deployments<a name="container-services-deployments"></a>

You can create a deployment in your Lightsail container service\. A deployment is a set of specifications for the container workload that you wish to launch on your service\.

You can specify the following parameters for each container entry in a deployment:
+ The name of your container that will be launched
+ The source container image to use for your container
+ The command to run when launching your container
+ The environment variables to apply to your container
+ The network ports to open on your container
+ The container in the deployment to make publicly accessible through the default domain of the container service
**Note**  
Only one container in a deployment can be made publicly accessible for each container service\.

Your container service can have one active deployment at a time, and a deployment can have up to 10 container entries\. You can create a deployment at the same time as you create your container service, or you can create it after your service is up and running\. For more information, see [Creating and managing deployments for your Amazon Lightsail container services]()\.

### Deployment versions<a name="container-services-deployment-versions"></a>

Every deployment that you create in your container service is saved as a deployment version\. If you modify the parameters of an existing deployment, the containers are re\-deployed to your service and the modified deployment results in a new deployment version\. The latest 50 deployment versions for each container service are saved\. You can use any of the 50 deployment versions to create a new deployment in the same container service\. For more information, see [Creating and managing deployments for your Amazon Lightsail container services]()\.

### Container image sources<a name="container-services-image-sources"></a>

When you create a deployment, you must specify a source container image for each container entry in your deployment\. Immediately after you create your deployment, your container service pulls the images from the sources you specify and uses them to create your containers\.

The images that you specify can originate from the following sources:
+ **A public registry**, such as Docker Hub or some other public container image registry\. For more information about Docker Hub, see [Docker Hub Quickstart](https://docs.docker.com/docker-hub/) in the *Docker documentation*\.
**Note**  
When you create your container service, you have the option to create an example deployment using an Nginx or Redis container image from Docker Hub\. Example deployments are pre\-configured to demonstrate how to launch a container on your service\.
+ **Images pushed from your local machine** to your container service\. If you create container images on your local machine, you can push them to your container service to use them when creating a deployment\. For more information, see [Creating container images for your Amazon Lightsail container services](amazon-lightsail-creating-container-images.md) and [Pushing and managing container images on your Amazon Lightsail container services](amazon-lightsail-pushing-container-images.md)\.

Lightsail container services support Linux\-based container images\. Windows\-based container images are currently not supported, but you can run Docker, the AWS Command Line Interface \(AWS CLI\), and the Lightsail Control \(lightsailctl\) plugin on Windows to build and push your Linux based images to your Lightsail container service\.

### Public endpoints and default domains<a name="container-services-endpoints-domains"></a>

When you create a deployment, you can specify the container entry in the deployment that will serve as the public endpoint of your container service\. The application on the public endpoint container is publicly accessible on the internet through a randomly generated default domain of your container service\. The default domain is formatted as `https://<ServiceName>.<RandomGUID>.<AWSRegion>.cs.amazonlightsail.com`, in which *<ServiceName>* is the name of your container service, *<RandomGUID>* is a randomly generated globally unique identifier of your container service in the AWS Region for your Lightsail account, and *<AWSRegion>* is the AWS Region in which the container service was created\. The public endpoint of Lightsail container services supports HTTPS only, and it does not support TCP or UDP traffic\. Only one container can be the public endpoint for a service\. So make sure that choose the container that is hosting the front\-end of your application as the public endpoint while rest of the containers are internally accessible\.

You can use the default domain of your container service, or you can use your own custom domain \(your registered domain name\)\. For more information about using custom domains with your container services, see [Enabling and managing custom domains for your Amazon Lightsail container services](amazon-lightsail-enabling-container-services-custom-domains.md)\.

**Private domain**

All container services also have a private domain that is formatted as `<ServiceName>.service.local`, in which *<ServiceName>* is the name of your container service\. Use the private domain to access your container service from another one of your Lightsail resources in the same AWS Region as your service\. The private domain is the only way to access your container service if you don't specify a public endpoint in the deployment of your service\. A default domain is generated for your container service even if you don't specify a public endpoint, but it will show a `404 No Such Service` error message when you try to browse to it\.

To access a specific container using the private domain of your container service, you must specify the open port of the container that will accept your connection request\. You do this by formatting the domain of your request as `<ServiceName>.service.local:<PortNumber>`, in which *<ServiceName>* is the name of your container service and *<PortNumber>* is the open port of the container that you wish to connect to\. For example, if you create a deployment on your container service named `container-service-1`, and you specify a Redis container with port `6379` open, then you should format the domain of your request as `container-service-1.service.local:6379`\.

### Custom domains and SSL/TLS certificates<a name="container-services-custom-domains-certificates"></a>

You can use up to 4 of your custom domains with your container service instead of using the default domain\. For example, you can direct traffic for your custom domain, such as `example.com`, to the container in your deployment that is labeled as the public endpoint\.

To use your custom domains with your service, you must first request an SSL/TLS certificate for the domains that you want to use\. You must then validate the SSL/TLS certificate by adding a set of CNAME records to the DNS of your domains\. After the SSL/TLS certificate is validated, you enable custom domains on your container service by attaching the valid SSL/TLS certificate to your service\. For more information see [Creating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-creating-container-services-certificates.md), [Validating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-validating-container-services-certificates.md), and [Enabling and managing custom domains for your Amazon Lightsail container services](amazon-lightsail-enabling-container-services-custom-domains.md)\.

### Container logs<a name="container-services-container-logs"></a>

Every container in your container service generates a log that you can access to diagnose the operation of your containers\. The logs provide the *stdout* and *stderr* streams of processes that run inside the container\. For more information, see [Viewing the container logs of your Amazon Lightsail container services](amazon-lightsail-viewing-container-service-container-logs.md)\.

### Metrics<a name="container-services-metrics"></a>

Monitor the metrics of your container service to diagnose issues that may be a result of over\-utilization\. You can also monitor metrics to help you determine if your service is under\-provisioned or over\-provisioned\. For more information, see [Viewing container service metrics in Amazon Lightsail](amazon-lightsail-viewing-container-services-metrics.md)\.

## Using Lightsail container services<a name="using-lightsail-container-services"></a>

These are the general steps to manage your Lightsail container service if you plan to push container images from your local machine to your service, and use them in your deployment:

1. Create your container service in your Lightsail account\. For more information, see [Creating Amazon Lightsail container services](amazon-lightsail-creating-container-services.md)\.

1. Install software on your local machine that you need to create your own container images and push them to your Lightsail container service\. For more information, see For more information, see the following guides:
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

These are the general steps to manage your Lightsail container service if you plan to use container images from a public registry, like Docker Hub, in your deployment:

1. Create your container service in your Lightsail account\. For more information, see [Creating Amazon Lightsail container services](amazon-lightsail-creating-container-services.md)\.

1. Find container images that you want to use from a public registry, such as Docker Hub\. For more information, see [Docker Hub Quickstart](https://docs.docker.com/docker-hub/) in the *Docker documentation*\.

1. Create a deployment in your container service that configures and launches your containers\. For more information, see [Creating and managing deployments for your Amazon Lightsail container services](amazon-lightsail-container-services-deployments.md)\.

1. View previous deployments for your container service\. You can create a new deployment using a previous deployment version\. For more information, see [Viewing and managing deployment versions of your Amazon Lightsail container services](amazon-lightsail-container-services-deployment-versions.md)\.

1. View the logs of containers on your container service\. For more information, see [Viewing the container logs of your Amazon Lightsail container services](amazon-lightsail-viewing-container-service-container-logs.md)\.

1. Create an SSL/TLS certificate for the domains that you want to use with your containers\. For more information, see [Creating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-creating-container-services-certificates.md)\.

1. Validate the SSL/TLS certificate by adding records to the DNS of your domains\. For more information, see [Validating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-validating-container-services-certificates.md)\.

1. Enable custom domains by attaching a valid SSL/TLS certificate to your container service\. For more information, see [Enabling and managing custom domains for your Amazon Lightsail container services](amazon-lightsail-enabling-container-services-custom-domains.md)\.

1. Monitor the utilization metrics of your container service\. For more information, see [Viewing container service metrics in Amazon Lightsail](amazon-lightsail-viewing-container-services-metrics.md)\.

1. \(Optional\) Scale the capacity of your container service vertically, by increasing its power specification, and horizontally, by increasing its scale specification\. For more information, see [Changing the capacity of your Amazon Lightsail container services](amazon-lightsail-changing-container-service-capacity.md)\.

1. Delete your container service if you're not using it to avoid incurring monthly charges\. For more information, see [Deleting Amazon Lightsail container services](amazon-lightsail-deleting-container-services.md)\.