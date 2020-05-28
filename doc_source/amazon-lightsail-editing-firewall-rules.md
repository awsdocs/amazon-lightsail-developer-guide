# Adding and editing firewall rules in Amazon Lightsail<a name="amazon-lightsail-editing-firewall-rules"></a>

 *Last updated: May 7, 2020* 

You can add rules to the firewall for your Amazon Lightsail instance to control the traffic that is allowed to connect to it\. When you add a firewall rule, you can specify the application layer protocol type, protocol, ports, and the source IP addresses that are allowed to connect to your instance\. For more information about firewalls, see [Firewall and ports in Amazon Lightsail](understanding-firewall-and-port-mappings-in-amazon-lightsail.md)\.

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

   The **Networking** tab displays your instance's public and private IP addresses, and the configured firewall rules for your instance\.

1. Scroll down to the **Firewall** section of the page, and choose **Add rule**\.

   You can also choose **Edit** \(pencil icon\) next to an existing rule to edit it\.

1. Choose an application layer protocol type in the **Application** drop\-down menu\.

   When you choose an application layer protocol type, a set of protocol and port presets are specified for you\. Example values are **Custom rule**, **All TCP**, **All UDP**, **SSH**, and **RDP**\.

1. \(Optional\) If you choose the **Custom rule** option, then you can select a value in the **Protocol** drop\-down menu\.

   The available protocol values are **All**, **ICMP**, **TCP**, and **UDP**\.
**Note**  
Ping is the only communication supported through the ICMP protocol in Lightsail\. Choose the **Ping \(ICMP\)** application layer protocol type to configure ping for your instance\.

1. \(Optional\) If you choose the **Custom rule** option, then you can enter a single port number or range of port numbers \(for example, 7000\-8000\) in the **Port** field\.

1. \(Optional\) Select **Restrict to IP address** to restrict access for the specified protocol and port to a specific IP address or range of IP addresses\. Leave this option unselected to allow all IP addresses for the specified protocol and port\.

   You can enter a single IPv4 address \(for example, 203\.0\.113\.1\), or a range of IPv4 addresses\. The range can be specified using a dash \(for example, 192\.0\.2\.0\-192\.0\.2\.255\) or in CIDR block notation \(for example, 192\.0\.2\.0/24\)\. For more information about CIDR block notation, see [Classless Inter\-Domain Routing](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing#CIDR_notation) on *Wikipedia*\.

1. \(Optional\) If you chose the **SSH** or **RDP** application layer protocol type, then you can select **Allow Lightsail browser SSH/RDP** to allow connection to your instance using the browser\-based SSH and RDP clients available in the Lightsail console\. Leave this option unselected to block access through those browser\-based clients\.

1. Choose **Create** to add the rule to the firewall\.

   The firewall rule is added after a few moments\.

## Deleting instance firewall rules<a name="firewall-deleting-rules"></a>

Complete the following steps to delete instance firewalls rule in the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Instances** tab\.

1. Choose the name of the instance for which you want to delete a firewall rule\.

1. Choose the **Networking** tab on your instance's management page\.

1. Scroll down to the **Firewall** section of the page, and choose **Delete** \(the trash icon\) next to an existing rule to delete it\.

1. Choose **Yes** to delete the rule when asked to confirm your action\.

   The firewall rule is deleted after a few moments\.

## More information about firewalls<a name="adding-firewall-rules-more-information"></a>

The following are some articles to help you manage firewalls in Lightsail\.
+ [Firewall and ports in Amazon Lightsail](understanding-firewall-and-port-mappings-in-amazon-lightsail.md)
+ [Firewall rules reference](amazon-lightsail-firewall-rules-reference.md)