# Creating SSL/TLS certificates for your Amazon Lightsail container services<a name="amazon-lightsail-creating-container-services-certificates"></a>

 *Last updated: May 26, 2021* 

You can create Amazon Lightsail TLS/SSL certificates for your Lightsail container service\. When you create a certificate, you specify the primary and alternate domain names for the certificate\. When you enable custom domains for your container service, and choose the certificate, you can choose up to four domains from the certificate that will be added as the custom domains of your container service\. After you update the DNS record of your domains to direct traffic to your container service, your service accepts the traffic and serves your content using HTTPS\. There is a quota for the number of certificates that you can create\. For more information, see [Lightsail service quotas](https://docs.aws.amazon.com/general/latest/gr/lightsail.html)\.

For more information about SSL/TLS certificates, see [SSL/TLS certificates in Lightsail](understanding-tls-ssl-certificates-in-lightsail-https.md)\.

## Prerequisites<a name="creating-container-service-certificate-prerequisites"></a>

Before you get started, you need to create a Lightsail container service\. For more information, see [Creating Amazon Lightsail container services and Container services in Amazon Lightsail](amazon-lightsail-creating-container-services.md)\.

## Create an SSL/TLS certificate for your container service<a name="creating-container-service-certificate"></a>

Complete the following procedure to create an SSL/TLS certificate for your container service\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Containers** tab\.

1. Choose the name of the container service for which want to create a certificate\.

1. Choose the **Custom domains** tab on your container service management page\.

1. Scroll down to the **Certificates** section of the page\.

   All of your certificates are listed under the Certificates section of the page, including certificates created for other Lightsail resources, and certificates that are in use and not in use\.

1. Choose **Create certificate**\.

1. Enter the primary domain name \(e\.g\., `example.com`\) that you want to use with the certificate into the **Primary Domain** text box\.

   The name of your certificate is automatically updated to match the primary domain \(i\.e\., example\-com\) but you can change it\.

1. \(Optional\) Enter another domain name \(e\.g\., www\.example\.com\) into the **Alternate domains and subdomains** field\.

   You can add up to nine alternate domains to your certificate\. You can use up to four of your certificate's domains with your container service after you enable custom domains and select the certificate for your service\.

1. Choose **Create**\.

   Your certificate request is submitted, and the status of your new certificate is changed to **Pending**\. After a while, the status will change to **Validation in progress** and you will be required to validate the certificate with your domains before you can use it with your container service\. For more information, see [Validating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-validating-container-services-certificates.md)\.

## Additional information about container services<a name="creating-container-service-certificate-additional-info"></a>

These are the general steps to manage your Lightsail container service after it's up and running:

1. Get familiar with all of the elements of Lightsail container services\. For more information, see [Container services in Amazon Lightsail](amazon-lightsail-container-services.md)\.

1. Create your container service in your Lightsail account\. For more information, see [Creating Amazon Lightsail container services](amazon-lightsail-creating-container-services.md)\.

1. If you plan to use container images from a public registry, find container images that you want to use from a public registry like the Amazon ECR Public Gallery or Docker Hub\. For more information about Amazon ECR Public, see [What Is Amazon Elastic Container Registry Public?](https://docs.aws.amazon.com/AmazonECR/latest/public/what-is-ecr.html) in the *Amazon ECR Public User Guide*\. For more information about Docker Hub, see [Docker Hub Quickstart](https://docs.docker.com/docker-hub/) in the *Docker documentation*\.

1. If you plan to push container images from your local machine to your service, install software on your local machine that you need to create your own container images and push them to your Lightsail container service\. For more information, see the following guides:
   + [Installing software to manage container images for your Amazon Lightsail container services](amazon-lightsail-install-software.md)
   + [Creating container images for your Amazon Lightsail container services](amazon-lightsail-creating-container-images.md)
   + [Pushing and managing container images on your Amazon Lightsail container services](amazon-lightsail-pushing-container-images.md)

1. Create a deployment in your container service that configures and launches your containers\. For more information, see [Creating and managing deployments for your Amazon Lightsail container services](amazon-lightsail-container-services-deployments.md)\.

1. View previous deployments for your container service\. You can create a new deployment using a previous deployment version\. For more information, see [Viewing and managing deployment versions of your Amazon Lightsail container services](amazon-lightsail-container-services-deployment-versions.md)\.

1. View the logs of containers on your container service\. For more information, see [Viewing the container logs of your Amazon Lightsail container services](amazon-lightsail-viewing-container-service-container-logs.md)\.

1. Create an SSL/TLS certificate for the domains that you want to use with your containers\. For more information, see [Creating SSL/TLS certificates for your Amazon Lightsail container services](#amazon-lightsail-creating-container-services-certificates)\.

1. Validate the SSL/TLS certificate by adding records to the DNS of your domains\. For more information, see [Validating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-validating-container-services-certificates.md)\.

1. Enable custom domains by attaching a valid SSL/TLS certificate to your container service\. For more information, see [Enabling and managing custom domains for your Amazon Lightsail container services](amazon-lightsail-enabling-container-services-custom-domains.md)\.

1. Monitor the utilization metrics of your container service\. For more information, see [Viewing container service metrics in Amazon Lightsail](amazon-lightsail-viewing-container-services-metrics.md)\.

1. \(Optional\) Scale the capacity of your container service vertically, by increasing its power specification, and horizontally, by increasing its scale specification\. For more information, see [Changing the capacity of your Amazon Lightsail container services](amazon-lightsail-changing-container-service-capacity.md)\.

1. Delete your container service if you're not using it to avoid incurring monthly charges\. For more information, see [Deleting Amazon Lightsail container services](amazon-lightsail-deleting-container-services.md)\.