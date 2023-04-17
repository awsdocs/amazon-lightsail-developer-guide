# How internet traffic is routed to your website<a name="amazon-lightsail-internet-traffic-routing"></a>

 *Last updated: November 1, 2022* 

All computers on the internet, including smart phones, laptops, and website servers, communicate with one another by using unique strings of characters\. These strings, known as IP addresses, are in one of the following formats:
+ Internet Protocol version 4 \(IPv4\) format, such as 192\.0\.2\.44
+ Internet Protocol version 6 \(IPv6\) format, such as 2001:DB8::/32

When you open a browser and go to a website, you don't have to remember and enter a long string of characters like that\. Instead, you can enter a domain name like **example\.com** and still end up in the right place\. This is achieved through the Domain Name System \(DNS\), which functions as a directory that maps registered domain names to IP addresses\.

**Contents**
+ [Overview of how you configure Lightsail to route internet traffic for your domain](#internet-traffic-routing)
+ [How traffic is routed for your domain](#lightsail-traffic-routing)
+ [Next steps](#internet-traffic-routing-next-steps)

## Overview of how you configure Lightsail to route internet traffic for your domain<a name="internet-traffic-routing"></a>

This overview explains how to use Lightsail to register and configure a domain that routes internet traffic to your website or web application\. 

1. Register your domain name\. For an overview, see [Domain registration in Lightsail](amazon-lightsail-domain-registration.md)\.

1. After you register your domain name, Lightsail automatically creates a DNS zone that has the same name as the domain\.

1. The Lightsail console allows you to easily assign a domain to a Lightsail resource, such as an instance or load balancer\. You can also create DNS records in your DNS zone to route traffic to your resources\. Each record includes information about how you want to route traffic for your domain, such as the following:

   **Name**

   The name of the record corresponds with the domain name \(example\.com\) or subdomain name \(www\.example\.com, retail\.example\.com\)\. The name of every record in a DNS zone must end with the name of the DNS zone\. For example, if the name of the DNS zone is example\.com, all record names must end in example\.com\. 

   **Type**

   The record type usually depends on the type of resource that you want traffic to be routed to\. For example, to route traffic to an email server, you specify **MX** for **Type**\. To route traffic for your domain name to your Lightsail instance, you add an **A** record that points your domain name to the static IPv4 address of your instance, or a **AAAA** record that points to the IPv6 address of your instance\.

1. **Target**

   The target is where you want traffic to be routed to\. You can create alias records that route traffic to Lightsail instances, Lightsail container services, and other Lightsail resources\. For more information, see [DNS in Amazon Lightsail](understanding-dns-in-amazon-lightsail.md)\.

## How traffic is routed for your domain<a name="lightsail-traffic-routing"></a>

After you configure Lightsail to route your internet traffic to your resources, such as instances, load balancers, distributions, or container services, here’s what happens when someone requests content for **www\.example\.com**\.

1. A user opens a web browser, enters **www\.example\.com** in the address bar, and presses **Enter**\.

1. The request for **www\.example\.com** is routed to a DNS resolver, which is typically managed by the user's internet service provider \(ISP\)\. ISPs can be cable internet providers, DSL broadband providers, or corporate networks\.

1. The DNS resolver for the ISP forwards the request for **www\.example\.com** to a DNS root name server\. 

1. The DNS resolver forwards the request for **www\.example\.com** again, this time to one of the TLD name servers for **\.com** domains\. The name server for **\.com** domains responds to the request with the names of the four name servers that are associated with the **example\.com** domain\. 

   The DNS resolver caches \(stores\) the four name servers\. The next time someone browses to **example\.com**, the resolver skips steps 3 and 4 because it already has the name servers for **example\.com**\. The name servers are typically cached for two days\.

1. The DNS resolver chooses a name server and forwards the request for **www\.example\.com** to that name server\.

1. The name server looks in the **example\.com** DNS zone for the **www\.example\.com** record and gets the associated value, such as the IP address for a web server \(192\.0\.2\.44\)\. Then, the name server returns the IP address to the DNS resolver\.

1. The DNS resolver finally has the IP address that the user needs\. The resolver returns that value to the web browser\.

1. The web browser sends a request for **www\.example\.com** to the IP address that it got from the DNS resolver\. This is where your content is, for example, a web server running on an Lightsail instance or container service that's configured as a website endpoint\.

1. The web server or other resource at 192\.0\.2\.44 returns the web\-page for **www\.example\.com** to the web browser, and the web browser displays the page\.

## Next steps<a name="internet-traffic-routing-next-steps"></a>
+ [DNS in Amazon Lightsail](understanding-dns-in-amazon-lightsail.md)
+ [Point your domain to a Lightsail instance](amazon-lightsail-routing-to-instance.md)
+ [Point your domain to your Lightsail load balancer](add-alias-record-for-lightsail-load-balancer.md)
+ [Pointing your domains to your Amazon Lightsail distributions](amazon-lightsail-point-domain-to-distribution.md)