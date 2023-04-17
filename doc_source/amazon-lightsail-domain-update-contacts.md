# Updating contact information for a domain<a name="amazon-lightsail-domain-update-contacts"></a>

 *Last updated: November 1, 2022* 

When you register a domain with Amazon Lightsail, you specify contact information for your domain\. Following are three types of contact information:
+ Registrant: Owner of the domain
+ Administrator: Person responsible for administering your domain
+ Technical: Person responsible for making technical changes to your domain

Your domain’s contact information is used to verify ownership of your domain and to keep you updated about any information related to your domain name\.

**Topics**
+ [Who is the owner of a domain?](#who-is-domain-owner)
+ [Updating contact information for a domain](#update-contacts-update-domain-contact-info)

## Who is the owner of a domain?<a name="who-is-domain-owner"></a>

When the contact type is **Person** and you change the **First Name** or **Last Name** fields for the registrant contact, you change the owner of the domain\.

When the contact type is any value except **Person** and you change **Organization**, you change the owner of the domain\.

The following actions happen when you change the contact information for a domain that is currently registered with Lightsail:
+ If you change contact information for the domain, we send an email notification to the registrant contact about the change\. This email comes from **noreply@amazon\.com**\. For most changes, the registrant contact is not required to respond\.
+ For changes to contact information that also constitute a change in ownership, we send the registrant contact an additional email\. ICANN, the organization that maintains a central database of domain names, requires that the registrant contact confirm receiving the email\.

## Updating contact information for a domain<a name="update-contacts-update-domain-contact-info"></a>

To update contact information for a domain, perform the following procedure\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Choose the **Domains & DNS** tab\.

1. Choose the name of the domain that you want to update\.

1. Choose the **Contact info** tab\. Then, choose **Edit contact**\.

1. Update the applicable values\. For more information, see [Values that you specify when you register or transfer a domain](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/domain-register-values-specify.html) in the Amazon Route 53 Developer Guide\.

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