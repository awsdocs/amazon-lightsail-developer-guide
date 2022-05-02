# Enabling and managing custom domains for your Amazon Lightsail container services<a name="amazon-lightsail-enabling-container-services-custom-domains"></a>

 *Last updated: January 25, 2022* 

Enable custom domains for your Amazon Lightsail container service to use your registered domain names with your service\. Before you enable custom domains, your container service accepts traffic only for the default domain that is associated with your service when you first create it \(e\.g\., `containerservicename.123456abcdef.us-west-2.cs.amazonlightsail.com`\)\. When you enable custom domains, you choose the Lightsail SSL/TLS certificate that you created for the domains that you want to use with your container service, and then you choose the domains you want to use from that certificate\. After you enable custom domains, your container service accepts traffic for all of the domains that are associated with the certificate that you chose\.

**Important**  
If you choose a Lightsail container service as the origin of your distribution, Lightsail automatically adds the default domain name of your distribution as a custom domain on your container service\. This enables traffic to be routed between your distribution and your container service\. However, there are some circumstances in which you might need to manually add the default domain name of your distribution to your container service\. For more information, see [Add the default domain of an Amazon Lightsail distribution to Lightsail container service](amazon-lightsail-adding-distribution-default-domain-to-container-service.md)\.

**Contents:**
+ [Container service custom domain limits](#container-service-custom-domains-prerequisites)
+ [Prerequisites](#container-service-custom-domains-prerequisites)
+ [View custom domains for a container service](#container-service-view-custom-domains)
+ [Enable custom domains for a container service](#container-service-enable-custom-domains)
+ [Disable custom domains for a container service](#container-service-disable-custom-domains)
+ [Additional information about container services](#container-service-custom-domains-additional-info)

## Container service custom domain limits<a name="container-service-custom-domains-limits"></a>

The following limits apply to container service custom domains:
+ You can use up to 4 custom domains with each of your Lightsail container services, and you cannot use the same domains on more than one service\.
+ If you use a Lightsail DNS zone to manage the DNS of your domain, then you can route traffic for the apex of your domain \(e\.g\., `example.com`\) and for subdomains \(e\.g\., `www.example.com`\) to your container services\.

## Prerequisites<a name="container-service-custom-domains-prerequisites"></a>

Before you get started, you need to create a Lightsail container service\. For more information, see [Creating Amazon Lightsail container services](amazon-lightsail-creating-container-services.md)\.

You also should have created and validated an SSL/TLS certificate for your container service\. For more information, see [Creating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-creating-container-services-certificates.md) and [Validating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-validating-container-services-certificates.md)\.

## View custom domains for a container service<a name="container-service-view-custom-domains"></a>

Complete the following procedure to view the custom domains that are currently enabled for your container service\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Containers** tab\.

1. Choose the name of the container service for which you want to view the enabled custom domains\.

1. Locate the custom domain values in the heading of the container service management page, as shown in the following example\. These are the custom domains that are currently enabled for the container service\.  
![\[Custom domains for a container service in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/container-service-custom-domains-heading.png)

1. On the container service management page, choose the **Custom domains** tab\.

   The certificates currently attached to your container service, and the custom domains being used under each attached certificate, are listed under the **Custom domain SSL/TLS certificates** section of the page\.  
![\[Custom domain certificates for a container service in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/container-service-custom-domains-certificate.png)

## Enable custom domains for a container service<a name="container-service-enable-custom-domains"></a>

Complete the following procedure to enable custom domains for your Lightsail container service by attaching a certificate to your service\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Containers** tab\.

1. Choose the name of the container service for which you want to enable custom domains\.

1. On the container service management page, choose the **Custom domains** tab\.

   The **Custom domains** page displays the SSL/TLS certificates currently attached to your container service, if any\. It also displays the SSL/TLS certificates that you previously created\.

1. Choose **Attach certificate**\.

   If you have no certificates, then you must first create an SSL/TLS certificate for your domains, and then validate it, before you can attach it to your container service\. For more information, see [Creating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-creating-container-services-certificates.md)\.

1. In the dropdown menu that appears, select a valid certificate for the domains that you want to use with your container service\.  
![\[Choosing a custom domain for a container service in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/container-service-custom-domains-picker.png)

1. Choose the domains for the selected certificate that you want to use with your container service\.  
![\[Choosing a custom domain for a container service in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/container-service-custom-domains-picker-checkbox.png)

1. Choose **Attach**\. After a few moments, traffic for the domain that you selected will begin to be accepted by your container service\.
**Important**  
If you haven't already done so, modify the DNS of your domain to route traffic for your domain to your container service\. For more information, see [Routing traffic for a domain in Amazon Lightsail to a Lightsail container service](amazon-lightsail-point-domain-to-container-service.md) or [Routing traffic for a domain in Route 53 to an Amazon Lightsail container service](amazon-lightsail-route-53-alias-record-for-container-service.md)\.

   If you already added the DNS records to the DNS of your domain, then open a new browser window and browse to the custom domain that you enabled for your container service\. The application that is running on your container service, if any, should load\.

## Disable custom domains for a container service<a name="container-service-disable-custom-domains"></a>

Complete the following procedure to disable custom domains for your Lightsail container service by detaching a certificate from your service, or by deselecting a previously selected domain\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Containers** tab\.

1. Choose the name of the container service for which you want to disable custom domains\.

1. On the container service management page, choose the **Custom domains** tab\.

   The **Custom domains** page displays the SSL/TLS certificates currently attached to your container service, if any\. It also displays the SSL/TLS certificates that you previously created\.

1. Choose the actions menu \(⋮\) for the certificate of the custom domains that you want to disable\.

1. Choose one of the following options:

   1. Choose **Detach** to detach the certificate from the container service, and disable all of its associated domains from the service\.

   1. Choose **Modify** to either deselect domains that were previously selected, or to select more domains that are associated to the container service\.
**Important**  
If you haven't already done so, modify the DNS records of your domain so that traffic routes stops routing to your container service and instead routes to another resource\.

## Additional information about container services<a name="container-service-custom-domains-additional-info"></a>

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

1. View the logs of containers on your container service\. For more information, see [Viewing the container logs of your Amazon Lightsail container services](amazon-lightsail-viewing-container-service-container-logs.md)\.

1. Create an SSL/TLS certificate for the domains that you want to use with your containers\. For more information, see [Creating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-creating-container-services-certificates.md)\.

1. Validate the SSL/TLS certificate by adding records to the DNS of your domains\. For more information, see [Validating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-validating-container-services-certificates.md)\.

1. Enable custom domains by attaching a valid SSL/TLS certificate to your container service\. For more information, see [Enabling and managing custom domains for your Amazon Lightsail container services](#amazon-lightsail-enabling-container-services-custom-domains)\.

1. Monitor the utilization metrics of your container service\. For more information, see [Viewing container service metrics in Amazon Lightsail](amazon-lightsail-viewing-container-services-metrics.md)\.

1. \(Optional\) Scale the capacity of your container service vertically, by increasing its power specification, and horizontally, by increasing its scale specification\. For more information, see [Changing the capacity of your Amazon Lightsail container services](amazon-lightsail-changing-container-service-capacity.md)\.

1. Delete your container service if you're not using it to avoid incurring monthly charges\. For more information, see [Deleting Amazon Lightsail container services](amazon-lightsail-deleting-container-services.md)\.