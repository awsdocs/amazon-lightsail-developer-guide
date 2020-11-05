# Changing the caching behavior of your Amazon Lightsail distribution<a name="amazon-lightsail-changing-default-cache-behavior"></a>

 *Last updated: July 23, 2020* 

A cache behavior lets you configure what is cached or isn't cached from your origin by your Amazon Lightsail distribution\. For example, you can specify to cache individual directories, files, or file types from your origin\. You can also specify the HTML methods and headers that are forwarded to your origin\. In this guide, we show you how to change the caching behavior of your distribution\. For more information about distributions, see [Content delivery network distributions in Amazon Lightsail](amazon-lightsail-content-delivery-network-distributions.md)\.

**Contents**
+ [Caching preset](#changing-caching-behavior-distribution-caching-preset)
+ [Best for WordPress caching preset](#changing-caching-behavior-wordpress-distribution-preset)
+ [Default behavior](#changing-caching-behavior-distribution-default-behavior)
+ [Directory and file overrides](#changing-caching-behavior-distribution-directory-file-overrides)
+ [Advanced cache settings](#changing-caching-behavior-distribution-advanced-settings)
+ [Change your distribution's cache behavior](#change-distribution-cache-behavior)
+ [Additional information](#changing-distribution-cache-behavior-additional-information)

## Caching preset<a name="changing-caching-behavior-distribution-caching-preset"></a>

A *caching preset* automatically configures the settings of your distribution for the type of content that you host on your origin\. For example, choosing the **Best for static content** preset automatically configures your distribution with settings that work best with static websites\. If your website is hosted on a WordPress instance, then choose the **Best for WordPress** preset to have your distribution automatically configured to work with your WordPress website\.

You can choose one of the follow caching presets for your distribution:
+ **Best for static content** \- This preset configures your distribution to *cache everything*\. This preset is ideal if you host static content \(e\.g\., static HTML pages\) on your origin, or content that does not change for each user who visits your website\. All content on your distribution is cached when you choose this preset\.
+ **Best for dynamic content** \- This preset configures your distribution to cache nothing except the files that you specify as **Cache** in the **Directory and file overrides** section of the **Create a distribution** page\. For more information, see [Directory and file overrides](#changing-caching-behavior-distribution-directory-file-overrides) later in this guide\. This preset is ideal if you host dynamic content on your origin, or content that may change for each user who visits your website or web application\.
+ **Best for WordPress** \- This preset configures your distribution to *cache nothing* except the files in the `wp-includes/` and `wp-content/` directories of your WordPress instance\. This preset is ideal if your origin is an instance that uses the **WordPress Certified by Bitnami and Automattic** blueprint \(excluding the multisite blueprint\)\. For more information about this preset, see [Best for WordPress caching preset](#changing-caching-behavior-wordpress-distribution-preset)\.
**Note**  
The **Custom settings** preset cannot be selected\. It is automatically selected for you if you choose a preset but then manually modify your distribution's settings\.

A caching preset can be specified only in the Lightsail console\. It cannot be specified using the Lightsail API, AWS CLI, and SDKs\.

## Best for WordPress caching preset<a name="changing-caching-behavior-wordpress-distribution-preset"></a>

When you select an instance that uses the **WordPress Certified by Bitnami and Automattic** blueprint as the origin of your distribution, Lightsail asks if you want to apply the **Best for WordPress** caching preset to your distribution\. If you apply the present, then your distribution is automatically configured to work best with your WordPress website\. There are no other distribution settings that you need to apply\. The Best for WordPress preset to *cache nothing* except the files in the `wp-includes/` and `wp-content/` directories of your WordPress website\. It also configures your distribution to clear its cache every day \(cache lifespan of 1 day\), allow all HTTP methods, forward only the `Host` header, forward no cookies, and forwards all query strings\.

**Important**  
You must edit the WordPress configuration file in your instance to make your WordPress website work with your distribution\. For more information, see [Configuring your WordPress instance to work with your Amazon Lightsail distribution](amazon-lightsail-editing-wp-config-for-distribution.md)\.

## Default behavior<a name="changing-caching-behavior-distribution-default-behavior"></a>

A *default behavior* specifies how your distribution handles content caching\. The default behavior of your distribution is automatically specified for you depending on the [caching preset](#changing-caching-behavior-distribution-caching-preset) that you select\. If you select a different default behavior, then the caching preset is automatically changed to **Custom settings**\.

You can choose one of the follow default behaviors for your distribution:
+ **Cache everything** \- This behavior configures your distribution to cache and serve your entire website as static content\. This option is ideal if your origin hosts content that doesn't change depending on who views it, or if your website does not use cookies, headers, or query strings to personalize content\.
+ **Cache nothing** \- This behavior configures your distribution to cache only the origin files and folder paths that you specify\. This option is ideal if your website or web application uses cookies, headers, and query strings to personalize content for individual users\. If you select this option, you *must* specify the [directory and file path overrides](#changing-caching-behavior-distribution-directory-file-overrides) to cache\.

## Directory and file overrides<a name="changing-caching-behavior-distribution-directory-file-overrides"></a>

A *directory and file override* can be used to override, or add an exception to, the default behavior you selected\. For example, if you chose to *cache everything*, use an override to specify a directory, file, or file type that your distribution shouldn't cache\. Alternately, if you chose to *cache nothing*, use an override to specify a directory, file, or file type that your distribution should cache\.

In the **Directory and file overrides** section of the page, you can specify a path to a directory or a file to cache, or not cache\. Use an asterisk symbol to specify wildcard directories \(`path/to/assets/*`\), and file types \(`*.html`, `*jpg`, `*js`\)\. Directories and file paths are case\-sensitive\.

These are a few examples of how you can specify directory and file overrides:
+ Specify the following to cache all files in the document root of an Apache web server running on a Lightsail instance\.

  ```
  var/www/html/
  ```
+ Specify the following to cache only the index page in the document root of an Apache web server\.

  ```
  var/www/html/index.html
  ```
+ Specify the following to cache only the \.html files in the document root of an Apache web server\.

  ```
  var/www/html/*.html
  ```
+ Specify the following to cache only the \.jpg, \.png, and \.gif files in the images sub\-directory of the document root of an Apache web server\.

  ```
  var/www/html/images/*.jpg
  ```

  ```
  var/www/html/images/*.png
  ```

  ```
  var/www/html/images/*.gif
  ```

  Specify the following to cache all files in the images sub\-directory of the document root of an Apache web server\.

  ```
  var/www/html/images/
  ```

## Advanced cache settings<a name="changing-caching-behavior-distribution-advanced-settings"></a>

The *advanced settings* can be used to specify the cache lifespan of content on your distribution, the allowed HTTP methods, HTTP header forwarding, cookie forwarding, and query string forwarding\. The advanced settings that you specify apply only to the directory and files that your distribution caches, including the directory and file overrides that you specify as **Cache**\.

You can configure the following advanced settings:

**Cache lifespan \(TTL\)**

Controls the amount of time your content stays in your distribution's cache before your distribution forwards another request to your origin to determine if your content has been updated\. The default value is one day\. Reducing the duration allows you to better serve dynamic content\. Increasing the duration means that your users get better performance because your files are more likely to be served directly from the edge location\. Increasing the duration also reduces the load on your origin, because your distribution pulls content less frequently\.

**Note**  
The cache lifespan value that you specify applies only when your origin does not add HTTP headers such as `Cache-Control max-age`, `Cache-Control s-maxage`, or `Expires` to your content\.

**Allowed HTTP methods**

Controls the HTTP methods that your distribution processes and forwards to your origin\. HTTP methods indicate the desired action to be performed on the origin\. For example, the GET method retrieves data from your origin, and the PUT method requests that the enclosed entity be stored on your origin\.

You can choose one of the following HTTP method options for your distribution:
+ **Allow GET, HEAD, OPTIONS, PUT, PATCH, POST, and DELETE methods**
+ **Allow the GET, HEAD, and OPTIONS methods**
+ **Allow the GET and HEAD methods**

Your distribution always caches responses to the GET and HEAD requests\. Your distribution also caches responses to the OPTIONS requests, if you choose to allow those requests\. Your distribution does not cache responses to any other HTTP methods\.

**Important**  
If you configure your distribution to allow all of the HTTP methods that are supported, you must configure your origin instance to handle all methods\. For example, if you configure your distribution to allow these methods because you want to use POST, you must configure your origin server to handle DELETE requests appropriately so viewers can't delete resources that you don't want them to\. For more information, search the documentation for your website or web application\.

**HTTP header forwarding**

Controls whether your distribution caches your content based on the values of specified headers, and if so, which ones\. HTTP headers carry information about the client browser, the requested page, the origin and more\. For example, the `Accept-Language` header sends the language of the client \(e\.g\., `en-US` for English\), so that the origin can respond with content in the language of the client, if it's available\. 

You can choose one of the following HTTP header options for your distribution:
+ **Forward no headers**
+ **Forward only the headers I specify**

When you select **Forward no headers**, your distribution doesn't cache your content based on header values\. Regardless of the option that you select, your distribution forwards certain headers to your origin and takes specific actions based on the headers that you forward\.

**Cookie forwarding**

Controls whether your distribution forwards cookies to your origin and, if so, which ones\. A cookie contains a small piece of data sent to the origin, such as information about a visitor's actions on a web page of your origin, as well as any information the visitor has provided, such as their name and interests\. 

You can choose one of the following cookie forwarding options for your distribution:
+ **Don't forward cookies**
+ **Forward all cookies**
+ **Forward cookies I specify**

If you choose **Forward all cookies**, your distribution forwards all cookies regardless of how many your application uses\. If you chose **Forward cookies I specify**, then enter the names of cookies that you want your distribution to forward in the text box that appears\. You can specify the following wildcards when you specify cookie names:
+ \* matches 0 or more characters in the cookie name
+ ? matches exactly one character in the cookie name

For example, suppose that a viewer's request for an object includes a cookie named `userid_member-number`\. Where each of your users has a unique value for `member-number` \(`userid_123`, `userid_124`, `userid_125`, etc\.\)\. You want your distribution to cache a separate version of the content for each member\. You could accomplish this by forwarding all cookies to your origin, but the viewer requests include some cookies that you don't want your distribution to cache\. You could specify the following value as a cookie name, which causes your distribution to forward all of the cookies that begin with `userid_` to your origin: `userid_*`

**Query string forwarding**

Controls whether your distribution forwards query strings to your origin and, if so, which ones\. A query string is a part of a URL that assigns values to specified parameters\. For example, the `https://example.com/over/there?name=ferret` URL contains the `name=ferret` query string\. When a server receives a request for such a page, it may run a program, passing the `name=ferret` query string unchanged, to the program\. The question mark is used as a separator, and is not part of the query string\. 

You can choose to have your distribution forward no query strings, or forward only the query strings that you specify\. Choose not to forward query strings if your origin returns the same version of your content regardless of the values of query string parameters\. This increases the likelihood that your distribution can serve a request from the cache, which improves performance and reduces the load on your origin\. Choose to forward only the query strings that you specify if your origin server returns different versions of your content based on one or more query string parameters\.

## Change your distribution's cache behavior<a name="change-distribution-cache-behavior"></a>

Complete the following procedure to change the default cache behavior of your distribution\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On the Lightsail home page, choose the **Networking** tab\.

1. Choose the name of the distribution for which you want to change the default cache behavior\.

1. Choose the **Cache** tab on your distribution's management page\.

1. In the **Configure caching** section of the page, choose the caching preset for your distribution\. For more information, see [Caching preset](#changing-caching-behavior-distribution-caching-preset)\.

1. Choose **Change default cache behavior** to change the default behavior for your distribution\. Then, choose a default behavior for your distribution\. For more information, see [Default behavior](#changing-caching-behavior-distribution-default-behavior)\.

1. Choose **Add path** to add a directory and file override to your distribution's caching behavior\. For more information, see [Directory and file overrides](#changing-caching-behavior-distribution-directory-file-overrides)\.

1. Choose the pencil icon displayed next to the advanced setting you want to edit for your distribution\. For more information, see [Advanced cache settings](#changing-caching-behavior-distribution-advanced-settings)\.

When you save changes to your distribution's configuration, your distribution starts to propagate the changes to all edge locations\. Until your configuration is updated in an edge location, your distribution continues to serve your content from that location based on the previous configuration\. After your configuration is updated in an edge location, your distribution immediately starts to serve your content from that location based on the new configuration\.

Your changes don't propagate to every edge location instantaneously\. When propagation is complete, the status of your distribution changes from **InProgress** to **Enabled**\. While your distribution is propagating your changes, we can't determine whether a given edge location is serving your content based on the previous configuration or the new configuration\.

## Additional information<a name="changing-distribution-cache-behavior-additional-information"></a>

Here are some articles to help you manage distributions in Lightsail:
+ [Content delivery network distributions in Amazon Lightsail](amazon-lightsail-content-delivery-network-distributions.md)
+ [Creating Amazon Lightsail distributions](amazon-lightsail-creating-content-delivery-network-distribution.md)
+ [Understanding request and response behaviors of an Amazon Lightsail distribution](amazon-lightsail-distribution-request-and-response.md)
+ [Configuring your WordPress instance to work with your Amazon Lightsail distribution](amazon-lightsail-editing-wp-config-for-distribution.md)
+ [Testing your Amazon Lightsail distribution](amazon-lightsail-testing-distribution.md)
+ [Changing the origin of your Amazon Lightsail distribution](amazon-lightsail-changing-distribution-origin.md)
+ [Changing the caching behavior of your Amazon Lightsail distribution](#amazon-lightsail-changing-default-cache-behavior)
+ [Resetting the cache of your Amazon Lightsail distribution](amazon-lightsail-resetting-distribution-cache.md)
+ [Changing the plan of your Amazon Lightsail distribution](amazon-lighstail-changing-distribution-plan.md)
+ [Enabling custom domains for your Amazon Lightsail distributions](amazon-lightsail-enabling-distribution-custom-domains.md)
+ [Pointing your domains to your Amazon Lightsail distributions](amazon-lightsail-point-domain-to-distribution.md)
+ [Changing custom domains for your Amazon Lightsail distribution](amazon-lightsail-changing-distribution-custom-domains.md)
+ [Disabling custom domains for your Amazon Lightsail distributions](amazon-lightsail-disabling-distribution-custom-domains.md)
+ [Viewing distribution metrics in Amazon Lightsail](amazon-lightsail-viewing-distribution-health-metrics.md)
+ [Deleting your Amazon Lightsail distribution](amazon-lightsail-deleting-distribution.md)
+ [SSL/TLS certificates in Lightsail](understanding-tls-ssl-certificates-in-lightsail-https.md)
+ [Creating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-create-a-distribution-certificate.md)
+ [Validating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-validating-a-distribution-certificate.md)
+ [Viewing SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-viewing-distribution-certificates.md)
+ [Deleting SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-deleting-distribution-certificates.md)