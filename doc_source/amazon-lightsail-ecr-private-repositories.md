# Managing Amazon Lightsail container service access to Amazon ECR private repositories<a name="amazon-lightsail-ecr-private-repositories"></a>

 *Last updated: May 26, 2022* 

Amazon Elastic Container Registry \(Amazon ECR\) is an AWS managed container image registry service that supports private repositories with resource\-based permissions using AWS Identity and Access Management \(IAM\)\. You can give your Amazon Lightsail container services access to your Amazon ECR private repositories in the same AWS Region\. Then, you can deploy images from your private repository to your container services\.

In this guide, we show you how to manage access for your Lightsail container services and your Amazon ECR private repositories by using the Lightsail console and the AWS Command Line Interface \(AWS CLI\)\. For more information about container services, see [Container services in Amazon Lightsail](amazon-lightsail-container-services.md)\. For more information about Amazon ECR, see the [Amazon ECR User Guide](https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html)\.

**Note**  
We recommend that you use the Lightsail console to manage container service access to Amazon ECR private repositories\. When you use the console, you don't have to manually add the Amazon Resource Name \(ARN\) of the IAM role principal to your private repositories\. Lightsail automatically adds the ARN for you\. For more information, see the [Manage access to private repositories using the Lightsail console](amazon-lightsail-container-service-ecr-private-repo-access.md#ecr-private-repo-access-lightsail-console) section in this guide\.

**Contents**
+ [Required permissions](#ecr-private-repos-permissions1)
+ [Manage access to private repositories using the Lightsail console](#ecr-private-repo-access-lightsail-console1)
+ [Manage access to private repositories using the AWS CLI](#ecr-private-repo-access-cli1)
  + [Activate or deactivate the Amazon ECR image puller IAM role](#activate-ecr-puller-role1)

    [Determine if your Amazon ECR private repository has a policy statement](#identify-ecr-repo-policy-statement1)
    + [Add a policy to a private repository that doesn't have a policy statement](#ecr-private-repo-add-policy-no-policy1)
    + [Add a policy to a private repository that has a policy statement](#ecr-private-repo-add-policy-existing-policy1)
+ [Additional information about container services](#container-service-ecr-private-repo-access-info1)

## Required permissions<a name="ecr-private-repos-permissions1"></a>

The user who will manage access for Lightsail container services to Amazon ECR private repositories must have one of the following permissions policies in IAM\. For more information, see [Adding and removing IAM identity permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_manage-attach-detach.html) in the *AWS Identity and Access Management User Guide*\.

**Grant access to any Amazon ECR private repository**

The following permissions policy grants a user permission to configure access to any Amazon ECR private repository\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ManageEcrPrivateRepositoriesAccess",
            "Effect": "Allow",
            "Action": [
                "ecr:SetRepositoryPolicy",
                "ecr:DescribeRepositories",
                "ecr:DeleteRepositoryPolicy",
                "ecr:GetRepositoryPolicy"
            ],
            "Resource": "arn:aws:ecr:*:AwsAccountId:repository/*"
        }
    ]
}
```

In the policy, replace *AwsAccountId* with your AWS account ID number\.

**Grant access to a specific Amazon ECR private repository**

The following permissions policy grants a user permission to configure access to a specific Amazon ECR private repository, in a specific AWS Region\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ManageEcrPrivateRepositoriesAccess",
            "Effect": "Allow",
            "Action": [
                "ecr:SetRepositoryPolicy",
                "ecr:DescribeRepositories",
                "ecr:DeleteRepositoryPolicy",
                "ecr:GetRepositoryPolicy"
            ],
            "Resource": "arn:aws:ecr:AwsRegion:AwsAccountId:repository/RepositoryName"
        }
    ]
}
```

In the policy, replace the following example text with your own:
+ *AwsRegion* — The AWS Region code \(for example, `us-east-1`\) of the private repository\. Your Lightsail container service must be in the same AWS Region as the private repositories that you want to access\.
+ *AwsAccountId* — Your AWS account ID number\.
+ *RepositoryName* — The name of the private repository for which you want to manage access\.

Following is an example of the permissions policy populated with example values\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ManageEcrPrivateRepositoriesAccess",
            "Effect": "Allow",
            "Action": [
                "ecr:SetRepositoryPolicy",
                "ecr:DescribeRepositories",
                "ecr:DeleteRepositoryPolicy",
                "ecr:GetRepositoryPolicy"
            ],
            "Resource": "arn:aws:ecr:us-east-1:111122223333:repository/my-private-repo"
        }
    ]
}
```

## Manage access to private repositories using the Lightsail console<a name="ecr-private-repo-access-lightsail-console1"></a>

Complete the following procedure to configure access for a Lightsail container service to an Amazon ECR private repository\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Containers** tab\.

1. Choose the name of the container service for which you want to configure access to an Amazon ECR private repository\.  
![\[Container service in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/container-service-card.png)

1. Choose the **Images** tab\.  
![\[Images tab in the container service management page of the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/container-service-images-tab.png)

1. Choose one of the following options in the **Amazon ECR private repositories** section of the page:
   + **Add repository** to grant access for your container service to an Amazon ECR private repository\. To finish adding the repository, continue to step 6 of this procedure\.
   + **Remove** to remove access for your container service from a previously added Amazon ECR private repository\. Access from your container service to the repository is immediately removed\.  
![\[Amazon ECR private repositories section of the Images tab\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/container-service-ecr-repos-section.png)

1. In the dropdown that appears, select the private repository that you would like to access\.  
![\[Amazon ECR private repositories dropdown selection\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/container-service-ecr-repos-selection.png)

1. Choose **Add**\.

   Lightsail takes a few moments to activate the Amazon ECR image puller IAM role for your container service, which includes a principal Amazon Resource Name \(ARN\)\. Lightsail then automatically adds the IAM role principal ARN to the permissions policy of the Amazon ECR private repository that you selected\. This grants your container service access to the private repository and its images\. Don't close the browser window until the modal that appears indicates that the process is completed and you can choose **Continue**\.  
![\[Modal confirming that permissions are being added to Amazon ECR private repository\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/container-service-ecr-repos-confirmation-modal.png)

1. Choose **Continue** when the activation is completed\.

The selected Amazon ECR private repository is listed in the **Amazon ECR private repositories** section of the page\. To use an image from your repository, specify the URI format that is displayed on the page in your container service deployment\. In the URI, replace the example *tag* with the tag of the image you want to deploy\. For more information, see [Creating and managing deployments for your Amazon Lightsail container services](amazon-lightsail-container-services-deployments.md)\.

![\[Next steps after adding an Amazon ECR private repository\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/container-service-ecr-repos-next-steps.png)

## Manage access to private repositories using the AWS CLI<a name="ecr-private-repo-access-cli1"></a>

Managing access for a Lightsail container service to an Amazon ECR private repository using the AWS Command Line Interface \(AWS CLI\) requires the following steps:

1. **Activate or deactivate the Amazon ECR image puller IAM role** — Use the AWS CLI `update-container-service` command for Lightsail to activate or deactivate the Amazon ECR image puller IAM role\. A principal Amazon Resource Name \(ARN\) is created for the Amazon ECR image puller IAM role when you activate it\. For more information, see the [Activate or deactivate the Amazon ECR image puller IAM role](#activate-ecr-puller-role1) section of this guide\.

1. **Determine if your Amazon ECR private repository has a policy statement** — After you activate the Amazon ECR image puller IAM role, you need to determine if the Amazon ECR private repository that you want to access with your container service has an existing policy statement\. For more information, see [Determine if your Amazon ECR private repository has a policy statement](#identify-ecr-repo-policy-statement1) later in this guide\. 

   You add the IAM role principal ARN to your repository using one of the following methods, depending on whether your repository has an existing policy statement:

   1. **Add a policy to a private repository that doesn't have a policy statement** — Use the AWS CLI `set-repository-policy` command for Amazon ECR to add the Amazon ECR image puller role principal ARN for your container service to a private repository that has an existing policy\. For more information, see [Add a policy to a private repository that doesn't have a policy statement](#ecr-private-repo-add-policy-no-policy1) later in this guide\.

   1. **Add a policy to a private repository that has a policy statement** — Use the AWS CLI `set-repository-policy` command for Amazon ECR to add the Amazon ECR image puller role for your container service to a private repository that doesn't have an existing policy\. For more information, see [Add a policy to a private repository that has a policy statement](#ecr-private-repo-add-policy-existing-policy1) later in this guide\.
**Important**  
Lightsail automatically adds the Amazon ECR image puller IAM role principal ARN to your Amazon ECR private repositories when you use the Lightsail console to configure access\. When you use the console, you don't have to manually add the IAM role principal ARN to your private repositories\. For more information, see [Manage access to private repositories using the Lightsail console](amazon-lightsail-container-service-ecr-private-repo-access.md#ecr-private-repo-access-lightsail-console) earlier in this guide\.

### Activate or deactivate the Amazon ECR image puller IAM role<a name="activate-ecr-puller-role1"></a>

Complete the following procedure to activate or deactivate the Amazon ECR image puller IAM role for your Lightsail container service\. You can activate or deactivate the Amazon ECR image puller IAM role using the AWS CLI `update-container-service` command for Lightsail\. For more information, see [update\-container\-service](https://docs.aws.amazon.com/cli/latest/reference/lightsail/update-container-service.html) in the *AWS CLI Command Reference*\.

**Note**  
You must install the AWS CLI and configure it for Lightsail before you can continue with this procedure\. For more information, see [Configuring the AWS Command Line Interface to work with Amazon Lightsail](lightsail-how-to-set-up-and-configure-aws-cli.md)\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to update a container service and activate or deactivate the Amazon ECR image puller IAM role\.

   ```
   aws lightsail update-container-service --service-name ContainerServiceName --private-registry-access ecrImagePullerRole={isActive=RoleActivationState} --region AwsRegionCode
   ```

   In the command, replace the following example text with your own:
   + *ContainerServiceName* — The name of the container service for which to activate or deactivate the Amazon ECR image puller IAM role\.
   + *RoleActivationState* — The activation state of the Amazon ECR image puller IAM role\. Specify `true` to activate the role, or `false` to deactivate it\.
   + *AwsRegionCode* — The AWS Region code of the container service \(for example, `us-east-1`\)\.

   Examples:
   + To activate the Amazon ECR image puller IAM role:

     ```
     aws lightsail update-container-service --service-name my-container-service --private-registry-access ecrImagePullerRole={isActive=true} --region us-east-1
     ```
   + To deactivate the Amazon ECR image puller IAM role:

     ```
     aws lightsail update-container-service --service-name my-container-service --private-registry-access ecrImagePullerRole={isActive=false} --region us-east-1
     ```

1. If you:
   + **Activated the Amazon ECR image puller role** — Wait at least 30 seconds after getting the previous response\. Then, continue to the next step to get the principal ARN of the Amazon ECR image puller IAM role for your container service\.
   + **Deactivated the Amazon ECR image puller role** — If you previously added the Amazon ECR image puller IAM role principal ARN to the permissions policy of your Amazon ECR private repository, you should remove that permissions policy from your repository\. For more information, see [Deleting a private repository policy statement](https://docs.aws.amazon.com/AmazonECR/latest/userguide/delete-repository-policy.html) in the *Amazon ECR User Guide*\.

1. Enter the following command to get the principal ARN of the Amazon ECR image puller IAM role for your container service\.

   ```
   aws lightsail get-container-services --service-name ContainerServiceName --region AwsRegionCode
   ```

   In the command, replace the following example text with your own:
   + *ContainerServiceName* — The name of your container service for which to get the Amazon ECR image puller IAM role principal ARN\.
   + *AwsRegionCode* — The AWS Region code of the container service \(for example, `us-east-1`\)\.

   Example:

   ```
   aws lightsail get-container-services --service-name my-container-service --region us-east-1
   ```

   Look for the ECR image puller IAM role principal ARN in the response\. If a role is listed, copy it or write it down\. You will need it for the next section of this guide\. Next, you need to determine if there is an existing policy statement on the Amazon ECR private repository that you want to access with your container service\. Continue to the [Determine if your Amazon ECR private repository has a policy statement](#identify-ecr-repo-policy-statement1) section of this guide\.

### Determine if your Amazon ECR private repository has a policy statement<a name="identify-ecr-repo-policy-statement1"></a>

Use the following procedure to determine if your Amazon ECR private repository has a policy statement\. You can use the AWS CLI `get-repository-policy` command for Amazon ECR\. For more information, see [update\-container\-service](https://docs.aws.amazon.com/cli/latest/reference/ecr/get-repository-policy.html) in the *AWS CLI Command Reference*\.

**Note**  
You must install the AWS CLI and configure it for Amazon ECR before you can continue with this procedure\. For more information, see [Setting up with Amazon ECR](https://docs.aws.amazon.com/AmazonECR/latest/userguide/get-set-up-for-amazon-ecr.html) in the *Amazon ECR User Guide*\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to get the policy statement for a specific private repository\.

   ```
   aws ecr get-repository-policy --repository-name RepositoryName --region AwsRegionCode
   ```

   In the command, replace the following example text with your own:
   + *RepositoryName* — The name of the private repository for which you want to configure access for a Lightsail container service\.
   + *AwsRegionCode* — The AWS Region code of the private repository \(for example, `us-east-1`\)\.

   Example:

   ```
   aws ecr get-repository-policy --repository-name my-private-repo --region us-east-1
   ```

   You should see one of the following responses:
   + **RepositoryPolicyNotFoundException** — Your private repository does not have a policy statement\. If your repository doesn't have a policy statement, follow the steps in the [Add a policy to a private repository that doesn't have a policy statement](#ecr-private-repo-add-policy-no-policy1) section later in this guide\.  
![\[Response to the get-repository-policy command for a private repository that doesn't have a policy statement\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/ecr-no-policy-statement.png)
   + **A repository policy was found** \- Your private repository has a policy statement, and it is displayed in the response of your request\. If your repository has a policy statement, copy the existing policy and then follow the steps in the [Add a policy to a private repository that has a policy statement](#ecr-private-repo-add-policy-existing-policy1) section later in this guide\.  
![\[Response to the get-repository-policy command for a private repository that has a policy statement\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/ecr-existing-policy-statement.png)

### Add a policy to a private repository that doesn't have a policy statement<a name="ecr-private-repo-add-policy-no-policy1"></a>

Complete the following procedure to add a policy to an Amazon ECR private repository that doesn't have a policy statement\. The policy that you add must include the Amazon ECR image puller IAM role principal ARN of your Lightsail container service\. This grants access for your container service to deploy images from the private repository\.

**Important**  
Lightsail automatically adds the Amazon ECR image puller role to your Amazon ECR private repositories when you use the Lightsail console to configure access\. In that case, you don't have to manually add the Amazon ECR image puller role to your private repositories using the procedure in this section\. For more information, see [Manage access to private repositories using the Lightsail console](amazon-lightsail-container-service-ecr-private-repo-access.md#ecr-private-repo-access-lightsail-console) earlier in this guide\.

You can add a policy to a private repository using the AWS CLI\. You do this by creating a JSON file that contains the policy, and then referencing that file with the `set-repository-policy` command for Amazon ECR\. For more information, see [set\-repository\-policy](https://docs.aws.amazon.com/cli/latest/reference/ecr/set-repository-policy.html) in the *AWS CLI Command Reference*\.

**Note**  
You must install the AWS CLI and configure it for Amazon ECR before continuing with this procedure\. For more information, see [Setting up with Amazon ECR](https://docs.aws.amazon.com/AmazonECR/latest/userguide/get-set-up-for-amazon-ecr.html) in the *Amazon ECR User Guide*\.

1. Open a text editor, and paste the following policy statement into a new text file\.

   ```
   { 
     "Version": "2008-10-17",
     "Statement": [
     {
         "Sid": "AllowLightsailPull-ecr-private-repo-demo",
         "Effect": "Allow",
         "Principal": {
           "AWS": "IamRolePrincipalArn"
         },
         "Action": [
           "ecr:BatchGetImage",
           "ecr:GetDownloadUrlForLayer"
         ]
       }
     ]
   }
   ```

   In the text, replace *IamRolePrincipalArn* with the Amazon ECR image puller IAM role principal ARN of your container service that you got earlier in this guide\.

1. Save the file as `ecr-policy.json` to an accessible location on your computer \(for example, `C:\Temp\ecr-policy.json` on Windows or `/tmp/ecr-policy.json` on macOS or Linux\)\.

1. Write down the file path location of the `ecr-policy.json` file created\. You will specify it in a command later in this procedure\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to set the policy statement for the private repository that you want to access with your container service\.

   ```
   aws ecr set-repository-policy --repository-name RepositoryName --policy-text file://path/to/ecr-policy.json --region AwsRegionCode
   ```

   In the command, replace the following example text with your own:
   + *RepositoryName* — The name of the private repository for which you want to add the policy\.
   + *path/to/* — The path to the `ecr-policy.json` file on your computer that you created earlier in this guide\.
   + *AwsRegionCode* — The AWS Region code of the private repository \(for example, `us-east-1`\)\.

   Examples:
   + On Windows:

     ```
     aws ecr set-repository-policy --repository-name my-private-repo --policy-text file://C:\Temp\ecr-policy.json --region us-east-1
     ```
   + On macOS or Linux:

     ```
     aws ecr set-repository-policy --repository-name my-private-repo --policy-text file:///tmp/ecr-policy.json --region us-east-1
     ```

   Your container service is now able to access your private repository and its images\. To use an image from your repository, specify the following URI as the **Image** value for your container service deployment\. In the URI, replace the example *tag* with the tag of the image you want to deploy\. For more information, see [Creating and managing deployments for your Amazon Lightsail container services](amazon-lightsail-container-services-deployments.md)\.

   ```
   AwsAccountId.dkr.ecr.AwsRegionCode.amazonaws.com/RepositoryName:ImageTag
   ```

   In the URI, replace the following example text with your own:
   + *AwsAccountId* — Your AWS account ID number\.
   + *AwsRegionCode* — The AWS Region code of the private repository \(for example, `us-east-1`\)\.
   + *RepositoryName* — The name of the private repository from which to deploy a container image\.
   + *ImageTag* — The tag of the container image from the private repository to deploy on your container service\.

   Example:

   ```
   111122223333.dkr.ecr.us-east-1.amazonaws.com/my-private-repo:myappimage
   ```

### Add a policy to a private repository that has a policy statement<a name="ecr-private-repo-add-policy-existing-policy1"></a>

Complete the following procedure to add a policy to an Amazon ECR private repository that has a policy statement\. The policy that you add must include the existing policy and a new policy that contains the Amazon ECR image puller IAM role principal ARN of your Lightsail container service\. This maintains the existing permissions on your private repository while also granting access for your container service to deploy images from the private repository\.

**Important**  
Lightsail automatically adds the Amazon ECR image puller role to your Amazon ECR private repositories when you use the Lightsail console to configure access\. In that case, you don't have to manually add the Amazon ECR image puller role to your private repositories using the procedure in this section\. For more information, see [Manage access to private repositories using the Lightsail console](amazon-lightsail-container-service-ecr-private-repo-access.md#ecr-private-repo-access-lightsail-console) earlier in this guide\.

You can add a policy to a private repository using the AWS CLI\. You do this by creating a JSON file that contains the existing policy and the new policy\. Then, reference that file with the `set-repository-policy` command for Amazon ECR\. For more information, see [set\-repository\-policy](https://docs.aws.amazon.com/cli/latest/reference/ecr/set-repository-policy.html) in the *AWS CLI Command Reference*\.

**Note**  
You must install the AWS CLI and configure it for Amazon ECR before you can continue with this procedure\. For more information, see [Setting up with Amazon ECR](https://docs.aws.amazon.com/AmazonECR/latest/userguide/get-set-up-for-amazon-ecr.html) in the *Amazon ECR User Guide*\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to get the policy statement for a specific private repository\.

   ```
   aws ecr get-repository-policy --repository-name RepositoryName --region AwsRegionCode
   ```

   In the command, replace the following example text with your own:
   + *RepositoryName* — The name of the private repository for which you want to configure access for a Lightsail container service\.
   + *AwsRegionCode* — The AWS Region code of the private repository \(for example, `us-east-1`\)\.

   Example:

   ```
   aws ecr get-repository-policy --repository-name my-private-repo --region us-east-1
   ```

1. In the response, copy the existing policy and continue to the next step\.

   You should copy only the content of the `policyText` that appears between the double quotes, as highlighted in the following example\.  
![\[Response to the get-repository-policy command for a private repository that doesn't have a policy statement\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/ecr-existing-policy-copy-statement.png)

1. Open a text editor, and paste the existing policy from your private repository that you copied in the previous step\.

   The result should look like the following example\.  
![\[Example policy statement JSON file\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/ecr-existing-policy-statement-json.png)

1. In the text that you pasted, replace `\n` with line breaks and delete the remaining `\`\.

   The result should look like the following example\.  
![\[Example edited policy statement JSON file\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/ecr-existing-policy-statement-json-edited.png)

1. Paste the following policy statement at the end of the text file\.

   ```
   ,
   { 
     "Version": "2008-10-17",
     "Statement": [
     {
         "Sid": "AllowLightsailPull-ecr-private-repo-demo",
         "Effect": "Allow",
         "Principal": {
           "AWS": "IamRolePrincipalArn"
         },
         "Action": [
           "ecr:BatchGetImage",
           "ecr:GetDownloadUrlForLayer"
         ]
       }
     ]
   }
   ```

1. In the text, replace *IamRolePrincipalArn* with the Amazon ECR image puller IAM role principal ARN of your container service that you got earlier in this guide\.

   The result should look like the following example\.  
![\[Example complete policy statement JSON file\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/ecr-existing-policy-statement-json-completed.png)

1. Save the file as `ecr-policy.json` to an accessible location on your computer \(for example, `C:\Temp\ecr-policy.json` on Windows or `/tmp/ecr-policy.json` on macOS or Linux\)\.

1. Write down the file path location of the `ecr-policy.json` file\. You will specify it in a command later in this procedure\.

1. Open a Command Prompt or Terminal window\.

1. Enter the following command to set the policy statement for the private repository that you want to access with your container service\.

   ```
   aws ecr set-repository-policy --repository-name RepositoryName --policy-text file://path/to/ecr-policy.json --region AwsRegionCode
   ```

   In the command, replace the following example text with your own:
   + *RepositoryName* — The name of the private repository for which you want to add the policy\.
   + *path/to/* — The path to the `ecr-policy.json` file on your computer that you created earlier in this guide\.
   + *AwsRegionCode* — The AWS Region code of the private repository \(for example, `us-east-1`\)\.

   Examples:
   + On Windows:

     ```
     aws ecr set-repository-policy --repository-name my-private-repo --policy-text file://C:\Temp\ecr-policy.json --region us-east-1
     ```
   + On macOS or Linux:

     ```
     aws ecr set-repository-policy --repository-name my-private-repo --policy-text file:///tmp/ecr-policy.json --region us-east-1
     ```

   You should see a response similar to the following example\.  
![\[Response to the set-repository-policy command\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/ecr-set-policy-statement-response.png)

   If you run the `get-repository-policy` command again, you should see the new additional policy statement on your private repository\. Your container service is now able to access your private repository and its images\. To use an image from your repository, specify the following URI as the **Image** value for your container service deployment\. In the URI, replace the example *tag* with the tag of the image you want to deploy\. For more information, see [Creating and managing deployments for your Amazon Lightsail container services](amazon-lightsail-container-services-deployments.md)\.

   ```
   AwsAccountId.dkr.ecr.AwsRegionCode.amazonaws.com/RepositoryName:ImageTag
   ```

   In the URI, replace the following example text with your own:
   + *AwsAccountId* — Your AWS account ID number\.
   + *AwsRegionCode* — The AWS Region code of the private repository \(for example, `us-east-1`\)\.
   + *RepositoryName* — The name of the private repository from which to deploy a container image\.
   + *ImageTag* — The tag of the container image from the private repository to deploy on your container service\.

   Example:

   ```
   111122223333.dkr.ecr.us-east-1.amazonaws.com/my-private-repo:myappimage
   ```

## Additional information about container services<a name="container-service-ecr-private-repo-access-info1"></a>

Following are the general steps to manage your Lightsail container service after it is running:

1. Familiarize yourself with all of the elements of Lightsail container services\. For more information, see [Container services in Amazon Lightsail](amazon-lightsail-container-services.md)\.

1. Create your container service in your Lightsail account\. For more information, see [Creating Amazon Lightsail container services](amazon-lightsail-creating-container-services.md)\.

1. If you plan to use container images from a public registry, find container images from a public registry, such as the Amazon ECR Public Gallery\. For more information about Amazon ECR Public, see [What Is Amazon Elastic Container Registry Public?](https://docs.aws.amazon.com/AmazonECR/latest/public/what-is-ecr.html) in the *Amazon ECR Public User Guide*\.

1. If you plan to push container images from your local machine to your service, install software on your local machine that you need to create your own container images and push them to your Lightsail container service\. For more information, see the following guides:
   + [Installing software to manage container images for your Amazon Lightsail container services](amazon-lightsail-install-software.md)
   + [Creating container images for your Amazon Lightsail container services](amazon-lightsail-creating-container-images.md)
   + [Pushing and managing container images on your Amazon Lightsail container services](amazon-lightsail-pushing-container-images.md)

1. Create a deployment in your container service that configures and launches your containers\. For more information, see [Creating and managing deployments for your Amazon Lightsail container services](amazon-lightsail-container-services-deployments.md)\.

1. View previous deployments for your container service\. You can create a new deployment using a previous deployment version\. For more information, see [Viewing and managing deployment versions of your Amazon Lightsail container services](amazon-lightsail-container-services-deployment-versions.md)\.

1. View the logs of containers on your container service\. For more information, see [Viewing the container logs of your Amazon Lightsail container services](amazon-lightsail-viewing-container-service-container-logs.md)\.

1. Create an SSL/TLS certificate for the domains that you want to use with your containers\. For more information, see [Creating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-creating-container-services-certificates.md)\.

1. Validate the SSL/TLS certificate by adding records to the DNS of your domains\. For more information, see [Validating SSL/TLS certificates for your Amazon Lightsail container services](amazon-lightsail-validating-container-services-certificates.md)\.

1. Enable custom domains by attaching a valid SSL/TLS certificate to your container service\. For more information, see [Enabling and managing custom domains for your Amazon Lightsail container services](amazon-lightsail-enabling-container-services-custom-domains.md)\.

1. Monitor the utilization metrics of your container service\. For more information, see [Viewing container service metrics in Amazon Lightsail](amazon-lightsail-viewing-container-services-metrics.md)\.

1. \(Optional\) Scale the capacity of your container service vertically, by increasing its power specification, and horizontally, by increasing its scale specification\. For more information, see [Changing the capacity of your Amazon Lightsail container services](amazon-lightsail-changing-container-service-capacity.md)\.

1. To avoid incurring monthly charges, delete your container service if you're not using it\. For more information, see [Deleting Amazon Lightsail container services](amazon-lightsail-deleting-container-services.md)\.