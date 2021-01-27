# IP addresses in Amazon Lightsail<a name="understanding-public-ip-and-private-ip-addresses-in-amazon-lightsail"></a>

**Note**  
IP addresses enable resources in your Amazon Lightsail account to communicate with each other, and with resources over the internet\. Lightsail instances, container services, content delivery network \(CDN\) distributions, and load balancers support both the IPv4 and IPv6 addressing protocols\.

 *Last updated: January 12, 2021* 

You can communicate with your Lightsail instance, and other Lightsail resources, using their IP addresses\. For example, using the public IP address of your instance, you can check the network status of your instance \(using PING\), establish an SSH connection to your instance, and route traffic to your instance from a custom domain name\. There are many more things you can do with the IP address of your Lightsail resources\.

Lightsail instances, container services, CDN distributions, and load balancers support both the IPv4 and IPv6 addressing protocols\. These resources use the IPv4 addressing protocol by default; you can't disable this behavior\. You can optionally enable IPv6 for your instances, container services, CDN distributions, and load balancers\.

In this guide, we cover what you need to know about IP addresses in Lightsail\.

**Contents**
+ [Private and public IPv4 addresses for instances](#ipv4-addresses)
+ [Static IP addresses for instances](#static-ip-addresses-for-instances)
+ [IPv6 for instances, container services, CDN distributions, and load balancers](#ipv6-for-resources)

## Private and public IPv4 addresses for instances<a name="ipv4-addresses"></a>

When you create a Lightsail instance, it is assigned a public and a private IPv4 address\. The public IP address is accessible to the internet, while the private IP address is accessible only to resources in your Lightsail account in the same AWS Region\.

**Note**  
The private IP address of your instance can be accessible to other AWS resources in the same AWS Region, but outside of your Lightsail account, if you enable VPC peering\. For more information, see [Set up Amazon VPC peering to work with AWS resources outside of Amazon Lightsail](lightsail-how-to-set-up-vpc-peering-with-aws-resources.md)\.

The IP addresses of your instance are displayed in the following areas of the Lightsail console:
+ The following example shows the public IP address of an instance on the Lightsail home page\.  
![\[Instance IP addresses on the Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/lightsail-home-page-ip-addresses.png)
+ The following example shows the public and private IP addresses of an instance in the header area of the instance management page\.  
![\[Instance IP addresses in the header area of the instance management page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/lightsail-header-ip-addresses.png)
+ The following example shows the public and private IP addresses of an instance on the **Networking** tab of the instance management page\.  
![\[Instance IP addresses in the Networking tab of the instance management page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/lightsail-networking-tab-ip-addresses.png)

Keep the following in mind when using the IPv4 addresses of your instances:
+ The public IP address of your instance might change\. Give your instance an IP address that never changes by attaching a static IP to it\. For more information, see the [Static IP addresses for instances](#static-ip-addresses-for-instances) section of this guide\.
+ Lightsail uses IPv4 addresses by default\. However, You can optionally enable IPv6 for some Lightsail resources that were created before January 12, 2021\. Resources created on or after January 12, 2021, have IPv6 enabled by default\. For more information, see the [IPv6 for instances, container services, CDN distributions, and load balancers](#ipv6-for-resources) section of this guide\.
+ Add rules to your instance firewall to control the traffic that is allowed to connect to it\. For more information, see [Instance firewalls in Amazon Lightsail](understanding-firewall-and-port-mappings-in-amazon-lightsail.md)\.

## Static IPv4 addresses for instances<a name="static-ip-addresses-for-instances"></a>

The default public IPv4 address that is assigned to your instance when you create it will change when you stop and start your instance\. You can optionally create and attach a static IPv4 address to your instance\. The static IPv4 address replaces the default public IPv4 address of your instance, and it stays the same when you stop and start your instance\. For more information, see [Create a static IP and attach it to an instance in Amazon Lightsail](lightsail-create-static-ip.md)\.

After you create a static IP, and attach it to your instance, it is displayed in the following areas of the Lightsail console:
+ The following example shows the static IP address of an instance on the Lightsail home page\. The thumbtack icon signifies that the public IP address is static\.  
![\[Instance static IP address in the Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/lightsail-home-page-static-ip-address.png)
+ The following example shows the static IP address of an instance in the header area of the instance management page\. The thumbtack icon signifies that the public IP address is static\.  
![\[Instance static IP address in the header area of the instance management page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/lightsail-header-static-ip-address.png)
+ The following example shows the static IP address of an instance on the **Networking** tab of the instance management page\. The default public IP address is no longer listed, and it has been replaced by the static IP address\. The thumbtack icon signifies that the public IP address is static\.  
![\[Instance static IP address in the networking tab of the instance management page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/lightsail-networking-tab-static-ip-address.png)
+ You can view all of the static IPs that you've created by going to the Networking tab of the Lightsail home page as shown in the following example\.  
![\[All static IP addresses in the Networking tab of the Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/lightsail-all-static-ip-addresses.png)

## IPv6 for instances, container services, CDN distributions, and load balancers<a name="ipv6-for-resources"></a>

IPv6 is enabled by default for Lightsail instances, container services, CDN distributions, and load balancers created on or after January 12, 2021\. You can optionally enable IPv6 for those resources that were created before January 12, 2021\. When you enable IPv6 for a specific resource, Lightsail automatically assigns an IPv6 address to that resource; you cannot choose or specify the IPv6 address yourself\. For more information, see [Enabling or disabling IPv6 in Amazon Lightsail](amazon-lightsail-enable-disable-ipv6.md)\.

After you enable IPv6 for a resource, it is displayed in the following areas of the Lightsail console:
+ The following example shows the IPv6 address of an instance on the Lightsail home page\.  
![\[Instance IPv6 address in the Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/lightsail-home-page-ipv6-address.png)
+ The following example shows the IPv6 address of a resource in the header area of the resource's management page\.  
![\[Instance IPv6 address in the header area of the instance management page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/lightsail-header-ipv6-address.png)
+ The following example shows the IPv6 address of a resource on the Networking tab of the resource management page\.  
![\[Instance IPv6 address in the Networking tab of the instance management page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/lightsail-networking-ipv6-address.png)

Keep the following in mind when you enable and use IPv6 for your resources:
+ Your resources can communicate over IPv4 only, or over IPv4 and IPv6 \(in dual\-stack mode\) when you enable IPv6 for a resource\.
+ When you enable IPv6 for a resource, Lightsail automatically assigns an IPv6 address to that resource; you cannot choose or specify the IPv6 address yourself\. When you enable IPv6 for a resource, it begins accepting network traffic over the IPv6 protocol\.
+ The IPv6 address for an instance persists when you stop and start your instance\. It's released only when you delete your instance, or disable IPv6 for your instance\. You cannot get the IPv6 address back after you perform either of those actions\.
+ All IPv6 addresses that are assigned to your instances are public and reachable over the internet\. There are no private IPv6 addresses that are assigned to your instances\.
+ IPv4 and IPv6 addresses for instances are independent of each other; you must configure instance firewall rules separately for IPv4 and IPv6\. For more information, see [Instance firewalls in Amazon Lightsail](understanding-firewall-and-port-mappings-in-amazon-lightsail.md)\.
+ Not all instance blueprints available in Lightsail become aware of their IPv6 address automatically when it's enabled\. Instances that use the following blueprints require additional configuration steps after you enable IPv6 for them:
  + **cPanel** – For more information, see [Configuring IPv6 on cPanel instances in Amazon Lightsail](amazon-lightsail-configure-ipv6-on-cpanel.md)\.
  + **Debian 8** – For more information, see [Configuring IPv6 on Debian 8 instances in Amazon Lightsail](amazon-lightsail-configure-ipv6-on-debian.md)\.
  + **GitLab** – For more information, see [Configuring IPv6 on GitLab instances in Amazon Lightsail](amazon-lightsail-configure-ipv6-on-gitlab.md)\.
  + **Nginx** – For more information, see [Configuring IPv6 on Nginx instances in Amazon Lightsail](amazon-lightsail-configure-ipv6-on-nginx.md)\.
  + **Plesk** – For more information, see [Configuring IPv6 on Plesk instances in Amazon Lightsail](amazon-lightsail-configure-ipv6-on-plesk.md)\.
  + **Ubuntu 16** – For more information, see [Configuring IPv6 on Ubuntu 16 instances in Amazon Lightsail](amazon-lightsail-configure-ipv6-on-ubuntu-16.md)\.