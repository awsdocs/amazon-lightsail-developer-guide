# Create an access key to use the Amazon Lightsail API or the AWS Command Line Interface<a name="lightsail-how-to-set-up-access-keys-to-use-sdk-api-cli"></a>

 *Last updated: January 25, 2021* 

To use the Lightsail API or the AWS Command Line Interface \(AWS CLI\), you need to create a new access key\. The access key consists of an **Access Key ID** and a **Secret Access Key**\. Use the following procedures to create the key and configure the AWS CLI to make calls to the Lightsail API\.

## Step 1: Create a new access key<a name="set-up-access-keys-create-new-access-key"></a>

You can create a new access key in the AWS Identity and Access Management \(IAM\) console\. 

1. Sign in to the [the IAM console](https://console.aws.amazon.com/iam/home#/users)\.

1. Choose the name of the user for which you want to create an access key\. The user you choose should have full access or specific access to Lightsail actions\.

1. Choose the **Security credentials** tabs\.

1. Choose **Create access key** under the **Access keys** section of the page\.
**Note**  
You can have a maximum of two access keys \(active or inactive\) at a time per user\. If you already have two access keys, then you must delete one of them before creating a new one\. Make sure that an access key is not actively in use before deleting it\.

1. Make note of the **Access key ID** and **Secret access key** listed\. Choose **Show** under the **Secret access key** column to see your **Secret access key**\.

   You can copy them from this screen or choose **Download Key File** to download a \.csv file containing the access key ID and secret access key\.
**Important**  
Keep your access keys in a safe place\. You should name the file something like `MyLightsailKeys.csv` so that you don't struggle to find them later\. If you've downloaded the CSV file from the IAM console, you should delete it after you've completed step 2\. You can create a new access keys later if you need to\.

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