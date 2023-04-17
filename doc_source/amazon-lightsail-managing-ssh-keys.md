# Managing key pairs in Amazon Lightsail<a name="amazon-lightsail-managing-ssh-keys"></a>

 *Last updated: February 24, 2022* 

You can establish a secure connection to your Amazon Lightsail instances using key pairs\. When you first create an Amazon Lightsail instance, you can choose to use a key pair that Lightsail creates for you \(the Lightsail default key pair\) or a custom key pair that you create\. For more information, see [Key pairs and connecting to instances in Amazon Lightsail](understanding-ssh-in-amazon-lightsail.md)\.

On Linux and Unix instances, the private key allows you to establish a secure SSH connection to your instance\. On Windows instances, the private key decrypts the default administrator password that you use to establish a secure RDP connection to your instance\.

In this guide, we show you how to manage the keys that you can use with your Lightsail instances\. You can view your keys, delete existing keys, and create or upload new keys\.

**Contents**
+ [View your default and custom keys](#view-default-and-custom-keys)
+ [Download the private key of a default key from the Lightsail console](#download-the-private-key)
+ [Delete a custom key in the Lightsail console](#delete-a-custom-key)
+ [Delete a default key and create a new one in the Lightsail console](#delete-default-key-create-new-one)
+ [Create a custom key using the Lightsail console](#create-a-custom-key-console)
+ [Create a custom key using ssh\-keygen and upload to Lightsail](#create-a-custom-key-ssh-keygen)

## View your default and custom keys<a name="view-default-and-custom-keys"></a>

Complete the following procedure to view your default and custom keys from the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose **Account** on the top navigation menu\.

1. Choose **Account** in the dropdown menu\.  
![\[Lightsail account tab\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-01.png)

1. Choose the **SSH keys** tab\.

   The **SSH keys** page lists:
   + **Custom keys** – These are keys that you create either using the Lightsail console or a third\-party tool such as ssh\-keygen\. You can have many custom keys in each AWS Region\.
   + **Default keys** – These are keys that Lightsail creates for you\. You can have only one default key in each AWS Region\.  
![\[SSH keys page\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-02.png)

Custom and default keys are Regional\. For example, keys in the US West \(Oregon\) AWS Region can be configured only on instances created in that Region\. For more information about keys, see [Key pairs and connecting to instances in Amazon Lightsail](understanding-ssh-in-amazon-lightsail.md)\.

On the **SSH keys** page, you can create key pairs, upload keys, delete keys, and download the private key of a Lightsail default key pair\.

**Note**  
You cannot download the private key of a custom key pair because Lightsail does not store that key for you\. If you’ve lost the private key of a custom key pair, then you should create a new one, and configure it on your instance\. Then, delete the key which has been lost\. For more information, see [Create a custom key using the Lightsail console](#create-a-custom-key-console) or [Create a custom key using ssh\-keygen and upload to Lightsail](#create-a-custom-key-ssh-keygen) later in this guide\.

## Download the private key of a default key from the Lightsail console<a name="download-the-private-key"></a>

Complete the following procedure to download the private key of a default key pair from the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose **Account** on the top navigation pane\.

1. Choose **Account** in the dropdown menu\.  
![\[Lightsail account tab\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-03.png)

1. Choose the **SSH keys** tab\.

1. Under the **Default keys** section of the page, choose the download icon for the key that you want to download\.  
![\[Default keys download icon\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-04.png)
**Important**  
Store the private key in a secure location\. Don't share it publicly because it can be used to connect to your instances\.

You can configure an SSH client to connect to your instances using the private key\. For more information, see [Connecting to your instances](understanding-ssh-in-amazon-lightsail.md#connecting-to-your-instances)\.

## Delete a custom key in the Lightsail console<a name="delete-a-custom-key"></a>

Complete the following procedure to delete a custom key in the Lightsail console\. This prevents the custom key from being configured on new instances that you create in Lightsail\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose **Account** on the top navigation pane\.

1. Choose **Account** in the dropdown menu\.  
![\[Lightsail account tab\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-05.png)

1. Choose the **SSH keys** tab\.

1. Under the **Custom keys** section of the page, choose the delete icon for the key that you want to delete\.  
![\[Custom keys delete icon\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-06.png)

   This doesn't remove the public key of the custom key pair from instances that were previously created and are currently running\. To remove a previously configured public key stored on a running instance, see [Managing keys stored on an instance in Amazon Lightsail](amazon-lightsail-remove-ssh-key-on-instance.md)\.

## Delete a default key and create a new one in the Lightsail console<a name="delete-default-key-create-new-one"></a>

Complete the following procedure to delete a default key in the Lightsail console\. This prevents that default key from being configured on new instances that you create in Lightsail\. You can then create a new default key to replace the one that you deleted\. You will be able to configure the new default key on new instances that you create in Lightsail\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail homepage, choose **Account** on the top navigation pane\.

1. Choose **Account** in the dropdown menu\.  
![\[Lightsail account tab\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-07.png)

1. Choose the **SSH keys** tab\.

1. Under the **Default keys** section of the page, choose the delete icon for the default key that you want to delete\.  
![\[Default keys delete icon\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-08.png)
**Important**  
Deleting a default key doesn't remove the public key of the custom key pair from instances that were previously created and are currently running\. For more information, see [Managing keys stored on an instance in Amazon Lightsail](amazon-lightsail-remove-ssh-key-on-instance.md)\.

1. The default key is used to generate the administrator password for Windows instances\. Before you delete the default key, you should retrieve and save the administrator password from any Windows instances that use the default key you want to delete\.

1. Choose **Continue** to delete the default key\.  
![\[Before you delete this key prompt\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-09.png)

1. You must download the default key before you can delete it\. After you download the default key, you will be able to choose **Yes, delete** to permanently delete the default key\.  
![\[Download default key prompt\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-10.png)

1. The default key has been deleted\. Choose **Okay**\.  
![\[Default key deleted prompt\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-11.png)

   The following steps are optional and you should only complete them if you want to replace the default key pair you deleted\.

1. Under the **Default keys** section of the page, choose **Create key pair**\.

1. In the **Select a region** prompt that appears, choose the AWS Region in which you want to create your new default key\. You will be able to configure your new default key on new instances in the same AWS Region\.
**Note**  
Using these steps, you can create default key pairs only in AWS Regions where you have created Lightsail resources\. To create a default key pair in a new Region, you must create a Lightsail resource in that Region\. Creating the resource also creates a default key pair\.

1. Download the private key and store it in a safe location\.

1. Choose **Ok, got it\!** to continue\.  
![\[Key pair created\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-13.png)

1. Confirm the new default key on the Lightsail console SSH keys page\.  
![\[Default keys list\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-14.png)

   You can configure your new default key on new instances that you create in Lightsail\. To configure your new default key on instances that were previously created and are currently running, see [Managing keys stored on an instance in Amazon Lightsail](amazon-lightsail-remove-ssh-key-on-instance.md)\.

## Create a custom key using the Lightsail console<a name="create-a-custom-key-console"></a>

Complete the following procedure to create a custom key pair using the Lightsail console\. You will be able to configure the new custom key on new instances that you create in Lightsail\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail homepage, choose **Account** on the top navigation pane\.

1. Choose **Account** in the dropdown menu\.  
![\[Lightsail account tab\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-15.png)

1. Choose the **SSH keys** tab\.

1. Choose **Create key pair** under the **Custom keys** section of the page\.  
![\[Create custom key\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-16.png)

1. In the **Select a region** prompt that appears, choose the AWS Region in which you want to create your new custom key\. You will be able to configure your new custom key on new instances in the same AWS Region\.  
![\[AWS Region list\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-17.png)

1. In the **Create a new SSH key pair** prompt that appears, give your custom key a name, and choose **Generate key pair**\.  
![\[Create a new SSH key pair\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-18.png)

1. In the **Key pair created\!** prompt that appears, choose **Download private key** to save the private key to your local computer\.
**Important**  
Store the private key in a secured location\. Don't share it publicly because it can be used to connect to your instances\.  
This is the only time you can download the private key of the custom key pair\. Lightsail does not store the private key of custom key pairs\. After you close this prompt, you will not be able to download it again\.  
![\[Download private key prompt\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-19.png)

1. Choose **Ok, got it\!** to close the prompt\.  
![\[You can only download private key once prompt\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-20.png)

1. Your new custom key is listed under the Custom keys section of the page\.  
![\[Custom keys list\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-21.png)

   You can configure your new custom key on new instances that you create in Lightsail\. To configure your new custom key on instances that were previously created and are currently running, see [Managing keys stored on an instance in Amazon Lightsail](amazon-lightsail-remove-ssh-key-on-instance.md)\.

## Create a custom key using ssh\-keygen and upload to Lightsail<a name="create-a-custom-key-ssh-keygen"></a>

Complete the following procedure to create a custom key pair on your local computer using a third\-party tool, such as ssh\-keygen\. After you create the key, you can upload it to the Lightsail console\. You will be able to configure the new custom key on new instances that you create in Lightsail\.

1. Open Command Prompt or Terminal on your local computer\.

1. Enter the following command to create a key pair\.

   ```
   ssh-keygen -t rsa
   ```

1. Specify a directory location on your computer where the key pair should be saved\.

   For example, you can specify one of the following directories:

   1. On Windows: `C:\Users\<UserName>\.ssh\<KeyPairName>`

   1. On macOS, Linux or Unix: `/home/<UserName>/.ssh/<KeyPairName>`

   Replace `<UserName>` with the name of the user you're currently signed in as, and replace `<KeyPairName>` with the name of your new key pair\.

   In the following example, we specified the `C:\Keys` directory on our Windows computer, and gave the new key a name of `MyNewLightsailCustomKey`\.  
![\[ssh-keygen\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-22.png)

1. Enter a passphrase for your key and press **Enter**\. You will not see the passphrase as you enter it\.

   You will need this passphrase later when configuring the private key of the key pair on an SSH client to connect to an instance that has the public key of the key pair configured on it\.  
![\[passphrase\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-23.png)

1. Enter the passphrase again to confirm it and press **Enter**\. You will not see the passphrase as you enter it\.  
![\[passphrase\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-24.png)

1. A prompt confirms that your private key and public key have been saved to the specified directory\.  
![\[key pair save location\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-25.png)

   Next you will upload the public key of the key pair to the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose **Account** on the top navigation pane\.

1. Choose **Account** in the dropdown menu\.  
![\[Lightsail account tab\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-26.png)

1. Choose the **SSH keys** tab\.

1. Choose **Upload key** under the **Custom keys** section of the page\.  
![\[Upload custom key\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-27.png)

1. In the **Select a region** prompt that appears, choose the AWS Region in which you want to upload your new custom key\. You will be able to configure your new custom key on new instances in the same AWS Region\.  
![\[AWS Region list\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-28.png)

1. Choose **Upload**\.

1. Click **Choose File** in the **Upload a public key** prompt that appears\.  
![\[Choose public key file location\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-29.png)

1. Find the public key of the key pair you created earlier in this procedure, on your local computer, and choose **Open**\. The public key of the key pair is the file with a \.PUB file extension\.  
![\[Select public key\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-30.png)

1. Choose **Upload key**\.  
![\[Choose upload key button\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-31.png)

1. Your new custom key is listed in the **Custom keys** section of the page\.  
![\[Custom keys list\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/managing-key-pairs-32.png)

   You can configure your new custom key on new instances that you create in the AWS Region where you uploaded your key\. To configure your new custom key on instances that were previously created and are currently running, see [Managing keys stored on an instance in Amazon Lightsail](amazon-lightsail-remove-ssh-key-on-instance.md)\.