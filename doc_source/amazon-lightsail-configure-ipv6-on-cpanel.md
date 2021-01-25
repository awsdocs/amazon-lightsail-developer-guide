# Configuring IPv6 on cPanel instances in Amazon Lightsail<a name="amazon-lightsail-configure-ipv6-on-cpanel"></a>

 *Last updated: January 12, 2021* 

All instances in Amazon Lightsail have a public and a private IPv4 address assigned to them by default\. You can optionally enable IPv6 for your instances to have a public IPv6 address assigned to them\. For more information, see [IP addresses in Amazon Lightsail](understanding-public-ip-and-private-ip-addresses-in-amazon-lightsail.md) and [Enabling or disabling IPv6 in Amazon Lightsail](amazon-lightsail-enable-disable-ipv6.md)\.

After you enable IPv6 for an instance that uses the cPanel & WHM blueprint, you must perform an additional set of steps to make the instance aware of its IPv6 address\. In this guide, we show you the additional steps that you must perform for cPanel & WHM instances\.

## Prerequisites<a name="ipv6-cpanel-prerequisites"></a>

Complete the following prerequisites if you haven't already:
+ Create an cPanel & WHM instance in Lightsail\. For more information, see [Create an Amazon Lightsail instance](how-to-create-amazon-lightsail-instance-virtual-private-server-vps.md)\.
+ Configure your cPanel & WHM instance\. For more information, see [Quick start guide: cPanel & WHM on Amazon Lightsail](amazon-lightsail-quick-start-guide-cpanel.md)\.
**Important**  
Make sure that all software updates and required system reboots are performed before continuing with the steps in this guide\.
+ Enable IPv6 for your cPanel & WHM instance\. For more information, see [Enabling or disabling IPv6 in Amazon Lightsail](amazon-lightsail-enable-disable-ipv6.md)\.
**Note**  
New cPanel & WHM instances created on or after January 12, 2021, have IPv6 enabled by default when they are created in the Lightsail console\. You must complete the following steps in this guide to configure IPv6 on your instance even if IPv6 was enabled by default when you created your instance\.

## Configure IPv6 on a cPanel & WHM instance<a name="configure-ipv6-cpanel"></a>

Complete the following procedure to configure IPv6 on a cPanel & WHM instance in Lightsail\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. In the **Instances** tab of the Lightsail home page, locate the cPanel & WHM instance that you wish to configure, and choose the browser\-based SSH client icon to connect to it using SSH\.  
![\[Browser-based SSH client icon in the Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-cpanel-ssh-quick-connect.png)

1. After you're connected to your instance, enter the following command to open the `ifcfg-eth0` network interface configuration file using Nano\.

   ```
   sudo nano /etc/sysconfig/network-scripts/ifcfg-eth0
   ```

1. Add the following text to the file if they are not already there\.

   ```
   IPV6INIT=yes
   IPV6_AUTOCONF=yes
   ```

   The result should look like the following example\.  
![\[Network interfaces configuration file on the instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-cpanel-network-interface-configuration-file.png)

1. Press **CTRL\+C** on your keyboard to exit the file\.

1. Press **Y** when prompted to save the modified buffer, then press **Enter** to save to the existing file\. This saves the edits you made to the `ifcfg-eth0` network interface configuration file\.

1. Close the browser\-based SSH window and toggle back to the Lightsail console\.

1. In the **Instances** tab of the Lightsail home page, choose the actions menu \(⋮\) for the cPanel & WHM instance, and choose **Reboot**\.  
![\[Instance reboot option on the Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-cpanel-instance-reboot.png)

   Wait a few minutes for your instance to be done rebooting before continuing to the next step\.

1. In the **Instances** tab of the Lightsail home page, make note of the IPv6 address assigned to your cPanel & WHM instance\.  
![\[Instance IPv6 address on the Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-cpanel-ipv6-address.png)

1. Open a new browser tab, and sign in to the Web Host Manager \(WHM\) of your cPanel & WHM instance\.

1. In the left navigation pane of the WHM console, choose **Basic WebHost Manager Setup**\.  
![\[Basic WebHost Manager Setup option in the navigation pane.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-cpanel-basic-webhost-manager-menu-option.png)

1. In the **All** tab, find the text for the **IPv6 address to use**, then enter the IPv6 address assigned to your instance\. You should have made note of the IPv6 address assigned to your instance from step 9 of this procedure\.  
![\[IPv6 address of the instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-cpanel-ipv6-address-entry.png)

1. Scroll to the bottom for the page and choose **Save Changes**\.

1. In the left navigation pane of the WHM console, choose **Tweak Settings**\.  
![\[Tweak settings option in the navigation pane.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-cpanel-tweak-settings.png)

1. In the **All** tab, scroll down to find the **Listen on IPv6 Addresses** setting, and set it to **On**\.  
![\[Listen to IPv6 address option.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-cpanel-listen-to-ipv6-addresses.png)

1. Scroll to the bottom for the page and choose **Save**\.

1. Toggle back to the Lightsail console\.

1. In the **Instances** tab of the Lightsail home page, choose the actions menu \(⋮\) for the cPanel & WHM instance, and choose **Reboot**\.  
![\[Instance reboot option on the Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-cpanel-instance-reboot.png)

   Wait a few minutes for your instance to be done rebooting before continuing to the next step\.

1. Choose the browser\-based SSH client icon for the cPanel & WHM instance to connect to it using SSH\.  
![\[Browser-based SSH client icon in the Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-cpanel-ssh-quick-connect.png)

1. After you're connected to your instance, enter the following command to view the IP addresses configured on your instance, and confirm that it is now recognizing its assigned IPv6 address\.

   ```
   ip addr
   ```

   You will see a response similar to the following example\. If your instance does recognize its IPv6 address, then you will see it listed in the response with a label of **scope global** as shown in this example\.  
![\[IPv6 configured on the instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-cpanel-ssh-ip-addr-ipv6-configured.png)

1. Enter the following command to confirm that your instance is able to ping an IPv6 address\.

   ```
   ping6 ipv6.google.com -c 6
   ```

   The result should look like the following example, which confirms that your instance is able to ping IPv6 addresses\.  
![\[Ping6 result.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-cpanel-ssh-ping6-result.png)