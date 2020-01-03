# Connecting to your Windows instance in Amazon Lightsail<a name="connect-to-your-windows-based-instance-using-amazon-lightsail"></a>

 *Last updated: July 5, 2018* 

Amazon Lightsail provides you with a browser\-based RDP client, which is the fastest way to connect to your Windows instance\. You can also use your own RDP client to connect to your instance, such as Remote Desktop Connection\.

Connect to your instance with RDP to perform administrative tasks on the server, such as installing software or configuring web applications\. The browser\-based RDP client requires no software installation\.

**Note**  
To connect to a Linux or Unix instance in Lightsail, see [Connecting to your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-connect-to-your-instance-virtual-private-server.md)\.

**To connect to your Windows instance**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Access the browser\-based RDP client for the instance that you want to connect to by using any of the following:

   1. Choose the quick connect icon, as shown in the following example\.  
![\[Open the browser-based RDP client with quick connect.\]](https://d9yljz1nd5001.cloudfront.net/en_us/aa4810f664dabff907209ee92babaa14/images/connect-to-windows-instance-using-rdp-connection-shortcut.png)

   1. Choose the actions menu icon \(⋮\), then choose **Connect**\.  
![\[Open the browser-based RDP client with the actions menu.\]](https://d9yljz1nd5001.cloudfront.net/en_us/aa4810f664dabff907209ee92babaa14/images/animated-gif-lightsail-instance-actions-menu-windows.gif)

   1. Choose the name of the instance, and on the **Connect** tab, choose **Connect using RDP**\.  
![\[Open the browser-based RDP client through the Connect tab.\]](https://d9yljz1nd5001.cloudfront.net/en_us/aa4810f664dabff907209ee92babaa14/images/amazon-lightsail-connect-using-rdp-button.png)

   You can start interacting with your instance when the browser\-based RDP client opens, and a Windows desktop is displayed as shown in the following example:  
![\[Browser-based RDP client in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/aa4810f664dabff907209ee92babaa14/images/amazon-lightsail-web-based-rdp-client.png)
**Note**  
The **Connect** tab also provides the information required to connect using your own RDP client, such as the default user name and password for your Windows instance\.

## Interact with your Windows instance using the browser\-based RDP client<a name="interact-with-your-instance"></a>

Use the browser\-based RDP client as you would your own local Windows desktop\. RDP includes function keys and other keys specific to Windows to help you interact with your instance\. The following sections show you how to copy and paste text to and from the clipboard in RDP\.

**To paste text into the browser\-based RDP client**

1. Highlight text in your local desktop, then press **Ctrl\+C** or **Cmd\+C** to copy it to your local clipboard\.

1. In the bottom right corner of the browser\-based RDP client, choose the clipboard icon\. The browser\-based RDP client clipboard text box appears\.

1. Click into the text box, then press **Ctrl\+V** or **Cmd\+V** to paste the contents from your local clipboard into the browser\-based RDP client clipboard\.

1. Right\-click any area on the remote desktop screen to paste the text from the browser\-based RDP client clipboard to the remote desktop screen\.  
![\[Paste text into the browser-based RDP client in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/aa4810f664dabff907209ee92babaa14/images/amazon-lightsail-paste-rdp-windows.gif)

**To copy text from the browser\-based RDP client**

1. Highlight text on the remote desktop screen\.

1. In the bottom right corner of the browser\-based RDP client, choose the clipboard icon\. The browser\-based RDP client clipboard text box appears\.

1. Highlight the text that you want to copy, then press **Ctrl\+C** or **Cmd\+C** to copy the text to your local clipboard\. You can now paste the copied text anywhere in your local desktop\.  
![\[Copy text from the browser-based RDP client in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/aa4810f664dabff907209ee92babaa14/images/amazon-lightsail-copy-rdp-windows.gif)