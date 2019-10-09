# Configuring the AWS Command Line Interface to work with Amazon Lightsail<a name="lightsail-how-to-set-up-and-configure-aws-cli"></a>

 *Last updated: October 2, 2019* 

The AWS Command Line Interface \(AWS CLI\) is a tool that allows advanced users and developers to control the Amazon Lightsail service by typing commands in the terminal \(on Linux and Unix\) or Command Prompt \(on Windows\)\. You can also control Lightsail using the Lightsail console, a graphical user interface, and the Lightsail application program interface \(API\)\.

In Lightsail, you can install the AWS CLI on your local desktop or install it on your Lightsail instance\.
+ To install the AWS CLI on your local desktop, see [Installing the AWS CLI](http://docs.aws.amazon.com/cli/latest/userguide/installing.html) in the AWS Command Line Interface documentation\.
+ To install the AWS CLI on your Ubuntu\-based Lightsail instance, connect to your instance, and type `sudo apt-get -y install awscli`\.

**Note**  
The AWS CLI should already be installed on the Amazon Linux Lightsail instance\. If you need to reinstall it, connect to your instance, and type `sudo yum install aws-cli`\.

After you install the AWS CLI, you need to obtain access keys and then configure the AWS CLI to use them\. For more information, see [Create an access key to use the Amazon Lightsail API or the AWS Command Line Interface](lightsail-how-to-set-up-access-keys-to-use-sdk-api-cli.md)\.