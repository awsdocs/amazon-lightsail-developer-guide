# Point your domain to a Lightsail instance<a name="amazon-lightsail-routing-to-instance"></a>

 *Last updated: November 1, 2022* 

You can use the DNS zone in Amazon Lightsail to point a registered domain name, like **example\.com**, to your website running on a Lightsail instance, also known as a virtual private server \(VPS\)\. You can create up to six DNS zones in you Lightsail account\. Not all DNS record types are supported\. For more information about Lightsail DNS zones, see[ DNS in Amazon Lightsail](understanding-dns-in-amazon-lightsail.md)\.

If you expect to create more than six DNS zones or use DNS record types that aren’t supported in Lightsail, we recommend using an Amazon Route 53 hosted zone\. With Route 53, you can manage the DNS for up to 500 domains\. It also supports a greater variety of DNS record types\. For more information, see [Working with hosted zones](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/hosted-zones-working-with.html) in the Amazon Route 53 Developer Guide\.

This guide shows you how to edit the DNS records for a domain managed in Lightsail so that it points to your Lightsail instance\. Allow up to 48 hours for any DNS zone changes to propagate through the internet's DNS\.

**Prerequisites**

Complete the following prerequisites if you haven’t already done so:
+ Register a domain name using Lightsail\. For more information, see [Registering a new domain in Amazon Lightsail](amazon-lightsail-register-new-domain.md)\.
+ If you already registered a domain but you’re not using Lightsail to manage its records, then you must transfer management of the DNS records for your domain to Lightsail\. For more information, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)\.
+ The default dynamic public IP address attached to your Lightsail instance changes every time you stop and restart the instance\. Create a static IP and attach it to your instance to keep the public IP address from changing\. In this guide, you create a DNS record in your domain’s DNS zone that resolves to the static IP address so you don’t have to update your domain’s DNS records every time you stop and restart your instance\. For more information, see [Create a static IP and attach it to an instance in Amazon Lightsail](lightsail-create-static-ip.md)\.

  **Optional**–You can leave IPv6 enabled for your Lightsail instance\. The IPV6 address persists when you stop and start your instance\. For more information, see [Enabling and disabling IPv6 for your resources in Amazon Lightsail](amazon-lightsail-enable-disable-ipv6.md)\.

**Assign a domain to a Lightsail instance**

Use one of the following methods to assign a domain to an instance in Lightsail:
+ [Instance domains tab](#instance-domains-tab)
+ [Static IP domains tab](#static-ip-domains-tab)
+ [DNS zone assignments tab](#dns-zone-assignments-tab)

## Instance domains tab<a name="instance-domains-tab"></a>

Complete the following procedure to assign your domain to a Lightsail instance in the instance **Domains** tab of the Lightsail console\.

**To assign your domain by using the instance **Domains** tab**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Choose the instance name that you want to assign the domain to\.

1. Choose **Assign domain** in the **Domains** tab\.

1. Select the domain that you want to assign to your Lightsail instance\.

1. Verify that the routing information is correct, and then choose **Assign**\.

**Optional**

To edit or remove your domain assignment from the instance, choose the edit icon or the waste bin icon next to the domain name\.

## Static IP domains tab<a name="static-ip-domains-tab"></a>

Complete the following procedure to assign your domain to a Lightsail instance in the static IP **Domains** tab of the Lightsail console\.

**To assign your domain by using the static IP **Domains** tab**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Choose the **Networking** tab\.

1. Choose the static IP that you want to assign the domain to\.

1. Choose **Assign domain** in the **Domains** tab\.

1. Select the domain that you want to assign to your static IP\.

1. Verify that the routing information is correct, and then choose **Assign**\.

**Optional**

To edit or remove your domain assignment from the static IP, choose the edit icon or the waste bin icon next to the domain name\.

## DNS zone assignments tab<a name="dns-zone-assignments-tab"></a>

Complete the following procedure to assign your domain to a Lightsail instance in the **Assignments** tab of the DNS zone\.

**To assign your domain by using the **Assignments** tab**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Choose the **Domains & DNS** tab\.

1. Choose the DNS zone for the domain name that you want to use\.

1. Choose **Add assignment** in the **Assignments** tab\.

1. Select the domain name that you want to assign to your Lightsail instance\. If a static IP isn’t already attached to the instance, you are prompted to attach one\.

1. Verify that the routing information is correct, and then choose **Assign**\.

**Optional**

To edit or remove your domain assignment from the resource, choose the edit icon or the waste bin icon next to the domain name\.

**Additional information about domains**

The following articles can help you manage domains in Lightsail:
+ [DNS in Amazon Lightsail](understanding-dns-in-amazon-lightsail.md)
+ [Domain registration in Amazon Lightsail](amazon-lightsail-domain-registration.md)
+ [Formatting domain names in Amazon Lightsail](amazon-lightsail-domain-name-format.md)
+ [Managing a Lightsail domain in Amazon Route 53](amazon-lightsail-manage-domain-advanced.md)
+ [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)
+ [Managing domain registration renewal in Amazon Lightsail](amazon-lightsail-domain-manage-auto-renew.md)
+ [Edit or delete a DNS zone in Amazon Lightsail](amazon-lightsail-edit-or-delete-a-dns-zone.md)
+ [Point your domain to your Lightsail load balancer](add-alias-record-for-lightsail-load-balancer.md)
+ [Pointing your domains to your Amazon Lightsail distributions](amazon-lightsail-point-domain-to-distribution.md)
+ [Routing traffic for a domain in Amazon Lightsail to a Lightsail container service](amazon-lightsail-point-domain-to-container-service.md)