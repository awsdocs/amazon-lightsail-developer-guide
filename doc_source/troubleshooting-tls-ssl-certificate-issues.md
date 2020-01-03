# Troubleshooting Lightsail SSL/TLS certificate issues<a name="troubleshooting-tls-ssl-certificate-issues"></a>

 *Last updated: November 29, 2017* 

You might encounter errors with your Lightsail load balancers\. This topic identifies common issues and workarounds for those errors\.

Choose the issue below that best describes your problem, and follow the links to fix the issue\. If you encounter an issue that's not in the list, use the **Questions? Comments?** link at the bottom of this page to submit feedback or contact AWS Customer Support\.

**I can't create a certificate\.**  
There is a quota to the number of certificates you can create in an AWS account\. For more information, see [Quotas](http://docs.aws.amazon.com/acm/latest/userguide/acm-limits.html) in the AWS Certificate Manager User Guide\. The same quotas apply to Lightsail certificates for load balancers\.  
*Actual error message:*  **Sorry, you've requested too many certificates for your account\.**

**My certificate request failed\.**  
If your certificate request failed, you can **Retry** on the **Inbound traffic** tab of the load balancer management page\.  
If you still can't figure out what went wrong, contact AWS Customer Support\.

**My domain showed as invalid\.**  
If you're having trouble verifying that you control a domain, check to see that you have access to the DNS management\. If you do and you followed [these instructions](understanding-tls-ssl-certificates-in-lightsail-https.md) but still can't validate, contact AWS Customer Support\.