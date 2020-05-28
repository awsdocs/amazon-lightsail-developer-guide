# Firewall rules reference<a name="amazon-lightsail-firewall-rules-reference"></a>

 *Last updated: May 7, 2020* 

You can add rules to an Amazon Lightsail instance's firewall that reflects the role of the instance\. For example, an instance that's configured as a web server needs firewall rules that allow inbound HTTP and HTTPS access\. A database instance needs rules that allow access for the type of database, such as access over port 3306 for MySQL\. For more information about firewalls, see [Firewall and ports in Amazon Lightsail](understanding-firewall-and-port-mappings-in-amazon-lightsail.md)

This guide provides examples of the kinds of firewall rules that you can add to an instance firewall for specific kinds of access\. The rules are listed as application, protocol, port, and source IP address \(for example, application \- protocol \- port \- source IP address\), unless otherwise stated\.

**Contents**
+ [Web server rules](#firewall-web-server-rules)
+ [Rules to connect to your instance from your computer](#firewall-connect-to-instance)
+ [Database server rules](#firewall-database-server-rules)
+ [DNS server rules](#firewall-dns-server)
+ [SMTP email](#firewall-smtp)
+ [More information about firewalls](#rules-reference-more-information)

## Web server rules<a name="firewall-web-server-rules"></a>

The following inbound rules allow HTTP and HTTPS access\.

**Note**  
Some Lightsail instances have the following firewall rules configured by default\. For more information, see [Firewall and ports in Amazon Lightsail](understanding-firewall-and-port-mappings-in-amazon-lightsail.md)\.

**HTTP**  
HTTP \- TCP \- 80 \- all IP addresses

**HTTPS**  
HTTPs \- TCP \- 443 \- all IP addresses

## Rules to connect to your instance from your computer<a name="firewall-connect-to-instance"></a>

To connect to your instance, you add a rule that allows SSH access \(for Linux instances\) or RDP access \(for Windows instances\)\.

**Note**  
All Lightsail instances have either of the following firewall rules configured by default\. For more information, see [Firewall and ports in Amazon Lightsail](understanding-firewall-and-port-mappings-in-amazon-lightsail.md)\.

**SSH**  
SSH \- TCP \- 22 \- The public IP address of your computer, or a range of IP addresses \(in CIDR block notation\) in your local network

**RDP**  
RDP \- TCP \- 3389 \- The public IP address of your computer, or a range of IP addresses \(in CIDR block notation\) in your local network

## Database server rules<a name="firewall-database-server-rules"></a>

The following inbound rules are examples of rules that you might add for database access, depending on what type of database you're running on your instance\.

**SQL Server**  
Custom \- TCP \- 1433 \- The public IP address of your computer, or a range of IP addresses \(in CIDR block notation\) in your local network

**MySQL/Aurora**  
MySQL/Aurora \- TCP \- 3306 \- The public IP address of your computer, or a range of IP addresses \(in CIDR block notation\) in your local network

**PostgreSQL**  
PostgreSQL \- TCP \- 5432 \- The public IP address of your computer, or a range of IP addresses \(in CIDR block notation\) in your local network

**Oracle\-RDS**  
Oracle\-RDS \- TCP \- 1521 \- The public IP address of your computer, or a range of IP addresses \(in CIDR block notation\) in your local network

**Amazon Redshift**  
Custom \- TCP \- 5439 \- The public IP address of your computer, or a range of IP addresses \(in CIDR block notation\) in your local network

## DNS server rules<a name="firewall-dns-server"></a>

If you've set up your instance as a DNS server, you must ensure that TCP and UDP traffic can reach your DNS server over port 53\.

**DNS \(TCP\)**  
DNS \(TCP\) \- TCP \- 53 \- The IP address of a computer, or a range of IP addresses \(in CIDR block notation\) in your local network

**DNS \(UDP\)**  
DNS \(UDP\) \- UDP \- 53 \- The IP address of a computer, or a range of IP addresses \(in CIDR block notation\) in your local network

## SMTP email<a name="firewall-smtp"></a>

To enable SMTP on your instance, you must configure the following firewall rule\.

**Important**  
After configuring the following rule, you must also configure reverse DNS for your instance\. Otherwise, your email may be limited over TCP port 25\. For more information, see [Configuring reverse DNS for an email server on your Amazon Lightsail instance](amazon-lightsail-configuring-reverse-dns.md)\.

**SMTP**  
Custom \- TCP \- 25 \- The IP addresses of the hosts that communicate with your instance

## More information about firewalls<a name="rules-reference-more-information"></a>

The following are some articles to help you manage firewalls in Lightsail\.
+ [Firewall and ports in Amazon Lightsail](understanding-firewall-and-port-mappings-in-amazon-lightsail.md)
+ [Adding and editing firewall rules in Amazon Lightsail](amazon-lightsail-editing-firewall-rules.md)