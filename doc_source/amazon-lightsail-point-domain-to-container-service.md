# Routing traffic for a domain in Amazon Lightsail to a Lightsail container service<a name="amazon-lightsail-point-domain-to-container-service"></a>

 *Last updated: November 1, 2022* 

You must point your registered domain names to your Amazon Lightsail container service after you enabled custom domains for your service\. You do this by adding an alias record to the DNS zone of each of the domains specified on the certificates that you're using with your container service\. All of the records that you add should point to the default domain \(e\.g\., `https://<ServiceName>.<RandomGUID>.<AWSRegion>.cs.amazonlightsail.com`\) of your container service\.

In this guide, we provide you with the procedure to point your domains to your container service using a Lightsail DNS zone\. For more information about Lightsail DNS zones, see [DNS in Amazon Lightsail](understanding-dns-in-amazon-lightsail.md)\.

For more information about container services, see [Container services in Amazon Lightsail](amazon-lightsail-container-services.md)\.

**Note**  
If you're using Route 53 to host the DNS of your domain, then you should add the alias record to the hosted zone of your domain in Route 53\. For more information, see [Routing traffic for a domain in Route 53 to an Amazon Lightsail container service](amazon-lightsail-route-53-alias-record-for-container-service.md)\.

## Prerequisite<a name="point-domain-to-container-service-prerequisite"></a>

Before you get started, you should enable custom domains for your Lightsail container service\. For more information, see [Enabling and managing custom domains for your Amazon Lightsail container services](amazon-lightsail-enabling-container-services-custom-domains.md)\.

## Get the default domain of your container service<a name="get-container-service-default-domain"></a>

Complete the following procedure to get default domain name of your container service, which you specify when you add an alias record to the DNS of your domain\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Containers** tab\.

1. Choose the name of a container service for which want get the default domain name\.

1. In the header section of your container service management page, make note of your default domain name\. Your container service default domain name is similar to `<ServiceName>.<RandomGUID>.<AWSRegion>.cs.amazonlightsail.com`\.

   You must add this value as part of a canonical name \(CNAME\) record in the DNS of your domains\. We recommend that you copy and paste this value into a text file that you can refer to later\. For more information, see the following [Add the CNAME records to your domain's DNS zone](#add-container-service-default-domain-record) section of this guide\.

## Add a record to your domain's DNS zone<a name="add-container-service-default-domain-record"></a>

Complete the following procedure to add an address \(A for IPv4 or AAAA for IPv6\) record, or canonical \(CNAME\) record to your domain's DNS zone\.

1. On the Lightsail home page, choose the **Domains & DNS** tab\.

1. Under the **DNS zones** section of the page, choose the domain name to which you want to add the record that will direct traffic for your domain to your container service\.

1. Choose the **DNS records** tab\.

1. Complete one of the following steps depending on the current state of your DNS zone:
   + If you haven't added an A, AAAA, or CNAME record, choose **Add record**\.
   + If you previously added an A, AAAA, or CNAME record, choose the edit icon next to the existing A, AAAA, or CNAME record listed on the page, and then skip to step 5 of this procedure\.

1. Choose **A record**, **AAAA record**, or **CNAME record** in the **Record type** dropdown menu\.
   + Add an A record to map the apex of your domain \(e\.g\., `example.com`\) or a subdomain \(e\.g\., `www.example.com`\) to your container service under the IPv4 network\.
   + Add an AAAA record to map the apex of your domain \(e\.g\., `example.com`\) or a subdomain \(e\.g\., `www.example.com`\) to your container service under the IPv6 network\.
   + Add a CNAME record to map a subdomain \(e\.g\., `www.example.com`\) to the public domain \(default DNS\) of your container service\.

1. In the **Record name** text box, enter one of the following options:
   + For an A record or AAAA record, enter `@` to route traffic for the apex of your domain \(e\.g\., `example.com`\) to your container service, or enter a subdomain \(e\.g\., `www`\) to route traffic for a subdomain \(e\.g\., `www.example.com`\) to your container service\.
   + For a CNAME record, enter a subdomain \(e\.g\., `www`\) to route traffic for a subdomain \(e\.g\., `www.example.com`\) to your container service\.

1. Complete one of the following steps depending on the record you're adding:
   + For an A record or AAAA record, choose the name of your container service in the **Resolves to** text box\.
   + For a CNAME record, enter the default domain name of your container service into the **Maps to** text box\.

1. Choose the save icon to save the record to your DNS zone\.

   Repeat these steps to add additional DNS records for domains on your certificate that you are using with your container service\. Allow time for changes to propagate through the Internet’s DNS\. After a few minutes, you should see if your domain is pointing to your container service\.

## Additional information about container services<a name="point-domain-to-container-service-additional-info"></a>

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