# Tutorial: Launch and configure a LAMP instance in Amazon Lightsail<a name="amazon-lightsail-tutorial-launching-and-configuring-lamp"></a>

 *Last updated: July 26, 2019* 

Amazon Lightsail is the easiest way to get started with Amazon Web Services \(AWS\) if you just need virtual private servers\. Lightsail includes everything you need to launch your project quickly – a virtual machine, SSD\-based storage, data transfer, DNS management, and a static IP – for a low, predictable price\.

This tutorial shows you how to launch and configure a LAMP instance on Lightsail\. It includes steps to connect to your instance via SSH, get the application password for your instance, create a static IP and attach it to your instance, and create a DNS zone and map your domain\. When you’re done with this tutorial, you have the fundamentals to get your instance up and running on Lightsail\.

**Contents**
+ [Step 1: Sign up for AWS](#tutorial-launching-and-configuring-lamp-sign-up-for-aws)
+ [Step 2: Create a LAMP instance in Lightsail](#create-a-lamp-instance)
+ [Step 3: Connect to your instance via SSH and get the application password for your LAMP instance](#tutorial-launching-and-configuring-lamp-connecting-to-your-instance-via-ssh)
+ [Step 4: Install an application on top of your LAMP instance](#install-an-application-on-lamp)
+ [Step 5: Create a Lightsail static IP address and attach it to your LAMP instance](#tutorial-launching-and-configuring-lamp-creating-a-lightsail-static-ip)
+ [Step 6: Create a Lightsail DNS zone and map a domain to your LAMP instance](#creating-a-dns-zone)
+ [Next steps](#tutorial-launching-and-configuring-lamp-next-steps)

## Step 1: Sign up for AWS<a name="tutorial-launching-and-configuring-lamp-sign-up-for-aws"></a>

This tutorial requires an AWS account\. [Sign up for AWS](https://console.aws.amazon.com/console/home), or [sign in to AWS](https://console.aws.amazon.com/console/home) if you already have an account\.

## Step 2: Create a LAMP instance in Lightsail<a name="create-a-lamp-instance"></a>

Get your LAMP instance up and running in Lightsail\. For more information about creating an instance in Lightsail, see [Creating an Amazon Lightsail instance in the Lightsail](how-to-create-amazon-lightsail-instance-virtual-private-server-vps.md) documentation\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the **Instances** tab of the Lightsail home page, choose **Create instance**\.  
![\[Launching and configuring a LAMP instance in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lamp-tutorial-01.png)

1. Choose the AWS Region and Availability Zone for your instance\.  
![\[Launching and configuring a LAMP instance in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-02.png)

1. Choose your instance image\.

   1. Choose **Linux/Unix** as the platform\.

   1. Choose **LAMP \(PHP 7\)** as the blueprint\.  
![\[Launching and configuring a LAMP instance in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lamp-tutorial-03.png)

1. Choose an instance plan\.

   A plan includes a low, predictable cost, machine configuration \(RAM, SSD, vCPU\), and data transfer allowance\. You can try the $3\.50 USD Lightsail plan without charge for one month \(up to 750 hours\)\. AWS credits one free month to your account\.

1. Enter a name for your instance\.

   Resource names:
   + Must be unique within each AWS Region in your Lightsail account\.
   + Must contain 2 to 255 characters\.
   + Must start and end with an alphanumeric character or number\.
   + Can include alphanumeric characters, numbers, periods, dashes, and underscores\.  
![\[Launching and configuring a LAMP instance in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lamp-tutorial-04.png)

1. Choose one of the following options to add tags to your instance:
   + **Add key\-only tags** or **Edit key\-only tags** \(if tags have already been added\)\. Enter your new tag into the tag key text box, and press **Enter**\. Choose **Save** when you’re done entering your tags to add them, or choose **Cancel** to not add them\.  
![\[Key-only tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-key-only-tags.png)
   + **Create a key\-value tag**, then enter a key into the **Key** text box, and a value into the **Value** text box\. Choose **Save** when you’re done entering your tags, or choose **Cancel** to not add them\.

     Key\-value tags can only be added one at a time before saving\. To add more than one key\-value tag, repeat the previous steps\.  
![\[Key-value tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-key-value-tag.png)
**Note**  
For more information about key\-only and key\-value tags, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

1. Choose **Create instance**\.

## Step 3: Connect to your instance via SSH and get the application password for your LAMP instance<a name="tutorial-launching-and-configuring-lamp-connecting-to-your-instance-via-ssh"></a>

The default password to sign in to your database in LAMP is stored on your instance\. Retrieve it by connecting to your instance using the browser\-based SSH terminal in the Lightsail console and running a special command\. For more information, see [Getting the application user name and password for your Certified by Bitnami' instance in Amazon Lightsail](log-in-to-your-bitnami-application-running-on-amazon-lightsail.md) in the Lightsail documentation\.

1. On the **Instances** tab of the Lightsail home page, choose the SSH quick\-connect icon for your LAMP instance\.  
![\[Launching and configuring a LAMP instance in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lamp-tutorial-05.png)

1. After the browser\-based SSH client window opens, enter the following command to retrieve the default application password:

   ```
   cat bitnami_application_password
   ```
**Note**  
If you're in a directory other than the user home directory, then enter `cat $HOME/bitnami_application_password`\.

1. Make note of the password displayed on the screen\. You use this password later to install Bitnami applications on your instance, or to access the MySQL database with the user name of `root`\.  
![\[Launching and configuring a LAMP instance in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lamp-tutorial-06.png)

## Step 4: Install an application on top of your LAMP instance<a name="install-an-application-on-lamp"></a>

Deploy your PHP application on top of your LAMP instance, or install a Bitnami application\. The main directory to deploy your PHP application is `/opt/bitnami/apache2/htdocs`\. Copy your PHP application files to that directory and access the application by browsing to your instance’s public IP address\.

You can also install a Bitnami application using module installers\. Download WordPress, Drupal, Magento, Moodle among other applications from the [Bitnami website](https://bitnami.com/stack/lamp/modules) and extend the functionality of your server\. For more information about installing Bitnami applications, see [Add applications on top of LAMP](https://docs.bitnami.com/aws/infrastructure/lamp/get-started/add-applications-amp/) in the Bitnami documentation\.

## Step 5: Create a Lightsail static IP address and attach it to your LAMP instance<a name="tutorial-launching-and-configuring-lamp-creating-a-lightsail-static-ip"></a>

The default public IP for your LAMP instance changes if you stop and start the instance\. A static IP address, attached to an instance, stays the same even if you stop and start your instance\.

Create a static IP address and attach it to your LAMP instance\. For more information, see [Create a static IP and attach it to an instance in Amazon Lightsail](lightsail-create-static-ip.md) in the Lightsail documentation\.

1. On the **Instances** tab of the Lightsail home page, choose your running LAMP instance\.  
![\[Launching and configuring a LAMP instance in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lamp-tutorial-09.png)

1. Choose the **Networking** tab, then choose **Create static IP**\.  
![\[Launching and configuring a LAMP instance in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-10.png)

1. The static IP location, and attached instance are pre\-selected based on the instance that you chose earlier in this tutorial\.  
![\[Launching and configuring a LAMP instance in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lamp-tutorial-11.png)

1. Name your static IP, then choose **Create**\.  
![\[Launching and configuring a LAMP instance in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-12.png)

## Step 6: Create a Lightsail DNS zone and map a domain to your LAMP instance<a name="creating-a-dns-zone"></a>

Transfer management of your domain's DNS records to Lightsail\. This allows you to more easily map a domain to your LAMP instance, and manage all of your website’s resources using the Lightsail console\. For more information, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md) in the Lightsail documentation\.

1. On the **Networking** tab of the Lightsail home page, choose **Create DNS zone**\.  
![\[Launching and configuring a LAMP instance in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-13.png)

1. Enter your domain, then choose **Create DNS zone**\.  
![\[Launching and configuring a LAMP instance in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-14.png)

1. Make note of the name server addresses listed on the page\.

   You add these name server addresses to your domain name’s registrar to transfer management of your domain’s DNS records to Lightsail\.  
![\[Launching and configuring a LAMP instance in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-15.png)

1. After management of your domain’s DNS records are transferred to Lightsail, add an A record to point the apex of your domain to your LAMP instance, as follows:

   1. In the DNS zone for your domain, choose **Add record**\.

   1. In the **Subdomain** box, enter an @ symbol to map the apex of your domain \(such as example\.com\) to your instance\. The @ symbol explicitly symbolizes that you’re adding an apex record\. It is not added as a subdomain\.

   1. In the **Maps to** box, choose the static IP that you attached to the LAMP instance in the previous step of this tutorial\.

   1. Choose the save icon\.  
![\[Launching and configuring a LAMP instance in Lightsail.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-wordpress-tutorial-16.png)

   Allow time for the change to propagate through the internet's DNS before your domain begins routing traffic to your LAMP instance\.

## Next steps<a name="tutorial-launching-and-configuring-lamp-next-steps"></a>

Here are a few additional steps you can perform after launching a LAMP instance in Amazon Lightsail:
+ [Creating a snapshot of your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md)
+ [Create and attach additional block storage disks to your Linux\-based Lightsail instances](create-and-attach-additional-block-storage-disks-linux-unix.md)