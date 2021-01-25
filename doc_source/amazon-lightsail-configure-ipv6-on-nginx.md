# Configuring IPv6 on Nginx instances in Amazon Lightsail<a name="amazon-lightsail-configure-ipv6-on-nginx"></a>

 *Last updated: January 12, 2021* 

All instances in Amazon Lightsail have a public and a private IPv4 address assigned to them by default\. You can optionally enable IPv6 for your instances to have a public IPv6 address assigned to them\. For more information, see [IP addresses in Amazon Lightsail](understanding-public-ip-and-private-ip-addresses-in-amazon-lightsail.md) and [Enabling or disabling IPv6 in Amazon Lightsail](amazon-lightsail-enable-disable-ipv6.md)\.

After you enable IPv6 for an instance that uses the Nginx blueprint, you must perform an additional set of steps to make the instance aware of its IPv6 address\. In this guide, we show you the additional steps that you must perform for Nginx instances\.

## Prerequisites<a name="ipv6-nginx-prerequisites"></a>

Complete the following prerequisites if you haven't already:
+ Create an Nginx instance in Lightsail\. For more information, see [Create an Amazon Lightsail instance](how-to-create-amazon-lightsail-instance-virtual-private-server-vps.md)\.
+ Enable IPv6 for your Nginx instance\. For more information, see [Enabling or disabling IPv6 in Amazon Lightsail](amazon-lightsail-enable-disable-ipv6.md)\.
**Note**  
New Nginx instances created on or after January 12, 2021, have IPv6 enabled by default when they are created in the Lightsail console\. You must complete the following steps in this guide to configure IPv6 on your instance even if IPv6 was enabled by default when you created your instance\.

## Configure IPv6 on a Nginx instance<a name="configure-ipv6-nginx"></a>

Complete the following procedure to configure IPv6 on a Nginx instance in Lightsail\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. In the **Instances** tab of the Lightsail home page, locate the Ubuntu 16 instance that you wish to configure, and choose the browser\-based SSH client icon to connect to it using SSH\.  
![\[Browser-based SSH client incon in the Lightsail home page.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-nginx-ssh-quick-connect.png)

1. After you're connected to your instance, enter the following command to determine if your instance is listening to IPv6 requests over port 80\. Be sure to replace *<IPv6Address>* with the IPv6 address assigned to your instance\.

   ```
   curl -g -6 'http://[<IPv6Address>]'
   ```

   Example:

   ```
   curl -g -6 'http://[2001:0db8:85a3:0000:0000:8a2e:0370:7334]'
   ```

   You will see a response similar to one of the following examples:
   + If your instance is not listening to IPv6 requests over port 80, then you will see a response with a **Failed to connect** error message\. You should continue to complete steps 4 through 9 of this procedure\.  
![\[IPv6 not configured on the instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-nginx-ssh-curl-result-not-configured.png)
   + If your instance is listening to IPv6 requests over port 80, then you will see a response with the HTML code of the home page of your instance as shown in the following example\. You should stop here; you do not need to complete steps 4 through 9 of this procedure because your instance is already configure to for IPv6\.  
![\[IPv6 configured on the instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-nginx-ssh-curl-result-configured.png)

1. Enter the following command to open the nginx\.conf configuration file using Vim\.

   ```
   sudo vim /opt/bitnami/nginx/conf/nginx.conf
   ```

1. Press `I` to enter insert mode in Vim\.

1. Add the following text below the `listen 80;` text that is already in the file\. You might need to scroll down in Vim to see the section where you need to add the text\.

   ```
   listen [::]:80;
   ```

   The file will look like the following when done:  
![\[Nginx configuration file on the instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-nginx-ssh-nginx-conf-file.png)

1. Press the **Esc** key to exit insert mode in Vim, then type `:wq!` and press **Enter** to save your edits \(write\) and quit Vim\.

1. Enter the following command to restart the services of your instance\.

   ```
   sudo /opt/bitnami/ctlscript.sh restart
   ```

1. Enter the following command to determine if your instance is listening to IPv6 requests over port 80\. Be sure to replace *<IPv6Address>* with the IPv6 address assigned to your instance\.

   ```
   curl -g -6 'http://[<IPv6Address>]'
   ```

   Example:

   ```
   curl -g -6 'http://[2001:0db8:85a3:0000:0000:8a2e:0370:7334]'
   ```

   You will see a response similar to the following example\. If your instance is listening to IPv6 requests over port 80, then you will see a response with the HTML code of the home page of your instance\.  
![\[IPv6 configured on the instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/a7664053563006144d6133a21b463972/images/lightsail-nginx-ssh-curl-result-configured.png)