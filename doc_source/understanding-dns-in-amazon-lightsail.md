# DNS in Amazon Lightsail<a name="understanding-dns-in-amazon-lightsail"></a>

**Note**  
The Domain Name System \(DNS\) routes easy\-to\-remember domain names, such as `example.com`, to the internet protocol \(IP\) addresses of web servers\. In Amazon Lightsail, you can point a domain name to your running instance or load balancer\.

 *Last updated: May 7, 2020* 

People can access the web application on your Lightsail instance by browsing to the public internet protocol \(IP\) address of your instance\. However, IP addresses are complex and difficult for people to remember\. Therefore, you should have people browse to an easy\-to\-remember domain name, like `example.com`, to access the web application on your instance\. This is achieved through the Domain Name System \(DNS\), which functions as a directory that maps registered domain names to IP addresses\.

To map your domain name to your Lightsail instance, you add an address \(A\) record that points your domain name to the static IP address of your instance\. You can manage domain DNS records at the registrar where the domain name was registered, or you can manage them separately using another DNS hosting provider, such as Lightsail\. To make it easier to map your domain name to your Lightsail instance, we recommend that you transfer management of your domain's DNS records to Lightsail by creating a DNS zone\. For more information, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)\. You can create up to three DNS zones in Lightsail\. If you require more than three DNS zones, because you manage more than three domain names, we recommend using Route 53 to manage the DNS of all your domains\. You can use Route 53 to point your domain name to your Lightsail instance\. For more information about managing DNS with Route 53, see [Using Amazon Route 53 to point a domain to an Amazon Lightsail instance](amazon-lightsail-using-route-53-to-point-a-domain-to-an-instance.md)\.

## DNS terminology<a name="lightsail-dns-zone-terminology"></a>

So that you can manage DNS for your domain, there are terms you should be familiar with\.

**Apex domain / root domain**  
An apex domain, also known as a root domain, is a domain that does not contain a subdomain part\. An example of an apex domain is `example.com`\. Whereas, subdomain examples are `www.example.com` and `blog.example.com`\. These are subdomains because they contain the `www` and `blog` subdomain parts respectively\.

**Domain Name System \(DNS\)**  
DNS routes easy\-to\-remember domain names, such as `example.com`, to the IP addresses of web servers\.  
For more information, see [Domain Name System](https://en.wikipedia.org/wiki/Domain_Name_System) on Wikipedia\.

**DNS record**  
A DNS record is a mapping parameter\. It tells the DNS server which IP address or hostname a domain or subdomain is associated with\.  
For more information, see [List of DNS record types](https://en.wikipedia.org/wiki/List_of_DNS_record_types) on Wikipedia\.

**DNS zone**  
A DNS zone is a container that holds information about how you want to route traffic on the internet for a specific domain, such as `example.com`, and its subdomains, such as `blog.example.com`\.  
For more information, see [DNS zone](https://en.wikipedia.org/wiki/DNS_zone) on Wikipedia\.

**Domain name registrar**  
A domain name registrar, also known as a domain name provider, is a company or organization that manages the assignment of domain names\. You can purchase a domain or manage an existing domain using Amazon Route 53 or any other domain name registrar\.  
For more information, see [Domain name registrar](https://en.wikipedia.org/wiki/Domain_name_registrar) on Wikipedia\.

**Name server**  
A name server routes traffic to your domain\. In Lightsail, the name server is an AWS instance that runs a network service to help translate easy\-to\-remember domain names to IP addresses\. Lightsail provides several AWS name server options \(e\.g\., `ns-NN.awsdns-NN.com`\) to route traffic to your domain\. You can choose from among these AWS name servers when you change your domain using a domain registrar\.  
For more information, see [Name server](https://en.wikipedia.org/wiki/Name_server) on Wikipedia\.

**Subdomain**  
A subdomain is anything in the domain hierarchy, other than the root domain, that is part of the larger domain\. For example, `blog` is the subdomain part of the `blog.example.com` subdomain\.  
For more information, see [Subdomain](https://en.wikipedia.org/wiki/Subdomain) on Wikipedia\.

**Time to live \(TTL\)**  
TTL dictates the lifespan of a DNS record on local resolving name servers; for example, a shorter time means less time to wait until the changes go into effect\. TTL cannot be configured in the Lightsail DNS zone\. Instead, all Lightsail DNS records default to a TTL of 60 seconds\.  
For more information, see [Time to live](https://en.wikipedia.org/wiki/Time_to_live) on Wikipedia\.

**Wildcard DNS record**  
A wildcard DNS record matches requests for non\-existent domain names\. A wildcard DNS record is specified by using the asterisk symbol \(\*\) as the leftmost part of a domain name, such as `*.example.com` or `*example.com`\.  
The Lightsail DNS zone currently supports wildcard records only for name server domains \(e\.g\., `*awsdns.com`\) defined in a Name Server \(NS\) record\.

## DNS record types supported in the Lightsail DNS zone<a name="lightsail-dns-records-supported-in-lightsail"></a>

Address \(A\) record  
An A record maps a domain, such as `example.com`, or a subdomain, such as `blog.example.com`, to a web server’s IP address\.  
For example, in the Lightsail DNS zone, you want to direct web traffic for `example.com` \(the apex of the domain\) to your instance\. You would create an A record, enter an `@` symbol into the **Subdomain** text box, and enter the IP address of your web server into the **Resolves to address** text box\.  
For more information about the A record, see [List of DNS record types](https://en.wikipedia.org/wiki/List_of_DNS_record_types) on Wikipedia\.

Canonical name \(CNAME\) record  
A CNAME record maps an alias or subdomain, such as `blog.example.com`, to another domain or subdomain\.  
For example, in the Lightsail DNS zone, you want to direct web traffic for `www.example.com` to `example.com`\. You would create an alias CNAME record for `www` with a "resolves to" address of `example.com`\.  
For more information, see [CNAME Record](https://en.wikipedia.org/wiki/CNAME_record) on Wikipedia\.

Mail exchanger \(MX\) record  
An MX record maps a subdomain, such as `mail.example.com`, to an email server address with values for priority when multiple servers are defined\.  
For example, in the Lightsail DNS zone you want to direct mail for `mail.example.com` to the `10 inbound-smtp.us-west-2.amazonaws.com` Amazon WorkMail server\. You would create an MX record with a subdomain of `example.com`, a priority of `10`, and a "resolves to" address of `inbound-smtp.us-west-2.amazonaws.com`\.  
For more information, see [MX Record](https://en.wikipedia.org/wiki/MX_record) on Wikipedia\.

Name server \(NS\) record  
An NS record delegates a subdomain, such as `test.example.com`, to a name server, such as `ns-NN.awsdns-NN.com`\.  
For more information, see [Name server](https://en.wikipedia.org/wiki/Name_server) on Wikipedia\.

Service locator \(SRV\) record  
An SRV record maps a subdomain, such as `service.example.com`, to a service address with values for priority, weight, and port number\. Telephony or instant messaging are a couple of the services typically associated with SRV records\.  
For example, in the Lightsail DNS zone, you want to direct traffic for `service.example.com` to `1 10 5269 xmpp-server.example.com`\. You would create an SRV record with a priority of `1`, a weight of `10`, a port number of `5269`, and a "maps to" address of `xmpp-server.example.com`\.  
For more information, see [SRV Record](https://en.wikipedia.org/wiki/SRV_record) on Wikipedia\.

Text \(TXT\) record  
A TXT record maps a subdomain to plaintext\. You create TXT records to confirm ownership of your domain to a service provider\.  
For example, in the Lightsail DNS zone, you want to respond with `23223a30-7f1d-4sx7-84fb-31bdes7csdbb` when the `_amazonchime.example.com` hostname is queried\. You would create a TXT record with a subdomain value of `_amazonchime` and a "responds with" value of `23223a30-7f1d-4sx7-84fb-31bdes7csdbb`\.  
For more information, see [TXT Record](https://en.wikipedia.org/wiki/TXT_record) on Wikipedia\.