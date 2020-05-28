# Tutorial: Launch and configure a WordPress instance in Amazon Lightsail<a name="amazon-lightsail-tutorial-launching-and-configuring-wordpress"></a>

 *Last updated: November 1, 2018* 

Amazon Lightsail is the easiest way to get started with Amazon Web Services \(AWS\) if you just need instances \(virtual private servers\)\. Lightsail includes everything you need to launch your project quickly—instances, managed databases, SSD\-based storage, backups \(snapshots\), data transfer, domain DNS management, static IPs, and load balancers—for a [low, predictable price](https://aws.amazon.com/lightsail/pricing/)\.

This tutorial shows you how to launch and configure a WordPress instance on Lightsail\. It includes steps to connect to your instance by using SSH, sign in to your WordPress website, create a static IP and attaching it to your instance, and create a DNS zone and mapping your domain\. When you’re done with this tutorial, you have the fundamentals to get your instance up and running on Lightsail\.

**Contents**
+ [Step 1: Sign up for AWS](#tutorial-launching-and-configuring-wordpress-sign-up-for-aws)
+ [Step 2: Create a WordPress instance in Lightsail](#create-a-wordpress-instance)
+ [Step 3: Connect to your instance via SSH and get the password for your WordPress website](#tutorial-launching-and-configuring-wordpress-connecting-to-your-instance-via-ssh)
+ [Step 4: Sign in to the administration dashboard of your WordPress website](#signing-in-to-the-administration-dashboard)
+ [Step 5: Create a Lightsail static IP address and attach it to your WordPress instance](#tutorial-launching-and-configuring-wordpress-creating-a-lightsail-static-ip)
+ [Step 6: Create a Lightsail DNS zone and map a domain to your WordPress instance](#tutorial-launching-and-configuring-wordpress-creating-a-dns-zone)
+ [Step 7: Complete the next steps](#tutorial-launching-and-configuring-wordpress-next-steps)

## Step 1: Sign up for AWS<a name="tutorial-launching-and-configuring-wordpress-sign-up-for-aws"></a>

This tutorial requires an AWS account\. [Sign up for AWS](https://console.aws.amazon.com/console/home), or [sign in to AWS](https://console.aws.amazon.com/console/home) if you already have an account\.

## Step 2: Create a WordPress instance in Lightsail<a name="create-a-wordpress-instance"></a>

Complete the following steps to get your WordPress instance up and running on Lightsail\.

**Note**  
For more information about creating an instance in Lightsail, see [Creating an Amazon Lightsail instance in the Lightsail](how-to-create-amazon-lightsail-instance-virtual-private-server-vps.md) documentation\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the **Instances** tab of the Lightsail home page, choose **Create instance**\.  
![\[Launching and configuring WordPress in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-01.png)

1. Choose the AWS Region and Availability Zone for your instance\.  
![\[Launching and configuring WordPress in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-02.png)

1. Choose your instance image\.

   1. Choose **Linux/Unix** as the platform\.

   1. Choose **WordPress** as the blueprint\.  
![\[Launching and configuring WordPress in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-03.png)

1. Choose an instance plan\.

   A plan includes a low, predictable cost, machine configuration \(RAM, SSD, vCPU\), and data transfer allowance\. You can try the $3\.50 USD Lightsail plan without charge for one month \(up to 750 hours\)\. AWS credits one free month to your account\.

1. Enter a name for your instance\.

   Resource names:
   + Must be unique within each AWS Region in your Lightsail account\.
   + Must contain 2 to 255 characters\.
   + Must start and end with an alphanumeric character or number\.
   + Can include alphanumeric characters, numbers, periods, dashes, and underscores\.  
![\[Launching and configuring WordPress in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-04.png)

1. Choose **Create instance**\.

## Step 3: Connect to your instance via SSH and get the password for your WordPress website<a name="tutorial-launching-and-configuring-wordpress-connecting-to-your-instance-via-ssh"></a>

The default password to sign in to the administration dashboard of your WordPress website is stored on the instance\.

Complete the following steps to connect to your instance using the browser\-based SSH client in the Lightsail console, and get the password for the administration dashboard\.

**Note**  
For more information, see [Getting the application user name and password for your Certified by Bitnami' instance in Amazon Lightsail](log-in-to-your-bitnami-application-running-on-amazon-lightsail.md)

1. On the **Instances** tab of the [Lightsail home page](https://lightsail.aws.amazon.com/), choose the SSH quick\-connect icon for your WordPress instance\.  
![\[Launching and configuring WordPress in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-05.png)

1. After the browser\-based SSH client window opens, enter the following command to retrieve the default application password:

   ```
   $HOME/bitnami_application_password
   ```

1. Make note of the password displayed on the screen\. You use it later to sign in to the administration dashboard of your WordPress website\.  
![\[Launching and configuring WordPress in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-06.png)

## Step 4: Sign in to the administration dashboard of your WordPress website<a name="signing-in-to-the-administration-dashboard"></a>

Now that you have the password for the administration dashboard of your WordPress website, you can sign in\. In the administration dashboard, you can change your user password, install plugins, change the theme of your website, and more\.

Complete the following steps to sign in to the administration dashboard of your WordPress website\.

**Note**  
For more information, see [Getting the application user name and password for your Certified by Bitnami' instance in Amazon Lightsail](log-in-to-your-bitnami-application-running-on-amazon-lightsail.md)\.

1. In a browser window, go to:

   ```
   http://PublicIpAddress/wp-login.php
   ```

   In the address, replace *PublicIpAddress* with the public IP address of your WordPress instance\. You can get your instance's public IP address from the Lightsail console as shown in the following example:  
![\[Launching and configuring WordPress in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wordpress-tutorial-public-ip-address.png)

1. In the **Username or Email Address** box, enter `user`\.

1. In the **Password** box, enter the default password obtained earlier in this tutorial\.

1. Choose **Log in**\.  
![\[Launching and configuring WordPress in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-07.png)

   You are now signed in to the administration dashboard of your WordPress website where you can perform administrative actions\. For more information about administering your WordPress website, see the [WordPress Codex](https://codex.wordpress.org/) in the WordPress documentation\.  
![\[Launching and configuring WordPress in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-08.png)

## Step 5: Create a Lightsail static IP address and attach it to your WordPress instance<a name="tutorial-launching-and-configuring-wordpress-creating-a-lightsail-static-ip"></a>

The default public IP for your WordPress instance changes if you stop and start your instance\. A static IP address, attached to an instance, stays the same even if you stop and start your instance\.

Complete the following steps to create a static IP address and attach it to your WordPress instance\.

**Note**  
For more information, see [Create a static IP and attach it to an instance in Amazon Lightsail](lightsail-create-static-ip.md)\.

1. On the **Instances** tab of the [Lightsail home page](https://lightsail.aws.amazon.com/), choose your running WordPress instance\.  
![\[Launching and configuring WordPress in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-09.png)

1. Choose the **Networking** tab, then choose **Create static IP**\.  
![\[Launching and configuring WordPress in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-10.png)

1. The static IP location, and attached instance are pre\-selected based on the instance that you chose earlier in this tutorial\.  
![\[Launching and configuring WordPress in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-11.png)

1. Name your static IP, then choose **Create**\.  
![\[Launching and configuring WordPress in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-12.png)

## Step 6: Create a Lightsail DNS zone and map a domain to your WordPress instance<a name="tutorial-launching-and-configuring-wordpress-creating-a-dns-zone"></a>

Transfer management of your domain's DNS records to Lightsail\. This allows you to more easily map a domain to your WordPress instance, and manage more of your website’s resources using the Lightsail console\.

Complete the following steps to create a Lightsail DNS zone and map a domain to your WordPress instance\.

**Note**  
For more information, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)\.

1. On the **Networking** tab of the [Lightsail home page](https://lightsail.aws.amazon.com/), choose **Create DNS zone**\.  
![\[Launching and configuring WordPress in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-13.png)

1. Enter your domain, then choose **Create DNS zone**\.  
![\[Launching and configuring WordPress in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-14.png)

1. Make note of the name server addresses listed on the page\.

   You add these name server addresses to your domain name’s registrar to transfer management of your domain’s DNS records to Lightsail\.  
![\[Launching and configuring WordPress in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-15.png)

1. After management of your domain’s DNS records are transferred to Lightsail, add an A record to point the apex of your domain to your WordPress instance, as follows:

   1. In the DNS zone for your domain, choose **Add record**\.

   1. In the **Subdomain** box, enter an @ symbol to map the apex of your domain \(such as example\.com\) to your instance\. The @ symbol explicitly symbolizes that you’re adding an apex record\. It is not added as a subdomain\.

   1. In the **Maps to** box, choose the static IP that you attached to the WordPress instance in the previous step of this tutorial\.

   1. Choose the save icon\.  
![\[Launching and configuring WordPress in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-16.png)

   Allow time for the change to propagate through the internet's DNS before your domain begins routing traffic to your WordPress instance\.

## Step 7: Complete the next steps<a name="tutorial-launching-and-configuring-wordpress-next-steps"></a>

Here are a few additional steps you can perform after launching a WordPress instance in Amazon Lightsail:
+ [Creating a snapshot of your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md)
+ [Enabling or disabling automatic snapshots for instances or disks in Amazon Lightsail](amazon-lightsail-configuring-automatic-snapshots.md)
+ [Creating and attaching additional block storage disks to your Linux\-based Lightsail instances](create-and-attach-additional-block-storage-disks-linux-unix.md)