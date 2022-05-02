# Managing keys stored on an instance in Amazon Lightsail<a name="amazon-lightsail-remove-ssh-key-on-instance"></a>

 *Last updated: February 24, 2022* 

You can establish a secure connection to your Amazon Lightsail instances using key pairs\. Lightsail configures the public key of a key pair on your Linux or Unix instance when you first create it\. You use the private key of the key pair to authenticate to your instance when establishing an SSH connection to it\. For more information about keys, see [Key pairs and connecting to instances in Amazon Lightsail](understanding-ssh-in-amazon-lightsail.md)\.

After your instance is up and running, you can change the key pair that is used to connect to your instance by adding a new public key on the instance, or by replacing the public key \(deleting the existing public key and adding a new one\) on the instance\. You might do this for the following reasons:
+ If a user in your organization requires access to the instance using a separate key pair, you can add the public key to your instance\.
+ If you need to secure a new instance that was created from the snapshot of an instance which used a compromised key\.
+ If someone has a copy of the private key and you want to prevent them from connecting to your instance \(for example, if they left your organization\), you can delete the public key on the instance and replace it with a new one\.

To add or replace a key on your instance, you must be able to connect to your instance\. If you've lost your existing private key, you can connect to your instance using the Lightsail browser\- based SSH client\. For more information, see [Connecting to your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-connect-to-your-instance-virtual-private-server.md)\.

**Contents**
+ Step 1: [Learn about the process](#learn-about-the-process)
+ Step 2: [Create a key pair](#create-a-key-pair)
+ Step 3: [Add a public key to your instance](#add-public-key-to-instance)
+ Step 4: [Connect to your instance using the new key pair](#connect-to-instance-new-key-pair)
+ Step 5: [Delete an existing public key from your instance](#delete-public-key-from-instance)

## Step 1: Learn about the process<a name="learn-about-the-process"></a>

Following are the general steps to add and remove keys on an instance\. If you want to remove a key from your instance without adding a new key, see Step 5: [Delete an existing public key from your instance](#delete-public-key-from-instance) later in this guide\.

1. **Create a key pair** – To add a new key to your instance you must first create a new key pair\. You can create a custom or default key pair using the Lightsail console, or on your local computer using a third\-party tool, such as ssh\-keygen\. Both methods generate a new key pair, which consist of a public key and a private key\. For more information, see Step 2: [Create a key pair](#create-a-key-pair) later in this guide\.

1. **Add a public key to your instance** – After you create a key pair, you connect to your instance using SSH and add the public key of the key pair to your instance\. For more information, see Step 3: [Add a public key to your instance](#add-public-key-to-instance) later in this guide\.

1. **Test that you can connect to your instance using the new key pair** – After the public key of the key pair is saved on the instance, you should test that you can use the private key of the key pair to connect to the instance using SSH\. For more information, see Step 4: [Connect to your instance using the new key pair](#connect-to-instance-new-key-pair) later in this guide\.

1. **Remove an old public key from your instance** – After you successfully connect to your instance using the new key, you can remove an old public key from the instance\. Complete this step to prevent a user from connecting to an instance using an old key pair\. For more information, see Step 5: [Delete an existing public key from your instance](#delete-public-key-from-instance) later in this guide\.

## Step 2: Create a key pair<a name="create-a-key-pair"></a>

Complete the following procedure to create a key pair on your local computer using ssh\-keygen\.

1. Open Command Prompt or Terminal on your local computer\.

1. Enter the following command to create a key pair\.

   ```
   ssh-keygen -t rsa
   ```

1. Specify a directory location on your computer where the key pair should be saved\.

   For example:
   + On Windows: `C:\Users\<UserName>\.ssh\<KeyPairName>`
   + On macOS, Linux or Unix: `/home/<UserName>/.ssh/<KeyPairName>`

   Replace `<UserName>` with the name of the user you are currently signed in as, and replace `<KeyPairName>` with the name of your new key pair\.

   In the following example, we specified the `C:\Keys` directory on our Windows computer, and gave the new key a name of `MyNewLightsailCustomKey`\.  
![\[Directory location C:\Keys\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/managing-keys-on-instance-01.png)

1. Enter a passphrase for your key and press **Enter**\. You will not see the passphrase as you enter it\.

   You will need this passphrase later when configuring the private key on an SSH client to connect to an instance that has the public key configured on it\.  
![\[Passphrase\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/managing-keys-on-instance-02.png)

1. Enter the passphrase again to confirm it and press **Enter**\. You will not see the passphrase as you enter it\.  
![\[Passphrase\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/managing-keys-on-instance-03.png)

1. A prompt confirms that your private key and public key have been saved to the specified directory\.  
![\[Identity file save location\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/managing-keys-on-instance-04.png)

1. Open the public key \(\.PUB\) file, and copy the text in the file\.  
![\[Copy to contents of the public key file\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/managing-keys-on-instance-05.png)

Continue to the next section of this guide to add your new public key to your Lightsail instance\.

## Step 3: Add a public key to your instance<a name="add-public-key-to-instance"></a>

Complete the following procedure to add the public key to your instance\. Public key content is saved in the `~/.ssh/authorized_keys` file on Linux and Unix instances\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. Choose the **Instances** tab on the Lightsail home page\.

1. Choose the browser\-based SSH client icon for the instance that you want to connect to\.  
![\[Choose the browser based SSH client\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/managing-keys-on-instance-06.png)

1. After you're connected, enter the following command to edit the *authorized\_keys* file using the text editor of your choice\. The following steps use Vim for demonstration purposes\.

   ```
   sudo vim ~/.ssh/authorized_keys
   ```

   You should see a result similar to the following example, which shows the current public keys configured on your instance\. In our case, the Lightsail default key for the AWS Region in which the instance was created in, is the only public key configured on the instance\.  
![\[Edit the authorized keys file\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/managing-keys-on-instance-07.png)

1. Press the **I** key to enter insert mode in the Vim editor\.

1. Enter a line break after the last public key on the file\.

1. Paste the public key text that you copied earlier in this guide \(after creating a new key pair\)\. You should see a result similar to the following example:  
![\[Paste the public key\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/managing-keys-on-instance-08.png)

1. Press the **ESC** key\. Next, type `:wq!` and press **Enter** to save your edits and exit the Vim editor\.

The new public key is now added to your instance\. Continue to the next section of this guide to connect to your instance using the new key pair\.

## Step 4: Connect to your instance using the new key pair<a name="connect-to-instance-new-key-pair"></a>

To test the new key pair, disconnect from your instance, and reconnect to it using the private key that you created earlier in this guide\. For more information, see [Key pairs and connecting to instances in Amazon Lightsail](understanding-ssh-in-amazon-lightsail.md)\. After you successfully connect to your instance using the new key, you can remove an old key from the instance\. Continue to the next step to learn how to delete public keys from your instance\.

## Step 5: Delete an existing public key from your instance<a name="delete-public-key-from-instance"></a>

Complete the following procedure to remove a public key from your instance\. This prevents a user from connecting to an instance using an old key pair\. Do this after you successfully connect to the instance using the new key pair\.

1. Connect to your instance using SSH\.

1. Enter the following command to edit the *authorized\_keys* file using the text editor of your choice\. The following steps use Vim for demonstration purposes\.

   ```
   sudo vim ~/.ssh/authorized_keys
   ```

1. Press the letter **I** key to enter insert mode in the Vim editor\.

1. Delete the line of text that contains the public key that you want to remove from your instance\.  
![\[Delete old public key\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/managing-keys-on-instance-09.png)

   The result should look like the following example, where the new public key the only key that displays\.  
![\[Keep new public key\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/managing-keys-on-instance-10.png)

1. Press the **ESC** key\. Next, type `:wq!` and press **Enter** to save your edits and exit the Vim editor\.

The deleted public key is now removed from your instance\. Your instance will refuse connections that use the private key of that key pair\.