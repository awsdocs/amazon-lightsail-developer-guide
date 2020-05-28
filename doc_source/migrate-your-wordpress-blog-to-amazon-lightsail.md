# Migrate an existing WordPress blog to Amazon Lightsail<a name="migrate-your-wordpress-blog-to-amazon-lightsail"></a>

 *Last updated: June 19, 2018* 

Looking to change your WordPress hosting provider? Amazon Lightsail is the easiest way to run a WordPress site on AWS\.

You can choose one of our pricing plans \(starting at $3\.50 USD per month\) and have full control over your WordPress installation, including plugins, themes, and more\.

Creating a Lightsail WordPress instance only takes a few minutes\. Follow this tutorial to back up your existing WordPress blog and import it to a new instance running in Lightsail\.

Here's a quick overview of the process:

![\[Overview of the process to convert your existing WordPress blog to Amazon Lightsail\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/steps-for-migrating-your-existing-wordpress-blog-to-amazon-lightsail.png)

Let's get started\!

## Prerequisites<a name="migrate-wordpress-blog-prerequisites"></a>

Before you begin, you'll need the following:

1. You'll need to an AWS account\. [Sign up for AWS](https://console.aws.amazon.com/console/home), or [sign in to AWS](https://console.aws.amazon.com/console/home) if you already have an account\.

1. Make sure your account is set up to use Lightsail\. If it has been a while since you created your account, or if you haven't provided a credit card yet, you may need to log in to the AWS Management Console and update your account first\.

## Step 1: Back up your existing WordPress blog<a name="migrate-wordpress-blog-back-up-wordpress-blog"></a>

You can use WordPress to back up your existing blog\. You'll just need to be able to log into the WordPress admin console and manage your blog\.

1. Navigate to your blog, and then choose **Manage**\.

1. Enter your user name and password to log into the WordPress admin console\.

1. On the WordPress **Dashboard**, choose **Tools**, and then choose **Export**\.

1. On the **Export** page, choose **All content** to export everything as an XML file\.  
![\[Export your WordPress blog using the export tools\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wordpress-blog-export-file.png)

1. Choose **Download export file** to download your old blog as an XML file\.

   Save the XML file in a location that's easy to find\. You'll need it in Step 4\.

## Step 2: Create a new WordPress instance in Lightsail<a name="migrate-wordpress-blog-create-new-wordpress-blog-in-lightsail"></a>

You can create a new WordPress instance in Lightsail in just a few minutes\. Here's how:

1. Go to the [Lightsail home page](https://lightsail.aws.amazon.com/) and log in\.

1. Choose **Create instance**\.

1. Select the AWS Region where you'd like to create your blog\.

   You can choose the default Availability Zone or change that once you select an AWS Region\.

1. WordPress is the default application on this page\. Double\-check that **WordPress** is selected\.  
![\[Pick WordPress as your Lightsail instance image\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-pick-your-instance-image.png)

1. Choose your instance plan \(or *bundle*\)\.

   You can upgrade your Lightsail plan later if needed\. [Here's how](lightsail-how-to-create-instance-from-snapshot.md)\.

1. Enter a name for your instance\.

   Resource names:
   + Must be unique within each AWS Region in your Lightsail account\.
   + Must contain 2 to 255 characters\.
   + Must start and end with an alphanumeric character or number\.
   + Can include alphanumeric characters, numbers, periods, dashes, and underscores\.

1. Choose one of the following options to add tags to your instance:
   + **Add key\-only tags** or **Edit key\-only tags** \(if tags have already been added\)\. Enter your new tag into the tag key text box, and press **Enter**\. Choose **Save** when you’re done entering your tags to add them, or choose **Cancel** to not add them\.  
![\[Key-only tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-key-only-tags.png)
   + **Create a key\-value tag**, then enter a key into the **Key** text box, and a value into the **Value** text box\. Choose **Save** when you’re done entering your tags, or choose **Cancel** to not add them\.

     Key\-value tags can only be added one at a time before saving\. To add more than one key\-value tag, repeat the previous steps\.  
![\[Key-value tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-key-value-tag.png)
**Note**  
For more information about key\-only and key\-value tags, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

1. Choose **Create instance**\.

## Step 3: Log into your new Lightsail WordPress blog<a name="migrate-wordpress-blog-log-into-wordpress-lightsail"></a>

Now that you have a new blog in Lightsail, you'll need to access the WordPress Dashboard to import your old blog data\.

1. Go to the Lightsail home page and find your WordPress blog\.

1. Copy the **Public IP** address to the clipboard\. You'll find this address listed on the Lightsail home page or on the instance details page\.  
![\[Find your Lightsail WordPress blog public IP address on the home page\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-find-your-ip-address-updated.png)

1. Paste the IP address into your browser\.

   You should see something like this:  
![\[WordPress blog made using Lightsail\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/wordpress-blog-lightsail-bitnami-new.png)

1. Choose **Manage** in the lower right corner\.

1. Choose **Login** to log in to the admin console\.

1. Use the default user name \(**user**\)\.

1. To get the login password, you'll need to connect to your instance\.

   The simplest way to connect is to use the terminal icon next to your Lightsail instance\.  
![\[Choose the terminal icon to connect to your Lightsail instance\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-terminal-icon-wordpress-instance-updated.png)

1. Type the following:

   ```
   cat bitnami_application_password
   ```
**Note**  
If you're in a directory other than the user home directory, then type `cat $HOME/bitnami_application_password`\.

   You should see something like this:  
![\[Getting the WordPress password from the browser-based SSH terminal\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-bitnami-wordpress-password.png)

1. Highlight your password in the terminal screen, then choose the clipboard icon\.

1. Highlight the text you want to copy in the clipboard text box, then press Ctrl\+C or Cmd\+C to copy the text to your local clipboard\.  
![\[Copying text using the browser-based clipboard\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/lightsail-terminal-ssh-rdp-clipboard.png)
**Important**  
You should save your password somewhere at this time\. You can always change it later to something that's easier to remember\.

1. Paste your password into the WordPress login page, and then choose **Log In**\.

   If successful, you'll see the WordPress Dashboard\.  
![\[Successful login to the WordPress Dashboard\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wordpress-dashboard.png)

## Step 4: Import your XML file into your new Lightsail blog<a name="migrate-wordpress-blog-in-wordpress"></a>

Once you have successfully logged into the WordPress Dashboard on your new Lightsail instance, follow these steps to import the XML file into your new Lightsail blog\.

1. From the WordPress **Dashboard** on your new Lightsail instance, choose **Tools**\.

1. Choose **Import**, and then choose **Install Now** to install the WordPress import tool\.  
![\[Install the Import tool in the WordPress Dashboard\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-wordpress-dashboard-install-import-tool.png)

1. Once the tool is done installing, choose **Run Importer** to run the import tool\.

1. On the **Import WordPress** page, choose **Browse**\.

1. Find the XML file you saved in *Step 1: Back up your existing WordPress blog*, and then choose **Open**\.

1. Choose **Upload file and import**\.

   Accept the rest of the defaults, and then choose **Submit**\.

## Next steps<a name="migrate-wordpress-blog-lightsail-next-steps"></a>

You can verify that everything worked by choosing your blog \(next to the Home icon\), and then choosing **Visit Site** from the WordPress dashboard\. You can also type the IP address into a browser and view the blog\.

Here are some next steps:
+ Migrate your DNS so that your domain name servers point to the new version of your blog\.
+ Customize your new blog's appearance and/or install some WordPress plugins\.
+  [Enable HTTPS support with SSL certificates](https://docs.bitnami.com/aws/apps/wordpress/#how-to-enable-https-support-with-ssl-certificates) 