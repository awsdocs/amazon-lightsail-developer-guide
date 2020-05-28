# Connecting to your Windows instance in Amazon Lightsail<a name="connect-to-your-windows-based-instance-using-amazon-lightsail"></a>

 *Last updated: March 30, 2020* 

You can connect to your Windows Server instance in Amazon Lightsail using the browser\-based RDP client that is available in the Lightsail console\. The browser\-based RDP client does not require software installation, and you can connect to your Windows Server instance immediately after you create it, and it becomes available\. Connect to your instance to perform administrative tasks on the server, such as installing software, or configuring web applications\.

You can also use your own RDP client to connect to your instance, such as the Remote Desktop Connection that is bundled with Windows\. For more information about configuring your own RDP client, see [Connecting to your Windows instance in Amazon Lightsail using the Remote Desktop Connection client](amazon-lightsail-connecting-to-windows-instance-using-rdc.md)\. To connect to a Linux or Unix instance in Lightsail, see [Connecting to your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-connect-to-your-instance-virtual-private-server.md)\.

## Default administrator password for Windows Server instances<a name="windows-admin-password"></a>

A randomly generated default administrator password is assigned to Windows Server instances when they are created\. The browser\-based RDP client in the Lightsail console uses the default administrator password to sign in to your instance\. If you change the administrator password on your instance, you will be prompted to manually enter your new password each time you try to connect to your instance using the browser\-based RDP client\. Lightsail does not store your new administrator password, and it cannot be retrieved from your instance\.

**Important**  
If you lose your administrator password, you will not be able to sign in to your instance, and there is no way to reset the password\. Store your new administrator password in a secure location where you can retrieve it later if you lose it, such as AWS Secrets Manager\. For more information, see the [AWS Secrets Manager User guide](https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html)\.

You can change the administrator password back to the original default administrator password to avoid being prompted for it each time you access your instance using the browser\-based RDP client\. You can find the original default administrator password by choosing the **Instances** tab in the [Lightsail home page](https://lightsail.aws.amazon.com/)\. Choose the name of your Windows Server instance, choose the **Connect** tab, and choose **Show default password** to view the original default administrator password as shown in the following example\.

![\[Windows default administrator password in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-windows-default-admin-password.png)

## Connect to your Windows Server instance using the Lightsail browser\-based RDP client<a name="connect-to-windows-using-browser"></a>

Use the following procedure to connect to your Windows Server instance using the browser\-based RDP client in the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Access the browser\-based RDP client for the instance that you want to connect to by using one of the following steps:
   + Choose the browser\-based RDP client icon, as shown in the following example\.  
![\[Open the browser-based RDP client with quick connect.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/connect-to-windows-instance-using-rdp-connection-shortcut.png)
   + Choose the actions menu icon \(⋮\), then choose **Connect** as shown in the following example\.  
![\[Open the browser-based RDP client with the actions menu.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/animated-gif-lightsail-instance-actions-menu-windows.gif)
   + Choose the name of the instance, and on the **Connect** tab, choose **Connect using RDP**\.  
![\[Open the browser-based RDP client through the Connect tab.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-connect-using-rdp-button.png)

   You can start interacting with your instance when the browser\-based RDP client opens, and a Windows desktop is displayed as shown in the following example\.  
![\[Browser-based RDP client in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-web-based-rdp-client.png)
**Note**  
The **Connect** tab also provides the information required to connect using your own RDP client, such as the default user name and password for your Windows instance\. For more information about configuring your own RDP client, see [Connecting to your Windows instance in Amazon Lightsail using the Remote Desktop Connection client](amazon-lightsail-connecting-to-windows-instance-using-rdc.md)\.

## Interact with your Windows instance using the browser\-based RDP client<a name="interact-with-your-instance"></a>

Use the browser\-based RDP client as you would your own local Windows desktop\. RDP includes function keys and other keys specific to Windows to help you interact with your instance\. The following sections show you how to copy and paste text to and from the clipboard in RDP\.

**To paste text into the browser\-based RDP client**

1. Highlight text in your local desktop, then press **Ctrl\+C** or **Cmd\+C** to copy it to your local clipboard\.

1. In the bottom right corner of the browser\-based RDP client, choose the clipboard icon\. The browser\-based RDP client clipboard text box appears\.

1. Click into the text box, then press **Ctrl\+V** or **Cmd\+V** to paste the contents from your local clipboard into the browser\-based RDP client clipboard\.

1. Right\-click any area on the remote desktop screen to paste the text from the browser\-based RDP client clipboard to the remote desktop screen\.  
![\[Paste text into the browser-based RDP client in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-paste-rdp-windows.gif)

**To copy text from the browser\-based RDP client**

1. Highlight text on the remote desktop screen\.

1. In the bottom right corner of the browser\-based RDP client, choose the clipboard icon\. The browser\-based RDP client clipboard text box appears\.

1. Highlight the text that you want to copy, then press **Ctrl\+C** or **Cmd\+C** to copy the text to your local clipboard\. You can now paste the copied text anywhere in your local desktop\.  
![\[Copy text from the browser-based RDP client in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-copy-rdp-windows.gif)