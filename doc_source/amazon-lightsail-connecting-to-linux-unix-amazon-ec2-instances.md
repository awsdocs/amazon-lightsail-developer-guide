# Connecting to a Linux or Unix instance in Amazon EC2 created from an Amazon Lightsail snapshot<a name="amazon-lightsail-connecting-to-linux-unix-amazon-ec2-instances"></a>

 *Last updated: January 13, 2018* 

After a Linux or Unix instance is created in Amazon Elastic Compute Cloud \(Amazon EC2\) from an Amazon Lightsail snapshot, you can connect to the instance via SSH similar to how you connected to the source Lightsail instance\. To authenticate to your instance, use either the default Lightsail key pair for the source instance’s AWS Region, or your own key pair\. This guide shows you how to connect to your Linux or Unix instance in EC2 using PuTTY\.

**Note**  
For more information about connecting to a Windows Server instance, see [Connecting to a Windows Server instance in Amazon EC2 created from an Amazon Lightsail snapshot](amazon-lightsail-connecting-to-windows-server-amazon-ec2-instances.md)\.

**Contents**
+ [Get the key for your instance](#get-the-key-linux-unix-instance)
+ [Get the public DNS address for your instance](#get-the-public-dns-address-for-your-linux-unix-instance)
+ [Download and install PuTTY](#download-and-install-putty)
+ [Configure the key with PuTTYgen](#configure-the-key-with-puttygen)
+ [Configure PuTTY to connect to your instance](#configure-putty-to-connect)
+ [Next steps](#connecting-to-linux-unix-instances-next-steps)

## Get the key for your instance<a name="get-the-key-linux-unix-instance"></a>

Get the correct key required to connect to your new Amazon EC2 instance\. The key that you need depends on how you connected to the source Lightsail instance\. You may have connected to the source Lightsail instance using one of the following methods:
+ **Using the default Lightsail key pair for the source instance’s Region** — Download the default private key from the **SSH keys** tab on the [Lightsail account page](https://lightsail.aws.amazon.com/ls/webapp/account/keys)\. For more information about the default Lightsail keys, see [SSH and connecting to your Lightsail instance](understanding-ssh-in-amazon-lightsail.md)\.
**Note**  
After you connect to your EC2 instance, we recommend removing the default Lightsail key from the instance and replacing it with your own key pair\. For more information, see [Securing your Linux or Unix instance in Amazon EC2 created from an Amazon Lightsail snapshot](amazon-lightsail-securing-linux-unix-amazon-ec2-instances.md)\.
+ **Using your own key pair** — Locate your private key and use it to connect to your Amazon EC2 instance\. Lightsail does not store your private key when you use your own key pair\. If you’ve lost your private key, you cannot connect to your Amazon EC2 instance\.

## Get the public DNS address for your instance<a name="get-the-public-dns-address-for-your-linux-unix-instance"></a>

Get the public DNS address for your Amazon EC2 instance, so that you can use it when configuring an SSH client, such as PuTTY, to connect to your instance\.

**To get the public DNS address for your instance**

1. Sign in to the [Amazon EC2 console](https://console.aws.amazon.com/ec2/)\.

1. Choose **Instances** from the left navigation pane\. 

1. Choose the running Linux or Unix instance that you want to connect to\.

1. In the lower pane, locate the **Public DNS** address for your instance\.

   This is the address that you will use when configuring an SSH client to connect to your instance\. Continue to the [Download and install PuTTY](#download-and-install-putty) section of this guide to learn how to download and install the PuTTY SSH client\.  
![\[An instance's public DNS in the Amazon EC2 console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ec2-public-dns.png)

## Download and install PuTTY<a name="download-and-install-putty"></a>

PuTTY is a free SSH client for Windows\. For more information about [PuTTY, see PuTTY: a free SSH and Telnet client](http://www.chiark.greenend.org.uk/~sgtatham/putty/)\. This website also describes the restrictions in countries where encryption isn't allowed\. If you already have PuTTY, you can skip to the following *Configure the key with PuTTYgen* section of this guide\.

[Download the PuTTY installer or executable file](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)\. We recommend using the latest version\. However, for information about which download to choose, see the [PuTTY documentation](http://www.chiark.greenend.org.uk/~sgtatham/putty/docs.html)\.

Continue to the [Configure the key with PuTTYgen](#configure-the-key-with-puttygen) section of this guide to configure the key with PuTTYgen\.

## Configure the key with PuTTYgen<a name="configure-the-key-with-puttygen"></a>

PuTTYgen generates pairs of public and private keys to be used with PuTTY\. This step is required to use the key file type \(\.PPK\) that PuTTY accepts\.

**To configure the key with PuTTYgen**

1. Start PuTTYgen\.

   For example, choose the **Windows Start** menu, choose **All Programs**, choose **PuTTY**, and choose **PuTTYgen**\.  
![\[PuTTY Key Generator.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/puttygen-key-generator.png)

1. Choose **Load**\.

   By default, PuTTYgen displays only files with the \.PPK extension\. To locate your \.PEM file, select the option to display files of all types\.  
![\[Load the Lightsail private key to the PuTTY Key Generator.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-putty-load-private-key.png)

1. Choose the default Lightsail key file \(\.PEM\) that you downloaded earlier in this guide, and then choose **Open**\.

1. After PuTTYgen confirms that you successfully imported the key, choose **OK**\.  
![\[PuTTY Key Generator notice.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-putty-puttygen-notice.png)

1. Choose **Save private key**, and then confirm that you don't want to save it with a passphrase\.

   If you create a passphrase as an extra measure of security, you must enter it every time you connect to your instance using PuTTY\.  
![\[Save your private key in the PuTTY Key Generator.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-putty-save-private-key.png)

1. Specify a name and a location to save your private key, and then choose **Save**\.

   PuTTYgen saves your new key file as a \.PPK file type\.

1. Close PuTTYgen\.

   Continue to the [Configure PuTTY to connect to your instance](#configure-putty-to-connect) section of this guide to use the new \.PPK file that you generated to configure PuTTY and connect to your Linux or Unix instance in Amazon EC2\.

## Configure PuTTY to connect to your instance<a name="configure-putty-to-connect"></a>

Configure PuTTY, now that you have all of the requirements to connect to your Linux or Unix instance using SSH\.

**To configure PuTTY to connect to your Linux or Unix instance**

1. Open PuTTY\.

   For example, choose the **Windows Start** menu, choose **All Programs**, choose **PuTTY**, and choose **PuTTY**\.

1. In the **Host Name** text box, enter the public DNS address for your instance that you obtained from the Amazon EC2 console earlier in this guide\.  
![\[PuTTY SSH client.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-putty-host-name.png)

1. Under the **Connection** section in the left navigation pane, choose **Data**\.

1. In the **Auto\-login username** text box, enter a user name to use when logging in to the instance\.  
![\[Instance user name in PuTTY.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-putty-login-details.png)

   Enter one of the following default user names depending on the blueprint of the source Lightsail instance:
   + Amazon Linux, FreeBSD, and openSUSE instances: `ec2-user`
   + CentOS instances: `centos`
   + Debian instances: `admin`
   + Ubuntu instances: `ubuntu`
   + "Certified by Bitnami" instances: `bitnami`
   + Plesk instances: `ubuntu`

1. Under the **Connection** section in the left navigation pane, expand **SSH**, and then choose **Auth**\.

1. Choose **Browse** to navigate to the \.PPK file that you created in the previous section of this guide, and then choose **Open**\.  
![\[PuTTY authentication parameters.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-putty-authentication-parameters.png)

1. Choose **Open** to connect to your instance, and then choose **Yes** to trust this connection in the future\.

   You should see a screen similar to the following if you've successfully connected to your instance:  
![\[PuTTY connected to an EC2 instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-putty-connected.png)

## Next steps<a name="connecting-to-linux-unix-instances-next-steps"></a>

Your new Linux or Unix instance in Amazon EC2 contains residual keys from the Lightsail service, if you use Amazon EC2 to create new instances from your exported snapshots\. We recommend removing these keys to enhance security for your new Amazon EC2 instance\. For more information, see [Securing your Linux or Unix instance in Amazon EC2 created from a Lightsail snapshot](amazon-lightsail-securing-linux-unix-amazon-ec2-instances.md)\.