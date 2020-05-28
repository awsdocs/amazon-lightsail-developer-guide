# Enable session persistence for your load balancer in Amazon Lightsail<a name="enable-session-stickiness-persistence-or-change-cookie-duration"></a>

 *Last updated: November 29, 2017* 

You can enable *session persistence* for your users\. This is helpful if you're storing session information locally in the user's browser\. For example, you might be running a Magento e\-commerce application with a shopping cart on Lightsail\. If you turn on session persistence, your users can add items to their shopping carts, leave the site, and still find the items in their carts when they come back\.

You can also adjust the cookie duration using the AWS Command Line Interface \(AWS CLI\) or the Lightsail API\.

## Enable session persistence<a name="enable-session-persistence"></a>

1. On the Lightsail home page, choose **Networking**\.

1. Choose your load balancer to manage it\.

1. Choose the **Inbound traffic** tab\.

1. Choose **Enable session persistence**\.  
![\[Session persistence enabled\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/session-persistence-enabled.png)

## Adjust the cookie duration<a name="adjust-cookie-duration"></a>

You can also adjust the cookie duration for the persistent session\. This is useful if you want to have a particularly long or short duration\. For example, for many ecommerce sites the duration is quite long\. This lets customers leave and come back without losing items in their shopping carts\.

If you haven't done so already, set up the AWS CLI and configure it\.

 [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md) 

1. Open a command prompt or a terminal window\.

1. Type the following AWS CLI command to increase the cookie duration to three days \(259,200 seconds\)\.

   ```
   aws lightsail update-load-balancer-attribute --load-balancer-name LoadBalancerName --attribute-name SessionStickiness_LB_CookieDurationSeconds --attribute-value 259200
   ```

   In the command, replace *LoadBalancerName* with the name of your load balancer\.

   If successful, you should see the following response\.

   ```
   {
       "operations": [
           {
               "status": "Succeeded",
               "resourceType": "LoadBalancer",
               "isTerminal": true,
               "operationDetails": "SessionStickiness_LB_CookieDurationSeconds",
               "statusChangedAt": 1511758936.174,
               "location": {
                   "availabilityZone": "all",
                   "regionName": "us-west-2"
               },
               "operationType": "UpdateLoadBalancerAttribute",
               "resourceName": "example-load-balancer",
               "id": "681c2bd9-9a51-402b-8ad2-12345EXAMPLE",
               "createdAt": 1511758936.174
           }
       ]
   }
   ```