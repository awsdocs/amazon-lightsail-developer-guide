# Configuring reverse DNS for an email server on your Amazon Lightsail instance<a name="amazon-lightsail-configuring-reverse-dns"></a>

 *Last updated: August 21, 2018* 

A reverse Domain Name System \(DNS\) lookup is used by email servers to track where a message originated from, and confirm that it’s not spam or malicious\. A reverse DNS lookup returns the domain name of an IP address\. This is in contrast to a forward DNS lookup, which returns the IP address of a domain\.

For example, if a reverse DNS lookup of the IP address `192.168.1.2` returns the subdomain `mail.example.com`, and a forward DNS lookup of the subdomain `mail.example.com` returns the IP address `192.168.1.2`, then reverse DNS for IP address `192.168.1.2` is forward\-confirmed\. To learn more, see [Forward\-confirmed reverse DNS](https://en.wikipedia.org/wiki/Forward-confirmed_reverse_DNS) on Wikipedia\.

You can configure reverse DNS for your Amazon Lightsail instance by completing prerequisites, and then submitting a request to AWS Support to remove outbound messaging quotas\. These steps are covered in the following sections\.

## Prerequisites<a name="amazon-lightsail-reverse-dns-prerequisites"></a>

To configure reverse DNS, complete the following prerequisites in the order shown:

1. Create a Lightsail instance to be used as the email server\. For more information, see [Create an Amazon Lightsail instance](how-to-create-amazon-lightsail-instance-virtual-private-server-vps.md)\.

1. Create a static IP to be used for the reverse DNS record, and attach it to your running instance\. For more information, see [Create a static IP and attach it to an instance in Amazon Lightsail](lightsail-create-static-ip.md)\.
**Important**  
You cannot use the default public IP, which is assigned to an instance when you first create it, for reverse DNS\. This is because the default public IP for your instance changes when you stop and start your instance\.

1. In your domain’s DNS zone, add an alias record \(A record\) that points a subdomain, such as `mail.example.com`, to the static IP address of your running instance\. This is the subdomain that is returned when a reverse DNS lookup of the static IP address is performed\. For more information, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)\.
**Note**  
We recommend that you transfer management of your domain’s DNS records to Lightsail\. This allows you to manage all of your resources, including your domain, in one place—the Lightsail console\. For more information, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)\.

1. Allow time for changes to propagate through the internet's DNS\. Then, you can continue submitting the request to AWS Support to configure reverse DNS\.

## Submit a request to AWS Support to configure reverse DNS<a name="amazon-lightsail-submit-request-for-reverse-dns"></a>

For security reasons, Lightsail limits outbound messages through port 25 by default\. However, you can request AWS Support to remove this quota from your account and configure reverse DNS for your static IP\.

**To submit a request to AWS Support**

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/) as the AWS account root user\.
**Important**  
The request must be submitted using the AWS account root user\. For more information about the AWS account root user, see [The AWS Account Root User](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html)\.

1. Navigate to the [Request to Remove Email Sending Limitations](https://aws-portal.amazon.com/gp/aws/html-forms-controller/contactus/ec2-email-limit-rdns-request) form, and enter the following required information:
**Note**  
The form references Amazon Elastic Compute \(EC2\) resources, such as elastic IPs \(EIPs\) and EC2 instances\. However, you can also use the form for your Lightsail resources, such as static IPs and Lightsail instances\.
   + **Email address** — Enter the email address where you can receive correspondence about your request\. Your account email address is prepopulated in this text box\.
   + **Use case description** — Enter the reason for requesting removal of the email quota\.
   + **Elastic IP address** — Enter the static IP address that you attached to your instance in step 2 of the prerequisites earlier in this guide\. You can enter up to two static IP addresses\.
   + **Reverse DNS record for EIP** — Enter the subdomain that you defined in step 3 of the prerequisites earlier in this guide\. This is the domain that is returned when the reverse DNS lookup is performed\.

1. Choose **Submit** when done\.

   After your request is completed by AWS Support, your static IP address can be forward\-confirmed with reverse DNS lookup\.

   If you later want to delete the static IP address from your Lightsail account, you must submit a request to AWS Support to remove the reverse DNS configuration\. After the reverse DNS configuration is removed, you can delete the static IP address from your Lightsail account using the Lightsail console\. For more information, see [Delete a static IP in Amazon Lightsail](how-to-delete-static-ip.md)\.