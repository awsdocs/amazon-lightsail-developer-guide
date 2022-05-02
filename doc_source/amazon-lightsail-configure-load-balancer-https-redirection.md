# Configuring HTTP to HTTPS redirection on your Amazon Lightsail load balancers<a name="amazon-lightsail-configure-load-balancer-https-redirection"></a>

 *Last updated: April 26, 2022* 

After you configure HTTPS on your Amazon Lightsail load balancer, you can configure an HTTP to HTTPS redirect so that users who browse to your website or web application using an HTTP connection are automatically redirected to the encrypted HTTPS connection\. For more information about load balancers, see [Amazon Lightsail load balancers](understanding-lightsail-load-balancers.md)\.

## Complete the prerequisites<a name="configure-load-balancer-https-redirection-prerequisites"></a>

Complete the following prerequisites if you haven't already:
+ Create a Lightsail load balancer and attach instances to it\. For more information, see [Create an Amazon Lightsail load balancer and attach instances to it](create-lightsail-load-balancer-and-attach-lightsail-instances.md)\.
+ Create an SSL/TLS certificate and attach it to your load balancer to enable HTTPS\. For more information, see [Create an SSL/TLS certificate for your Lightsail load balancer](create-tls-ssl-certificate-and-attach-to-lightsail-load-balancer-https.md)\. For more information about certificates, see [SSL/TLS certificates in Amazon Lightsail](understanding-tls-ssl-certificates-in-lightsail-https.md)\.

## Configuring HTTPS redirection on your load balancer using the Lightsail console<a name="configure-load-balancer-https-redirection-console"></a>

Complete the following procedure to configure HTTPS redirection on your load balancer using the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Networking** tab\.

1. Choose the name of the load balancer for which you want to configure HTTPS redirection\.

1. Choose the **Inbound traffic** tab\.

1. In the **Protocols** section of the page, you can perform one of the following actions:  
![\[The toggle to activate or deactivate HTTP to HTTPS redirection on a load balancer\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lighstail-load-balancer-redirection-toggle.png)
   + Toggle the direction option to active to turn on HTTP to HTTPS redirection\.
   + Toggle the direction option to inactive to turn off HTTP to HTTPS redirection\.

   Your change takes a few moments to become effective\.

## Configuring HTTPS redirection on your load balancer using the AWS CLIAWS CLI<a name="configure-load-balancer-https-redirection-cli"></a>

Complete the following procedure to configure HTTPS redirection on your load balancer using the AWS Command Line Interface \(AWS CLI\)\. You do this by using the `update-load-balancer-attribute` command\. For more information, see [update\-load\-balancer\-attribute](https://docs.aws.amazon.com/cli/latest/reference/lightsail/update-load-balancer-attribute.html) in the *AWS CLI Command Reference*\.

**Note**  
You must install the AWS CLI and configure it for Lightsail before continuing with this procedure\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to configure HTTPS redirection on your load balancer\.

   ```
   aws lightsail update-load-balancer-attribute --load-balancer-name LoadBalancerName --attribute-name HttpsRedirectionEnabled --attribute-value AttributeValue
   ```

   In the command, replace the following example text with your own:
   + *LoadBalancerName* with the name of the load balancer for which you want to activate or deactivate HTTP to HTTPS redirection\.
   + *AttributeValue* with `true` to activate redirection, or `false` to deactivate redirection\.
**Note**  
The `HttpsRedirectionEnabled` attribute in the command specifies that you wish to edit whether HTTPS redirection is enabled or disabled for the specified load balancer\.

   Examples:
   + To activate HTTP to HTTPS redirection on your load balancer:

     ```
     aws lightsail update-load-balancer-attribute --load-balancer-name MyLoadBalancer --attribute-name HttpsRedirectionEnabled --attribute-value true
     ```
   + To deactivate HTTP to HTTPS redirection on your load balancer:

     ```
     aws lightsail update-load-balancer-attribute --load-balancer-name MyLoadBalancer --attribute-name HttpsRedirectionEnabled --attribute-value false
     ```

   Your change takes a few moments to become effective\.