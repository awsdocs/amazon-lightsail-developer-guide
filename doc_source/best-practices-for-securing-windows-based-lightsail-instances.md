# Best practices for securing Windows Server\-based Lightsail instances<a name="best-practices-for-securing-windows-based-lightsail-instances"></a>

 *Last updated: October 16, 2017* 

In this article, we provide tips and tricks to help you avoid security risks when using your Lightsail instance running Windows Server\.

## About Lightsail passwords<a name="best-practices-windows-security-about-passwords"></a>

When you create a Windows Server\-based instance, Lightsail randomly generates a long password that is hard to guess\. You use this password uniquely with your new instance\. You can use the default password to connect quickly to your instance using remote desktop \(RDP\)\. You are always logged in as the **Administrator** on your Lightsail instance\.

## Managing your password<a name="best-practices-windows-security-password-management"></a>

You can change the password on your Windows Server\-based instance to something you can remember\. This might be useful if you want to use a remote desktop client to access your Lightsail instance\. Lightsail never stores a password you generate\.

**Note**  
You can use either the Lightsail\-generated password or your own custom password with the browser\-based RDP client in Lightsail\. If you use a custom password, you will be prompted for your password every time you log in\. It's easier to use the Lightsail\-generated default password with the browser\-based RDP client if you want quick access to your instance\. 

Use the Windows Server password manager to change your password securely\. Press `Ctrl` \+ `Alt` \+ `Del`, and then choose **Change a password**\. Be sure to keep a record of your password, because Lightsail doesn't store your password\. If you need to retrieve your password, see the following: [Using the non\-default key with Windows\-based Lightsail instances](use-non-default-key-with-windows-based-instance-in-lightsail.md)\.

If you change your password from the unique, default password, be sure to use a strong password\. You should avoid passwords that are based on names or dictionary words, or repeating sequences of characters\.

## Security patching<a name="best-practices-windows-security-security-patching"></a>

We recommend keeping your Windows Server\-based Lightsail instances updated with the latest security patches\. Be sure your server is configured to download and install updates\. The following procedure tells you how to do this directly on your Lightsail instance running Windows Server\.

1. On your Windows Server\-based instance, open a command prompt\.

1. Type `sconfig`, and then press `Enter`\.

   Windows Update Settings \(number 5\) are at `Automatic` by default\.  
![\[Server configuration in Windows Server 2016\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/configure-server-windows-based-lightsail.png)

1. To download and install new updates, type `6`, and then press `Enter`\.

1. Type `A` to search for **\(A\)ll updates** in the new command window, and then press `Enter`\.

1. Type `A` again to install **\(A\)ll updates**, and then press `Enter`\.

   When finished, you see a message with the installation results and more instructions \(if those apply\)\.  
![\[Successfully downloaded and updated Windows Server 2016 security patch\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/download-install-updates-configure-server-windows-based-lightsail.png)

## Enabling Account Lockout Policy in Windows Server<a name="best-practices-windows-security-enable-lockout"></a>

You can configure Windows Server to temporarily or indefinitely disable accounts when a certain number of unsuccessful login attempts has been reached\. For example, you can lock out someone who attempts to log in to your instance using three unsuccessful passwords\.

For more information, see [Account Lockout Policy](https://technet.microsoft.com/en-us/library/hh994563(v=ws.11).aspx) in the *Windows Server documentation*\.

## Ports and firewall settings<a name="best-practices-windows-security-ports-firewall"></a>

By default, we open the following ports on your Windows Server\-based instances\.

![\[Firewall settings\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/windows-ports-firewall-open-by-default.png)

The ports you enable are exposed to the world and can't be restricted by source IP\. To restrict access to your instance, you can turn off these ports and only enable them when you need to access your instance\. Here's how:

1. Find the instance you want to manage in Lightsail, and then choose **Manage**\.

1. Choose **Networking**\.

1. On the **Networking** page for your instance, choose **Edit rules**\.

1. Delete the RDP/TCP/3389 rule by choosing the orange "x" next to the rule\.  
![\[Close your RDP port by deleting this rule\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/windows-ports-firewall-delete-rdp-port.png)

1. Choose **Save**\.