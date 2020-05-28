# Edit or delete a DNS zone in Amazon Lightsail<a name="amazon-lightsail-edit-or-delete-a-dns-zone"></a>

 *Last updated: September 21, 2018* 

You can add, edit, or delete the DNS records in your domain's DNS zone\. You can also delete your domain's DNS zone in Amazon Lightsail if you want to transfer management of your domain's DNS records to another DNS hosting provider or back to the registrar where you registered your domain\.

**Note**  
Before you can edit records using the DNS editor in the Lightsail console, you must transfer management of your domain's DNS records to Lightsail\. For more information, see [Creating a DNS zone to manage your domain’s DNS records in Amazon Lightsail](lightsail-how-to-create-dns-entry.md)\.

## Edit DNS records in a DNS zone in Lightsail<a name="lightsail-edit-dns-records"></a>

You can edit the DNS records in your domain's DNS zone at any time using the Lightsail console\.

**To edit the DNS zone**

1. Sign in to the Lightsail console\.

1. Choose the **Networking** tab, and then choose the name of the DNS zone you want to edit\.  
![\[DNS zone editor in the Amazon Lightsail console.\]](https://d9yljz1nd5001.cloudfront.net/en_us/2f596334045058acdba2fdcc5e035cef/images/amazon-lightsail-dns-zone-records.png)

1. On the DNS zone management page, choose one of the following options:
   + To add a new record, choose **Add record**\.
   + To edit an existing record, choose the **Edit** icon next to the record you want to edit\.
   + To delete an existing record, choose the **Delete** icon next to the record you want to delete\.

1. When you're done, choose the **Save** icon to save your changes\.
**Note**  
Allow time for the DNS record changes to propagate through the internet's DNS, which may take several hours\.

## Delete a DNS zone in Lightsail<a name="lightsail-delete-dns-zone"></a>

You can delete your domain's DNS zone in Lightsail\.

**Important**  
If you plan to continue routing traffic through your domain, prepare a different DNS hosting provider before deleting your domain's DNS zone in Lightsail\. Otherwise, all traffic to your website stops when you delete the Lightsail DNS zone\. 

**To delete a DNS zone**

1. On the Lightsail console home page, choose the **Networking** tab\.

1. Choose the name of the DNS zone you want to delete\.

1. Choose the **Delete** tab, then choose **Delete DNS zone**\.

1. Choose **Yes, delete** to confirm the deletion\.

   The DNS zone is deleted from Lightsail\.