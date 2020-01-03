# Lightsail load balancers<a name="understanding-lightsail-load-balancers"></a>

**Note**  
You can use Lightsail load balancers to add redundancy to your web application or to handle more web traffic\. You can attach Lightsail instances to your load balancer, and then you can configure HTTPS with a validated SSL/TLS certificate\. Lightsail also performs health checks on your instances so that you can monitor error codes, response time, and more\.

 *Last updated: November 29, 2017* 

A Lightsail load balancer distributes incoming web traffic among multiple Lightsail instances, in multiple Availability Zones\. Load balancing increases the availability and fault tolerance of the application on your instances\.

You can add and remove instances from your Lightsail load balancer as your needs change, without disrupting the overall flow of requests to your application\.

With Lightsail load balancing, we create a DNS host name and route any requests sent to this host name to a pool of target Lightsail instances\. You can add as many target instances to your load balancer as you like, as long as you stay within your Lightsail account quotas for total number of instances\.

## Lightsail load balancer features<a name="lightsail-load-balancer-features"></a>

The following features can be configured on Lightsail load balancers:
+ You can set up HTTPS using a validated SSL/TLS certificate so that your load balancer can also handle encrypted traffic\. For more information, see [SSL/TLS certificates in Lightsail](understanding-tls-ssl-certificates-in-lightsail-https.md)\.
**Note**  
By default, a Lightsail load balancer handles unencrypted traffic requests \(HTTP\) through port 80\.
+ By default, a Lightsail load balancer performs health checks on the attached instances at the root of the web application\. The health checks monitor the health of the instances so that the load balancer can send requests only to the healthy instances\. For more information, see [Health checking for a Lightsail load balancer](understanding-lightsail-load-balancer-health-checking.md)\.
+ You can also enable *session persistence* for your users\. This is helpful if you're storing session information locally in the user's browser\. For example, you might be running a Magento e\-commerce application with a shopping cart on Lightsail\. If your users add items to their shopping cart and then end their session, when they come back the shopping cart items will still be there if you turn on session persistence\. [Learn more about session persistence](enable-session-stickiness-persistence-or-change-cookie-duration.md)

## When to use load balancers<a name="when-to-use-lightsail-load-balancers"></a>

You should use a load balancer when you have a website that has occasional spikes in traffic or hosts content that can create a lot of load on an instance when many visitors are using it at once\. For example, if you have an image\-heavy website, you can load balance the image requests with the other page requests\. That way, your pages load faster and your users are happier\.

You can use a load balancer to create a highly available website\. *High availability* refers to how long your website or application stays up over a given time period\. If you have ever experienced a site outage, then a load balancer might help you have more uptime\. You can use a Lightsail load balancer to make your application highly available by adding target instances that are distributed across multiple Availability Zones\.

*Fault tolerance* is a related concept\. If your site continues to function even after one of your instances or your database fails, it is considered tolerant\. A load balancer can help you create a fault tolerant application or website\.

## Recommended Lightsail applications for load balancing<a name="which-applications-are-good-for-load-balancing"></a>

Not all Lightsail applications need load balancers\. If you decide to create a load\-balanced application, you must configure your application first\. For example, to prepare a LAMP stack application for load balancing, you should first create a centralized, dedicated database on a separate Lightsail instance for all the target instances to read/write from\. You might also consider sharing the file system, depending on the type of application you want to deploy\.

We have blueprint\-specific instructions in the following topic: [Configure your instances for load balancing](configure-lightsail-instances-for-load-balancing.md)\.

## Get started using load balancers<a name="get-started-using-lightsail-load-balancers"></a>

You can [create a load balancer](create-lightsail-load-balancer-and-attach-lightsail-instances.md) using the Lightsail console, the AWS Command Line Interface, or the Lightsail API\.

You must also [configure your instances for load balancing](configure-lightsail-instances-for-load-balancing.md)\.

Once you create your load balancer and attach your configured instances, you can enable HTTPS using the following topic\. [Set up HTTPS for your Lightsail load balancer](create-tls-ssl-certificate-and-attach-to-lightsail-load-balancer-https.md)