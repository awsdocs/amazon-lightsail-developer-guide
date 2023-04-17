# Managing a Lightsail domain in Amazon Route 53<a name="amazon-lightsail-manage-domain-advanced"></a>

 *Last updated: November 1, 2022* 

Amazon Lightsail registers domains through Amazon Route 53, a highly available and scalable DNS web service\. When you register a domain using Lightsail, you can manage the domain in both Lightsail and Route 53\. 

Tasks such as registering a domain, and routing traffic for a domain to Lightsail resources are done in the Lightsail console\. For more information, see [Domain registration in Amazon Lightsail](amazon-lightsail-domain-registration.md)\.

Advanced tasks, such as transferring domains, and deleting your registration must be done in the Amazon Route 53 console\.

This guide provides information for some of the advanced management tasks you can complete using the Route 53 console\. For a complete overview of Route 53, see [What is Amazon Route 53?](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/Welcome.html) in the *Amazon Route 53 Developer Guide*\.

**Contents**
+ [Viewing the status of a domain registration](#domain-registration-status)
+ [Locking a domain to prevent unauthorized transfer to another registrar](#locking-domain)
+ [Restoring an expired or deleted domain](#restoring-expired-domain)
+ [Transferring domains](#transfer-domain-registration)
+ [Deleting a domain name registration](#delete-domain-registration)

## Viewing the status of a domain registration<a name="domain-registration-status"></a>

Domain names have statuses that are also known as Extensible Provisioning Protocol \(EPP\) status codes\. ICANN, the organization that maintains a central database of domain names developed the EPP status code\. EPP status codes tell you the status of a variety of operations\. For example, registering a domain name, renewing the registration for a domain name, and so on\. All registrars use this same set of status codes\. To view the status code for your domains, see [Viewing the status of a domain registration](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/domain-view-status.html) in the *Amazon Route 53 Developer Guide*\.

## Locking a domain to prevent unauthorized transfer to another registrar<a name="locking-domain"></a>

The domain registries for all generic top\-level domains \(TLDs\) let you lock a domain to prevent someone from transferring the domain to another registrar without your permission\. For more information, see [Locking a domain to prevent unauthorized transfer to another registrar](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/domain-lock.html) in the *Amazon Route 53 Developer Guide*\.

## Restoring an expired or deleted domain<a name="restoring-expired-domain"></a>

If you don't renew a domain before the end of the late\-renewal period or if you accidentally delete the domain, some registries for top\-level domains \(TLDs\) allow you to restore the domain before it becomes available for others to register\. Use the linked procedure to try to restore your domain registration\. For more information, see [Restoring an expired or deleted domain](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/domain-restore-expired.html) in the *Amazon Route 53 Developer Guide*\.

## Transferring domain registrations<a name="transfer-domain-registration"></a>

You can transfer domain registration from another registrar to Route 53, from one AWS account to another, or from Route 53 to another registrar\. For more information, see [Transferring domains](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/domain-transfer.html) in the *Amazon Route 53 Developer Guide*\.

## Deleting a domain name registration<a name="delete-domain-registration"></a>

For most top\-level domains \(TLDs\), you can delete the registration if you no longer want it\. If the registry allows you to delete the registration, perform the procedure in this topic\. For more information, see [Deleting a domain name registration](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/domain-delete.html) in the *Amazon Route 53 Developer Guide*\.

**Additional information about domains**

The following articles can help you manage domains in Lightsail:
+ [DNS in Amazon Lightsail](understanding-dns-in-amazon-lightsail.md)
+ [Domain registration in Amazon Lightsail](amazon-lightsail-domain-registration.md)
+ [Formatting domain names in Amazon Lightsail](amazon-lightsail-domain-name-format.md)
+ [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)
+ [Managing domain registration renewal in Amazon Lightsail](amazon-lightsail-domain-manage-auto-renew.md)
+ [Edit or delete a DNS zone in Amazon Lightsail](amazon-lightsail-edit-or-delete-a-dns-zone.md)
+ [Point your domain to your Lightsail load balancer](add-alias-record-for-lightsail-load-balancer.md)
+ [Pointing your domains to your Amazon Lightsail distributions](amazon-lightsail-point-domain-to-distribution.md)
+ [Point your domain to a Lightsail instance](amazon-lightsail-routing-to-instance.md)
+ [Routing traffic for a domain in Amazon Lightsail to a Lightsail container service](amazon-lightsail-point-domain-to-container-service.md)