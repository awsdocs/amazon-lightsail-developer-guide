# OpenVPN with GUI install on Ubuntu 18.04 LTS Lightsail instance <a name="install-openvpn-ubuntu-18-lightsail"></a>

 *Last updated: February 19,2020* 

In this guide we will show how to quick perform installation of openvpn server on Ubuntu 18.04 LTS Lightsail instance.This instance will be helpfull as backup option to access your VPC. Make sure to enable [lightsail peering to your VPC](https://github.com/awsdocs/amazon-lightsail-developer-guide/blob/master/doc_source/lightsail-how-to-set-up-vpc-peering-with-aws-resources.md)\.
Note, that you can use static and dynamic IP. We cover here dynamic IP case.

## Create an Amazon Lightsail instance <a name="how-to-create-amazon-lightsail-instance-virtual-private-server-vps"></a>

1. [Create an Amazon Lightsail instance](https://raw.githubusercontent.com/awsdocs/amazon-lightsail-developer-guide/master/doc_source/how-to-create-amazon-lightsail-instance-virtual-private-server-vps.md)\. Select Linux/Unix-> OS only -> Ubuntu 18.04 LTS\.

2. Allow ports **SSH 22, HTTPS 443, UDP 1194**\. 

3. Connect to your instance and run commands bellow or specify launch script during instance creation\:

\#**!\/bin\/bash**\
**sudo su \-**\
**apt\-get update \&\& apt\-get upgrade all \-y**

4. Login to your instance using SSH. Please see [Set up SSH for your Linux\/Unix\-based Lightsail instances](https://github.com/awsdocs/amazon-lightsail-developer-guide/blob/master/doc_source/lightsail-how-to-set-up-ssh.md)\.

5. Run the script bellow\:

\#**!\/bin\/bash**\
**sudo su \-**\
**apt\-get install lighttpd**\
 **wget https\:\/\/raw.githubusercontent.com\/theonemule\/simple\-openvpn\-server\/master\/openvpn.sh**\
 **sh .\openvpn.sh \-\-adminpassword\=\<YOUR\_PASSWORD\> \-\-host\=\<INSTANCE\_HOSTNAME\>**

For options on openvpn.sh and further steps please check [post](https://www.blaize.net/2017/04/a-simple-openvpn-server-with-a-web-interface/)\.

6. Once you can connect to VPN disable ports **SSH 22, HTTPS 443**\.
