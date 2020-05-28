# Connecting to a Windows Server instance in Amazon EC2 created from an Amazon Lightsail snapshot<a name="amazon-lightsail-connecting-to-windows-server-amazon-ec2-instances"></a>

 *Last updated: November 28, 2018* 

After your new Windows Server instance is created in Amazon Elastic Compute Cloud \(Amazon EC2\), you can connect to it using Remote Desktop Protocol \(RDP\)\. This is similar to how you connected to the source Amazon Lightsail instance\. Connect to your EC2 instance using the default Lightsail key pair for the source instance’s AWS Region\. This guide shows you how to connect to your Windows Server instance using Microsoft Remote Desktop Connection\.

**Note**  
For more information about connecting to a Linux or Unix instance, see [Connecting to a Linux or Unix instance in Amazon EC2 created from an Amazon Lightsail snapshot](amazon-lightsail-connecting-to-linux-unix-amazon-ec2-instances.md)\.

**Contents**
+ [Get the key for your instance](#get-the-key-windows-instance)
+ [Get the public DNS address for your instance](#get-the-public-dns-address-for-your-windows-instance)
+ [Get the password for your Windows Server instance](#get-the-password-for-your-windows-instance)
+ [Configure Remote Desktop Connection to connect to your Windows Server instance](#configure-remote-desktop-connection)
+ [Next steps](#connecting-to-windows-server-amazon-ec2-instances-next-steps)

## Get the key for your instance<a name="get-the-key-windows-instance"></a>

Your Windows Server instance in Amazon EC2 uses the default Lightsail key pair for the source instance’s Region to retrieve the default administrator password\.

Download the default private key from the **SSH keys** tab on the [Lightsail account page](https://lightsail.aws.amazon.com/ls/webapp/account/keys)\. For more information about the default Lightsail SSH keys, see [SSH and connecting to your Lightsail instance](understanding-ssh-in-amazon-lightsail.md)\.

**Note**  
After you connect to your EC2 instance, we recommend changing the administrator password for your Windows Server instance in Amazon EC2\. It removes the association between the default Lightsail key pair and your Windows Server instance in Amazon EC2\. For more information, see [Securing a Windows Server instance in Amazon EC2 created from an Amazon Lightsail snapshot](amazon-lightsail-securing-windows-server-amazon-ec2-instances.md)\.

## Get the public DNS address for your instance<a name="get-the-public-dns-address-for-your-windows-instance"></a>

Get the public DNS address for your Amazon EC2 instance, so that you can use it when configuring an RDP client, such as Microsoft Remote Desktop Connection, to connect to your instance\.

**To get the public DNS address for your instance**

1. Sign in to the [Amazon EC2 console](https://console.aws.amazon.com/ec2/)\.

1. Choose **Instances** from the left navigation pane\. 

1. Choose the running Windows Server instance that you want to connect to\.

1. In the lower pane, locate the **Public DNS** address for your instance\.

   This is the address that you use when configuring an RDP client to connect to your instance\. Continue to the [Get the password for your Windows Server instance](#get-the-password-for-your-windows-instance) section of this guide to learn how to get the default administrator password for your Windows Server instance in Amazon EC2\.  
![\[An instance's public DNS in the Amazon EC2 console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ec2-public-dns.png)

## Get the password for your Windows Server instance<a name="get-the-password-for-your-windows-instance"></a>

Get the password for your Windows Server instance from the Amazon EC2 console\. You need this password to sign in to your Windows Server instance when connecting to it through RDP\.

**To get the password for your Windows Server instance**

1. Sign in to the [Amazon EC2 console](https://console.aws.amazon.com/ec2/)\.

1. From the left navigation pane, choose **Instances**\.

1. Choose the Windows Server instance that you want to connect to\.

1. Choose **Actions**, then choose **Get Windows Password**\.  
![\[Getting the Windows Server default administrator password in the Amazon EC2 console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ec2-get-windows-password.png)

1. At the prompt, choose **Browse** and open the default private key file that you downloaded from Lightsail earlier in this guide\.

1. Choose **Decrypt Password**\.  
![\[Decrypting the Windows default administrator password in the Amazon EC2 console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ec2-decrypt-password.png)

   The password is displayed on the screen, as well as the public DNS and user name\. Copy the password to your clipboard so that you can use it in the following [Configure Remote Desktop Connection to connect to your Windows Server instance](#configure-remote-desktop-connection) section of this guide\. Highlight the password, and press **Ctrl\+C** if you’re using Windows, or **Cmd\+C** if you’re using macOS\.  
![\[Decrypted Windows default administrator password in the Amazon EC2 console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ec2-decrypted-password.png)

   Continue to the [Configure Remote Desktop Connection to connect to your Windows Server instance](#configure-remote-desktop-connection) section of this guide to learn how to configure Remote Desktop Connection to connect to your Windows Server instance in Amazon EC2\.

## Configure Remote Desktop Connection to connect to your Windows Server instance<a name="configure-remote-desktop-connection"></a>

Remote Desktop Connection is an RDP client that comes pre\-installed on most Windows operating systems\. Use it to graphically connect to your Windows Server instance in Amazon EC2\.

**To configure Remote Desktop Connection to connect to your Windows Server instance**

1. Open Remote Desktop Connection\.

   For example, choose the **Windows Start** menu, then search for **Remote Desktop Connection**\.

1. In the **Computer** text box, enter the public DNS address for your Windows Server instance in Amazon EC2 obtained earlier in this guide\.

1. Choose **Show Options** to view additional options\.

1. Enter `Administrator` into the **User name** text box\.  
![\[Microsoft Remote Desktop Connection.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-rdc-configuration.png)

1. Choose **Connect** to connect to your Windows Server instance\.

1. At the Windows Security prompt, enter the password for your Windows Server instance into the **Password** text box, then choose **OK**\.  
![\[Microsoft Remote Desktop Connection password prompt.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-rdc-password.png)

1. At the Remote Desktop Connection prompt, chose **Yes** to connect\.  
![\[Microsoft Remote Desktop Connection security prompt.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-rdc-certificate-errors.png)

   You should see a screen similar to the following if you've successfully connected to your instance:  
![\[Microsoft Remote Desktop Connection connected to instance.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-rdc-connected.png)

## Next steps<a name="connecting-to-windows-server-amazon-ec2-instances-next-steps"></a>

We recommend changing the administrator password for your Windows Server instance in Amazon EC2\. It removes the association between the default Lightsail key pair and your Windows Server instance in Amazon EC2\. For more information, see [Securing a Windows Server instance in Amazon EC2 created from an Amazon Lightsail snapshot](amazon-lightsail-securing-windows-server-amazon-ec2-instances.md)\.