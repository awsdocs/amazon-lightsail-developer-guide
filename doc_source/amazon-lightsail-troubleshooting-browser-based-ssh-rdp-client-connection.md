# Troubleshooting connection issues with the Amazon Lightsail browser\-based SSH or RDP client<a name="amazon-lightsail-troubleshooting-browser-based-ssh-rdp-client-connection"></a>

 *Last updated: March 18, 2019* 

You may get an error message when trying to connect to an instance using the browser\-based SSH or RDP clients available in the Amazon Lightsail console\. The possible reasons for this error are discussed in the following sections\.

## Error message: Can’t connect<a name="error-cant-connect-reset-record"></a>

The SSH and RDP browser\-based clients use host key or certificate validation to authenticate an instance when trying to connect to it\. If the instance presents a host key or certificate that doesn’t match the one that Lightsail has on record, one of two error messages display\. Both error messages are shown and described in this section\.

**Can’t connect, reset record**

The following error message displays when there’s a host key or certificate mismatch, and Lightsail determines that the mismatch might have been caused by a recent operating system upgrade, or a deliberate update to the host key or certificate by you or another user\. In this case, Lightsail has determined that the host key or certificate mismatch was not caused by a bad actor on the network between your browser and the instance\.

![\[Host key or certificate mismatch error for the Lightsail browser-based SSH or RDP client.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-browser-ssh-rdp-cant-connect-resest-record.png)

Choose **Reset record** if you expected the mismatch\. This action deletes the host key or certificate that Lightsail has on record for the instance, and permits the browser\-based SSH or RDP session to connect to the instance\.

You can also delete the host key or certificate that Lightsail has on record by using the following AWS Command Line Interface \(AWS CLI\) command\. For *InstanceName*, enter the name of your instance for which you want to delete the known host key or certificate\. For *Region*, enter the AWS Region of the instance\.

```
aws lightsail delete-known-host-keys --region Region --instance-name InstanceName
```

Example:

```
aws lightsail delete-known-host-keys --region us-west-2 --instance-name WordPress-512MB-Oregon-1
```

**Note**  
For more information about the AWS CLI, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

**Can’t connect, contact customer support**

The following error message displays when there’s a host key or certificate mismatch, and Lightsail determines that there is suspicious activity that warrants further investigation, such as a man\-in\-the\-middle attack\.

![\[Host key or certificate mismatch error for the Lightsail browser-based SSH or RDP client.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-browser-ssh-rdp-cant-connect.png)

This error message means that you can’t connect to the instance using the browser\-based SSH or RDP client\. [Contact support](https://console.aws.amazon.com/support/home#/) for assistance\.

## Error message: Can’t connect right now<a name="error-cant-connect-right-now"></a>

The following error message displays when you try to connect to an instance that hasn’t yet started after it’s created, rebooted, or restarted\. Wait a few minutes and then choose **Reconnect** to try again\.

![\[Instance unavailable when trying to connect using the Lightsail browser-based SSH or RDP client.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-browser-ssh-rdp-cant-connect-right-now.png)

If you still can’t connect, [contact support](https://console.aws.amazon.com/support/home#/)\.