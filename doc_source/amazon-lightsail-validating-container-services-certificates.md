# Validating SSL/TLS certificates for your Amazon Lightsail container services<a name="amazon-lightsail-validating-container-services-certificates"></a>

 *Last updated: November 12, 2020* 

You must validate an Amazon Lightsail SSL/TLS certificate after you created it and before you can use it with your Lightsail container service\. When you validate a certificate, you verify that you control all the domain names that you specified for the certificate when you created it\. You do this by adding canonical name \(CNAME\) records to the DNS zone of each of the domains specified on the certificate\. The records that you need to add are listed in the Lightsail console\.

In this guide, we provide you with the procedure to validate your certificate using a Lightsail DNS zone\. The procedure to validate your certificate using a different DNS hosting provider, like Domain\.com or GoDaddy, may be similar\. For more information about Lightsail DNS zones, see [DNS in Amazon Lightsail](understanding-dns-in-amazon-lightsail.md)\.

For more information about SSL/TLS certificates, see [SSL/TLS certificates in Lightsail](understanding-tls-ssl-certificates-in-lightsail-https.md)\.

## Prerequisite<a name="validating-container-service-certificate-prerequisite"></a>

Before you get started, you need to create an SSL/TLS certificate for your container service\. For more information, see [Creating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-creating-container-services-certificates.md)\.

## Get the CNAME record values to validate your certificate<a name="get-container-service-certificate-cname"></a>

Complete the following procedure to get the CNAME records that you must add to your domains to validate the certificate\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Containers** tab\.

1. Choose the name of the container service for which want to create a certificate\.

1. Choose the **Custom domains** tab on your container service management page\.

1. Scroll down to the **Certificates** section of the page\.

   All of your certificates are listed under the **Certificates** section of the page, including certificates created for other Lightsail resources, and certificates with a **Pending validation** status\.

1. Find the certificate that you want to validate, and make note of the **Name** and **Value** of the CNAME records that you must add for each domain listed\.

   You must add these records exactly as listed\. We recommend that you copy and paste these values into a text file that you can refer to later\. For more information, see the following [Add the CNAME records to your domain's DNS zone](#add-container-service-certificate-cname) section of this guide\.

## Add the CNAME records to your domain's DNS zone<a name="add-container-service-certificate-cname"></a>

Complete the following procedure to add CNAME records to your domain's DNS zone\.

1. On the Lightsail home page, choose the **Networking** tab\.

1. Under the **DNS zones** section of the page, choose the domain name to which you want to add the CNAME records to validate your certificate\.

1. Choose **Add record** in the DNS zone management page\.

1. Choose **CNAME** in the DNS record type drop\-down\.

1. In the **Subdomain** text box, enter the **Name** value of the CNAME record that you got from your certificate\.

   The Lightsail console pre\-populates the apex portion of your domain\. For example, if you want to add the `www.example.com` subdomain, then you only have to enter `www` into the text box, and Lightsail adds the `.example.com` portion for you when you save the record\.

1. In the **Maps to** text box, enter the **Value** portion of the CNAME record that you got from your certificate\.

1. Confirm that the values you entered are exactly as they were listed on the certificate that you want to validate\.

1. Choose the save icon to save the record to your DNS zone\.

   Repeat these steps to add additional CNAME records for domains on your certificate that need to be validated\. Allow time for changes to propagate through the internet's DNS\. After a few minutes, you should see if the status of your certificate has changed to **Valid**\. For more information, see the following [Viewing the status of your certificate](#view-container-service-certificate-status) section of this guide\.

## View the status of your certificate<a name="view-container-service-certificate-status"></a>

Complete the following procedure to view the status of your SSL/TLS certificate\.

1. On the Lightsail home page, choose the **Networking** tab\.

1. Choose the name of the container service for which you want to view a certificate's status\.

1. Choose the **Custom domains** tab on your container service management page\.

1. Scroll down to the **Certificates** section of the page\.

   All of your certificates are listed under the **Certificates** section of the page, including certificates with **Pending** validation and **Valid** statuses\.
**Note**  
If you left the Custom domains page open while validating your certificates, you might have to refresh to see the updated status of your certificates\.

   A **Valid** status confirms that you successfully validated your certificate with the CNAME records that you added to your domains\. Choose **Show details** to view your certificate's important dates, encryption details, identification, and validation records\. Your certificates are valid for 13 months from the date on which you validated them, after which time Lightsail attempts to automatically re\-validate them\. Don't delete the CNAME records that you added to your domain because they are required when your certificate is re\-validated on the **Valid until** date listed\.

   After you validate your SSL/TLS certificate, you should enable custom domains for your container service to use the domain names of your certificate on your service\. For more information, see [Enabling and managing custom domains for your Amazon Lightsail container services](amazon-lightsail-enabling-container-services-custom-domains.md)\.

## Additional information about container services<a name="validating-container-service-certificate-additional-info"></a>

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

1. Validate the SSL/TLS certificate by adding records to the DNS of your domains\. For more information, see [Validating SSL/TLS certificates for your Amazon Lightsail container services](#amazon-lightsail-validating-container-services-certificates)\.

1. Enable custom domains by attaching a valid SSL/TLS certificate to your container service\. For more information, see [Enabling and managing custom domains for your Amazon Lightsail container services](amazon-lightsail-enabling-container-services-custom-domains.md)\.

1. Monitor the utilization metrics of your container service\. For more information, see [Viewing container service metrics in Amazon Lightsail](amazon-lightsail-viewing-container-services-metrics.md)\.

1. \(Optional\) Scale the capacity of your container service vertically, by increasing its power specification, and horizontally, by increasing its scale specification\. For more information, see [Changing the capacity of your Amazon Lightsail container services](amazon-lightsail-changing-container-service-capacity.md)\.

1. Delete your container service if you're not using it to avoid incurring monthly charges\. For more information, see [Deleting Amazon Lightsail container services](amazon-lightsail-deleting-container-services.md)\.