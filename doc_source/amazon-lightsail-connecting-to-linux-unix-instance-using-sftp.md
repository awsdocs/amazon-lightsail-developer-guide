# Connecting to your Linux or Unix instance in Amazon Lightsail using SFTP<a name="amazon-lightsail-connecting-to-linux-unix-instance-using-sftp"></a>

 *Last updated: April 11, 2022* 

You can transfer files between your local computer and your Linux or Unix instance in Amazon Lightsail by connecting to your instance using SFTP \(SSH File Transfer Protocol\)\. To do this, you must get the private key for your instance, and then use it to configure the FTP client\. This tutorial shows you how to configure the FileZilla FTP client to connect to your instance\. These steps may also apply to other FTP clients\.

**Contents**
+ [Prerequisites](#connecting-to-linux-unix-instance-using-sftp-prerequisites)
+ [Get the SSH key for your instance](#get-the-ssh-key-for-your-instance)
+ [Configure FileZilla and connect to your instance](#configure-filezilla-and-connect-to-your-instance)

## Prerequisites<a name="connecting-to-linux-unix-instance-using-sftp-prerequisites"></a>

Complete the following prerequisites if you haven't already:
+ Download and install FileZilla on your local computer\. For more information, see the following download options:
  + [Download FileZilla Client for Windows](https://filezilla-project.org/download.php?platform=win64)
  + [Download FileZilla Client for Mac OS X](https://filezilla-project.org/download.php?platform=osx)
  + [Download FileZilla Client for Linux](https://filezilla-project.org/download.php?platform=linux)
+ Get the public IP address of your instance\. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/), and then copy the public IP address that is displayed next to your instance, as shown in the following example:  
![\[The public IP for an instance in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-instance-public-ip.png)

## Get the SSH key for your instance<a name="get-the-ssh-key-for-your-instance"></a>

Complete the following steps to get the default private key for the AWS Region of your instance, which is required to connect to your instance using FileZilla\.

**Note**  
If you’re using your own key pair, or you created a key pair using the Lightsail console, locate your own private key and use it to connect to your instance\. Lightsail does not store your private key when you upload your own key or create a key pair using the Lightsail console\. You cannot connect to your instance using SFTP without your private key\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Choose **Account** on the top navigation bar, and then choose **Account** from the drop\-down\.

1. Choose the **SSH Keys** tab\.

1. Scroll down to the **Default keys** section of the page\.

1. Choose **Download** next to the default private key for the region where your instance is located\.  
![\[SSH keypairs in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-ssh-key-pairs.png)

1. Save your private key in a secured location on your local drive\.

## Configure FileZilla and connect to your instance<a name="configure-filezilla-and-connect-to-your-instance"></a>

Complete the following steps to configure FileZilla to connect to your instance\.

1. Open FileZilla\.

1. Choose **File**, **Site Manager**\.

1. Choose **New site**, then give your site a name\.  
![\[New site configuration in FileZilla.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-filezilla-sftp-new-site.png)

1. In the **Protocol** dropdown, choose **SFTP – SSH File Transfer Protocol**\.

1. In the **Host** text box, enter or paste your instance’s public IP address\.

1. In the **Logon Type** dropdown, choose **Key File**\.

1. In the **User** text box, enter one of the following default user names depending on your instance operating system:
   + Amazon Linux, Amazon Linux 2, FreeBSD, and openSUSE instances: `ec2-user`
   + CentOS instances: `centos`
   + Debian instances: `admin`
   + Ubuntu instances: `ubuntu`
   + Bitnami instances: `bitnami`
   + Plesk instances: `ubuntu`
   + cPanel & WHM instances: `centos`
**Important**  
If you are using a different user name than the default user names listed here, then you might need to give the user write permissions to your instance\.

1. Next to the **Key File** text box, choose **Browse**\.  
![\[SFTP configuration in FileZilla.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-filezilla-sftp-configuration.png)

1. Locate the private key file that you downloaded from the Lightsail console earlier in this procedure, and then choose **Open**\.
**Note**  
If you are using Windows, change the default file type to **All files** when searching for your pem file\.  
![\[File extention setting in FileZilla open dialog\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-filezilla-file-extention-setting.png)

1. Choose **Connect**\.

1. You may see a prompt similar to the following example, indicating that the host key is unknown\. Choose **OK** to acknowledge the prompt and connect to your instance\.  
![\[Unknown host key in FileZilla.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-filezilla-unknown-hostkeypng)

   You are successfully connected if you see status messages similar to the following example:  
![\[FileZilla successfully connected to an instance in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-filezilla-sftp-successfully-connected.png)

   For more information about using FileZilla, including how to transfer files between your local computer and your instance, see the [FileZilla Wiki page](https://wiki.filezilla-project.org/Using)\.