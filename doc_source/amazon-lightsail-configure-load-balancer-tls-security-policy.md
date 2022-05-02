# Configuring TLS security policies on your Amazon Lightsail load balancers<a name="amazon-lightsail-configure-load-balancer-tls-security-policy"></a>

 *Last updated: April 26, 2022* 

After you enable HTTPS on your Amazon Lightsail load balancer, you can configure a TLS security policy for the encrypted connections\. This guide provides information about the security policies that you can configure on Lightsail load balancers, and the procedures for updating your load balancer's security policy\. For more information about load balancers, see [Amazon Lightsail load balancers](understanding-lightsail-load-balancers.md)\.

**Contents**
+ [Security policies overview](#load-balancer-security-policies-overview)
+ [Supported policies](#load-balancer-supported-policies)
+ [Complete the prerequisites](#configure-load-balancer-security-policy-prerequisites)
+ [Configuring a security policy using the Lightsail console](#configure-load-balancer-security-policy-console)
+ [Configuring a security policy using the AWS CLI](#configure-load-balancer-security-policy-cli)

## Security policies overview<a name="load-balancer-security-policies-overview"></a>

Lightsail load balancing uses a Secure Socket Layer \(SSL\) negotiation configuration, known as a security policy, to negotiate SSL connections between a client and the load balancer\. A security policy is a combination of protocols and ciphers\. The protocol establishes a secure connection between a client and a server and ensures that all data passed between the client and your load balancer is private\. A cipher is an encryption algorithm that uses encryption keys to create a coded message\. Protocols use several ciphers to encrypt data over the internet\. During the connection negotiation process, the client and the load balancer present a list of ciphers and protocols that they each support, in order of preference\. By default, the first cipher on the server's list that matches any one of the client's ciphers is selected for the secure connection\. Lightsail load balancers do not support SSL renegotiation for client or target connections\.

The `TLS-2016-08` security policy is configured by default when you enable HTTPS on a Lightsail load balancer\. You can configure a different security policy as needed, as described later in this guide\. You can choose the security policy that is used for only for front\-end connections\. The `TLS-2016-08` security policy is always used for backend connections\. Lightsail load balancers do not support custom security policies\.

## Supported security policies and protocols<a name="load-balancer-supported-policies"></a>

Lightsail load balancers can be configured with the following security policies and protocols:

![\[Supported TLS security policies\]](https://d9yljz1nd5001.cloudfront.net/en_us/1490b6b36a8ed9d4b2232825b79c8222/images/amazon-lighstail-load-balancer-tls-protocols.png)

## Complete the prerequisites<a name="configure-load-balancer-security-policy-prerequisites"></a>

Complete the following prerequisites if you haven't already:
+ Create a Lightsail load balancer and attach instances to it\. For more information, see [Create an Amazon Lightsail load balancer and attach instances to it](create-lightsail-load-balancer-and-attach-lightsail-instances.md)\.
+ Create an SSL/TLS certificate and attach it to your load balancer to enable HTTPS\. For more information, see [Create an SSL/TLS certificate for your Lightsail load balancer](create-tls-ssl-certificate-and-attach-to-lightsail-load-balancer-https.md)\. For more information about certificates, see [SSL/TLS certificates in Amazon Lightsail](understanding-tls-ssl-certificates-in-lightsail-https.md)\.

## Configuring a security policy using the Lightsail console<a name="configure-load-balancer-security-policy-console"></a>

Complete the following procedure to configure a security policy using the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Networking** tab\.

1. Choose the name of the load balancer for which you want to configure a TLS security policy\.

1. Choose the **Inbound traffic** tab\.

1. Choose **Change protocols** under the **TLS security protocols** section of the page\.

1. Select one of the following options in the **Supported protocols** dropdown menu:
   + **TLS version 1\.2** — This option is the most secure but older browsers might be unable to connect\.
   + **TLS version 1\.0, 1\.1, and 1\.2** — This option offers the most compatibility with browsers\.

1. Choose **Save** to apply the selected protocol to your load balancer\.

   Your change takes a few moments to become effective\.

## Configuring a security policy using the AWS CLI<a name="configure-load-balancer-security-policy-cli"></a>

Complete the following procedure to configure a security policy using the AWS Command Line Interface \(AWS CLI\)\. You do this by using the `update-load-balancer-attribute` command\. For more information, see [update\-load\-balancer\-attribute](https://docs.aws.amazon.com/cli/latest/reference/lightsail/update-load-balancer-attribute.html) in the *AWS CLI Command Reference*\.

**Note**  
You must install the AWS CLI and configure it for Lightsail before continuing with this procedure\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to change the TLS security policy for your load balancer\.

   ```
   aws lightsail update-load-balancer-attribute --load-balancer-name LoadBalancerName --attribute-name TlsPolicyName --attribute-value AttributeValue
   ```

   In the command, replace the following example text with your own:
   + *LoadBalancerName* with the name of the load balancer for which you want to change the TLS security policy\.
   + *AttributeValue* with the `TLS-2016-08` or `TLS-FS-1-2-Res-2019-08` security policy\.
**Note**  
The `TlsPolicyName` attribute in the command specifies that you wish to edit the TLS security policy that is configured on the load balancer\.

   Example:

   ```
   aws lightsail update-load-balancer-attribute --load-balancer-name MyLoadBalancer --attribute-name TlsPolicyName --attribute-value TLS-2016-08
   ```

   Your change takes a few moments to become effective\.