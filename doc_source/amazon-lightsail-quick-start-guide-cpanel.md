# Quick start guide: cPanel & WHM on Amazon Lightsail<a name="amazon-lightsail-quick-start-guide-cpanel"></a>

 *Last updated: October 14, 2020* 

Here are a few steps you should take to get started after your cPanel & WHM instance is up and running on Amazon Lightsail\.

**Important**  
Your cPanel & WHM instance includes a 15\-day trial license\. After 15 days, you must purchase a license from cPanel to continue using cPanel & WHM\. If you plan on purchasing a license, complete steps 1\-7 of this guide before purchasing your license\.

**Contents:**
+ [Step 1: Change the root user password](#amazon-lightsail-cpanel-root-user-password)
+ [Step 2: Attach a static IP address to your cPanel & WHM instance](#amazon-lightsail-cpanel-attach-static-ip)
+ [Step 3: Sign in to the Web Host Manager for the first time](#amazon-lightsail-cpanel-sign-in)
+ [Step 4: Change the hostname and IP address of your cPanel & WHM instance](#amazon-lightsail-cpanel-change-hostname)
+ [Step 5: Map your domain name to your cPanel & WHM instance](#amazon-lightsail-cpanel-map-your-domain-to-your-instance)
+ [Step 6: Edit the firewall of your instance](#amazon-lightsail-cpanel-edit-firewall)
+ [Step 7: Read the cPanel & WHM documentation and get support](#amazon-lightsail-cpanel-read-the-documentation)
+ [Step 8: Purchase a license for cPanel & WHM](#amazon-lightsail-purchase-cpanel-license)
+ [Step 9: Create a snapshot of your cPanel & WHM instance](#amazon-lightsail-cpanel-create-a-snapshot)

## Step 1: Change the root user password<a name="amazon-lightsail-cpanel-root-user-password"></a>

Complete the following procedure to change the root user password on your cPanel instance\. You will use the root user and password to sign in to the Web Host Manager \(WHM\) console later\.

1. On your instance management page, under the **Connect** tab, choose **Connect using SSH**\.

1. After you're connected, enter the following command to change the password for the root user:

   ```
   sudo passwd
   ```

1. Enter a strong password and confirm it by entering it a second time\.
**Note**  
Your password should not include dictionary words and should be greater than 7 characters\. If you don't follow these guidelines, you'll get a `BAD PASSWORD` warning\.

   Remember this password because you will use it to sign in to the WHM console later in this guide\.

## Step 2: Attach a static IP address to your cPanel & WHM instance<a name="amazon-lightsail-cpanel-attach-static-ip"></a>

The default dynamic public IP address attached to your instance changes every time you stop and start the instance\. Create a static IP address, and attach it to your instance, to keep the public IP address from changing\. Later, when you use your domain name with your instance, you don’t have to update your domain’s DNS records each time you stop and start the instance\. Or if your instance fails, you can restore your instance from a backup and reassign your static IP to your new instance\.

**Important**  
You must specify the public IP address of your cPanel & WHM instance when purchasing a license from cPanel\. The license that you purchase is associated to that IP address\. Because of this, you must attach a static IP to your cPanel & WHM instance if you plan on purchasing a license from cPanel\. Specify your static IP when you purchase a license from cPanel, and keep your static IP for as long as you plan to use your cPanel & WHM license with a Lightsail instance\. If you need to transfer your license to another IP address later, you can submit a request to cPanel\. For more information, see [Transfer a license](https://docs.cpanel.net/manage2/licenses/transfer-a-license/) in the *WHM documentation*\.

On your instance management page, under the **Networking** tab, choose **Create static IP**, then follow the instructions on the page\.

For more information, see [Create a static IP and attach it to an instance in Amazon Lightsail](lightsail-create-static-ip.md)\.

## Step 3: Sign in to the Web Host Manager for the first time<a name="amazon-lightsail-cpanel-sign-in"></a>

Complete the following procedure to sign in to the WHM console for the first time\.

1. Open a web browser and navigate to the following web address\. Replace *<StaticIP>* with the static IP address of your instance\. Be sure to add `:2087` to the end of the address, which is the port on which you will establish a connection to your instance\.

   ```
   https://<StaticIP>:2087
   ```

   **Example:**

   ```
   https://192.0.2.0:2087
   ```
**Important**  
You must include `https://` in your browser's address bar when navigating to the IP address and port of your instance\. Otherwise, you will get an error stating that the site can't be reached\.

   If you're unable to establish a connection when browsing to the static IP address of your instance over port 2087, check that your router, VPN, or internet service provider allows HTTP/HTTPS connections through port 2087\. If it does not, then try to connect using a different network\.

   You might also see a browser warning that your connection is not private, not secure, or that there’s a security risk\. This happens because your cPanel instance does not yet have an SSL/TLS certificate applied to it\. In the browser window, choose **Advanced**, **Details**, or **More information** to view the options that are available\. Then choose to proceed to the website even if it’s not private or secure\.

1. Enter `root` in the **Username** text box\.

1. Enter the root user password in the **Password** text box\.

   This is the password that you specified earlier in the [Step 1: Change the root user password](#amazon-lightsail-cpanel-root-user-password) section of this guide\.

1. Choose **Log in**\.  
![\[WHM sign in page\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/whm-sign-in-page.png)

1. Read the cPanel & WHM terms, then choose **Agree to all** if you would like to proceed\.  
![\[cPanel & WHM terms\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/cpanel-whm-terms.png)

1. On the **Get started with a Free cPanel Trial** page, choose **Log in** to log in to the cPanel store\.

   You must sign in to the cPanel store in order to associate your trial license to your account\. If you don't have a cPanel store account, you should still choose **Log in**, and you will be given the option to create one\.  
![\[cPanel get started with a free trial\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/cpanel-free-trial-getting-started.png)

1. In the **Authorization Request** page that appears, enter your email address or username, and the password for your cPanel store account\.

   If you don't have a cPanel store account, then choose **Create Account** and follow the prompts to create your new cPanel store account\. You will be asked to enter your email address, and will be sent an email to set your cPanel store account password\. We recommend that you set your cPanel store account password using a new browser tab\. When your password is set, you can close that tab and return to your instance to authorize your account, and continue to the next step of this procedure\.

1. Choose **Sign in**\.  
![\[cPanel authorization request\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/cpanel-authorization-request.png)

   After you sign in, your cPanel & WHM instance will acquire a 15\-day trial license that is associated with your cPanel store account\. Go to the [Manage Licenses](http://store.cpanel.net/my/licenses) page in the cPanel store to view your issued licenses, including trial licenses\.

1. Choose **Server Setup** to continue\.  
![\[cPanel trial license confirmation\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/cpanel-trial-license-confirmation.png)

1. Choose **Skip** in the email address and name servers page\. You can configure these later\.  
![\[cPanel email address and nameservers configuration\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/cpanel-email-nameserver-configuration.png)

   The WHM console appears, where you can manage the settings and features for cPanel\.

## Step 4: Change the hostname and IP address of your cPanel & WHM instance<a name="amazon-lightsail-cpanel-change-hostname"></a>

Complete the following steps to change the hostname of your instance, so that you don't have to use its public IP address to access the WHM console\. You should also change the IP address of your instance to the new static IP address that you attached to your instance earlier in the [Step 2: Attach a static IP address to your cPanel & WHM instance](#amazon-lightsail-cpanel-attach-static-ip) section of this guide\.

1. Choose the navigation menu icon in the top\-left section of the WHM console\.  
![\[WHM navigation menu icon\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-whm-menu-icon.png)

1. Enter `Change hostname` in the search text box in the WHM console, then choose the **Change hostname** option in the results\.  
![\[Change the hostname of your cPanel & WHM instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-whm-change-hostname.png)

1. Enter the hostname that you want to use to access the WHM console in the **New hostname** text box\. For example, enter `management.example.com` or `administration.example.com`\.
**Note**  
You can only specify a subdomain as the hostname, and you cannot specify `whm` or `cpanel` as the subdomain\.  
![\[Change the hostname of your cPanel & WHM instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-whm-new-hostname.png)

1. Choose **Change**\.

1. Choose the navigation menu icon in the top\-left section of the WHM console\.  
![\[WHM navigation menu icon\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-whm-menu-icon.png)

1. Choose **Basic WebHost Manager Setup**\.  
![\[Basic WebHost Manager Setup\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-cpanel-whm-basic-setup.png)

1. Under the **All** tab, scroll down and find the **Basic Config** section of the page\.

1. In the IPv4 address text box, enter the new static IP address of the instance\.  
![\[IPv4 address text box\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lightsail-cpanel-whm-ip-address.png)

1. Scroll to the bottom of the page and choose **Save Changes**\.
**Note**  
If you receive an *Invalid License file* error message, wait and try to change the IP address again after a few minutes\.

The hostname and IP address of your instance are now changed, but you must still map your domain name to your cPanel & WHM instance\. You do this by adding an address \(A\) record in the domain name system \(DNS\) of your registered domain name\. The A record resolves the hostname of your instance to the static IP address of your instance\. We show you how to do this in the next section of this guide\.

## Step 5: Map your domain name to your cPanel & WHM instance<a name="amazon-lightsail-cpanel-map-your-domain-to-your-instance"></a>

**Note**  
You can map a domain to your cPanel & WHM instance, which you can use to access the WHM console\. You can also map multiple domains within WHM, which you can use to manage websites within WHM\. This section describes how to map your domain to your cPanel & WHM instance\. For more information about mapping multiple domains within the WHM console, which you do when you create a new account, see [Create a new account](https://docs.cpanel.net/whm/account-functions/create-a-new-account/) in the *WHM documentation*\.

To map your domain name, such as `management.example.com` or `administration.example.com` to your instance, you add an address \(A\) record to the DNS of your domain\. The record maps the hostname of your cPanel & WHM instance to the static IP address of your instance\. The subdomain that you specify in the A record must match the hostname that you specified in the [Step 4: Change the hostname and IP address of your cPanel & WHM instance](#amazon-lightsail-cpanel-change-hostname) section earlier in this guide\. After the A record is added, you can use the following address to access the WHM console of your instance, instead of using your instance's static IP address\. Replace *<InstanceHostName>* with the host name of your instance\.

```
https://<InstanceHostName>/whm
```

**Example:**

```
https//management.example.com/whm
```

DNS records are typically managed and hosted at the registrar where you registered your domain\. However, we recommend that you transfer management of your domain's DNS records to Lightsail so that you can administer it using the Lightsail console\. To do this, sign in to the Lightsail console\. On the Lightsail console home page, choose the **Networking** tab, and then choose **Create DNS zone**\. Follow the instructions on the page to add your domain name to Lightsail\. For more information, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)\.

## Step 6: Edit the firewall of your instance<a name="amazon-lightsail-cpanel-edit-firewall"></a>

The following firewall ports are open by default on your cPanel & WHM instance:
+ SSH \- TCP \- 22
+ DNS \(UDP\) \- UDP \- 53
+ DNS \(TCP\) \- TCP \- 53
+ HTTP \- TCP \- 80
+ HTTPS \- TCP \- 443
+ Custom \- TCP \- 2078
+ Custom \- TCP \- 2083
+ Custom \- TCP \- 2087
+ Custom \- TCP \- 2089

You may need to open additional ports depending on the services and applications that you plan to use on your instance\. Under the **Networking** tab of your instance’s management page, scroll to the Firewall section of the page, and choose **Add rule**\. Choose the application, protocol, and port or port range to open\. Choose **Create** when you're done\.

For more information about which ports to open, see [How to configure your firewall for cPanel services](https://documentation.cpanel.net/display/CKB/How+to+Configure+Your+Firewall+for+cPanel+Services) in the *cPanel documentation*\. For more information about editing your instance's firewall in Lightsail, see [Adding and editing firewall rules in Amazon Lightsail](amazon-lightsail-editing-firewall-rules.md)\.

## Step 7: Read the cPanel & WHM documentation and get support<a name="amazon-lightsail-cpanel-read-the-documentation"></a>

Read the cPanel & WHM documentation to learn how to administer web sites using cPanel and WHM\. For more information, see [cPanel & WHM documentation](https://docs.cpanel.net/)\.

If you have questions about cPanel & WHM or need support, you can contact cPanel using the following resources:
+ [cPanel Discord channel](https://go.cpanel.net/discord)
+ [cPanel subreddit](https://reddit.com/r/cpanel)
+ [cPanel support forum](https://forums.cpanel.net/)

## Step 8: Purchase a license for cPanel & WHM<a name="amazon-lightsail-purchase-cpanel-license"></a>

Your cPanel & WHM instance includes a 15\-day trial license\. After 15 days, you must purchase a license from cPanel to continue using cPanel & WHM\. For more information, see [How to purchase a cPanel license](https://docs.cpanel.net/knowledge-base/cpanel-product/how-to-purchase-a-cpanel-license/) in the cPanel documentation\.

**Important**  
You must specify the public IP address of your cPanel & WHM instance when purchasing a license from cPanel\. The license that you purchase is associated to that IP address\. Because of this, you must attach a static IP to your cPanel & WHM instance as described in [Step 2: Attach a static IP address to your cPanel & WHM instance](#amazon-lightsail-cpanel-attach-static-ip) section of this guide\. Specify your static IP when you purchase a license from cPanel, and keep your static IP for as long as you plan to use your cPanel & WHM license with a Lightsail instance\. If you need to transfer your license to another IP address later, you can submit a request to cPanel\. For more information, see [Transfer a license](https://docs.cpanel.net/manage2/licenses/transfer-a-license/) in the *WHM documentation*\.

## Step 9: Create a snapshot of your cPanel & WHM instance<a name="amazon-lightsail-cpanel-create-a-snapshot"></a>

A snapshot is a copy of the system disk and original configuration of an instance\. A snapshot contains all of the data that is needed to restore your instance \(from the moment when the snapshot was taken\)\. You can use a snapshot as a baseline for new instances, or as a data backup\. You can create a manual snapshot at any time, or you can enable automatic snapshots to have Lightsail create a daily snapshot for you\.

**Note**  
Snapshots of cPanel & WHM instances cannot be exported to Amazon EC2 at this time\.

Under the **Snapshot** tab of your instance’s management page, enter a name for the snapshot, then choose **Create snapshot**\. Or scroll to the **Automatic snapshots** section of the page, and choose the toggle to enable automatic snapshots\.

For more information, see [Creating a snapshot of your Linux or Unix instance in Amazon Lightsail](lightsail-how-to-create-a-snapshot-of-your-instance.md) and [Enabling or disabling automatic snapshots for instances or disks in Amazon Lightsail](amazon-lightsail-configuring-automatic-snapshots.md)\.