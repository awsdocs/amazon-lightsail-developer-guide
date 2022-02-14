# Delete instance SSH keys in Amazon Lightsail<a name="amazon-lightsail-remove-ssh-key-on-instance"></a>

 *Last updated: June 6, 2021* 

A key pair, consisting of a private key and a public key, is a set of security credentials that you use to prove your identity when establishing an SSH connection to an instance in Amazon Lightsail\. The public key is added on the instance, and the private key is kept in a safe place on your local computer, which you use when connecting to your instance\.

When you create a Lightsail instance, you can choose to use the Lightsail default key pair for the AWS Region in which you create the instance or you can use a custom key pair that you either create using the Lightsail console, or upload\. Later, after the instance is up and running, you can change the key pair on your instance\. For example, if a user in your organization requires access to the instance using a separate key pair, you can add that key pair to your instance\. Or, if someone has a copy of the private key \(the `.PEM` file\) and you want to prevent them from connecting to your instance \(for example, if they've left your organization\), you can replace the key pair with a new one or remove it\.

To add or replace a key pair, you must be able to connect to your instance\. Complete the procedure in this guide to add or replace a key pair on your instance in Lightsail\.

**Contents**
+ [Create a key pair using the Lightsail console](#create-a-key-pair-using-lightsail)
+ [Create a key pair using ssh\-keygen](#create-a-key-pair-using-ssh-keygen)
+ [Add a public key to your instance](#add-a-public-key)
+ [Delete existing public keys from your instance](#delete-existing-public-key)
+ [Delete an uploaded or created key in the Lightsail console](#delete-uploaded-created-key)
+ [Remove a Lightsail default key](#remove-default-lightsail-key)

## Create a key pair using Lightsail<a name="create-a-key-pair-using-lightsail"></a>

Complete the following procedure to create a key pair using the Lightsail console\. You can add the public key to your Lightsail instance after it's created\. Alternately, you can [use ssh\-keygen to generate a key pair](#create-a-key-pair-using-ssh-keygen) for your instance\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose **Account** on the top navigation menu\.

1. Choose **Account** in the dropdown menu\.

1. Choose the **SSH keys** tab\.

1. Choose **Create new**\.

1. Choose the AWS Region in which you want to create the key pair\.

1. Choose **Create**\.  
![\[Create SSH key pair in an AWS Region\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-create-ssh-key-pair-region.png)

1. Enter a name for your new key pair\.

1. Choose **Generate key pair**\.  
![\[Name your SSH key pair\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-name-ssh-key-pair.png)

1. Choose **Download key** to download the private key \(`.PEM`\) file of the key pair\.

   This is the only time you can download the private key\. Treat the private key as security credential for your instance, and store it somewhere safe\.  
![\[SSH key pair created\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-key-pair-created.png)

1. Save the file to the following folder:
   + On Windows: `C:\Users\%USERNAME%\.ssh`
   + On Linux: `$HOME/.ssh`

   The public key is now stored in the Lightsail console, which you can use when creating new Lightsail instances\. The private key is stored in the `.ssh` folder on your computer\.

   This action doesn't add the public key to Lightsail instances that were previously created\. To do that, you must generate the public key of the key pair using the private key you downloaded\.

   Complete the following steps to generate the public key using the private key\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to generate a public key using the private key you downloaded from the Lightsail console\.

   ```
   ssh-keygen -y -f PrivateKeyFile > PublicKeyFile
   ```

   In the command, replace:
   + *PrivateKeyFile* with the name of the private key file you downloaded from the Lightsail console\.
   + *PublicKeyFile* with the name of the public key file you want to create\.

   **Example**

   ```
   ssh-keygen -y -f MyCustomKeyPair.pem > MyCustomKeyPair.pub
   ```

1. Open the public key file, and copy the text in the file\. You will add this public key text to your instance in the next section of this guide\.  
![\[Contents of the public key file\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-ssh-keygen-public-key.png)

   Continue to the [Add a public key to your instance](#add-a-public-key) section of this guide to add your new public key to your Lightsail instance\.

## Create a key pair using ssh\-keygen<a name="create-a-key-pair-using-ssh-keygen"></a>

Complete the following procedure to create a key pair using ssh\-keygen\. You can add the public key to your Lightsail instance after it's created\. Alternately, you can [use the Lightsail console to generate a key pair](#create-a-key-pair-using-lightsail) for your instance\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to create a key pair\.

   ```
   ssh-keygen -t rsa
   ```

1. The command prompts you to enter the path to the file in which you want to save the key\. Enter the path and file name, and then press **Enter**\. In the following example, we specified the `my_key` file name for demonstration purposes\.  
![\[Result of the ssh-keygen command\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-ssh-keygen-command.png)

1. The command prompts you to enter a passphrase\. The passphrase is not mandatory\. However, it is recommended that you specify a passphrase to protect your private key against unauthorized use\.  
![\[Passphrase for ssh-keygen\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-ssh-keygen-command-passphrase.png)

1. Enter the passphrase again to confirm it\.  
![\[Enter the passphrase for ssh-keygen again\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-ssh-keygen-command-second-passphrase.png)

   The command generates an SSH key pair consisting of a public key and a private key\.  
![\[Keys saved\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-ssh-keygen-command-keys-saved.png)

1. Open the public key \(`.PUB`\) file, and copy the text in the file\. You will add this public key text to your instance in the next section of this guide\.  
![\[Contents of the public key file\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-ssh-keygen-public-key.png)

   Continue to the [Add a public key to your instance](#add-a-public-key) section of this guide to add your new public key to your Lightsail instance\.

## Add a public key to your instance<a name="add-a-public-key"></a>

Complete the following procedure to add the public key to your instance\. Public key content is saved in the `~/.ssh/authorized_keys` file on instances\.

1. Connect to your instance using SSH\.

1. Enter the following command to edit the `authorized_keys` file using the Vim text editor\.
**Note**  
These steps use Vim for demonstration purposes\. However, you can use any text editor for these steps\.

   ```
   sudo vim ~/.ssh/authorized_keys
   ```

   You should see a result similar to the following example, which shows the current public keys configured on your instance\. In our case, the Lightsail default key for the AWS Region in which the instance was created is the only public key configured on our instance\.  
![\[Contents of the authorzied_keys file\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-authorized-keys-contents.png)

1. Press the `I` key to enter the insert mode in the Vim editor\.

1. Enter a line break after the last public key on the file\.

1. Paste the public key text that you copied earlier in this guide \(after creating a new key pair\)\.

   You should see a result similar to the following example\.  
![\[New public key added to authorized_keys file\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-authorized-keys-new-key-added.png)

1. Press the **ESC** key, and then enter `:wq!` to save your edits and quit Vim\.

   Your new public key is now added to your instance\. To test the new key pair, disconnect from your instance, and reconnect to it using the private key pair that you created earlier in this guide\. For more information, see [SSH and connecting to your Lightsail instance](understanding-ssh-in-amazon-lightsail.md)\. If you’re able to successfully connect to your instance using your new key pair, continue to the [Delete existing public keys from your instance](#delete-existing-public-key) section of this guide to remove the Lightsail default key\.

## Delete existing public keys from your instance<a name="delete-existing-public-key"></a>

Complete the following procedure to remove a public key from your instance after you’ve added a new public key, and successfully connected to it using the new key pair\.

1. Connect to your instance using SSH\.

1. Enter the following command to edit the `authorized_keys` file using the Vim text editor\.

   ```
   sudo vim ~/.ssh/authorized_keys
   ```

1. Press the `I` key to enter the insert mode in the Vim editor\.

1. Delete the line of text that contains the public key that you want to remove from your instance\.  
![\[Delete old key from authorized_keys file\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-authorized-keys-delete-old-key.png)

   The result should look like the following example, in which only our new public key is left\.  
![\[Old key deleted from authorized_keys file\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-authorized-keys-old-key-deleted.png)

1. Press the **ESC** key, and then enter `:wq!` to save your edits and quit Vim\.

   The deleted public key is now removed from your instance\. Your instance will now refuse connections that use that key pair\.

## Delete an uploaded or created key in the Lightsail console<a name="delete-uploaded-created-key"></a>

Complete the following procedure to delete a key from the Lightsail console that you uploaded or created\. This prevents the key from being used when you create new Lightsail instances in the future\. However, deleting a key in this way doesn't delete the public key from instances that were previously created using that key or from snapshots of those instances\. It also doesn't delete the private key on your local computer\. To delete the public key from instances, see the [Delete existing public keys from your instance](#delete-existing-public-key) section earlier in this guide\.

**Note**  
Your Lightsail default key pairs do not need to be deleted for cost savings\. You are not charged for them\. For more information about removing the default key, see the [Remove a Lightsail default key](#remove-default-lightsail-key) section later in this guide\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose **Account** on the top navigation menu\.

1. Choose **Account** in the dropdown menu\.  
![\[Account menu option\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-account-drop-down.png)

1. Choose the **SSH keys** tab\.

1. Scroll down until you find the AWS Region for which you want to delete a key that you uploaded or created using the Lightsail console\.

1. Choose the **X** icon next to the key that you want to delete\.  
![\[Delete key from Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-delete-custom-key.png)

1. In the confirmation prompt that appears, choose **Yes** to delete the key, or choose **No** to not delete it\.  
![\[Confirm deletion of key\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-delete-custom-key-pair-confirmation.png)

## Remove a Lightsail default key<a name="remove-default-lightsail-key"></a>

You cannot remove and replace the Lightsail default key for an AWS Region on your own\. If you need to revoke access, or if the default key becomes compromised, complete the following procedure to submit a request for us to remove and replace the Lightsail default key for an AWS Region\. This prevents the key from being used when you create new Lightsail instances in the future\.

**Important Information**  
Your Lightsail default key pairs do not need to be deleted for cost savings\. You are not charged for them\.  
A new default key pair will be automatically generated upon deletion of the original default key pair\.

1. Browse to the [Support Center](https://console.aws.amazon.com/support/)

1. Choose **Create case**\.

1. Choose **Account and billing support**\.

1. Choose **Account** in the **Type** dropdown menu\.  
![\[Type dropdown menu on the Create case page\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-create-case-type-drop-down.png)

1. Choose **Security** in the **Category** dropdown menu\.  
![\[Category dropdown menu on the Create case page\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-create-case-category-drop-down.png)

1. In the **Subject** and **Description** fields of the ticket, describe your request as shown in the following example\.  
![\[Information in Subject and Description fields of case\]](https://d9yljz1nd5001.cloudfront.net/en_us/2c7274df55d082980824e6f5d4268a07/images/amazon-lightsail-create-case-subject-description.png)

1. Choose your own preferences for the contact options, and then choose **Submit**\.

   The Lightsail default key for the AWS Region that you specified will be deleted after a few days\. You should avoid creating new Lightsail instances in that AWS Region until the key is replaced\.