# Public IP and private IP addresses in Amazon Lightsail<a name="understanding-public-ip-and-private-ip-addresses-in-amazon-lightsail"></a>

**Note**  
A public IP address is the address that is assigned to a Lightsail instance to allow direct access over the Internet\. Web servers, email servers, or any server devices that can be accessed directly from the Internet are all candidates for a public IP address\. A public IP address is globally unique, and can only be assigned to a unique device\.  
A private IP address is the address space allocated by InterNIC to allow organizations to create their own private networks\.

 *Last updated: March 23, 2017* 

## What is the difference between a public IP and a private IP address?<a name="public-ip-addresses-how-different-from-private-ip"></a>

If you want to communicate between instances, it is cheaper and faster to do so using a private IP address\.

If you are working with a web server and a database server in the same data center, it is more secure to communicate over a private network, because you do not need to open any public ports\. If you want to communicate with AWS resources outside of Lightsail \(such as with an Amazon RDS database\), you can do that through [VPC peering](lightsail-how-to-set-up-vpc-peering-with-aws-resources.md)\.

For a detailed explanation of both public and private IP addresses, see [IP address](https://en.wikipedia.org/wiki/IP_address)\.

In addition to public and private IP addresses, Lightsail also has static IP addresses that are essentially public IP addresses that don't change\. You can assign a static IP address to your Lightsail instance so that you'll retain the same public IP address when you restart your instance\. Here's how: [Create a static IP address and attach it to your Lightsail instance](lightsail-create-static-ip.md)\.

Learn more about [Amazon EC2 Instance IP Addressing](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-instance-addressing.html)\.