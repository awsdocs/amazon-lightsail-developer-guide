# Create an access key to use the Amazon Lightsail API or the AWS Command Line Interface<a name="lightsail-how-to-set-up-access-keys-to-use-sdk-api-cli"></a>

 *Last updated: May 17, 2017* 

To use the Lightsail API or the AWS Command Line Interface \(AWS CLI\), you need to create a new access key\. The access key consists of an **Access Key ID** and a **Secret Access Key**\. Use the following procedures to create the key and configure the AWS CLI to make calls to the Lightsail API\.

## Step 1: Create a new access key<a name="set-up-access-keys-create-new-access-key"></a>

You can create a new access key in the AWS Identity and Access Management \(IAM\) console\. 

1. Open **Your Security Credentials** in [the IAM console](https://console.aws.amazon.com/iam/home#/users)\.

1. Choose **Access Keys \(Access Key ID and Secret Access Key\)**\.

1.  Choose **Create New Access Key**\. 
**Note**  
You can have a maximum of two access keys \(active or inactive\) at a time\.

1. Choose **Show Access Key** to see your **Access Key ID** and a **Secret Access Key**\. 

   You can copy them from this screen or choose **Download Key File** to download a \.csv file containing the access keys\.
**Important**  
Keep your access keys in a safe place\. You should name the file something like `MyLightsailKeys.csv` so that you don't struggle to find them later\.

## Step 2: Configure the AWS CLI<a name="set-up-access-keys-"></a>

 If you haven't installed the AWS CLI, you can do that now\. See [Installing the AWS Command Line Interface](http://docs.aws.amazon.com/cli/latest/userguide/installing.html)\. After you install the AWS CLI, you need to configure it so you can use it\. 

1. Open a terminal window or command prompt\.

1. Type `aws configure`\.

1. Paste your **AWS Access Key ID** from the \.csv file you created in the previous step\.

1. Paste your **AWS Secret Access Key** when prompted\.

1. Enter the AWS Region where your resources are located\. For example, if your resources are primarily in Ohio, choose `us-east-2` when prompted for the **Default region name**\.

   For more information about using the AWS CLI `--region` option, see [General Options](http://docs.aws.amazon.com/cli/latest/topic/config-vars.html#general-options) in the *AWS CLI Reference*\.

1. Choose a **Default output format**, such as `json`\.

## Next steps<a name="set-up-access-keys-next-steps"></a>
+  [Install the SDK](https://aws.amazon.com/tools/#sdk) 
+  [Configure the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md) 
+  [Read the API docs](https://docs.aws.amazon.com/lightsail/2016-11-28/api-reference/Welcome.html) 