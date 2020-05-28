# Troubleshooting the 503 service unavailable error for a Ghost instance in Amazon Lightsail<a name="troubleshoot-ghost-instance-service-unavailable"></a>

 *Last updated: March 27, 2020* 

After you create a new Ghost instance in Amazon Lightsail, and try to access your website, you might see an error stating that the service is unavailable \(503\)\. In some cases, the Ghost service on the instance is not automatically started when the instance is created\. This can happen when you select the $3\.50 USD/month bundle for your instance\. Use the following procedure to start the Ghost service, and resolve the "service is unavailable" error\.

## Starting the Ghost service<a name="start-ghost-service"></a>

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Instances** tab\.

1. Choose the browser\-based SSH client icon for your Ghost instance\.  
![\[Browser-based SSH client in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ghost-quick-connect.png)

1. After the SSH client is connected, enter the following command to restart all services on the instance:

   ```
   sudo /opt/bitnami/ctlscript.sh restart
   ```

   You should see a result similar to the following example:  
![\[Ghost service restarted.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-restart-ghost-services.png)

1. Browse to the public IP address of your instance to confirm that your Ghost website is up and running\.

   The public IP address of your instance is listed next to the instance name in the **Instances** tab of the Lightsail console\.  
![\[Instance public IP address.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ghost-public-ip.png)

   When you browse to the public IP of your new Ghost instance, you should see the default Ghost website template:  
![\[Ghost default website template.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-ghost-website.png)