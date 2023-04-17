# Managing privacy protection for domain contacts<a name="amazon-lightsail-domain-privacy-protection"></a>

 *Last updated: November 1, 2022* 

When you register a domain with Lightsail, we activate privacy protection by default for all the domain contacts\. This typically hides most of your contact information from WHOIS \("Who is"\) queries and reduces the amount of spam that you receive\. Your contact information is replaced with either the contact information for the registrar or with the phrase "REDACTED FOR PRIVACY\." There are no charges for using privacy protection\.

If you choose to deactivate privacy protection, anyone can send a WHOIS query for the domain and, for most top\-level domains \(TLDs\), they might be able to get all the contact information that you provided when you registered the domain\. This information includes name, address, phone number, and email address\. The WHOIS command is widely available\. It's included in many operating systems, and it's also available as a web application on many websites\.

To manage privacy protection for a domain that you registered by using Lightsail, perform the following procedure\.

**Contents**
+ [Complete the prerequisites](#privacy-protection-prerequisites)
+ [Manage privacy protection for your domain](#manage-domain-privacy-protection)

## Complete the prerequisites<a name="privacy-protection-prerequisites"></a>

Register a domain with Lightsail\. For more information, see [Registering a new domain in Amazon Lightsail](amazon-lightsail-register-new-domain.md)\.

## Manage privacy protection for your domain<a name="manage-domain-privacy-protection"></a>

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Choose the **Domains & DNS** tab\.

1. Choose the name of the domain that you want to change the privacy protection for\.

1. Choose **Contact info**\.

1. You can manage privacy protection for your contact information by turning the **Privacy protection** toggle switch on or off\.

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