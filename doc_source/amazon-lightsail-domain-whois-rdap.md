# Viewing information about domains that are registered with Amazon Registrar<a name="amazon-lightsail-domain-whois-rdap"></a>

 *Last updated: November 1, 2022* 

You can view information about \.com, \.net, and \.org domains that were registered using Amazon Lightsail and Amazon Route 53, for which Amazon Registrar is the registrar\. This information includes details such as when the domain was originally registered and contact information for the domain owner and for the technical and administrative contacts\.

Note the following:

**Emailing domain contacts when privacy protection is active**  
If privacy protection is active for the domain, contact information for the registrant, technical, and administrative contacts is replaced with contact information for the Amazon Registrar privacy service\. For example, if the **example\.com** domain is registered with Amazon Registrar and if privacy protection is active, the value of **Registrant Email** in the response to a WHOIS query would be similar to `owner1234@example.com.whoisprivacyservice.org`\.  
To contact one or more domain contacts when privacy protection is active, send an email to the corresponding email addresses\. We'll automatically forward your email to the applicable contact\. 

**Reporting abuse**  
To report any illegal activity or violation of the [Acceptable Use Policy](http://aws.amazon.com/route53/amazon-registrar-policies/#acceptable-use-policy) , including inappropriate content, phishing, malware, or spam, send an email to **abuse@amazon\.com**\.

**To view information about domains that are registered with Amazon Registrar**  

1. In a web browser, go to one of the following websites\. Both websites display the same information\. However, they use different protocols and display the information in different formats:
   + **WHOIS**: [https://registrar\.amazon\.com/whois](https://registrar.amazon.com/whois)
   + **RDAP**: [https://registrar\.amazon\.com/rdap](https://registrar.amazon.com/rdap)

1. Enter the name of the domain that you want to view information about, and choose **Search**\. If the domain you search for was not registered using Amazon Lightsail or Route 53, then you will see a message stating that the domain is not in the registrar database\.

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