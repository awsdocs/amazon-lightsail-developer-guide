# Enabling and disabling IPv6 for your resources in Amazon Lightsail<a name="amazon-lightsail-enable-disable-ipv6"></a>

 *Last updated: January 12, 2021* 

IPv6 is enabled by default for Lightsail instances, container services, CDN distributions, and load balancers created on or after January 12, 2021\. You can optionally enable IPv6 for those resources that were created before January 12, 2021\. In this guide, we show you how to enable or disable IPv6\. For more information about IPv6, see [IP addresses in Amazon Lightsail](understanding-public-ip-and-private-ip-addresses-in-amazon-lightsail.md)\.

**Contents**
+ [Considerations for using IPv6](#ipv6-considerations)
+ [Enable IPv6](#enable-ipv6)
+ [Disable IPv6](#disable-ipv6)

## Considerations for using IPv6<a name="ipv6-considerations"></a>

IPv6 became available in Lightsail on January 12, 2021; therefore, you might need to manually enable or disable IPv6 for some of your resources according to the following guidelines:
+ Instances, CDN distributions, and load balancers created *before* January 12 have IPv6 disabled until you enable it\. However, instances, CDN distributions, and load balancers created *after* January 12 have IPv6 enabled when they are created\.
+ Container services created *before* or *after* January 12 have IPv6 enabled\.
+ IPv6 can be manually enabled or disabled for instances, CDN distributions, and load balancers at any time\. It cannot be disabled for container services\.

Keep the following in mind when you enable and use IPv6:
+ Your resources can communicate over IPv4 only, or over IPv4 and IPv6 \(in dual\-stack mode\) when you enable IPv6 for a resource\.
+ When you enable IPv6 for an instance, Lightsail automatically assigns an IPv6 address to that instance; you cannot choose or specify the IPv6 address yourself\. When you enable IPv6 for a container service, CDN distribution, or load balancer, that resource will begin accepting internet traffic over IPv6\.
+ The IPv6 address for an instance persists when you stop and start your instance\. It's released only when you delete your instance, or disable IPv6 for your instance\. You cannot get the IPv6 address back after you perform either of those actions\.
+ All IPv6 addresses that are assigned to your instances are public and reachable over the internet\. There are no private IPv6 addresses that are assigned to your instances\.
+ IPv4 and IPv6 addresses for instances are independent of each other; you must configure instance firewall rules separately for IPv4 and IPv6\. For more information, see [Instance firewalls in Amazon Lightsail](understanding-firewall-and-port-mappings-in-amazon-lightsail.md)\.
+ Not all instance blueprints available in Lightsail become aware of their IPv6 address automatically when IPv6 enabled\. Instances that use the following blueprints require additional configuration steps after you enable IPv6 for them:
  + **cPanel** – For more information, see [Configuring IPv6 on cPanel instances in Amazon Lightsail](amazon-lightsail-configure-ipv6-on-cpanel.md)\.
  + **Debian 8** – For more information, see [Configuring IPv6 on Debian 8 instances in Amazon Lightsail](amazon-lightsail-configure-ipv6-on-debian.md)\.
  + **GitLab** – For more information, see [Configuring IPv6 on GitLab instances in Amazon Lightsail](amazon-lightsail-configure-ipv6-on-gitlab.md)\.
  + **Nginx** – For more information, see [Configuring IPv6 on Nginx instances in Amazon Lightsail](amazon-lightsail-configure-ipv6-on-nginx.md)\.
  + **Plesk** – For more information, see [Configuring IPv6 on Plesk instances in Amazon Lightsail](amazon-lightsail-configure-ipv6-on-plesk.md)\.
  + **Ubuntu 16** – For more information, see [Configuring IPv6 on Ubuntu 16 instances in Amazon Lightsail](amazon-lightsail-configure-ipv6-on-ubuntu-16.md)\.

## Enable IPv6<a name="enable-ipv6"></a>

Complete the following procedure to enable IPv6 for instances, CDN distributions, and load balancers\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Complete one of the following steps depending on the resource for which you want to enable IPv6:
   + To enable IPv6 for an instance, choose the **Instances** tab on the Lightsail home page, and then choose the name of the instance for which you want to enable IPv6\.
   + To enable IPv6 for a CDN distribution or a load balancer, choose the **Networking** tab on the Lightsail home page, and then choose the name of the CDN distribution or load balancer for which you want to enable IPv6\.

1. Choose the **Networking** tab in the resource's management page\.

1. In the **IPv6 Networking** section of the page, choose the toggle to enable IPv6 for the resource\.  
![\[Enable IPv6 in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/lightsail-enable-ipv6.png)

   Be aware of the following items after you enable IPv6 for a resource:
   + If you enable IPv6 for a CDN distribution or load balancer, then that resource begins accepting IPv6 traffic\. If you enable IPv6 for an instance, then an IPv6 address is assigned to it, and the IPv6 firewall becomes available, as shown in the following example\.  
![\[The instance IPv6 firewall in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/lightsail-ipv6-firewall.png)
   + Instances that use the following blueprints require additional steps after enabling IPv6 to ensure the instance becomes aware of its new IPv6 address:
     + **cPanel** – For more information, see [Configuring IPv6 on cPanel instances in Amazon Lightsail](amazon-lightsail-configure-ipv6-on-cpanel.md)\.
     + **Debian 8** – For more information, see [Configuring IPv6 on Debian 8 instances in Amazon Lightsail](amazon-lightsail-configure-ipv6-on-debian.md)\.
     + **GitLab** – For more information, see [Configuring IPv6 on GitLab instances in Amazon Lightsail](amazon-lightsail-configure-ipv6-on-gitlab.md)\.
     + **Nginx** – For more information, see [Configuring IPv6 on Nginx instances in Amazon Lightsail](amazon-lightsail-configure-ipv6-on-nginx.md)\.
     + **Plesk** – For more information, see [Configuring IPv6 on Plesk instances in Amazon Lightsail](amazon-lightsail-configure-ipv6-on-plesk.md)\.
     + **Ubuntu 16** – For more information, see [Configuring IPv6 on Ubuntu 16 instances in Amazon Lightsail](amazon-lightsail-configure-ipv6-on-ubuntu-16.md)\.
   + If you have a registered domain name directing traffic to you instance, container service, CDN distribution, or load balancer, then make sure to create an IPv6 address record \(AAAA\) in the DNS of your domain to route IPv6 traffic to your resource\.

## Disable IPv6<a name="disable-ipv6"></a>

Complete the following procedure to disable IPv6 for instances, CDN distributions, and load balancers\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Complete one of the following steps depending on the resource for which you want to disable IPv6:
   + To disable IPv6 for an instance, choose the **Instances** tab on the Lightsail home page, and then choose the name of the instance for which you want to disable IPv6\.
   + To disable IPv6 for a CDN distribution or a load balancer, choose the **Networking** tab on the Lightsail home page, and then choose the name of the CDN distribution or load balancer for which you want to disable IPv6\.

1. Choose the **Networking** tab in the resource's management page\.

1. In the **IPv6 Networking** section of the page, choose the toggle to disable IPv6 for the resource\.  
![\[Disable IPv6 in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/lightsail-disable-ipv6.png)