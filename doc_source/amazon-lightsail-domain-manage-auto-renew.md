# Managing domain registration renewal in Lightsail<a name="amazon-lightsail-domain-manage-auto-renew"></a>

 *Last updated: November 1, 2022* 

When you register a domain with Amazon Lightsail, we configure the domain to renew automatically by default\. The default automatic renewal period is one year, although the registries for some top\-level domains \(TLDs\) have longer renewal periods\. All generic TLDs let you extend domain registration for longer periods, typically up to ten years in one\-year increments\. 

**Note**  
Make sure to deactivate automatic renewal if you intend to close your AWS account\. Otherwise, your domain registration will be renewed even after you have closed your account\.

**Contents**
+ [Automatic renewal](#automatic-renewal)
+ [Configure automatic renewal for a domain during domain registration](#enable-disable-auto-renew-during-registration)
+ [Configure automatic renewal for a domain that is already registered](#enable-disable-auto-renew-after-registration)

## Automatic renewal<a name="automatic-renewal"></a>

The following timeline shows what happens when automatic renewal is active:

**45 days before expiration**  
We send an email to the registrant contact to tell you that automatic renewal is active\. The email also contains instructions for how to deactivate automatic renewal\. Keep the registrant contact email address current so the email isn't missed\.

**35 or 30 days before expiration**  
For all domains except **\.com\.ar**, **\.com\.br**, and **\.jp** domains, we renew domain registration 35 days before the expiration date\. This way, we have time to resolve any issues with the renewal before the domain name expires\.  
The registries for **\.com\.ar**, **\.com\.br**, and **\.jp** domains require that we renew the domains no more than 30 days before expiration\. Gandi, our registrar associate, will send a renewal email 30 days before expiration\. If automatic renewal is active, this email is sent on the same day that we renew the domain\.

If automatic renewal is inactive, the following timeline shows what happens as the domain name expiration date approaches:

**45 days before expiration**  
We send an email to inform the registrant contact that automatic renewal is currently inactive\. The email also contains instructions for how to activate automatic renewal\. Keep the registrant contact email address current so the email isn’t missed\.

**35 and 7 days before expiration**  
If automatic renewal is inactive for the domain, ICANN, the governing body for domain registration, requires the registrar to send the registrant contact an email\. The email comes from one of the following email addresses:    
**noreply@registrar\.amazon\.com**–For domains with Amazon Registrar as the registrar    
**noreply@domainnameverification\.net**–For domains with our registrar associate, Gandi, as the registrar  
If you activate automatic renewal less than 30 days before expiration, we renew the domain registration within 24 hours\.

For more information about renewal periods, see the "Deadlines for renewing and restoring domains" section for your TLD in [Domains that you can register with Amazon Route 53](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/registrar-tld-list.html) in the Amazon Route 53 Developer Guide\.

**After the expiration date**  
Most domains are held by the registrar for a brief time after expiration, so you might be able to renew an expired domain after the expiration date, but we strongly recommend keeping automatic renewal active if you want to keep the domain\. For information about trying to renew a domain after the expiration date, see [Restoring an expired or deleted domain](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/domain-restore-expired.html) in the Amazon Route 53 Developer Guide\.  
If your domain expires but late renewal is allowed for the domain, you can renew the domain for the standard renewal price\. To determine whether a domain is still within the late\-renewal period, perform the procedure in [Extending the registration period for a domain](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/domain-extend.html) in the Amazon Route 53 Developer Guide\. If the domain is still listed, it's within the late\-renewal period\.

## Configure automatic renewal for a domain during domain registration<a name="enable-disable-auto-renew-during-registration"></a>

When you register a new domain name with Lightsail, we configure the domain to renew automatically\. You can choose to deactivate automatic domain renewal during the domain registration procedure\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Choose the **Domains & DNS** tab\.

1. Choose the **Register domain** button\.

1. Specify the domain name that you want to register with Lightsail, then choose **Check availability**\.

1. If the domain name is available, you will see the domain registration page\. In the **Automatic domain renewal** section, turn the toggle switch on or off to activate or deactivate automatic domain renewal\.

## Configure automatic renewal for a domain that is already registered<a name="enable-disable-auto-renew-after-registration"></a>

When you want to change whether Lightsail automatically renews registration for a domain shortly before the expiration date, or if you want to view the current setting for automatic renewal, perform the following procedure\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Choose the **Domains & DNS** tab\.

1. Choose the domain that you want to view or update\.

1. Choose the **Contact info** tab

1. 5\. In the **Automatic domain renewal** section, turn the toggle switch on or off to activate or deactivate automatic renewal for the domain’s registration period\.

**Additional information about domains**

The following articles can help you manage domains in Lightsail:
+ [DNS in Amazon Lightsail](understanding-dns-in-amazon-lightsail.md)
+ [Domain registration in Amazon Lightsail](amazon-lightsail-domain-registration.md)
+ [Formatting domain names in Amazon Lightsail](amazon-lightsail-domain-name-format.md)
+ [Managing a Lightsail domain in Amazon Route 53](amazon-lightsail-manage-domain-advanced.md)
+ [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)
+ [Edit or delete a DNS zone in Amazon Lightsail](amazon-lightsail-edit-or-delete-a-dns-zone.md)
+ [Point your domain to your Lightsail load balancer](add-alias-record-for-lightsail-load-balancer.md)
+ [Pointing your domains to your Amazon Lightsail distributions](amazon-lightsail-point-domain-to-distribution.md)
+ [Point your domain to a Lightsail instance](amazon-lightsail-routing-to-instance.md)
+ [Routing traffic for a domain in Amazon Lightsail to a Lightsail container service](amazon-lightsail-point-domain-to-container-service.md)