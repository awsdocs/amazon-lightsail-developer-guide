# Register a new domain in Lightsail<a name="amazon-lightsail-register-new-domain"></a>

 *Last updated: November 1, 2022* 

You can register new domains using Amazon Lightsail\. Lightsail domains are registered through Amazon Route 53, a highly available and scalable DNS web service\. If you have domains that are registered with other providers, you can transfer DNS management of those domains to Lightsail\. You can also point those domains to your Lightsail resources\. 

Choose one of the following procedures to register a new domain with Lightsail:
+ For registering a new domain, see [Register a new domain by using Lightsail](#register-new-domain-using-lightsail)\.
+ For an existing domain, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)\.
+ For moving a domain to another registrar, see [Managing a Lightsail domain in Amazon Route 53](amazon-lightsail-manage-domain-advanced.md)\.

Before you start, note the following considerations for domain registration:

Domain registration pricing  
For information about the cost to register domains, see [Amazon Route 53 pricing guide](https://aws.amazon.com/route53/pricing/#Domain_Names)\.

Domain service quotas  
There is a limit for how many domains you can register\. For more information, see [Service quotas](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/DNSLimitations.html#limits-api-entities-domains) in the Amazon Route 53 Developer Guide\. Contact Route 53 if you want to increase the limit\.

Supported domains  
Lightsail supports the registration of all generic top\-level domains \(TLDs\)\. For a list of supported TLDs, see [Domains that you can register with Amazon Route 53](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/registrar-tld-list.html#registrar-tld-list-index-generic) in the Amazon Route 53 Developer Guide\.

Domain names can’t be changed after registration  
If you accidentally register the wrong domain name, you won’t be able to change it\. Instead, you must register another domain name and specify the correct name\. There are no refunds for accidentally registered domain names\.

Charges for DNS zones  
When you register a domain with Lightsail, we automatically create a DNS zone for the domain\. Lightsail does not charge a fee for the DNS zone\.

## Register a new domain by using Lightsail<a name="register-new-domain-using-lightsail"></a>

**Contents**
+ [Complete the prerequisites](#reg-new-domain-prerequisites)
+ [Register a new domain](#reg-new-domain-steps)
+ [Verify the domain contact information](#reg-new-domain-verify-info)

### Complete the prerequisites<a name="reg-new-domain-prerequisites"></a>

Complete the following prerequisites if you haven’t already done so:

1. Confirm that the necessary DNS record types for your domain are supported by the Lightsail DNS zone\. The Lightsail DNS zone currently supports address \(A\), canonical name \(CNAME\), mail exchanger \(MX\), name server \(NS\), service locator \(SRV\), and text \(TXT\) record types\. For NS records, you can use wildcard DNS record entries\.

   If the DNS record types required for your domain are not supported by the Lightsail DNS zone, you might want to use Route 53 as your domain's DNS hosting provider\. Route 53 supports more record types\. For more information, see [Supported DNS Record Types](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/ResourceRecordTypes.html) and [Making Amazon Route 53 the DNS Service for an Existing Domain](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/MigratingDNS.html) in the Amazon Route 53 Developer Guide\.

### Register a new domain<a name="reg-new-domain-steps"></a>

**To register a new domain**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Choose the **Domains & DNS** tab\.

1. Choose **Register domain**, and specify the domain that you want to register\.

   1. Enter the domain name that you want to register, and choose **Check availability** to find out whether the domain name is available\. If the domain is available, continue to **Automatic domain renewal**\.

   1. If the domain name isn’t available, you see a list of other domains that you might want to register instead of your first choice or in addition to your first choice\. Choose **Select** for the domain that you want to register\.

1. Choose whether to automatically renew your domain registration before the expiration date\. When you register a domain name, you own it for a year by default\. If you don't renew your domain name registration, it expires and someone else can register the domain name\. To make sure that you keep your domain name, you can choose to renew it automatically every year, or select a longer term\.

1. In the **Domain contact information** section, enter contact information for the domain registrant, administrator, and technical contacts\. For more information, see [Values that you specify when you register or transfer a domain](amazon-lightsail-domain-register-values-specify.md)\.

   Note the following considerations:  
**First name and Last name**  
For **First name** and **Last name**, we recommend that you specify the name on your official ID\. For some changes to domain settings, some domain registries require that you provide proof of identity\. The name on your ID must match the name of the registrant contact for the domain\.  
**Different contacts**  
By default, we use the same information for all three contacts\. If you want to enter different information for one or more contacts, uncheck the **Same as registrant** checkbox and enter the new contact information\.

1. In the **Privacy protection** section, choose whether you want to hide your contact information from WHOIS queries\.

   For more information, see the following topics:
   + [Managing privacy protection for a domain](amazon-lightsail-domain-privacy-protection.md)
   + [Domains that you can register with Amazon Route 53](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/registrar-tld-list.html#registrar-tld-list-index-generic)

1. Choose **Register domain** to continue\. The **DNS zones** and **Summary** sections show information about the domain’s DNS zone, pricing, and renewal schedule\.

1. You must accept the [Amazon Route 53 domain name registration agreement](https://aws.amazon.com/route53/domain-registration-agreement/) before you can register your domain\.

### Verify the domain contact information<a name="reg-new-domain-verify-info"></a>

After you register your domain, you must verify that the email address for the registrant contact is valid\.

We automatically send a verification email from one of the following email addresses:

**noreply@registrar\.amazon\.com**  
For domains with Amazon Registrar as the registrar

**noreply@domainnameverification\.net**  
For domains with our registrar associate, Gandi, as the registrar\. To determine who the registrar is for your TLD, see [Domains that you can register with Amazon Route 53](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/registrar-tld-list.html#registrar-tld-list-index-generic) in the Amazon Route 53 Developer Guide\.

Use the following procedure to complete the domain verification process\.

**To complete domain verification**

1. When you receive the verification email, choose the link in the email that verifies that the email address is valid\. If you don't receive the email immediately, check your junk email folder\.

1. Return to the Lightsail console\. If the status doesn't automatically update to **Verified**, choose **Refresh status**\.
**Important**  
The registrant contact must follow the instructions in the email to verify that the email was received, or we will suspend the domain as required by ICANN\. When a domain is suspended, it's not accessible on the internet\.

1. When domain registration is complete, choose whether to use Lightsail as your DNS service, or use a different DNS service\.
   + **Lightsail**

     In the DNS zone that Lightsail created when you registered the domain, create records to tell Lightsail how you want to route traffic for the domain and subdomains\. 

     For example, when someone enters your domain name in a browser and that query is forwarded to Lightsail, do you want Lightsail to respond to the query with the IP address of a web server or with the name of a load balancer? For more information, see [Edit or delete a DNS zone in Amazon Lightsail](https://lightsail.aws.amazon.com/ls/docs/en_us/articles/amazon-lightsail-edit-or-delete-a-dns-zone)\.
   + **Using another DNS service**

     Configure your new domain to route DNS queries to a DNS service other than Lightsail\. For more information, see [Update the name servers for your domain when you want to use another DNS service](amazon-lightsail-domain-register-other-dns-service-procedure.md)\.

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