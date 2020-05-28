# Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail<a name="lightsail-how-to-create-dns-entry"></a>

 *Last updated: May 7, 2020* 

To map your domain name, such as `example.com`, to your Amazon Lightsail instance, you add a record to the Domain Name System \(DNS\) of your domain\. You can manage domain DNS records at the registrar where the domain name was registered, or manage them separately using another DNS hosting provider, such as Lightsail\.

We recommend that you transfer management of your domain's DNS records to Lightsail\. This allows you to efficiently administer all of your instance resources in one place—the Lightsail console\. You can create up to three DNS zones in Lightsail\. If you require more than three DNS zones, because you manage more than three domain names, we recommend using Route 53 to manage the DNS of all your domains\. You can use Route 53 to point your domain name to your Lightsail instance\. For more information about managing DNS with Route 53, see [Using Amazon Route 53 to point a domain to an Amazon Lightsail instance](amazon-lightsail-using-route-53-to-point-a-domain-to-an-instance.md)\.

This guide shows you how to create a DNS zone in the Lightsail console so that you can transfer management of your domain’s DNS records to Lightsail\. 

**Note**  
You continue to manage renewals and billing for your domain at your domain registrar, even after transferring management of your domain's DNS records to Lightsail\.

**Contents**
+ [Step 1: Complete the prerequisites](#lightail-creating-dns-zone-prerequisites)
+ [Step 2: Create a DNS zone in the Lightsail console](#lightail-create-a-dns-zone)
+ [Step 3: Add records to the DNS zone](#lightail-add-records-to-the-dns-zone)
+ [Step 4: Change the name servers at your domain’s current DNS hosting provider](#lightail-change-the-name-servers)

## Step 1: Complete the prerequisites<a name="lightail-creating-dns-zone-prerequisites"></a>

Complete the following prerequisites if you haven’t already done so:

1. Register a domain name\. Then confirm that you have administrative access to edit the domain's name servers\.

   If you need a registered domain name, get one through a domain name registrar, such as Amazon Route 53\. For more information, see [Registering a New Domain](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/domain-register.html) in the Route 53 documentation\.

1. Confirm that the necessary DNS record types for your domain are supported by the DNS zone in Lightsail\. The Lightsail DNS zone currently supports address \(A\), canonical name \(CNAME\), mail exchanger \(MX\), name server \(NS\), service locator \(SRV\), and text \(TXT\) record types\. For NS records, you can use wildcard DNS record entries\.

   If the DNS record types required for your domain are not supported by the DNS zone in Lightsail, then you may want to use Route 53 as your domain's DNS hosting provider because it supports a greater number of record types\. For more information, see [Supported DNS Record Types](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/ResourceRecordTypes.html) and [Making Amazon Route 53 the DNS Service for an Existing Domain](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/MigratingDNS.html) in the Route 53 documentation\.

1. Create a Lightsail instance to which you will point your domain\. For more information, see [Create an Amazon Lightsail instance](how-to-create-amazon-lightsail-instance-virtual-private-server-vps.md)\.

1. Create a static IP and attach it to your Lightsail instance\. For more information, see [Create a static IP and attach it to an instance in Amazon Lightsail](lightsail-create-static-ip.md)\.

## Step 2: Create a DNS zone in the Lightsail console<a name="lightail-create-a-dns-zone"></a>

Complete the following steps to create a DNS zone in Lightsail\. When you create a DNS zone, you must specify the domain name that the DNS zone will apply to\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Choose the **Networking** tab, and then choose **Create DNS zone**\.

1. Enter your registered domain name, such as `example.com`, into the text box\.

   It isn’t necessary to include `www` when entering your domain name\. You can add the `www` using an address \(A\) record as part of the [Step 3: Add records to the DNS zone](#lightail-add-records-to-the-dns-zone) section later in this guide\.
**Note**  
Lightsail DNS zones are created in the Virginia \(`us-east-1`\) AWS Region\. You will get a resource name conflict error \("some names are already in use"\) if you named a resource in that region the same as the Lightsail DNS zone \(e\.g\., `example.com`\) you want to create\.  
To resolve the error, [create a snapshot of the resource](understanding-instance-snapshots-in-amazon-lightsail.md)\. [Create a new resource from the snapshot](lightsail-how-to-create-instance-from-snapshot.md) and give it a new, unique name\. Then, delete the original resource that is named the same as the domain for which you want to create a Lightsail DNS zone\.

1. Choose one of the following options to add tags to your DNS zone:
   + **Add key\-only tags** or **Edit key\-only tags** \(if tags have already been added\)\. Enter your new tag into the tag key text box, and press **Enter**\. Choose **Save** when you’re done entering your tags to add them, or choose **Cancel** to not add them\.  
![\[Key-only tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-key-only-tags.png)
   + **Create a key\-value tag**, then enter a key into the **Key** text box, and a value into the **Value** text box\. Choose **Save** when you’re done entering your tags, or choose **Cancel** to not add them\.

     Key\-value tags can only be added one at a time before saving\. To add more than one key\-value tag, repeat the previous steps\.  
![\[Key-value tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-key-value-tag.png)
**Note**  
For more information about key\-only and key\-value tags, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

1. Choose **Create DNS zone**\.

   You are redirected to the DNS zone management page, where you can add DNS records or delete the DNS zone\. Note the Lightsail name servers that are listed on this page; you need these later in this guide\.  
![\[The DNS zone management page in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-dns-zone-management-page.png)

## Step 3: Add records to the DNS zone<a name="lightail-add-records-to-the-dns-zone"></a>

Complete the following steps to add records to your domain’s DNS zone\. DNS records specify how internet traffic is routed for the domain\. For example, you could route traffic for the apex of your domain, such as `example.com`, to one instance, and route traffic for a subdomain, such as `blog.example.com`, to a different instance\.

1. On the DNS zone management page, choose **Add record**\.

   Your DNS zones are listed in the **Networking tab** of the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Choose one of the following record types:  
**Address \(A\) record**  
An A record maps a domain, such as `example.com`, or a subdomain, such as `blog.example.com`, to a web server’s or instance’s IP address, such as `192.0.2.255`\.  

   1. In the **Subdomain** text box, enter the target subdomain for the record, or enter an @ symbol to define the apex of your domain\.

   1. In the **Resolves to** text box, enter the target IP address for the record, select your running instance, or configured load balancer\. When you select a running instance, the public IP address of that instance is automatically added\.
**Note**  
We recommend that you attach a static IP to your Lightsail instance and then choose the static IP as the value that the record resolves to\. For more information, see [Create a static IP in Amazon Lightsail](lightsail-create-static-ip.md)\.  
**Canonical name \(CNAME\) record**  
A CNAME record maps an alias or subdomain, such as `www.example.com`, to another domain, such as `example.com`, or another subdomain, such as `blog.example.com`\.  

   1. In the **Subdomain** text box, enter the subdomain for the record\.

   1. In the **Maps to** text box, enter the target domain or subdomain for the record\.  
**Mail exchanger \(MX\) record**  
An MX record maps a subdomain, such as `mail.example.com`, to an email server address with priority values when multiple servers are defined\.  

   1. In the **Subdomain** text box, enter the subdomain for the record\.

   1. In the **Priority** text box, enter the priority for the record\. This is important when adding records for multiple servers\.

   1. In the **Maps to** text box, enter the target domain or subdomain for the record\.  
**Service locator \(SRV\) record**  
An SRV record maps a subdomain, such as `service.example.com`, to a service address with values for priority, weight, and port number\. Telephony or instant messaging are a couple of the services typically associated with SRV records\.  

   1. In the **Subdomain** text box, enter the subdomain for the record\.

   1. In the **Priority** text box, enter the priority for the record\.

   1. In the **Weight** text box, enter a relative weight for SRV records with the same priority\.

   1. In the **Port** text box, enter the port number in which a connection to the service can be made\.  
**Text \(TXT\) record**  
A TXT record maps a subdomain to plain text\. You create TXT records to confirm ownership of your domain to a service provider\.  

   1. In the **Subdomain** text box, enter the subdomain for the record\.

   1. In the **Responds with** text box, enter the text response that is given when the subdomain is queried\.

1. When you're done adding the record, choose the **Save** icon to save your changes\.

   The record is added to the DNS zone\. Repeat the above steps to add multiple records to your domain's DNS zone\.
**Note**  
Time to live \(TTL\) for DNS records cannot be configured in the Lightsail DNS zone\. Instead, all Lightsail DNS records default to a TTL of 60 seconds\. For more information, see [Time to live](https://en.wikipedia.org/wiki/Time_to_live) on Wikipedia\.

## Step 4: Change the name servers at your domain’s current DNS hosting provider<a name="lightail-change-the-name-servers"></a>

Complete the following steps to transfer management of your domain's DNS records to Lightsail\. To do this, you sign in to the website of your domain’s current DNS hosting provider, and change your domain’s name servers to the Lightsail name servers\.

For detailed steps to complete this process, see the documentation from your domain’s current DNS hosting provider\. The following steps are provided only for general guidance\. If your domain was registered using Amazon Route 53, see [Adding or Changing Name Servers or Glue Records](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/domain-name-servers-glue-records.html#domain-name-servers-glue-records-procedure) in the *Route 53 Developer Guide* for detailed steps to change the name servers for your domain\.

**Important**  
If web traffic is currently being routed to your domain, make sure that all of the existing DNS records are present in the Lightsail DNS zone before changing the name servers at your domain’s current DNS hosting provider\. This way, traffic continually flows uninterrupted after the transfer to the Lightsail DNS zone\.

1. Write down the Lightsail name servers that are listed in on your domain's DNS zone management page\.  
![\[The DNS zone name servers in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-dns-zone-name-servers.png)

1. Sign in to your domain’s current DNS hosting provider’s website\.

1. Find the page where you can edit your domain's name servers\.

   For more information about locating this page, see the documentation from your domain’s current DNS hosting provider\.

1. Enter the Lightsail name servers, and remove other name servers listed\.

1. Save your changes\.

   Allow time for the name server change to propagate through the internet's DNS, which may take several hours\. After that is completed, internet traffic for your domain should begin routing through the Lightsail DNS zone\.

## Next steps<a name="lightail-dns-management-next-steps"></a>
+ [Edit or delete a DNS zone in Amazon Lightsail](amazon-lightsail-edit-or-delete-a-dns-zone.md)
+ [Create an Amazon Lightsail load balancer and attach instances to it](create-lightsail-load-balancer-and-attach-lightsail-instances.md)