# Point your domain to your Lightsail load balancer<a name="add-alias-record-for-lightsail-load-balancer"></a>

 *Last updated: May 28, 2020* 

After you [verify that you control the domain where you want to have encrypted \(HTTPS\) traffic](verify-tls-ssl-certificate-using-dns-cname-https.md), you need to add an address \(A\) record to your domain's DNS hosting provider that points your domain to your Lightsail load balancer\. In this guide, we show you how to add the A record to a Lightsail DNS zone, and a Amazon Route 53 hosted zone\.

## Add an A record in Lightsail<a name="add-address-record-lightsail"></a>

1. On the Lightsail home page, choose **Networking**\.

1. Choose the DNS zone you want to manage\.

1. If you haven't created any records yet, choose **Add record**\.

   If you already have CNAME or other DNS records, choose **Add another**\.

1. For **Type**, choose the default record type \(**A**\)\.

1. For **Sub\-domain**, type `www` in front of `example.com` or don't use a prefix if using an apex domain\.

1. For destination IP, choose your load balancer from the list of available load balancers\.  
![\[Choose your load balancer and create an alias (A) record\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/create-alias-a-record-for-lightsail-load-balancer.png)

1. Choose **Save**\.

## Add an A record in Route 53<a name="add-address-record-route-53"></a>

1. Open the [Amazon Route 53 console](https://console.aws.amazon.com/route53/)\.

1. In the navigation pane, choose **Hosted Zones**\.

1. Choose the name of the hosted zone that has the domain name that you want to use to route traffic to your load balancer\.

1. Choose **Create Record Set**\.

1. For **Name**, type `www` in front of `example.com`, or don't use a prefix if using an apex domain\.

1. Accept the default record \(**A \- IPv4 address**\)\.

1. For **Alias**, choose **Yes**\.

1. Go to the Lightsail console and copy the **DNS name** from your load balancer management page\.  
![\[DNS name on the load balancer management page\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/dns-name-on-load-balancer-management-page.png)

1. Go back to the Amazon Route 53 console and paste the DNS name into the **Alias Target** field\.

1. Accept the default value of **Simple** for **Routing Policy**, and leave **No** selected for **Evaluate Target Health**\.

   Lightsail already performs health checks on your load balancer\. [Learn more about health checking](enable-set-up-health-checking-for-lightsail-load-balancer-metrics.md)

   Your record set should look something like this\.  
![\[Create a record set in Route 53 to point an alias to your Lightsail load balancer\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/create-record-set-alias-record-route-53.png)

1. Choose **Create**\.