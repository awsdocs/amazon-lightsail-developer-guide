# Understanding public network ports and firewall settings in Amazon Lightsail<a name="understanding-firewall-and-port-mappings-in-amazon-lightsail"></a>

 *Last updated: January 13, 2020* 

**Note**  
When you create a Lightsail instance, some network ports are open by default\. When a port is open, your instance can accept public network connections\. You can change the network port settings for your Lightsail instance on the **Networking** tab of your instance management page\.

The firewall and port settings are listed in the **Networking** tab of your instance's management page in the Amazon Lightsail console\. Choose **Edit rules** or **Add another** to change or create rules\.

![\[Networking tab on the manage instance page\]](https://s3-us-west-2.amazonaws.com/parkside-localized-docs-devo/v1/en_us/b3f6d19f6c5a2810c4336f10d978ee98/images/amazon-lightsail-manage-instance-page-networking-tab.png)

## Application layer protocol types<a name="understanding-firewall-and-port-mappings-in-amazon-lightsail-application-types"></a>

The following application layer protocol types are available in Lightsail\. For more general information, see [Application layer](https://en.wikipedia.org/wiki/Application_layer) on Wikipedia\.

**All TCP**  
Transmission Control Protocol \(TCP\) provides reliable, ordered, and error\-checked delivery of streamed data between applications running on hosts communicating on an IP network\. If your application doesn't require reliable data stream service, use User Datagram Protocol \(UDP\) instead\.

**Custom**  
You can also define a custom rule to apply to your protocol\. For example you might want to create a custom TCP rule that permits access via the port you used when you created your database instance, such as port 3306 for MySQL\.

**DNS**  
The Domain Name System \(DNS\) maintains the domain name hierarchy and provides translation services between the hierarchy and the address spaces\. Internet name servers and a communication protocol implement the DNS\. A DNS name server is a server that stores the DNS records for a domain\. A DNS name server responds with answers to queries against its database\.

**DNS \(TCP\)**  
The TCP application layer for the Domain Name System \(DNS\)\.

**DNS \(UDP\)**  
User Datagram Protocol \(UDP\) application layer for the DNS\. With UDP, computer applications can send messages \(or *datagrams*\) to other hosts on an Internet Protocol \(IP\) network\. Prior communications are not required to set up transmission channels or data paths\. Applications that don't require reliable data stream service can use UDP, which provides a connectionless datagram service that emphasizes reduced latency over reliability\. If you do require reliable data stream service, use TCP instead\.

**HTTP**  
Hypertext transfer protocol \(HTTP\) is an application protocol for distributed, collaborative, hypermedia information systems\. HTTP is the foundation of data communication for the World Wide Web\. For more general information, see [Application layer](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) on Wikipedia\.

**HTTPS**  
HTTPS \(also called HTTP over TLS, HTTP over SSL, and HTTP Secure\) is a protocol for secure communication over a computer network\. HTTPS consists of communication over HTTP within a connection encrypted by Transport Layer Security \(TLS\) or its predecessor, Secure Sockets Layer \(SSL\)\. The main motivation for HTTPS is authentication of the visited website and protection of the privacy and integrity of the exchanged data\.

**MySQL/Aurora**  
A TCP rule that accepts traffic between the specified port on your Lightsail instance and a MySQL or Aurora database\.

**Oracle\-RDS**  
A TCP rule that accepts traffic between the specified port on your Lightsail instance and an Oracle or RDS database\.

**PostgreSQL**  
A TCP rule that accepts traffic between the specified port on your Lightsail instance and a PostgreSQL database\.

**SSH**  
Secure Shell \(SSH\) is a cryptographic network protocol for operating network services securely over an unsecured network\. Lightsail uses SSH to connect to instances securely by matching authenticated users to a remote server\.

## Transport layer protocol types<a name="understanding-firewall-and-port-mappings-in-amazon-lightsail-protocols"></a>

The following transport layer protocol types are available in Lightsail\.

**All**  
All transport layer protocol types\. For more general information, see [Transport layer](https://en.wikipedia.org/wiki/Transport_layer) on Wikipedia\.

**TCP**  
Transmission Control Protocol \(TCP\) provides reliable, ordered, and error\-checked delivery of streamed data between applications running on hosts communicating by an IP network\. If you have an application that doesn't require reliable data stream service, use UDP instead\.

**UDP**  
With User Datagram Protocol \(UDP\), computer applications can send messages \(or *datagrams*\) to other hosts on an Internet Protocol \(IP\) network\. Prior communications are not required to set up transmission channels or data paths\. Applications that don't require reliable data stream service can use UDP, which provides a connectionless datagram service that emphasizes reduced latency over reliability\. If you do require reliable data stream service, use TCP instead\.

## Default public network ports open for specific instance images<a name="understanding-firewall-and-port-mappings-in-amazon-lightsail-default-port-mappings-for-instance-images"></a>

Each Lightsail image \(or *blueprint*\) has a default set of network ports that are open to the public\. The following list provides network port details\.

**Amazon Linux, CentOS, Debian, FreeBSD, openSUSE, and Ubuntu \(base operating systems\)**  
SSH \- TCP \- 22  
HTTP \- TCP \- 80

**WordPress, Ghost, Joomla\!, and Drupal \(CMS applications\)**  
SSH \- TCP \- 22  
HTTP \- TCP \- 80  
HTTPS \- TCP \- 443

**LAMP, Django, Node\.js, MEAN, GitLab, and LEMP/Nginx \(development stacks\)**  
SSH \- TCP \- 22  
HTTP \- TCP \- 80  
HTTPS \- TCP \- 443

**Magento \(e\-Commerce application\)**  
SSH \- TCP \- 22  
HTTP \- TCP \- 80  
HTTPS \- TCP \- 443

**Redmine \(project management application\)**  
SSH \- TCP \- 22  
HTTP \- TCP \- 80  
HTTPS \- TCP \- 443

**Plesk \(hosting stack\)**  
SSH \- TCP \- 22  
HTTP \- TCP \- 80  
HTTPS \- TCP \- 443  
Custom \- TCP \- 53  
Custom \- UDP \- 53  
Custom \- TCP \- 8443  
Custom \- TCP \- 8447

**Windows Server 2016 and 2012 R2**  
SSH \- TCP \- 22  
HTTP \- TCP \- 80  
RDP \- TCP \- 3389

**SQL Server Express 2016**  
SSH \- TCP \- 22  
HTTP \- TCP \- 80  
RDP \- TCP \- 3389