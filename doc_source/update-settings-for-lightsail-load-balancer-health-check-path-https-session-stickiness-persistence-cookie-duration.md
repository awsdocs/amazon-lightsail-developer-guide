# Update the settings for your Lightsail load balancer<a name="update-settings-for-lightsail-load-balancer-health-check-path-https-session-stickiness-persistence-cookie-duration"></a>

 *Last updated: November 29, 2017* 

When you create a Lightsail load balancer, you simply choose the AWS Region and the name\. This topic tells you how to update your load balancer to enable more options\.

Of course, you'll need a Lightsail load balancer first\. [Learn how to create a Lightsail load balancer](create-lightsail-load-balancer-and-attach-lightsail-instances.md)

## Health checking<a name="instance-health-checking"></a>

The first thing you're going to want to do is [configure your Lightsail instances for load balancing](configure-lightsail-instances-for-load-balancing.md)\. Once that's done, you can attach an instance to your load balancer\. Attaching an instance starts the health checking process, and you get a **Passed** or **Failed** message on the load balancer management page\.

![\[Health check status indicator\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/target-instances-health-check-passed.png)

You can also customize your health check path\. For example, if your home page loads slowly or has a lot of images on it, you can configure Lightsail to check a different page that loads faster\. [Learn more about customizing the health check path](enable-set-up-health-checking-for-lightsail-load-balancer-metrics.md)

## Encrypted traffic \(HTTPS\)<a name="enable-https-by-attaching-an-ssl-tls-certificate"></a>

You can set up HTTPS to create a more secure experience for your website users\. It's a three\-step process to create and validate an SSL/TLS certificate once you set up your load balancer\.

 [Learn more about HTTPS](understanding-tls-ssl-certificates-in-lightsail-https.md) 

## Session persistence<a name="load-balancer-session-persistence"></a>

Session persistence is useful if you're storing session information locally in the user's browser\. For example, you might be running a Magento e\-commerce application with a shopping cart on Lightsail\. If you turn on session persistence, your users can add items to their shopping carts,end their sessions, and still find the items in their carts when they come back\.

You can also adjust the cookie duration for the persistent session\. This is useful if you want to have a particularly long or short duration\.

 [Learn more about session persistence](enable-session-stickiness-persistence-or-change-cookie-duration.md) 