# Configuring IPv6 on Debian 8 instances in Amazon Lightsail<a name="amazon-lightsail-configure-ipv6-on-debian"></a>

 *Last updated: January 12, 2021* 

All instances in Amazon Lightsail have a public and a private IPv4 address assigned to them by default\. You can optionally enable IPv6 for your instances to have a public IPv6 address assigned to them\. For more information, see [IP addresses in Amazon Lightsail](understanding-public-ip-and-private-ip-addresses-in-amazon-lightsail.md) and [Enabling or disabling IPv6 in Amazon Lightsail](amazon-lightsail-enable-disable-ipv6.md)\.

After you enable IPv6 for an instance that uses the Debian 8 blueprint, you must perform an additional set of steps to make the instance aware of its IPv6 address\. In this guide, we show you the additional steps that you must perform for Debian 8 instances\.

## Prerequisites<a name="ipv6-debian-8-prerequisites"></a>

Complete the following prerequisites if you haven't already:
+ Create a Debian 8 instance in Lightsail\. For more information, see [Create an Amazon Lightsail instance](how-to-create-amazon-lightsail-instance-virtual-private-server-vps.md)\.
+ Enable IPv6 for your Debian 8 instance\. For more information, see [Enabling or disabling IPv6 in Amazon Lightsail](amazon-lightsail-enable-disable-ipv6.md)\.
**Note**  
New Debian instances created on or after January 12, 2021, have IPv6 enabled by default when they are created in the Lightsail console\. You must complete the following steps in this guide to configure IPv6 on your instance even if IPv6 was enabled by default when you created your instance\.

## Configure IPv6 on a Debian 8 instance<a name="configure-ipv6-debian-8"></a>

Complete the following procedure to configure IPv6 on a Debian 8 instance in Lightsail\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. In the **Instances** tab of the Lightsail home page, locate the Debian 8 instance that you wish to configure, and choose the browser\-based SSH client icon to connect to it using SSH\.  
![\[Browser-based SSH client icon in the Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-debian-ssh-quick-connect.png)

1. After you're connected to your instance, enter the following command to view the IP addresses configured on your instance\.

   ```
   ip addr
   ```

   You will see a response similar to one of the following examples:
   + If your instance *does not* recognize its IPv6 address, then you will not see it listed in the response\. You should continue to complete steps 4 through 9 of this procedure\.  
![\[IPv6 not configured on the instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-debian-ssh-ip-addr-ipv6-not-configured.png)
   + If your instance does recognize its IPv6 address, then you will see it listed in the response with a `scope global` as shown in this example\. You should stop here; you do not need to complete steps 4 through 9 of this procedure because your instance is already configure to recognize its IPv6 address\.  
![\[IPv6 configured on the instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-debian-ssh-ip-addr-ipv6-configured.png)

1. Enter the following command to open the `interfaces` configuration file using Nano\.

   ```
   sudo nano /etc/network/interfaces
   ```

1. Add the following line of text to the end of the file\.

   ```
   iface eth0 inet6 dhcp
   ```

   The file will look like the following when done:  
![\[Interfaces configuration file on the instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-debian-ssh-interfaces-file.png)

1. Press the **Ctrl\+Esc** keys to exit Nano\.

1. Press **Y** when asked if you would like to save the modified buffer, then press **Enter** to save to the existing interfaces configuration file\.

1. Enter the following command to restart the networking service of your instance\.

   ```
   sudo systemctl restart networking
   ```

   You might need to wait a few more minutes to allow your instance to recognize its IPv6 address after you restart the networking service of your instance\.

1. Enter the following command to view the IP addresses configured on your instance, and confirm that it is now recognizing its assigned IPv6 address\.

   ```
   ip addr
   ```

   You will see a response similar to the following example\. If your instance does recognize its IPv6 address, then you will see it listed in the response with a label of `scope global` as shown in this example\.  
![\[IPv6 configured on the instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-debian-ssh-ip-addr-ipv6-configured.png)