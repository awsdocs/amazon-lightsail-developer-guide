# Set up and configure the AWS Command Line Interface to work with Amazon Lightsail<a name="lightsail-how-to-set-up-and-configure-aws-cli"></a>

 *Last updated: October 16, 2017* 

The AWS Command Line Interface \(AWS CLI\) is a unified tool to manage your AWS services\. With just one tool to download and configure, you can control multiple AWS services from the command line and use scripts to automate them\.

In Lightsail, you can install the AWS CLI on your local machine or install it on your Lightsail instance\.
+ To install the AWS CLI on your local machine, see [Installing the AWS CLI](http://docs.aws.amazon.com/cli/latest/userguide/installing.html)\.
+ To install the AWS CLI on your Ubuntu\-based Lightsail instance, connect to your instance and then type `sudo apt-get -y install awscli`\.

**Note**  
The AWS CLI should already be installed on the Amazon Linux Lightsail instance\. If you need to reinstall it for some reason, connect to your instance and then type `sudo yum install aws-cli`\.

Once you install the AWS CLI, you need to obtain access keys and then configure the AWS CLI\. See [Create a new access key to configure and use the AWS CLI](lightsail-how-to-set-up-access-keys-to-use-sdk-api-cli.md)\.

When you configure the AWS CLI, you'll need to enter the AWS Region where your resources are located\. For example, if your resources are primarily in Ohio, choose `us-east-2` when prompted for the **Default region name**\.

For more information about using the AWS CLI `--region` option, see [General Options](http://docs.aws.amazon.com/cli/latest/topic/config-vars.html#general-options) in the *AWS CLI Reference*\.