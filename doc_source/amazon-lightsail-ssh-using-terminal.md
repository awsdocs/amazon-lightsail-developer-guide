# Connect to your Linux or Unix instance using SSH in terminal<a name="amazon-lightsail-ssh-using-terminal"></a>

 *Last updated: January 25, 2021* 

If your local machine uses a Linux or Unix operating system, including macOS, then you can connect to your Linux or Unix instance in Amazon Lightsail using the SSH client through a terminal window\.

The method to connect to your instance described in this guide is one of many\. For more information about the other methods, see [SSH and connecting to your Lightsail instance](understanding-ssh-in-amazon-lightsail.md)\.

The easiest way to connect to your Linux or Unix instance in Lightsail is by using the browser\-based SSH client that is available in the Lightsail console\. For more information, see [Connecting to your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-connect-to-your-instance-virtual-private-server.md)\.

**Contents**
+ [Step 1: Confirm your instance is running and get the public IP address](#terminal-ssh-get-public-ip-address)
+ [Step 2: Confirm the SSH key pair being used by your instance](#terminal-ssh-confirm-key-pair)
+ [Step 3: Change the permissions of your private key and connect to your instance using SSH](#terminal-ssh-change-key-file-permissions)

## Step 1: Confirm your instance is running and get the public IP address<a name="terminal-ssh-get-public-ip-address"></a>

In the following procedure you sign in to the Lightsail console to confirm your instance is in a running state, and to get the public IP address of your instance\. Your instance must be in a running state in order to establish an SSH connection, and you will need the public IP address of your instance to connect to it later in this guide\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. In the **Instances** tab of the Lightsail home page, locate the instance that you want to connect to\.

1. Confirm that the instance is in a running state, and make note of the public IP address of your instance\.

   The state of your instance and its public IP address are listed next the name of your instance as shown in the following example\.  
![\[The status and public IP address of an instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/amazon-lightsail-status-and-public-ip-address.png)

## Step 2: Confirm the SSH key pair being used by your instance<a name="terminal-ssh-confirm-key-pair"></a>

In the following procedure you confirm the SSH key pair that is being used by your instance\. You will need the private key of the key pair to authenticate to your instance and establish an SSH connection\.

1. In the **Instances** tab of the Lightsail home page, choose the name of the instance that you want to connect to\.

   The **Instance management** page appears, with various tab options to manage your instance\.  
![\[Instance management page in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/amazon-lightsail-instance-management-page.png)

1. In the **Connect** tab, scroll down to see the key pair that is being used by your instance\. There are two possibilities:

   1. The following example shows an instance that uses the default key pair for the AWS Region in which you created your instance\. If your instance is using the default key pair, then you can continue to step 3 of this procedure to download the private key of the key pair\. Lightsail stores the private key only for the default key pair of each AWS Region\.  
![\[Default key pair used for a Lightsail instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/amazon-lightsail-default-key-pair.png)

   1. The following example shows an instance that uses a custom key pair that you either uploaded or created\. If your instance is using a custom key pair, then you need to locate the private key of the custom key pair where you store your keys\. If you lost the private key of the custom key pair, then you will not be able to establish an SSH connection to your instance using your own client\. However, you can continue to use the browser\-based SSH client available in the Lightsail console\. Continue to the next [Step 3: Change the permissions of your private key and connect to your instance using SSH](#terminal-ssh-change-key-file-permissions) section of this guide after you locate the private key of the custom key pair\.  
![\[Custom key pair used for a Lightsail instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/amazon-lightsail-custom-key-pair.png)

1. Choose **Account** on the top navigation menu, then choose **Account**\.  
![\[Account menu in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/amazon-lightsail-console-account-menu.png)

   The **Account management** page appears, with various tab options to manage your account settings\.  
![\[Account management page in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/amazon-lightsail-account-management-page.png)

1. Choose the **SSH keys** tab\.

1. Scroll down, and choose **Download** next to the default key of the AWS Region of the instance that you want to connect to\.  
![\[Download private key of default key pair from the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/amazon-lightsail-public-key-download.png)

   The private key is downloaded to your local machine\. You might want to move the downloaded key to a directory in which you store all of your SSH keys, such as a "Keys" folder in your user's home directory\. You will need to refer to the directory where the private key is saved in the next section of this guide\.

   Continue to the next [Step 3: Change the permissions of your private key and connect to your instance using SSH](#terminal-ssh-change-key-file-permissions) section of this guide to use the private key you just downloaded and establish an SSH connection to your instance\.

## Step 3: Change the permissions of your private key and connect to your instance using SSH<a name="terminal-ssh-change-key-file-permissions"></a>

In the following procedure you will change the permissions of your private key file to be readable and writable only by you\. You then open a terminal window in your local machine, and run the SSH command to establish a connection with your instance in Lightsail\.

1. Open a terminal window on your local machine\.

1. Enter the following command to make the private key of the key pair readable and writable only by you\. This is a security best practice required by some operating systems\.

   ```
   sudo chmod 600 /path/to/private-key.pem
   ```

   In the command, replace `/path/to/private-key.pem` with the directory path to where you saved the private key of the key pair that is being used by your instance\.

   **Example:**

   ```
   sudo chmod 600 /Users/user/Keys/LightsailDefaultKey-us-west-2.pem
   ```

1. Enter the following command to connect to your instance in Lightsail using SSH:

   ```
   ssh -i /path/to/private-key.pem username@public-ip-address
   ```

   In the command, replace:
   + */path/to/private\-key\.pem* with the directory path to where you saved the private key of the key pair that is being used by your instance\.
   + *username* with the username of your instance\. You can specify one of the following user names depending on the blueprint that is used by your instance:
     + Amazon Linux, Amazon Linux 2, FreeBSD, and openSUSE instances: `ec2-user`
     + CentOS instances: `centos`
     + Debian instances: `admin`
     + Ubuntu instances: `ubuntu`
     + Certified by Bitnami instances: `bitnami`
     + Plesk instances: `ubuntu`
     + cPanel & WHM instances: `centos`
   + *public\-ip\-address* with the public IP address of your instance that you noted from the Lightsail console earlier in this guide\.

   **Example with aboslute path:**

   ```
   ssh -i /Users/user/Keys/LightsailDefaultKey-us-west-2.pem ec2-user@192.0.1.0
   ```

   **Example with relative path:**

   Notice the `./` prefixing the pem file\. Omitting `./` and simply writing `LightsailDefaultKey-us-west-2.pem` will not work\.

   ```
   ssh -i ./LightsailDefaultKey-us-west-2.pem ec2-user@192.0.1.0
   ```

   You are successfully connected to your instance if you see the welcome message for your instance\. The following example shows the welcome message for an Amazon Linux 2 instance; other instances blueprints have a similar welcome message\. After you're connected, you can execute commands on your instance in Lightsail\. To disconnect, enter `exit` and press Enter\.  
![\[SSH connectione stablished with a Lightsail instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/c61ab0669fef62b2778d591e8e619b4d/images/amazon-lightsail-ssh-connection-established.png)