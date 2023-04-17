# Creating a DNS zone to manage your domain’s DNS records in Lightsail<a name="lightsail-how-to-create-dns-entry"></a>

 *Last updated: December 2, 2022* 

To route traffic for a domain name, such as `example.com`, to an Amazon Lightsail instance, you add a record to the Domain Name System \(DNS\) of your domain\. You can manage the DNS records of your domain using the registrar where you registered your domain, or you can manage them using Lightsail\.

We recommend that you transfer management of your domain's DNS records to Lightsail\. This allows you to efficiently administer your domain and compute resources together in one place—Lightsail\. You can manage the DNS records of your domain using Lightsail by creating a Lightsail DNS zone\. You can create up to six Lightsail DNS zones\. If you require more than six DNS zones, because you manage more than six domain names, we recommend using Amazon Route 53 to manage the DNS of all of your domains\. You can use Route 53 to route traffic for your domain to your Lightsail resources\. For more information about managing DNS with Route 53, see [Using Amazon Route 53 to point a domain to an Amazon Lightsail instance](amazon-lightsail-using-route-53-to-point-a-domain-to-an-instance.md)\.

This guide shows you how to create a Lightsail DNS zone for your domain, and how to transfer management of your domain's DNS records to Lightsail\. After transferring management of your domain's DNS records to Lightsail, you will continue to manage renewals and billing for your domain at your domain's registrar\.

**Important**  
Any changes you make to the DNS of your domain might require several hours to propagate through the internet's DNS\. Because of this, you should keep the DNS records of your domain in place at your domain's current DNS hosting provider while the transfer of management to Lightsail propagates\. This ensures that traffic for your domain continues to route to your resources uninterrupted while the transfer takes place\.

**Contents**
+ [Step 1: Complete the prerequisites](#lightail-creating-dns-zone-prerequisites)
+ [Step 2: Create a DNS zone in the Lightsail console](#lightail-create-a-dns-zone)
+ [Step 3: Add records to the DNS zone](#lightail-add-records-to-the-dns-zone)
+ [Step 4: Change the name servers at your domain’s current DNS hosting provider](#lightail-change-the-name-servers)

## Step 1: Complete the prerequisites<a name="lightail-creating-dns-zone-prerequisites"></a>

Complete the following prerequisites if you haven’t already done so:

1. Register a domain name\. Then, confirm that you have administrative access to edit the domain's name servers\.

   If you need a registered domain name, you can register a domain using Lightsail\. For more information, see [Domain registration in Lightsail](amazon-lightsail-domain-registration.md)\.

1. Confirm that the necessary DNS record types for your domain are supported by the Lightsail DNS zone\. The Lightsail DNS zone currently supports address \(A and AAAA\), canonical name \(CNAME\), mail exchanger \(MX\), name server \(NS\), service locator \(SRV\), and text \(TXT\) record types\. For NS records, you can use wildcard DNS record entries\.

   If the DNS record types required for your domain are not supported by the Lightsail DNS zone, you might want to use Route 53 as your domain's DNS hosting provider because it supports a greater number of record types\. For more information, see [Supported DNS Record Types](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/ResourceRecordTypes.html) and [Making Amazon Route 53 the DNS Service for an Existing Domain](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/MigratingDNS.html) in the Amazon Route 53 Developer Guide\.

1. Create a Lightsail instance to which you will point your domain\. For more information, see [Create an Amazon Lightsail instance](how-to-create-amazon-lightsail-instance-virtual-private-server-vps.md)\.

1. Create a static IP and attach it to your Lightsail instance\. For more information, see [Create a static IP and attach it to an instance in Amazon Lightsail](lightsail-create-static-ip.md)\.

## Step 2: Create a DNS zone in the Lightsail console<a name="lightail-create-a-dns-zone"></a>

Complete the following steps to create a DNS zone in Lightsail\. When you create a DNS zone, you must specify the domain name that the DNS zone will apply to\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Choose the **Domains & DNS** tab, and then choose **Create DNS zone**\.

1. Choose one of the following options:
   + **Use a domain that is registered with Amazon Route 53**, to specify a domain that was registered with Amazon Route 53
   + **Use a domain from another registrar**, to specify a domain that was registered using another registrar

1. Select or enter your registered domain name, such as `example.com`\.

   It isn’t necessary to include `www` when entering your domain name\. You can add the `www` using an address \(A\) record as part of the [Step 3: Add records to the DNS zone](#lightail-add-records-to-the-dns-zone) section later in this guide\.
**Note**  
Lightsail DNS zones are created in the Virginia \(`us-east-1`\) AWS  Region\. You will get a resource name conflict error \("some names are already in use"\) if you named a resource in that region the same as the Lightsail DNS zone \(e\.g\., `example.com`\) you want to create\.  
To resolve the error, [create a snapshot of the resource](understanding-instance-snapshots-in-amazon-lightsail.md)\. [Create a new resource from the snapshot](lightsail-how-to-create-instance-from-snapshot.md) and give it a new, unique name\. Then, delete the original resource that is named the same as the domain for which you want to create a Lightsail DNS zone\.

1. Choose **Create DNS zone**\.

   You are redirected to the DNS zone **Assignments** page, where you can manage domain resource assignments\. Use assignments to point a domain to your Lightsail resources, such as load balancers and instances\.

## Step 3: Add records to the DNS zone<a name="lightail-add-records-to-the-dns-zone"></a>

Complete the following steps to add records to your domain’s DNS zone\. DNS records specify how internet traffic is routed for the domain\. For example, you could route traffic for the apex of your domain, such as `example.com`, to one instance, and route traffic for a subdomain, such as `blog.example.com`, to a different instance\.

1. From the DNS zone assignments page, choose the **DNS records** tab\.

   Your DNS zones are listed in the **Domains & DNS** tab of the [Lightsail console](https://lightsail.aws.amazon.com/)\.
**Note**  
On the DNS zone **Assignments** page, you can add, remove, or change which Lightsail resource your domain points to\. You can point domains at Lightsail instances, distributions, container services, load balancers, static IP addresses and more\. On the **DNS records** page, you can add, edit, or delete your domain’s DNS records\.

1. Choose one of the following record types:  
**Address \(A\) record**  
An A record maps a domain, such as `example.com`, or a subdomain, such as `blog.example.com`, to a web server’s or instance’s IP address, such as `192.0.2.255`\.  

   1. In the **Record name** text box, enter the target subdomain for the record, or enter an @ symbol to define the apex of your domain\.

   1. In the **Resolves to** text box, enter the target IP address for the record, select your running instance, or configured load balancer\. When you select a running instance, the public IP address of that instance is automatically added\.
**Note**  
We recommend that you attach a static IP to your Lightsail instance and then choose the static IP as the value that the record resolves to\. For more information, see [Create a static IP in Amazon Lightsail](lightsail-create-static-ip.md)\.  
**AAAA record**  
An AAAA record maps a domain, such as `example.com`, or a subdomain, such as `blog.example.com`, to a web server’s or instance’s IPv6 address, such as `2001:0db8:85a3:0000:0000:8a2e:0370:7334`\.  
Lightsail does not support static IPv6 addresses\. If you delete your Lightsail resource and create a new resource, or if you disable and reenable IPv6 on the same resource, you might need to update your AAAA record to reflect the latest IPv6 address for the resource\.

   1. In the **Record name** text box, enter the target subdomain for the record, or enter an `@` symbol to define the apex of your domain\.

   1. In the **Resolves to** text box, enter the target IPv6 address for the record, select your running instance, or configured load balancer\. When you select a running instance, the public IPv6 address of that instance is automatically added\.  
**Canonical name \(CNAME\) record**  
A CNAME record maps an alias or subdomain, such as `www.example.com`, to another domain, such as `example.com`, or another subdomain, such as `blog.example.com`\.  

   1. In the **Record name** text box, enter the subdomain for the record\.

   1. In the **Route traffic to** text box, enter the target domain or subdomain for the record\.  
**Mail exchanger \(MX\) record**  
An MX record maps a subdomain, such as `mail.example.com`, to an email server address with priority values when multiple servers are defined\.  

   1. In the **Record name** text box, enter the subdomain for the record\.

   1. In the **Priority** text box, enter the priority for the record\. This is important when adding records for multiple servers\.

   1. In the **Route traffic to** text box, enter the target domain or subdomain for the record\.  
**Service locator \(SRV\) record**  
An SRV record maps a subdomain, such as `service.example.com`, to a service address with values for priority, weight, and port number\. Telephony or instant messaging are a couple of the services typically associated with SRV records\.  

   1. In the **Record name** text box, enter the subdomain for the record\.

   1. In the **Priority** text box, enter the priority for the record\.

   1. In the **Weight** text box, enter a relative weight for SRV records with the same priority\.

   1. In the **Route traffic to** text box, enter the target domain or subdomain for the record\.

   1. In the **Port** text box, enter the port number in which a connection to the service can be made\.  
**Text \(TXT\) record**  
A TXT record maps a subdomain to plain text\. You create TXT records to confirm ownership of your domain to a service provider\.  

   1. In the **Record name** text box, enter the subdomain for the record\.

   1. In the **Responds with** text box, enter the text response that is given when the subdomain is queried\.
**Note**  
The input text doesn't need to be enclosed with quotes\.

1. When you're done adding the record, choose the **Save** icon to save your changes\.

   The record is added to the DNS zone\. Repeat the above steps to add multiple records to your domain's DNS zone\.
**Note**  
Time to live \(TTL\) for DNS records cannot be configured in the Lightsail DNS zone\. Instead, all Lightsail DNS records default to a TTL of 60 seconds\. For more information, see [Time to live](https://en.wikipedia.org/wiki/Time_to_live) on Wikipedia\.

## Step 4: Change the name servers at your domain’s current DNS hosting provider<a name="lightail-change-the-name-servers"></a>

Complete the following steps to transfer management of your domain's DNS records to Lightsail\. To do this, you sign in to the website of your domain’s current DNS hosting provider, and change your domain’s name servers to the Lightsail name servers\.

The name servers are located on the **Name servers** tab of your DNS zone\.

**Important**  
If web traffic is currently being routed to your domain, make sure that all of the existing DNS records are present in the Lightsail DNS zone before changing the name servers at your domain’s current DNS hosting provider\. This way, traffic continually flows uninterrupted after the transfer to the Lightsail DNS zone\.

1. Write down the Lightsail name servers that are listed in on your domain's DNS zone management page\.

1. Sign in to your domain’s current DNS hosting provider’s website\.

1. Find the page where you can edit your domain's name servers\.

   For more information about locating this page, see the documentation from your domain’s current DNS hosting provider\.

1. Enter the Lightsail name servers, and remove other name servers listed\.

1. Save your changes\.

   Allow time for the name server change to propagate through the internet's DNS, which might take several hours\. After that is completed, internet traffic for your domain should begin routing through the Lightsail DNS zone\.

## Next steps<a name="lightail-dns-management-next-steps"></a>
+ [Edit or delete a DNS zone in Amazon Lightsail](amazon-lightsail-edit-or-delete-a-dns-zone.md)
+ [Create an Amazon Lightsail load balancer and attach instances to it](create-lightsail-load-balancer-and-attach-lightsail-instances.md)