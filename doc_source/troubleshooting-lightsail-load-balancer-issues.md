# Troubleshooting Lightsail load balancer issues<a name="troubleshooting-lightsail-load-balancer-issues"></a>

 *Last updated: November 29, 2017* 

You might encounter errors with your Lightsail load balancers\. This topic identifies common issues and workarounds for those errors\.

## General load balancer errors<a name="general-load-balancer-errors"></a>

Choose the issue below that best describes your problem, and follow the links to fix the issue\. If you encounter an issue that's not in the list, use the **Questions? Comments?** link at the bottom of this page to submit feedback or contact AWS Customer Support\.

**I can't create a certificate\.**  
There is a quota to the number of certificates you can create in an AWS account\. For more information, see [Quotas](http://docs.aws.amazon.com/acm/latest/userguide/acm-limits.html) in the AWS Certificate Manager User Guide\. The same quota apply to Lightsail certificates for load balancers\.  
*Actual error message:*  **Sorry, you've requested too many certificates for your account\.**

**I can't attach any more instances to my load balancer\.**  
You can attach as many Lightsail instances as you like to your load balancer, as long as you stay within the quota of 20 total Lightsail instances per AWS account\.  
*Actual error message:*  **Sorry, you've reached the maximum number of instances you can attach to this load balancer\.**

**I can't attach a specific instance to my load balancer\.**  
First, check to make sure your Lightsail instance is running\. If it is stopped, you can start it from the instance management page\. Lightsail instances must be running to be successfully attached to a load balancer\.  
It could be that you have attached the same instance to too many load balancers\.  
*Actual error message:*  **Sorry, you've reached the maximum number of times an instance can be registered with a load balancer\.**

**Lightsail can't find the instance I'm trying to attach to my load balancer**  
You might be trying to attach an instance that no longer exists or is not in the same VPC as the target group\.  
*Actual error message:*  **Sorry, the instance you specified doesn't exist, isn't in the same VPC as the target group, or has an unsupported instance type\.**