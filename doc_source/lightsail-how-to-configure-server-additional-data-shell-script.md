# Use a launch script to configure your Amazon Lightsail instance when it starts up<a name="lightsail-how-to-configure-server-additional-data-shell-script"></a>

 *Last updated: October 16, 2017* 

When you create a Linux/Unix\-based instance, you can add a launch script that does things like add software, update software, or configure your instance in some other way\. To configure a Windows\-based instance with additional data, see [Configure your new Lightsail instance using Windows PowerShell](create-powershell-script-that-runs-when-you-create-windows-based-instance-in-lightsail.md)\.

**Note**  
Depending on the machine image you choose, the command to get software on your instance varies\. Amazon Linux uses `yum`, while Debian and Ubuntu both use `apt-get`\. WordPress and other application images use `apt-get` because they run Ubuntu as their operating system\. FreeBSD and openSUSE require additional user configuration to use custom tools such as `freebsd-update` or `zypper` \(openSUSE\)\.

## Example: Configure an Ubuntu server to install Node\.js<a name="example-configure-ubuntu-using-apt-get-install-node-js"></a>

The following example updates the package list and then installs Node\.js through the `apt-get` command\.

1. On the **Create an instance** page, choose **Ubuntu** on the **OS Only** tab\.

1. Scroll down and choose **Add launch script**\.

1. Type the following:

   ```
   # update package list
   apt-get –y update
   # install some of my favorite tools
   apt-get install –y nodejs
   ```
**Note**  
Commands you send to configure your server are run as root, so you don't need to include `sudo` before your commands\.

1. Choose **Create instance**\.

## Example: Configure a WordPress server to download and install a plugin<a name="example-configure-wordpress-install-plugins"></a>

The following example updates the package list, and then downloads and installs the [BuddyPress plugin](https://wordpress.org/plugins/buddypress/) for WordPress\.

1. On the **Create an instance** page, choose **WordPress**\.

1. Choose **Add launch script**\.

1. Type the following:

   ```
   # update package list
   apt-get –y update
   # download wordpress plugin
   wget "https://downloads.wordpress.org/plugin/buddypress.2.7.0.zip"
   apt-get –y install unzip
   # unzip into wordpress plugin directory
   unzip buddypress.2.7.0.zip -d /var/wordpress/plugins
   ```

1. Choose **Create instance**\.