# Changing the capacity of your Amazon Lightsail container services<a name="amazon-lightsail-changing-container-service-capacity"></a>

 *Last updated: November 12, 2020* 

The capacity of your Amazon Lightsail container service is made up of its scale and power\. The scale specifies the number of compute nodes in your container service, and the power specifies the memory and vCPUs of each node in your service\. You pick the scale based on the number of nodes you want powering your service for better availability and higher capacity

By following the procedure in this guide, you can dynamically increase the power and scale of your container service at any time without any down\-time if you find that it's under\-provisioned, or decrease it if you find that it's over\-provisioned\. Lightsail automatically manages the capacity change along with your current deployment\.

**Note**  
If you create a new deployment, then the existing utilization metrics of your container service will disappear, and only metrics for the new current deployment will be shown\.

For more information about container services, see [Container services in Amazon Lightsail](amazon-lightsail-container-services.md)\.

## Change the capacity of your container service<a name="change-container-service-capacity"></a>

Complete the following procedure to change the capacity of your Lightsail container service\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Containers** tab\.

1. Choose the name of the container service for which you want to change the capacity\.

1. On the container service management page, choose the **Capacity** tab\.

   The current power, scale, and monthly price of your container service is displayed in the **Capacity** page\.

1. Choose **Change capacity** to change the power and scale to something else\.

1. On the confirmation prompt that appears, choose **Yes, continue** to acknowledge that changing the capacity of your container service will re\-deploy the current deployment\.

1. Choose the new power and scale of your container service\.

1. Choose **Yes, apply** to apply the new capacity to your container service\.

   The status of your container service changes to **Updating**\. After a few moments, the status of your service changes to **Enabled**, and it begins operating under its new capacity\.

## Additional information about container services<a name="change-container-service-capacity-additional-information"></a>

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

1. Enable custom domains by attaching a valid SSL/TLS certificate to your container service\. For more information, see [Enabling and managing custom domains for your Amazon Lightsail container services](amazon-lightsail-enabling-container-services-custom-domains.md)\.

1. Monitor the utilization metrics of your container service\. For more information, see [Viewing container service metrics in Amazon Lightsail](amazon-lightsail-viewing-container-services-metrics.md)\.

1. \(Optional\) Scale the capacity of your container service vertically, by increasing its power specification, and horizontally, by increasing its scale specification\. For more information, see [Changing the capacity of your Amazon Lightsail container services](#amazon-lightsail-changing-container-service-capacity)\.

1. Delete your container service if you're not using it to avoid incurring monthly charges\. For more information, see [Deleting Amazon Lightsail container services](amazon-lightsail-deleting-container-services.md)\.