# Instance firewalls in Amazon Lightsail<a name="understanding-firewall-and-port-mappings-in-amazon-lightsail"></a>

**Note**  
A firewall in Amazon Lightsail controls the traffic allowed to connect to your instance at the protocol and port level\. When you create a new instance, its firewall is preconfigured with a set of default rules that allow basic access to your instance\. Edit your instance's firewall, at any time, by adding and deleting firewall rules to allow traffic to reach your instance\.

 *Last updated: May 7, 2020* 

The firewall in the Amazon Lightsail console acts as a virtual firewall that controls the traffic allowed to connect to your instance\. Each instance that you create in Lightsail has its own firewall\. Each firewall contains a set of rules that filter traffic coming into the instance\. Edit your instance's firewall, at any time, by adding and deleting rules to allow or restrict traffic\. 

**Contents:**
+ [Understanding Lightsail firewalls](#understanding-firewalls)
+ [Creating firewall rules](#creating-firewall-rules)
+ [Specifying protocols](#specifying-protocols)
+ [Specifying ports](#specifying-ports)
+ [Specifying application layer protocol types](#specifying-application-layer-protocol-types)
+ [Specifying source IP addresses](#specifying-source-ip-addresses)
+ [Default Lightsail firewall rules](#default-lightsail-firewall-rules)
+ [More information about firewalls](#firewall-more-information)

## Understanding Lightsail firewalls<a name="understanding-firewalls"></a>

All internet traffic into and out of your Lightsail instance passes through its firewall\. A Lightsail firewall controls the internet traffic that is allowed to flow into your instance\. However, it does not control the traffic that flows out of it—the firewall allows all outbound traffic\.

Firewall rules are always permissive; you can't create rules that deny access\. You add rules to your firewall to allow traffic to reach your instance\. When you add a rule to your firewall, you specify the protocol to use, the port to open, and the IP addresses that are allowed to connect to your instance, as shown in the following example\. You can also specify an application layer protocol type, which is a preset that specifies the protocol and port range for you based on the service that you plan to use on your instance\.

![\[Plugins menu on the WordPress administration dashboard.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/firewall-rule-example.png)

Firewall rules, and their configurable parameters are explained in the next few sections of this guide\.

## Creating firewall rules<a name="creating-firewall-rules"></a>

Create a firewall rule to enable a client to establish a connection with your instance, or with an application running on your instance\. For example, to enable all web browsers to connect to the WordPress application on your instance, you configure a firewall rule that enables the Transmission Contact Protocol \(TCP\) over port 80 from any IP address\. If this rule is already configured on your instance's firewall, then you can delete it to block web browsers from being able to connect to the WordPress application on your instance\.

You can also enable an SSH client to connect to your instance, to perform administrative tasks on the server, by configuring a firewall rule that enables TCP over port 22 only from the IP address of the computer that needs to establish a connection\. In this case, you would not want to allow any IP address to establish an SSH connection to your instance; since doing so could lead to a security risk on your instance\.

**Note**  
The firewall rule examples described in this section may exist in your instance's firewall by default\. For more information, see [Default firewall rules](#default-lightsail-firewall-rules) later in this guide\.

If there is more than one rule for a specific port, we apply the most permissive rule\. For example, if you add a rule that allows access to TCP port 22 \(SSH\) from IP address 192\.0\.2\.1\. Then, you add another rule that allows access to TCP port 22 from everyone\. As a result, everyone has access to TCP port 22\.

## Specifying protocols<a name="specifying-protocols"></a>

A protocol is the format in which data is transmitted between two computers\. Lightsail allows you to specify the following protocols in a firewall rule:
+ **Transmission Contact Protocol \(TCP\)** is primarily used for establishing and maintaining a connection between clients and the application running on your instance, until the exchange of data is complete\. It is a widely used protocol, and one which you might often specify in your firewall rules\. TCP guarantees that no transmitted data is missing, and that all of the data that's sent makes it to the intended recipient\. It is ideal use is for network applications that need high reliability, and for which transmission time is relatively less critical, such as web browsing, financial transactions, and text messaging\. These use\-cases will lose significant value if parts of the data is lost\.
+ **User Datagram Protocol \(UDP\)** is primarily used for establishing low\-latency and loss\-tolerating connections between clients and the application running on your instance\. It is ideal use is for network applications in which perceived latency is critical, such as gaming, voice, and video communications\. These use\-cases can suffer some data loss without adversely affecting perceived quality\.
+ **Internet Control Message Protocol \(ICMP\)** is primarily used to diagnose network communication issues, such as to determine if data is reaching its intended destination in a timely manner\. It is ideal use is for the Ping utility, which you can use to test the speed of the connection between your local computer and your instance\. It reports how long it takes data to reach your instance and come back to your local computer\.
+ **All** is used to allow all protocol traffic to flow into your instance\. Specify this protocol when you're unsure which protocol to specify\. This includes all internet protocols; not just the ones specified above\. For more information, see [Protocol Numbers](https://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml) on the *Internet Assigned Numbers Authority website*\.

## Specifying ports<a name="specifying-ports"></a>

Similar to physical ports on your computer, which allow your computer to communicate with peripherals like your keyboard and mouse, network ports serve as internet communications endpoints for your instance\. When a computer seeks to connect with your instance, it will expose a port to establish the communication\.

The ports that you can specify in a firewall rule can range from 0 to 65535\. When you create a firewall rule to enable a client to establish a connection with your instance, you specify the protocol that will be used \(covered earlier in this guide\), and the port numbers through which the connection can be established\. You can also specify the IP addresses that are allowed to establish a using the protocol and port; this is covered in the next section of this guide\.

Here are some of the commonly used ports along with the services that use them:
+ Data transfer over File Transfer Protocol \(FTP\) uses port 20\.
+ Command control over FTP uses port 21\.
+ Secure Shell \(SSH\) uses port 22\.
+ Telnet remote login service, and unencrypted text messages uses port 23\.
+ Simple Mail Transfer Protocol \(SMTP\) email routing uses port 25\.
+ Domain Name System \(DNS\) service uses port 53\.
+ Hypertext Transfer Protocol \(HTTP\) used by web browsers to connect to websites uses port 80\.
+ Post Office Protocol \(POP3\) used by email clients to retrieve email from a server uses port 110\.
+ Network News Transfer Protocol \(NNTP\) uses port 119\.
+ Network Time Protocol \(NTP\) uses port 123\.
+ Internet Message Access Protocol \(IMAP\) used to manage digital mail uses port 143\.
+ Simple Network Management Protocol \(SNMP\) uses port 161\.
+ HTTP Secure \(HTTPS\) HTTP over TLS/SSL used by web browsers to establish an encrypted connection to websites uses port 443\.

For more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml) on the *Internet Assigned Numbers Authority website*\.

## Specifying application layer protocol types<a name="specifying-application-layer-protocol-types"></a>

You can specify an application layer protocol type when you create a firewall rule, which are presets that specify the rule's protocol and port range for you based on the service that you want to enable on your instance\. This way, you don't have to search for the common protocol and ports to use for services like SSH, RDP, HTTP, and others\. You can simply choose those application layer protocol types, and the protocol and port is specified for you\. If you prefer to specify your own protocol and port, then you can choose the **Custom rule** application layer protocol type, which gives you control of those parameters\.

**Note**  
You can specify the application layer protocol type only by using the Lightsail console\. You cannot specify the application layer protocol type using the Lightsail API, AWS Command Line Interface \(AWS CLI\), or SDKs\.

The following application layer protocol types are available in the Lightsail console:
+ **Custom rule** – Choose this option to specify your own protocol and ports\.
+ **All protocols** – Choose this option to specify all protocols, and specify your own ports\.
+ **All TCP** – Choose this option to use the TCP protocol but you're unsure of which port to open\. This enables the TCP over all ports \(0\-65535\)\.
+ **All UDP** – Choose this option to use the UDP protocol but you're unsure of which port to open\. This enables the UDP over all ports \(0\-65535\)\.
+ **DNS** – Choose this option when you want to enable DNS on your instance\. This enables TCP and UDP over ports 53\.
+ **HTTP** – Choose this option when you want to enable web browsers to connect to a website that is hosted on your instance\. This enables TCP over port 80\.
+ **HTTPS** – Choose this option when you want to enable web browsers to establish an encrypted connection to a website that is hosted on your instance\. This enables TCP over port 443\.
+ **MySQL/Aurora** – Choose this option to enable a client to connect to a MySQL or Aurora database hosted on your instance\. This enables TCP over port 3306\. 
+ **Oracle\-RDS** – Choose this option to enable a client to connect to an Oracle or RDS database hosted on your instance\. This enables TCP over port 1521\.
+ **Ping \(ICMP\)** – Choose this option to enable your instance to respond to requests using the Ping utility\. This enables ICMP type 8 \(echo\) and code \-1 \(all codes\)\.
+ **RDP** – Choose this option to enable an RDP client to connect to your instance\. This enables TCP over port 3389\.
+ **SSH** – Choose this option to enable an SSH client to connect to your instance\. This enables TCP over port 22\.

## Specifying source IP addresses<a name="specifying-source-ip-addresses"></a>

By default, firewall rules allow all IP addresses to connect to your instance through the specified protocol and port\. This is ideal for traffic such as web browsers over HTTP and HTTPS\. However, this poses a security risk for traffic such as SSH and RDP, since you would not want to allow all IP addresses to be able to connect to your instance using those applications\. For that reason, you can choose to restrict restrict a firewall rule to an IP address or range of IP addresses\. You can specify a single IPv4 address \(for example, 203\.0\.113\.1\), or a range of IPv4 addresses\. In the Lightsail console, the range can be specified using a dash \(for example, 192\.0\.2\.0\-192\.0\.2\.255\) or in CIDR block notation \(for example, 192\.0\.2\.0/24\)\. For more information about CIDR block notation, see [Classless Inter\-Domain Routing](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing) on *Wikipedia*\.

## Default Lightsail firewall rules<a name="default-lightsail-firewall-rules"></a>

When you create a new instance, its firewall is preconfigured with the following set of default rules that allow basic access to your instance\. The default rules are different depending on the type of instance that you create\. These rules are listed as application, protocol, port, and source IP address \(for example, application \- protocol \- port \- source IP address\)\.

**Amazon Linux, CentOS, Debian, FreeBSD, openSUSE, and Ubuntu \(base operating systems\)**  
SSH \- TCP \- 22 \- all IP addresses  
HTTP \- TCP \- 80 \- all IP addresses

**WordPress, Ghost, Joomla\!, and Drupal \(CMS applications\)**  
SSH \- TCP \- 22 \- all IP addresses  
HTTP \- TCP \- 80 \- all IP addresses  
HTTPS \- TCP \- 443 \- all IP addresses

**LAMP, Django, Node\.js, MEAN, GitLab, and LEMP/Nginx \(development stacks\)**  
SSH \- TCP \- 22 \- all IP addresses  
HTTP \- TCP \- 80 \- all IP addresses  
HTTPS \- TCP \- 443 \- all IP addresses

**Magento \(eCommerce application\)**  
SSH \- TCP \- 22 \- all IP addresses  
HTTP \- TCP \- 80 \- all IP addresses  
HTTPS \- TCP \- 443 \- all IP addresses

**Redmine \(project management application\)**  
SSH \- TCP \- 22 \- all IP addresses  
HTTP \- TCP \- 80 \- all IP addresses  
HTTPS \- TCP \- 443 \- all IP addresses

**Plesk \(hosting stack\)**  
SSH \- TCP \- 22 \- all IP addresses  
HTTP \- TCP \- 80 \- all IP addresses  
HTTPS \- TCP \- 443 \- all IP addresses  
Custom \- TCP \- 53 \- all IP addresses  
Custom \- UDP \- 53 \- all IP addresses  
Custom \- TCP \- 8443 \- all IP addresses  
Custom \- TCP \- 8447 \- all IP addresses

**Windows Server 2016 and 2012 R2**  
SSH \- TCP \- 22 \- all IP addresses  
HTTP \- TCP \- 80 \- all IP addresses  
RDP \- TCP \- 3389 \- all IP addresses

**SQL Server Express 2016**  
SSH \- TCP \- 22 \- all IP addresses  
HTTP \- TCP \- 80 \- all IP addresses  
RDP \- TCP \- 3389 \- all IP addresses

## More information about firewalls<a name="firewall-more-information"></a>

The following are some articles to help you manage firewalls in Lightsail\.
+ [Adding and editing firewall rules in Amazon Lightsail](amazon-lightsail-editing-firewall-rules.md)
+ [Firewall rules reference](amazon-lightsail-firewall-rules-reference.md)