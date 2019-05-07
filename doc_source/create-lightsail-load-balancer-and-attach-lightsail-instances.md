# Create a Lightsail load balancer and attach instances to it<a name="create-lightsail-load-balancer-and-attach-lightsail-instances"></a>

 *Last updated: November 29, 2017* 

You can create a Lightsail load balancer to add redundancy to your application or to handle more web traffic\. [Learn more about Lightsail load balancers](understanding-lightsail-load-balancers.md)

Before you begin, make sure you've prepared your Lightsail instances for load balancing\. [Configure your instances for load balancing](configure-lightsail-instances-for-load-balancing.md)

## Create a Lightsail load balancer<a name="create-lightsail-load-balancer"></a>

1. On the Lightsail home page, choose **Networking**\.

1. Choose **Create load balancer**\.

1. Choose the location where you want to create your load balancer\.

1. By default, we create your load balancer with port 80 open to accept HTTP requests\.

   After you create your load balancer, you can [create an SSL/TLS certificate and configure HTTPS](create-tls-ssl-certificate-and-attach-to-lightsail-load-balancer-https.md)\.

1. Enter a unique name for your load balancer\.

1. Choose one of the following options to add tags to your load balancer:
   + **Add key\-only tags** or **Edit key\-only tags** \(if tags have already been added\)\. Enter your new tag into the tag key text box, and press **Enter**\. Choose **Save** when you’re done entering your tags to add them, or choose **Cancel** to not add them\.  
![\[Key-only tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/b2fb86c05aa70ef4defbdc74847a0bb8/images/amazon-lightsail-key-only-tags.png)
   + **Create a key\-value tag**, then enter a key into the **Key** text box, and a value into the **Value** text box\. Choose **Save** when you’re done entering your tags, or choose **Cancel** to not add them\.

     Key\-value tags can only be added one at a time before saving\. To add more than one key\-value tag, repeat the previous steps\.  
![\[Key-value tags in the Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/b2fb86c05aa70ef4defbdc74847a0bb8/images/amazon-lightsail-key-value-tag.png)
**Note**  
For more information about key\-only and key\-value tags, see [Tags in Amazon Lightsail](amazon-lightsail-tags.md)\.

1. Choose **Create load balancer**\.

## Attach Lightsail instances to your load balancer<a name="attach-lightsail-instances-to-load-balancer"></a>

After you create your load balancer, Lightsail takes you to the load balancer management page\. If you need to find that page again, choose the **Networking** tab on the home page\. You can choose the name of your Lightsail load balancer to manage it\.

**Note**  
Your Lightsail instance must be running before you can successfully attach it to your load balancer\.

1. On the load balancer management page, choose **Target instances**\.

1. Choose an instance in the same AWS Region as your load balancer\.

1. Choose **Attach**\.
**Note**  
Attachment can take several minutes\. You can attach another instance to this load balancer by choosing **Attach another**\.

## Next steps<a name="create-load-balancer-attach-instances-next-steps"></a>
+  [Configure HTTPS by creating and validating an SSL/TLS certificate](create-tls-ssl-certificate-and-attach-to-lightsail-load-balancer-https.md) 
+  [Update settings for your load balancer](update-settings-for-lightsail-load-balancer-health-check-path-https-session-stickiness-persistence-cookie-duration.md) 
+  [Troubleshoot a health check failure](troubleshooting-lightsail-load-balancer-issues.md) 