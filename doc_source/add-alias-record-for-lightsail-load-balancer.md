# Point your domain to your Lightsail load balancer<a name="add-alias-record-for-lightsail-load-balancer"></a>

 *Last updated: December 2, 2022* 

After you [verify that you control the domain where you want to have encrypted \(HTTPS\) traffic](verify-tls-ssl-certificate-using-dns-cname-https.md), you need to add an address \(A\) record to your domain's DNS hosting provider that points your domain to your Lightsail load balancer\. In this guide, we show you how to add the A record to a Lightsail DNS zone, and an Amazon Route 53 hosted zone\.

## Add an A record using the DNS zone \- Assignments page<a name="add-a-record-assignments"></a>

1. On the Lightsail home page, choose **Domains & DNS**\.

1. Choose the DNS zone you want to manage\.

1. Choose the **Assignments** tab\.

1. Choose **Add assignment**\.

1. In the **Select a domain name** field, choose whether to use the domain name, or a subdomain of the domain\.

1. In the **Select a resource** drop down, select the load balancer you want to assign the domain to\.

1. Choose **Assign**\.

Allow time for the change to propagate through the internet's DNS\. This may take a few minutes to several hours\.

## Add an A record using the DNS zone \- DNS records page<a name="add-address-record-lightsail"></a>

1. On the Lightsail home page, choose **Domains & DNS**\.

1. Choose the DNS zone you want to manage\.

1. Choose the **DNS records** tab\.

1. Complete one of the following steps depending on the current state of your DNS zone:
   + If you haven't added an A record, choose **Add record**\.
   + If you previously added an A record, choose the edit icon next to the existing A record listed on the page, and then skip to step 5 of this procedure\.

1. Choose **A record** in the **Record type** dropdown menu\.

1. In the **Record name** text box, enter one of the following options:
   + Enter `@` to route traffic for the apex of your domain \(e\.g\., `example.com`\) to your load balancer\.
   + Enter `www` to route traffic for the www subdomain \(e\.g\., `www.example.com`\) to your load balancer\.

1. In the **Resolves to** text box, choose the name of your Lightsail load balancer\.

1. Choose the **Save** icon\.

Allow time for the change to propagate through the internet's DNS\. This may take a few minutes to several hours\.

## Add an A record in Route 53<a name="add-address-record-route-53"></a>

1. Sign in to the [Route 53 console](https://console.aws.amazon.com/route53)\.

1. In the navigation pane, choose **Hosted zones**\.

1. Choose the hosted zone for the domain name that you want to use to route traffic to your load balancer\.

1. Choose **Create record**\.

   The **Quick create record** page appears\.  
![\[Create a record in Route 53 to point an alias to your Lightsail load balancer\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/create-record-set-alias-record-route-53-blank.png)
**Note**  
If you see the **Choose routing policy** page, then choose **Switch to quick create** to switch to the quick create wizard before continuing with the following steps\.

1. For **Record name**, type `www` if you plan to use the `www` subdomain \(i\.e\., `www.example.com`\) or leave it blank if you plan to use the apex of the domain \(i\.e\., `example.com`\)\.

1. For **Record type**, choose **A \- Routes traffic to an IPv4 address and some AWS resources**\.

1. Choose the **Alias** toggle to enable alias records\.

1. Choose the following options for **Route traffic to**:

   1. For **Choose endpoint**, choose **Alias to Application and Classic Load Balancer**\.

   1. For **Choose Region**, choose the AWS Region in which you created your Lightsail load balancer\.

   1. For **Choose load balancer**, enter or paste the endpoint URL \(i\.e\., DNS name\) of your Lightsail load balancer\.

1. For **Routing Policy**, choose **Simple routing**, and disable the **Evaluate target health** toggle\.

   Lightsail already performs health checks on your load balancer\. For more information, see [Health checking for your Lightsail load balancer](enable-set-up-health-checking-for-lightsail-load-balancer-metrics.md)\.

   Your record should look like the following example\.  
![\[Create a record in Route 53 to point an alias to your Lightsail load balancer\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/create-record-set-alias-record-route-53.png)

1. Choose **Create records** to add the record to your hosted zone\.
**Note**  
Allow time for the change to propagate through the internet's DNS\. This may take a few minutes to several hours\.