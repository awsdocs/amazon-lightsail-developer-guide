# Connecting to your Windows instance in Amazon Lightsail using the Microsoft Remote Desktop client on a Mac<a name="amazon-lightsail-connecting-to-windows-instance-using-microsoft-remote-desktop"></a>

 *Last updated: February 24, 2022* 

You can use the Microsoft Remote Desktop client to connect to your Windows instance from your macOS computer\. Microsoft Remote Desktop requires that you use the administrator user name and password for your Lightsail Windows instance\. This can be the default password assigned to the instance when it is created, or your own password if you changed the default password\.

This topic walks you through the steps to obtain your default administrator password from the Lightsail console, and configure Microsoft Remote Desktop to connect to your Windows instance\. You can also connect to your instance from within the Lightsail console using your browser\. For more information, see [Connecting to your Windows instance in Amazon Lightsail using the Microsoft Remote Desktop client](connect-to-your-windows-based-instance-using-amazon-lightsail.md)\.

## Get the required connection information for your Windows instance<a name="get-required-connection-information"></a>

You will need the public IP address, user name, and administrator password for your Windows instance to connect to it using the Microsoft Remote Desktop client\.

Complete the following procedure to get the required information\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Choose the **Instances** tab on the Lightsail home page\.

1. Make note of the public IP address of the instance you want to connect to\.

1. Choose the name of the instance you want to connect to\.

1. Choose the **Connect** tab\.

1. Choose **Show default password** to obtain the Windows administrator password for your instance\.  
![\[Image NOT FOUND\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/connect-using-remote-desktop-mac-01.png)

   The prompt displays the default administrator password for your Windows instance\.  
![\[Image NOT FOUND\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/connect-using-remote-desktop-mac-02.png)

1. Copy the administrator password\. You will use it to sign in to your instance using the Microsoft Remote Desktop client later in this guide\.

## Configure Microsoft Remote Desktop and connect to your instance<a name="configure-remote-desktop-to-connect-to-instance"></a>

Complete the following procedure to install the Microsoft Remote Desktop client on your Mac, and configure it to connect to your instance\.

1. Open the App Store on your Mac, and search for **Microsoft Remote Desktop**\.

1. Find the **Microsoft Remote Desktop** app in the search results, and choose **GET** to install the application\.  
![\[Image NOT FOUND\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/connect-using-remote-desktop-mac-03.png)

1. Open **Microsoft Remote Desktop** after the installation is complete\.

1. At the top, choose the **plus \(\+\)** icon, and choose **Add PC**\.  
![\[Image NOT FOUND\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/connect-using-remote-desktop-mac-04.png)

1. In the **PC name** text box, paste the public IP address of your instance\.

1. Choose **Add**\.  
![\[Image NOT FOUND\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/connect-using-remote-desktop-mac-05.png)

1. Right\-click the icon for your instance, and choose **Connect**\.  
![\[Image NOT FOUND\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/connect-using-remote-desktop-mac-06.png)

1. Enter **Administrator** into the **Username** text box, and enter the default administrator password that you got earlier in this guide into the **Password** text box\.

1. Choose **Continue** to connect to your instance\.  
![\[Image NOT FOUND\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/connect-using-remote-desktop-mac-07.png)

You are now connected to your Lightsail Windows instance\.

![\[Image NOT FOUND\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/connect-using-remote-desktop-mac-08.png)