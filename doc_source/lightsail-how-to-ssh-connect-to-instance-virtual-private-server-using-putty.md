# Connect to your Linux/Unix\-based Lightsail instance using PuTTY<a name="lightsail-how-to-ssh-connect-to-instance-virtual-private-server-using-putty"></a>

 *Last updated: January 13, 2020* 

In addition to the browser\-based SSH terminal in Lightsail, you can also connect to your Linux\-based instance using an SSH client such as PuTTY\. To learn how to set up PuTTY, see [Download and set up PuTTY to connect using SSH in Lightsail](lightsail-how-to-set-up-putty-to-connect-using-ssh.md)\.

**Note**  
To connect to a Windows\-based instance using RDP, see [Connect to your Windows\-based Lightsail instance](connect-to-your-windows-based-instance-using-amazon-lightsail.md)\.

You can use the default private key that Lightsail provides, a new private key from Lightsail, or another private key that you use with another service\.

1. Start PuTTY \(for example, from the **Start** menu, choose **All Programs**, **PuTTY**, **PuTTY**\)\.

1. Choose **Load**, and then find your saved session\.

   If you don't have a saved session, see [Step 4: Finish configuring PuTTY with your private key and instance information](lightsail-how-to-set-up-putty-to-connect-using-ssh.md)\.

1. Log in using one of the following default user names depending on your instance operating system:
   + Amazon Linux, FreeBSD, and openSUSE instances: `ec2-user`
   + CentOS instances: `centos`
   + Debian instances: `admin`
   + Ubuntu instances: `ubuntu`
   + Certified by Bitnami instances: `bitnami`
   + Plesk instances: `ubuntu`

   For more information about instance operating systems, see [Choosing an image in Lightsail](compare-options-choose-lightsail-instance-image.md)\.

To learn more about SSH, see [SSH and connecting to your Amazon Lightsail instance](understanding-ssh-in-amazon-lightsail.md)\.