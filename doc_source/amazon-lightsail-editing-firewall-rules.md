# Adding and editing instance firewall rules in Amazon Lightsail<a name="amazon-lightsail-editing-firewall-rules"></a>

 *Last updated: February 22, 2022* 

You can add rules to the IPv4 and IPv6 firewalls of your Amazon Lightsail instance to control the traffic that is allowed to connect to it\. When you add a firewall rule, you can specify the application layer protocol type, protocol, ports, and the source IPv4 or IPv6 addresses that are allowed to connect to your instance\. For more information about firewalls, see [Firewall and ports in Amazon Lightsail](understanding-firewall-and-port-mappings-in-amazon-lightsail.md)\.

**Contents**
+ [Adding and editing firewall rules](#firewall-adding-rules)
+ [Deleting instance firewall rules](#firewall-deleting-rules)
+ [More information about firewalls](#adding-firewall-rules-more-information)

## Adding and editing instance firewall rules<a name="firewall-adding-rules"></a>

Complete the following steps to add or edit firewall rules in the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Instances** tab\.

1. Choose the name of the instance for which you want to add or edit a firewall rule\.

1. Choose the **Networking** tab on your instance's management page\.

   The **Networking** tab displays your instance's public and private IP addresses, and the configured IPv4 or IPv6 firewalls for your instance\.
**Note**  
The IPv6 firewall is displayed only if you have enabled IPv6 for the instance\. For more information, see [Enabling or disabling IPv6 in Amazon Lightsail](amazon-lightsail-enable-disable-ipv6.md)\.

1. Complete one of the following steps depending on whether the source IP for the rule is an IPv4 or IPv6 address:
   + To add an IPv4 firewall rule, scroll down to the **IPv4 Firewall** section of the page, and choose **Add rule**\.
   + To add an IPv6 firewall rule, scroll down to the **IPv6 Firewall** section of the page and choose **Add rule**\.

   You can also choose **Edit** \(pencil icon\) next to an existing rule on either of the firewalls to edit it\.

1. Choose an application layer protocol type in the **Application** drop\-down menu\.

   When you choose an application layer protocol type, a set of protocol and port presets are specified for you\. Example values are **Custom**, **All TCP**, **All UDP**, **Custom ICMP**, **SSH**, and **RDP**\.

   You can configure the following optional settings depending on the application layer protocol type you select:
   + \(Optional\) If you choose the **Custom** option, then you can select a value in the **Protocol** drop\-down menu\. The available protocol values are **TCP** and **UDP**\.

     You can also enter a single port number or range of port numbers \(for example, 7000\-8000\) in the **Port** field\.
   + \(Optional\) If you choose the **Custom ICMP** option, then you can specify an ICMP type in the **Type** field, and an ICMP code in the **Code** field\. For more information about ICMP types and codes, see [Control Messages](https://en.wikipedia.org/wiki/Internet_Control_Message_Protocol#Control_messages) on *Wikipedia*\.
**Note**  
When you add an ICMP rule to the IPv6 firewall of your instance using the Lightsail console, the rule is automatically configured to use ICMPv6\. For more information, see [Internet Control Message Protocol for IPv6](https://en.wikipedia.org/wiki/Internet_Control_Message_Protocol_for_IPv6) on *Wikipedia*\.
   + \(Optional\) Select **Restrict to IP address** to restrict access for the specified protocol and port to a specific IP address or range of IP addresses\. Leave this option unselected to allow all IP addresses for the specified protocol and port\.

     You can enter a single IPv4 address \(for example, `203.0.113.1`\), or a range of IPv4 addresses\. The range can be specified using a dash \(for example, `192.0.2.0-192.0.2.255`\) or in CIDR block notation \(for example, `192.0.2.0/24`\)\. For more information about CIDR block notation, see [Classless Inter\-Domain Routing](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing#CIDR_notation) on *Wikipedia*\.
   + \(Optional\) If you choose the **SSH** or **RDP** application layer protocol type, and then choose **Restrict to IP address**, you can choose **Allow Lightsail browser SSH/RDP** to allow connection to your instance using the browser\-based SSH and RDP clients available in the Lightsail console\. Leave this option unselected to block access through those browser\-based clients\.

1. Choose **Create** to add the rule to the firewall\.

   The firewall rule is added after a few moments\.

## Deleting instance firewall rules<a name="firewall-deleting-rules"></a>

Complete the following steps to delete instance firewalls rule in the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Instances** tab\.

1. Choose the name of the instance for which you want to delete a firewall rule\.

1. Choose the **Networking** tab on your instance's management page\.

1. Complete one of the following steps depending on whether the source IP for the rule is an IPv4 or IPv6 address:
   + To delete an IPv4 firewall rule, scroll down to the **IPv4 Firewall** section of the page, and choose **Delete** \(the trash icon\) next to an existing rule to delete it\.
   + To delete an IPv6 firewall rule, scroll down to the **IPv6 Firewall** section of the page, and choose **Delete** \(the trash icon\) next to an existing rule to delete it\.
**Important**  
Firewall rules affect only traffic that flows in through the public IP address of an instance\. It does not affect traffic that flows in through the private IP address of an instance, which can originate from Lightsail resources in your account, in the same AWS Region, or resources in a peered virtual private cloud \(VPC\), in the same AWS Region\. For example, if you delete the SSH rule \(TCP port 22\) from the instance firewall, other instances in the same Lightsail account, and in the same AWS Region, can continue to connect to it using SSH by specifying the private IP address of the instance\.

   The firewall rule is deleted after a few moments\.

## More information about firewalls<a name="adding-firewall-rules-more-information"></a>

The following are some articles to help you manage firewalls in Lightsail\.
+ [Firewall and ports in Amazon Lightsail](understanding-firewall-and-port-mappings-in-amazon-lightsail.md)
+ [Firewall rules reference](amazon-lightsail-firewall-rules-reference.md)