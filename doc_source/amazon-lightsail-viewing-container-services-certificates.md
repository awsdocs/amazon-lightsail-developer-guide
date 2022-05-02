# Viewing SSL/TLS certificates for your Amazon Lightsail container services<a name="amazon-lightsail-viewing-container-services-certificates"></a>

 *Last updated: November 12, 2020* 

You can view the Amazon Lightsail SSL/TLS certificates that you created for your Lightsail container service\. You do this by accessing the management page of any container service in the Lightsail console\.

For more information about SSL/TLS certificates, see [SSL/TLS certificates in Amazon Lightsail](understanding-tls-ssl-certificates-in-lightsail-https.md)\.

## Prerequisites<a name="viewing-container-service-certificates-prerequisites"></a>

Before you get started, you need to create a Lightsail container service\. For more information, see [Creating Amazon Lightsail container services and Container services in Amazon Lightsail](amazon-lightsail-creating-container-services.md)\.

You also should have created an SSL/TLS certificate for your container service\. For more information, see [Creating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-creating-container-services-certificates.md)\.

## View your container service SSL/TLS certificates<a name="view-container-service-certificates"></a>

Complete the following procedure to view your container service SSL/TLS certificates\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Containers** tab\.

1. Choose the name of a container service\.

   You can view all of your certificates regardless of the container service you choose\.

1. Choose the **Custom domains** tab on your container service management page\.

1. Scroll down to the **Certificates** section of the page\.

   All of your certificates are listed under the **Certificates** section of the page\. Choose **Show details** to view your certificate's important dates, encryption details, identification, and validation records\. Your certificates are valid for 13 months from the date you created them, after which time Lightsail attempts to automatically revalidate them\. Don't delete the CNAME records that you added to your domain because they are required when your certificate is re\-validated on the **Valid until** date listed\.

   After you have a valid SSL/TLS certificate to use with your container service, you should enable custom domains so that you can use the domain names of the certificate on your service\. For more information, see [Enabling and managing custom domains for your Amazon Lightsail container services](amazon-lightsail-enabling-container-services-custom-domains.md)\.

## Additional information about container services<a name="viewing-container-service-certificate-additional-info"></a>

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

1. \(Optional\) Scale the capacity of your container service vertically, by increasing its power specification, and horizontally, by increasing its scale specification\. For more information, see [Changing the capacity of your Amazon Lightsail container services](amazon-lightsail-changing-container-service-capacity.md)\.

1. Delete your container service if you're not using it to avoid incurring monthly charges\. For more information, see [Deleting Amazon Lightsail container services](amazon-lightsail-deleting-container-services.md)\.