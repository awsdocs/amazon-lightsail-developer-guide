# SSH and connecting to your Lightsail instance<a name="understanding-ssh-in-amazon-lightsail"></a>

**Note**  
Secure Shell \(SSH\) is a protocol for securely connecting to a virtual private server \(or Lightsail *instance*\)\. SSH works by creating a public key and a private key that match the remote server to an authorized user\. Using that key pair, you can connect to your Lightsail instance using a browser\-based SSH terminal\.

 *Last updated: October 23, 2020* 

In Amazon Lightsail, you can choose from three options in each region to set up SSH as you create your Lightsail instance \(a virtual private server\):
+ **Default**\. Choose the default key pair and connection method to use the Lightsail console to connect securely to your instance\. Lightsail provides a browser\-based SSH terminal, so you won't even need to set up a client\! You can also download the key to use with an SSH client such as PuTTY\.
+ **Create new**\. When creating your instance, choose **Change key pair**, and then choose **Create new** to get a new public and private key pair for connecting\. This enables you to use a client such as PuTTY to connect securely to your instance\. In this option, Lightsail creates and manages the SSH keys\.
+ **Upload new**\. When creating your instance, choose **Change key pair**, and then choose **Upload new**\. This enables you to use an SSH client such as PuTTY to connect securely to your instance\. In this option, you are using an existing SSH key that you might also use with another service, such as GitHub\.

To learn more about SSH, see [Secure SHell](https://en.wikipedia.org/wiki/Secure_Shell) on Wikipedia\.

## SSH keys and AWS Regions<a name="ssh-keys-and-aws-regions"></a>

In Lightsail, the SSH key pairs you use are AWS Region specific\. Lightsail creates a **Default** key in each region\. If you want to create a new key pair to use with your instances, you'll need to create or upload a new key pair in each region where you have Lightsail instances\. After you create a new key pair, you can upload the same key to multiple regions\. For more information, see [Regions and Availability Zones in Lightsail](understanding-regions-and-availability-zones-in-amazon-lightsail.md)\.

## Connect to your Linux or Unix Lightsail instance<a name="setting-up-putty-and-other-clients"></a>

The easiest way to connect to your Linux or Unix instance in Lightsail is by using the browser\-based SSH client that is available in the Lightsail console\. For more information, see [Connecting to your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-connect-to-your-instance-virtual-private-server.md)\.

If your local machine uses a Windows operating system, then you can set up PuTTY to connect to your Linux or Unix Lightsail instance\. For more information, see [Set up PuTTY to connect to your Lightsail instance](lightsail-how-to-set-up-putty-to-connect-using-ssh.md)\.

If your local machine uses a Linux or Unix operating system, including macOS, then you can set up the native SSH client in terminal to connect to your Linux or Unix Lightsail instance\. For more information, see [Connect to your Linux or Unix instance using SSH in terminal](amazon-lightsail-ssh-using-terminal.md)\.
