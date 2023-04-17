# Formatting domain names in Lightsail<a name="amazon-lightsail-domain-name-format"></a>

 *Last updated: November 1, 2022* 

To help people access the website or application, choose a domain name that’s easy to remember\. Domain names \(and the names of DNS zones, and records\) consist of a series of labels separated by periods \(\.\)\. Naming requirements depend on whether you're registering a domain name or specifying the name of a DNS zone or a record\.

Format your domain name according to the following guidelines\.

**Contents**
+ [Formatting domain names for domain name registration](#formatting-for-registration)
+ [Formatting domain names for DNS zones and records](#formatting-for-dns-zones-and-records)
+ [Using an asterisk \(\*\) in the names of DNS zones and records](#using-asterisk)
+ [Next steps](#domain-name-format-next-steps)

## Formatting domain names for domain name registration<a name="formatting-for-registration"></a>

For domain name registration, your domain name must have 1\-255 characters\. Valid characters for domain names include \(a\-z\), \(A\-Z\), \(0\-9\), hyphens \(\-\), and periods \(\.\)\.

You can't use spaces or put a hyphen at the beginning or end of a domain name\. Lightsail supports any valid generic top\-level domain \(TLD\) name\. For more information, see [Generic top\-level domains](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/registrar-tld-list-generic.html) in the Amazon Route 53 Developer Guide\.

## Formatting domain names for DNS zones and records<a name="formatting-for-dns-zones-and-records"></a>

For DNS zones and records, the domain name must have 1\-255 characters\. Valid characters for domain names include \(a\-z\), \(A\-Z\), \(0\-9\), hyphens \(\-\), and periods \(\.\)\. You can’t use spaces\.

Lightsail stores alphabetic characters as lowercase letters \(a\-z\), even if you specify them as uppercase letters \(A\-Z\)\.

Lightsail supports DNS zones for both generic and geographic TLDs\. For more examples of geographic TLDs, see [Geographic top\-level domains](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/registrar-tld-list.html#registrar-tld-list-index-geographic) in the Amazon Route 53 Developer Guide\.

## Using an asterisk \(\*\) in the names of DNS zones and records<a name="using-asterisk"></a>

DNS treats the asterisk \(\*\) character as a wildcard character, depending on where the asterisk appears in the name\. A wildcard DNS record is a record that answers DNS requests for any subdomain that you haven’t already defined\. In Lightsail, you can create DNS zones and records that include the asterisk \(\*\) in the name with the following conditions: 

**DNS zones**
+ You can't include an asterisk \(\*\) in the leftmost label in a domain name\. For example, you can’t use **subdomain\.\*\.example\.com**\.
+ If you include the asterisk \(\*\) in other positions, DNS treats it as an ASCII 42 character, not a wildcard\. For more information about ASCII characters, see [ASCII](https://en.wikipedia.org/wiki/ASCII) in *Wikipedia*\.

**DNS Records**

Note the following restrictions on using an asterisk \(\*\) as a wildcard in a DNS record name:
+ As a wildcard, the asterisk must replace the leftmost label in a domain name, for example, **** **\*\.example\.com** or **\*\.acme\.example\.com**\. If you include an asterisk in any other position, such as **prod\.\*\.example\.com**, DNS treats it as an ASCII 42 character, not as a wildcard\.
+ The asterisk must replace the entire label\. For example, you can't specify **\*prod\.example\.com** or **prod\.\*\.example\.com**\.
+ Specific domain names take precedence\. For example, if you create records for **\*\.example\.com** and **acme\.example\.com**, DNS queries for **acme\.example\.com** respond with the values in the **acme\.example\.com** record\.
+ The asterisk applies to DNS queries for the subdomain level that includes the asterisk, and all the subdomains of that subdomain\. For example, if you create a record named **\*\.example\.com**, DNS queries for **\*\.example\.com** will respond to the following:

  **zenith\.example\.com** 

  **acme\.zenith\.example\.com**

  **pinnacle\.acme\.zenith\.example\.com** \(if there are no records of any type for that DNS zone\)

If you create a record named **\*\.example\.com** and there's no **example\.com** record, Lightsail responds to DNS queries for **example\.com** with `NXDOMAIN` \(non\-existent domain\)\.

You can configure Lightsail to return the same response to DNS queries for all subdomains at the same level and also for the domain name\. For example, you can configure Lightsail to respond to DNS queries such as **acme\.example\.com** and **zenith\.example\.com** by using the **example\.com** record\. Perform the following steps to route traffic for subdomains to the **example\.com** top\-level domain:

1. Create a record for the domain, such as **example\.com**\.

1. Create an alias record for the subdomain, such as **\*\.example\.com**\. Specify the record that you created in the previous step as the target for the alias record\.

## Next steps<a name="domain-name-format-next-steps"></a>

For more information, see the following topics:
+ [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)
+ [DNS in Amazon Lightsail](understanding-dns-in-amazon-lightsail.md)