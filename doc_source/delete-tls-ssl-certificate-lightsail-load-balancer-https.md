# Delete an SSL/TLS certificate in Amazon Lightsail<a name="delete-tls-ssl-certificate-lightsail-load-balancer-https"></a>

 *Last updated: July 23, 2020* 

You can delete an SSL/TLS certificate that you're no longer using\. For example, your certificate might be expired and you've already attached an updated certificate that's validated\. If you want to duplicate your certificate before deleting it, you can choose **Duplicate** from the same shortcut menu in step 5, below\.

**Important**  
If the certificate you're deleting is valid and in use, your load balancer will no longer be able to handle encrypted \(HTTPS\) traffic\. Your Lightsail load balancer will still support unencrypted \(HTTP\) traffic\.  
Deleting an SSL/TLS certificate is final and can't be undone\. You have a quota of certificates you can create over a 365\-day period\. For more information, see [Quotas](http://docs.aws.amazon.com/acm/latest/userguide/acm-limits.html) in the AWS Certificate Manager User Guide\.

1. On the Lightsail home page, choose **Networking**\.

1. Choose the load balancer where your SSL/TLS certificate is attached\.

1. Choose the **Inbound traffic** tab on your load balancer's management page\.

1. In the **Certificates** section of the page, choose the ellipsis icon \(⋮\) for the certificate that you want to delete, and choose **Delete**\.

   The **Delete** option is unavailable if the certificate you want to delete is in use\. To delete certificates that are in use, you need to first change the certificate of the load balancer that is using the certificate, or disable HTTPS on the load balancer that is using the certificate\.