# Updating your domain name servers to use another DNS service<a name="amazon-lightsail-domain-register-other-dns-service-procedure"></a>

 *Last updated: November 1, 2022* 

You can use an Amazon Lightsail DNS zone to manage the DNS records for a domain that you registered using Lightsail\. Or, if you'd like, you can transfer management of DNS records for the domain to another DNS hosting provider\. In this guide, we show you how to transfer management of DNS records for a domain you registered with Lightsail to another DNS hosting provider\.

**Important**  
Any changes you make to the DNS of your domain might require several hours to propagate through the internet’s DNS\. Because of this, you should keep the DNS records of your domain in place at your current DNS hosting provider until the transfer of management is done\. This ensures that traffic for your domain continues to route to your resources uninterrupted while the transfer takes place\.

**Contents**
+ [Complete the prerequisites](#other-dns-service-prerequisites)
+ [Add records to the DNS zone](#other-dns-service-add-records-dns-zone)

## Complete the prerequisites<a name="other-dns-service-prerequisites"></a>

Complete the following prerequisites if you haven’t already done so:

1. Register a domain name\. You can register a domain name using Lightsail\. For more information, see [Registering a New Domain in Amazon Lightsail](amazon-lightsail-register-new-domain.md)\.

1. Use the process that’s provided by your DNS service to get the name servers for your domain\.

## Add records to the DNS zone<a name="other-dns-service-add-records-dns-zone"></a>

Complete the following procedure to add the name servers for another DNS hosting provider into your registered domain in Lightsail\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Choose the **Domains & DNS** tab\.

1. Choose the name of the domain that you want to configure to use another DNS service\.

1. Choose **Edit Name Servers**\.

1. Change the names of the name servers to the name servers that you got from your DNS service when you completed the prerequisites\.

1. Choose **Save**\.

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
+ [Point your domain to a Lightsail instance](amazon-lightsail-routing-to-instance.md)
+ [Routing traffic for a domain in Amazon Lightsail to a Lightsail container service](amazon-lightsail-point-domain-to-container-service.md)