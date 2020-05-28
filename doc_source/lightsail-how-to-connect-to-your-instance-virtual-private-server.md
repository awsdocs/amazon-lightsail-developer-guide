# Connecting to your Linux or Unix instance in Amazon Lightsail<a name="lightsail-how-to-connect-to-your-instance-virtual-private-server"></a>

 *Last updated: July 5, 2018* 

Amazon Lightsail provides you with a browser\-based SSH client, which is the fastest way to connect to your Linux or Unix instance\. You can also use your own SSH client to connect to your instance\. For more information, see [Download and set up PuTTY to connect using SSH in Amazon Lightsail](lightsail-how-to-set-up-putty-to-connect-using-ssh.md)\.

Connect to your instance with SSH to perform administrative tasks on the server, such as installing software packages or configuring web applications\. The browser\-based SSH client requires no software installation, and is available almost immediately after you create an instance\.

**Note**  
To connect to a Windows Server instance in Lightsail, see [Connect to your Windows\-based instance using Amazon Lightsail](connect-to-your-windows-based-instance-using-amazon-lightsail.md)\.

**To connect to your Linux or Unix instance**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Access the browser\-based SSH client for the instance that you want to connect to by using any of the following:
   + Choose the quick connect icon, as shown in the following example\.  
![\[Open the browser-based SSH client with quick connect.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-quick-connect-to-your-instance-button.png)
   + Choose the actions menu icon \(⋮\), then choose **Connect**\.  
![\[Open the browser-based SSH client with the actions menu.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/animated-gif-lightsail-instance-actions-menu-optimized.gif)
   + Choose the name of the instance, and on the **Connect** tab, choose **Connect using SSH**\.  
![\[Open the browser-based SSH client through the Connect tab.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-connect-using-ssh-button.png)

   You can start interacting with your instance when the browser\-based SSH client opens, and a terminal screen is displayed as shown in the following example:  
![\[Browser-based SSH client in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-web-based-ssh-terminal.png)
**Note**  
The **Connect** tab also provides the information required to connect using your own SSH client\. For more information, see [Download and set up PuTTY to connect using SSH in Amazon Lightsail](lightsail-how-to-set-up-putty-to-connect-using-ssh.md)

## Interact with your Linux or Unix instance using the browser\-based SSH client<a name="interact-with-your-instance"></a>

Type Linux or Unix commands directly into the terminal screen, paste text into the terminal screen, or copy text from the terminal screen of the browser\-based SSH client\. The following sections show you how to copy and paste text to and from the clipboard in SSH\.

**To paste text into the browser\-based SSH client**

1. Highlight text in your local desktop, then press **Ctrl\+C** or **Cmd\+C** to copy it to your local clipboard\.

1. In the bottom right corner of the browser\-based SSH client, choose the clipboard icon\. The browser\-based SSH client clipboard text box appears\.

1. Click into the text box, then press **Ctrl\+V** or **Cmd\+V** to paste the contents from your local clipboard into the browser\-based SSH client clipboard\.

1. Right\-click any area on the SSH terminal screen to paste the text from the browser\-based SSH client clipboard to the terminal screen\.  
![\[Paste text into the browser-based SSH client in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/animated-gif-lightsail-paste-into-browser-terminal.gif)

**To copy text from the browser\-based SSH client**

1. Highlight text on the terminal screen\.

1. In the bottom right corner of the browser\-based SSH client, choose the clipboard icon\. The browser\-based SSH client clipboard text box appears\.

1. Highlight the text that you want to copy, then press **Ctrl\+C** or **Cmd\+C** to copy the text to your local clipboard\. You can now paste the copied text anywhere in your local desktop\.  
![\[Copy text from the browser-based SSH client in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/animated-gif-lightsail-copy-from-browser-terminal.gif)