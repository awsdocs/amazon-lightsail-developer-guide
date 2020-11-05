# Viewing distribution metrics in Amazon Lightsail<a name="amazon-lightsail-viewing-distribution-health-metrics"></a>

 *Last updated: July 23, 2020* 

After you create a distribution in Amazon Lightsail, you can view its metric graphs on the **Metrics** tab of the distribution’s management page\. Monitoring metrics is an important part of maintaining the reliability, availability, and performance of your resources\. Monitor and collect metric data from your resources regularly so that you can more readily debug a multi\-point failure, if one occurs\. For more information about metrics, see [Metrics in Amazon Lightsail](amazon-lightsail-resource-health-metrics.md)\.

When monitoring your resources, you should establish a baseline for normal resource performance in your environment\. Then you can configure alarms in the Lightsail console to notify you when your resources are performing outside of specified thresholds\. For more information, see [Notifications in Amazon Lightsail](amazon-lightsail-notifications.md) and [Alarms in Amazon Lightsail](amazon-lightsail-alarms.md)\.

**Contents**
+ [Distribution metrics available in Lightsail](#distribution-metrics)
+ [Viewing distribution metrics in the Lightsail console](#viewing-distribution-metrics-console)
+ [Next steps after viewing your distribution metrics](#next-steps-viewing-distribution-metrics)
+ [Additional information](#viewing-distribution-metrics-additional-information)

## Distribution metrics available in Lightsail<a name="distribution-metrics"></a>

The following distribution metrics are available:
+ **Requests** — The total number of viewer requests received by your distribution, for all HTTP methods, and for both HTTP and HTTPS requests\.
+ **Bytes uploaded** — The number of bytes uploaded to your origin by your distribution, using POST and PUT requests\.
+ **Bytes downloaded** — The number of bytes downloaded by viewers for GET, HEAD, and OPTIONS requests\.
+ **Total error rate** — The percentage of all viewer requests for which the response’s HTTP status code was 4xx or 5xx\.
+ **HTTP 4xx error rate** — The percentage of all viewer requests for which the response’s HTTP status code was 4xx\. In these cases, the client or client viewer may have made an error\. For example, a status code of 404 \(Not Found\) means that the client requested an object that could not be found\.
+ **HTTP 5xx error rate** — The percentage of all viewer requests for which the response’s HTTP status code was 5xx\. In these cases, the origin server did not satisfy the request\. For example, a status code of 503 \(Service Unavailable\) means that the origin server is currently unavailable\.

## Viewing distribution metrics in the Lightsail console<a name="viewing-distribution-metrics-console"></a>

Complete the following procedure to view distribution metrics in the Lightsail console\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Networking** tab\.

1. Choose the name of the distribution for which you want to view metrics\.

1. Choose the **Metrics** tab on the distribution management page\.

1. Choose the metric that you want to view in the drop\-down menu under the **Metrics graphs** heading\.

   The graph displays a visual representation of the data points for the chosen metric\.

1. You can perform the following actions on the metrics graph:
   + Change the view of the graph to show data for 1 hour, 6 hours, 1 day, 1 week, and 2 weeks\.
   + Pause your cursor on a data point to view detailed information about that data point\.
   + Add an alarm for the chosen metric to be notified when the metric crosses a threshold you specify\. For more information, see [Alarms in Amazon Lightsail](amazon-lightsail-alarms.md) and [Creating instance metric alarms in Amazon Lightsail](amazon-lightsail-adding-distribution-health-metric-alarms.md)\.

## Next steps after viewing your distribution metrics<a name="next-steps-viewing-distribution-metrics"></a>

There are a few additional tasks that you can perform for your distribution metrics:
+ Add an alarm for the chosen metric to be notified when the metric crosses a threshold you specify\. For more information, see [Alarms in Amazon Lightsail](amazon-lightsail-alarms.md) and [Creating distribution metric alarms in Amazon Lightsail](amazon-lightsail-adding-distribution-health-metric-alarms.md)\.
+ When an alarm is triggered, a notification banner is displayed in the Lightsail console\. To be notified by email and SMS text message, you must add your email address and mobile phone number as notification contacts in each AWS Region where you want to monitor your resources\. For more information, see [Adding notification contacts in Amazon Lightsail](amazon-lightsail-adding-editing-notification-contacts.md)\.
+ To stop receiving notifications, you can remove your email and mobile phone from Lightsail\. For more information, see [Deleting or disabling metric alarms in Amazon Lightsail](amazon-lightsail-deleting-notification-contacts.md)\. You can also disable or delete an alarm to stop receiving notifications for a specific alarm\. For more information, see [Deleting or disabling metric alarms in Amazon Lightsail](amazon-lightsail-deleting-health-metric-alarms.md)\.

## Additional information<a name="viewing-distribution-metrics-additional-information"></a>

Here are some articles to help you manage distributions in Lightsail:
+ [Content delivery network distributions in Amazon Lightsail](amazon-lightsail-content-delivery-network-distributions.md)
+ [Creating Amazon Lightsail distributions](amazon-lightsail-creating-content-delivery-network-distribution.md)
+ [Understanding request and response behaviors of an Amazon Lightsail distribution](amazon-lightsail-distribution-request-and-response.md)
+ [Configuring your WordPress instance to work with your Amazon Lightsail distribution](amazon-lightsail-editing-wp-config-for-distribution.md)
+ [Testing your Amazon Lightsail distribution](amazon-lightsail-testing-distribution.md)
+ [Changing the origin of your Amazon Lightsail distribution](amazon-lightsail-changing-distribution-origin.md)
+ [Changing the caching behavior of your Amazon Lightsail distribution](amazon-lightsail-changing-default-cache-behavior.md)
+ [Resetting the cache of your Amazon Lightsail distribution](amazon-lightsail-resetting-distribution-cache.md)
+ [Changing the plan of your Amazon Lightsail distribution](amazon-lighstail-changing-distribution-plan.md)
+ [Enabling custom domains for your Amazon Lightsail distributions](amazon-lightsail-enabling-distribution-custom-domains.md)
+ [Pointing your domains to your Amazon Lightsail distributions](amazon-lightsail-point-domain-to-distribution.md)
+ [Changing custom domains for your Amazon Lightsail distribution](amazon-lightsail-changing-distribution-custom-domains.md)
+ [Disabling custom domains for your Amazon Lightsail distributions](amazon-lightsail-disabling-distribution-custom-domains.md)
+ [Viewing distribution metrics in Amazon Lightsail](#amazon-lightsail-viewing-distribution-health-metrics)
+ [Deleting your Amazon Lightsail distribution](amazon-lightsail-deleting-distribution.md)
+ [SSL/TLS certificates in Lightsail](understanding-tls-ssl-certificates-in-lightsail-https.md)
+ [Creating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-create-a-distribution-certificate.md)
+ [Validating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-validating-a-distribution-certificate.md)
+ [Viewing SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-viewing-distribution-certificates.md)
+ [Deleting SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-deleting-distribution-certificates.md)