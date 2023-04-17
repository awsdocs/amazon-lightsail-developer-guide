# Tutorial: How to create a HAR file<a name="amazon-lightsail-create-har-file"></a>

 *Last updated: October 25, 2022* 

If you're experiencing difficulties with the Amazon Lightsail console or a Lightsail virtual private server \(VPS\), AWS Support might ask you to submit a HAR file from your web browser\. A HAR file contains critical information that can help troubleshoot common, and hard to diagnose issues\. The HAR file also allows AWS Support to investigate or replicate these issues\.

**Important**  
HAR files can capture sensitive information, such as user names, passwords, and keys\. Be sure to remove any sensitive information from a HAR file before you share it\.

In this guide, you will learn how to create a HAR file from your web browser\. An HTTP Archive \(HAR\) file is a JSON file that contains the latest network activity recorded by your browser\. Follow this step\-by\-step procedure to create a HAR file\.

**Contents**
+ [Step 1: Create a HAR file in your browser](#create-a-har-file-in-browser)
+ [Step 2: Edit the HAR file to remove sensitive information](#edit-har-file)
+ [Step 3: Submit the HAR file for review](#submit-har-file)

## Step 1: Create a HAR file in your browser<a name="create-a-har-file-in-browser"></a>

**Note**  
These instructions were last tested on Google Chrome version 101\.0\.4951\.64, Microsoft Edge \(Chromium\) version 101\.0\.1210\.47, and Mozilla Firefox version 91\.9\. Because these browsers are third\-party products, these instructions might not match the experience in the latest versions or in the version that you use\. In another browser, such as legacy Microsoft Edge \(EdgeHTML\) or Apple Safari for macOS, the process to generate a HAR file might be similar, but the steps will be different\.

**Google Chrome**

1. In the browser, at the top right, choose **Customize and control Google Chrome**\.  
![\[Google Chrome customize and control menu.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-har-tutorial-chrome.png)

1. Pause on **More tools**, and then choose **Developer tools**\.

1. With DevTools open in the browser, choose the **Network** panel\.

1. Select the **Preserve log** check box\.

1. Choose **Clear** to clear all current network requests\.

1. Reproduce the issue you are facing

1. In DevTools, open the context \(right\-click\) menu on any network request\.

1. Choose **Save all as HAR with content**, and then save the file\.

For more information, see [Open Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools/open) and [Save all network requests to a HAR file](https://developers.google.com/web/tools/chrome-devtools/network/reference#save-as-har) on the Google Developers website\.

**Microsoft Edge \(Chromium\)**

1. In the browser, at the top right, choose **Settings and more**\.  
![\[Microsoft Edge settings and more menu.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-har-tutorial-edge.png)

1. Pause on **More tools**, and then choose **Developer tools**\.

1. With DevTools open in the browser, choose the **Network** panel\.

1. Select the **Preserve log** check box\.

1. Choose **Clear** to clear all current network requests\.

1. Reproduce the issue you are facing

1. In DevTools, open the context \(right\-click\) menu on any network request\.

1. Choose **Save all as HAR with content**, and then save the file\.

**Mozilla Firefox**

1. In the browser, at the top right, choose **Open Application Menu**\.  
![\[Mozilla Firefox open application menu.\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-har-tutorial-firefox.png)

1. Choose **More tools**, and then choose **Web Developer tools**\.

1. In the **Web Developer** menu, choose **Network**\. \(In some versions of Firefox, the **Web Developer** menu is in the **Tools** menu\.\)

1. Choose the gear icon, and then select **Persist Logs**\.

1. Choose the trash can icon \(**Clear**\) to clear all current network requests\.

1. Reproduce the issue you are facing\.

1. In the Network Monitor, open the context menu \(right\-click\) on any network request in the request list\.

1. Choose **Save All As HAR**, and then save the file\.

## Step 2: Edit the HAR file to remove sensitive information<a name="edit-har-file"></a>

1. Open the HAR file in a text editor application\.

1. Use the text editor's Find and Replace tools to identify and replace all sensitive information captured in the HAR file\. This includes any user names, passwords, and keys that you entered in your browser while creating the file\.

1. Save the edited HAR file with the sensitive information removed\.

## Step 3: Submit the HAR file for review<a name="submit-har-file"></a>

1. In the [AWS Support Center Console ](https://aws.amazon.com/support), under **Open support cases**, choose your support case\.

1. In your support case, choose your preferred contact option, attach the edited HAR file, and then submit\.