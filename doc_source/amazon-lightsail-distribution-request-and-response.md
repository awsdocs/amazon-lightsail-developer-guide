# Understanding request and response behaviors of your Amazon Lightsail distribution<a name="amazon-lightsail-distribution-request-and-response"></a>

 *Last updated: July 23, 2020* 

In this guide, we describe the way your Amazon Lightsail distribution behaves when processing and forwarding requests to your origin, and processing responses from your origin\. For more information about distributions, see [Content delivery network distributions in Amazon Lightsail](amazon-lightsail-content-delivery-network-distributions.md)\.

**Topics**
+ [How your distribution processes and forwards requests to your origin](#distribution-process-and-forward-requests)
+ [How your distribution processes responses from your origin](#distribution-process-responses)
+ [Additional information](#distribution-request-and-response-additional-information)

## How your distribution processes and forwards requests to your origin<a name="distribution-process-and-forward-requests"></a>

This section contains information about how your distribution processes viewer requests and forwards the requests to your origin\.

**Contents**
+ [Authentication](#RequestCustomClientAuth)
+ [Caching duration](#RequestCustomCaching)
+ [Client IP addresses](#RequestCustomIPAddresses)
+ [Client\-side SSL authentication](#RequestCustomClientSideSslAuth)
+ [Compression](#RequestCustomCompression)
+ [Conditional requests](#RequestCustomConditionalGETs)
+ [Cookies](#RequestCustomCookies)
+ [Cross\-origin resource sharing \(CORS\)](#request-custom-cors)
+ [Encryption](#RequestCustomEncryption)
+ [GET requests that include a body](#RequestCustom-get-body)
+ [HTTP methods](#RequestCustomHTTPMethods)
+ [HTTP request headers and distribution behavior](#request-custom-headers-behavior)
+ [HTTP version](#RequestCustomHTTPVersion)
+ [Maximum length of a request and maximum length of a URL](#RequestCustomMaxRequestStringLength)
+ [OCSP stapling](#request-custom-ocsp-stapling)
+ [Persistent connections](#request-custom-persistent-connections)
+ [Protocols](#RequestCustomProtocols)
+ [Query strings](#RequestCustomQueryStrings)
+ [Origin connection timeout and attempts](#custom-origin-timeout-attempts)
+ [Origin response timeout](#request-custom-request-timeout)
+ [Simultaneous requests for the same object \(traffic spikes\)](#request-custom-traffic-spikes)
+ [User\-agent header](#request-custom-user-agent-header)

### Authentication<a name="RequestCustomClientAuth"></a>

For `DELETE`, `GET`, `HEAD`, `PATCH`, `POST`, and `PUT` requests, if you configure your distribution to forward the `Authorization` header to your origin, you can configure your origin server to request client authentication\.

For `OPTIONS` requests, you can configure your origin server to request client authentication only if you use the following distribution settings:
+ Configure your distribution to forward the `Authorization` header to your origin\.
+ Configure your distribution to not cache the response to `OPTIONS` requests\.

You can configure your distribution to forward requests to your origin using either HTTP or HTTPS\.

### Caching duration<a name="RequestCustomCaching"></a>

To control how long your objects stay in your distribution's cache before your distribution forwards another request to your origin, you can:
+ Configure your origin to add a `Cache-Control` or an `Expires` header field to each object\.
+ Use the default value of 1 day for the cache lifespan \(TTL\)\.

For more information, see [distribution advanced settings](https://lightsail.aws.amazon.com/ls/docs/en_us/articles/amazon-lightsail-changing-default-cache-behavior#changing-caching-behavior-distribution-advanced-settings)\.

### Client IP addresses<a name="RequestCustomIPAddresses"></a>

If a viewer sends a request to your distribution and does not include an `X-Forwarded-For` request header, your distribution gets the IP address of the viewer from the TCP connection, adds an `X-Forwarded-For` header that includes the IP address, and forwards the request to the origin\. For example, if your distribution gets the IP address `192.0.2.2` from the TCP connection, it forwards the following header to the origin:

`X-Forwarded-For: 192.0.2.2`

If a viewer sends a request to your distribution and includes an `X-Forwarded-For` request header, your distribution gets the IP address of the viewer from the TCP connection, appends it to the end of the `X-Forwarded-For` header, and forwards the request to the origin\. For example, if the viewer request includes `X-Forwarded-For: 192.0.2.4,192.0.2.3` and your distribution gets the IP address `192.0.2.2` from the TCP connection, it forwards the following header to the origin:

`X-Forwarded-For: 192.0.2.4,192.0.2.3,192.0.2.2`

Some applications, such as load balancers, web application firewalls, reverse proxies, intrusion prevention systems, and API Gateway, append the IP address of the distribution edge server that forwarded the request onto the end of the `X-Forwarded-For` header\. For example, if your distribution includes `X-Forwarded-For: 192.0.2.2` in a request that it forwards to ELB and if the IP address of the distribution edge server is 192\.0\.2\.199, the request that your instance receives contains the following header:

`X-Forwarded-For: 192.0.2.2,192.0.2.199`

**Note**  
The `X-Forwarded-For` header contains IPv4 addresses \(such as 192\.0\.2\.44\) and IPv6 addresses \(such as 2001:0db8:85a3:0000:0000:8a2e:0370:7334\)\.

### Client\-side SSL authentication<a name="RequestCustomClientSideSslAuth"></a>

Lightsail distributions don't support client authentication with client\-side SSL certificates\. If an origin requests a client\-side certificate, your distribution drops the request\. 

### Compression<a name="RequestCustomCompression"></a>

Lightsail distributions forward requests that have the `Accept-Encoding` field values `"identity"` and `"gzip"`\.

### Conditional requests<a name="RequestCustomConditionalGETs"></a>

When your distribution receives a request for an object that has expired from an edge cache, it forwards the request to your origin either to get the latest version of the object or to get confirmation from the origin that the distribution edge cache already has the latest version\. Typically, when the origin last sent the object to your distribution, it included an `ETag` value, a `LastModified` value, or both values in the response\. In the new request that your distribution forwards to your origin, your distribution adds one or both of the following:
+ An `If-Match` or `If-None-Match` header that contains the `ETag` value for the expired version of the object\.
+ An `If-Modified-Since` header that contains the `LastModified` value for the expired version of the object\.

The origin uses this information to determine whether the object has been updated and, therefore, whether to return the entire object to your distribution or to return only an HTTP 304 status code \(not modified\)\.

### Cookies<a name="RequestCustomCookies"></a>

You can configure your distribution to forward cookies to your origin\. For more information, see [distribution advanced settings](https://lightsail.aws.amazon.com/ls/docs/en_us/articles/amazon-lightsail-changing-default-cache-behavior#changing-caching-behavior-distribution-advanced-settings)\.

### Cross\-origin resource sharing \(CORS\)<a name="request-custom-cors"></a>

If you want your distribution to respect cross\-origin resource sharing settings, configure your origin to forward the `Origin` header to your origin\.

### Encryption<a name="RequestCustomEncryption"></a>

You can require viewers to connect to your distribution using HTTPS and require your distribution to forward requests to your origin by using HTTP or HTTPS\. 

Your distribution forwards HTTPS requests to your origin using the SSLv3, TLSv1\.0, TLSv1\.1, and TLSv1\.2 protocols\. Other versions of SSL and TLS are not supported\.

### GET requests that include a body<a name="RequestCustom-get-body"></a>

If a viewer `GET` request includes a body, your distribution returns an HTTP status code 403 \(Forbidden\) to the viewer\.

### HTTP methods<a name="RequestCustomHTTPMethods"></a>

If you configure your distribution to allow all of the HTTP methods that it supports, your distribution accepts the following requests from viewers and forwards them to your origin:
+ `DELETE`
+ `GET`
+ `HEAD`
+ `OPTIONS`
+ `PATCH`
+ `POST`
+ `PUT`

Your distribution always caches responses to `GET` and `HEAD` requests\. You can also configure your distribution to cache responses to `OPTIONS` requests\. Your distribution does not cache responses to requests that use the other methods\.

For information about configuring whether your origin processes these methods, see the documentation for your origin\.

**Important**  
If you configure your distribution to accept and forward to your origin all of the HTTP methods that it supports, configure your origin server to handle all methods\. For example, if you configure your distribution to accept and forward these methods because you want to use `POST`, you must configure your origin server to handle `DELETE` requests appropriately so viewers can't delete resources that you don't want them to\. For more information, see the documentation for your HTTP server\. 

### HTTP request headers and distribution behavior<a name="request-custom-headers-behavior"></a>

The following list contains the HTTP request headers that you can forward to your origin \(with the exceptions that are noted\)\. For each header, the list includes information about the following:
+ **Supported** \- Whether you can configure your distribution to cache objects based on header values for that header\. 

  You can configure your distribution to cache objects based on values in the `Date` and `User-Agent` headers, but we don't recommend it\. These headers have many possible values, and caching based on their values would cause your distribution to forward significantly more requests to your origin\.
+ **Behavior if you not configured** \- The behavior of your distribution if you don't configure it to forward the header to your origin, which causes your distribution to cache your objects based on header values\.
+ **Header** \- Other\-defined headers

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution forwards the headers to your origin\.
+ **Header** \- `Accept`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution removes the header\.
+ **Header** \- `Accept-Charset`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution removes the header\.
+ **Header** \- `Accept-Encoding`

  **Supported** \- Yes

  **Behavior if not configured** \- If the value contains `gzip`, Your distribution forwards `Accept-Encoding: gzip` to your origin\. If the value does not contain `gzip`, Your distribution removes the `Accept-Encoding` header field before forwarding the request to your origin\.
+ **Header** \- `Accept-Language`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution removes the header\.
+ **Header** \- `Authorization`

  **Supported** \- Yes

  **Behavior if not configured**:
  + `GET` and `HEAD` requests – Your distribution removes the `Authorization` header field before forwarding the request to your origin\.
  + `OPTIONS` requests – Your distribution removes the `Authorization` header field before forwarding the request to your origin if you configure your distribution to cache responses to `OPTIONS` requests\.

    Your distribution forwards the `Authorization` header field to your origin if you do not configure your distribution to cache responses to OPTIONS requests\.
  + `DELETE`, `PATCH`, `POST`, and `PUT` requests – Your distribution does not remove the header field before forwarding the request to your origin\.
+ **Header** \- `Cache-Control`

  **Supported** \- No

  **Behavior if not configured** \- Your distribution forwards the header to your origin\.
+ **Header** \- `CloudFront-Forwarded-Proto`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution does not add the header before forwarding the request to your origin\.
+ **Header** \- `CloudFront-Is-Desktop-Viewer`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution does not add the header before forwarding the request to your origin\.
+ **Header** \- `CloudFront-Is-Mobile-Viewer`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution does not add the header before forwarding the request to your origin\.
+ **Header** \- `CloudFront-Is-Tablet-Viewer`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution does not add the header before forwarding the request to your origin\.
+ **Header** \- `CloudFront-Viewer-Country`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution does not add the header before forwarding the request to your origin\.
+ **Header** \- `Connection`

  **Supported** \- No

  **Behavior if not configured** \- Your distribution replaces this header with `Connection: Keep-Alive` before forwarding the request to your origin\.
+ **Header** \- `Content-Length`

  **Supported** \- No

  **Behavior if not configured** \- Your distribution forwards the header to your origin\.
+ **Header** \- `Content-MD5`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution forwards the header to your origin\.
+ **Header** \- `Content-Type`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution forwards the header to your origin\.
+ **Header** \- `Cookie`

  **Supported** \- No

  **Behavior if not configured** \- If you configure Your distribution to forward cookies, it will forward the `Cookie` header field to your origin\. If you don't, your distribution removes the `Cookie` header field\.
+ **Header** \- `Date`

  **Supported** \- Yes, but not recommended

  **Behavior if not configured** \- Your distribution forwards the header to your origin\.
+ **Header** \- `Expect`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution removes the header\.
+ **Header** \- `From`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution forwards the header to your origin\.
+ **Header** \- `Host`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution sets the value to the domain name of the origin that is associated with the requested object\. 
+ **Header** \- `If-Match`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution forwards the header to your origin\.
+ **Header** \- `If-Modified-Since`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution forwards the header to your origin\.
+ **Header** \- `If-None-Match`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution forwards the header to your origin\.
+ **Header** \- `If-Range`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution forwards the header to your origin\.
+ **Header** \- `If-Unmodified-Since`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution forwards the header to your origin\.
+ **Header** \- `Max-Forwards`

  **Supported** \- No

  **Behavior if not configured** \- Your distribution forwards the header to your origin\.
+ **Header** \- `Origin`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution forwards the header to your origin\.
+ **Header** \- `Pragma`

  **Supported** \- No

  **Behavior if not configured** \- Your distribution forwards the header to your origin\.
+ **Header** \- `Proxy-Authenticate`

  **Supported** \- No

  **Behavior if not configured** \- Your distribution removes the header\.
+ **Header** \- `Proxy-Authorization`

  **Supported** \- No

  **Behavior if not configured** \- Your distribution removes the header\.
+ **Header** \- `Proxy-Connection`

  **Supported** \- No

  **Behavior if not configured** \- Your distribution removes the header\.
+ **Header** \- `Range`

  **Supported** \- Yes, by default

  **Behavior if not configured** \- Your distribution forwards the header to your origin\.
+ **Header** \- `Referer`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution removes the header\.
+ **Header** \- `Request-Range`

  **Supported** \- No

  **Behavior if not configured** \- >Your distribution forwards the header to your origin\.
+ **Header** \- `TE`

  **Supported** \- No

  **Behavior if not configured** \- Your distribution removes the header\.
+ **Header** \- `Trailer`

  **Supported** \- No

  **Behavior if not configured** \- Your distribution removes the header\.
+ **Header** \- `Transfer-Encoding`

  **Supported** \- No

  **Behavior if not configured** \- Your distribution forwards the header to your origin\.
+ **Header** \- `Upgrade`

  **Supported** \- No \(except for WebSocket connections\)

  **Behavior if not configured** \- Your distribution removes the header, unless you've established a WebSocket connection\.
+ **Header** \- `User-Agent`

  **Supported** \- Yes, but not recommended

  **Behavior if not configured** \- Your distribution replaces the value of this header field with `Amazon CloudFront`\.
+ **Header** \- `Via`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution forwards the header to your origin\.
+ **Header** \- `Warning`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution forwards the header to your origin\.
+ **Header** \- `X-Amz-Cf-Id`

  **Supported** \- No

  **Behavior if not configured** \- Your distribution adds the header to the viewer request before forwarding the request to your origin\. The header value contains an encrypted string that uniquely identifies the request\.
+ **Header** \- `X-Edge-*`

  **Supported** \- No

  **Behavior if not configured** \- Your distribution removes all `X-Edge-*` headers\.
+ **Header** \- `X-Forwarded-For`

  **Supported** \- Yes

  **Behavior if not configured** \- Your distribution forwards the header to your origin\.
+ **Header** \- `X-Forwarded-Proto`

  **Supported** \- No

  **Behavior if not configured** \- Your distribution removes the header\.
+ **Header** \- `X-Real-IP`

  **Supported** \- No

  **Behavior if not configured** \- Your distribution removes the header\.

### HTTP version<a name="RequestCustomHTTPVersion"></a>

Your distribution forwards requests to your origin using HTTP/1\.1\.

### Maximum length of a request and maximum length of a URL<a name="RequestCustomMaxRequestStringLength"></a>

The maximum length of a request, including the path, the query string \(if any\), and headers, is 20,480 bytes\.

Your distribution constructs a URL from the request\. The maximum length of this URL is 8192 bytes\.

If a request or a URL exceeds these maximums, your distribution returns HTTP status code 413, Request Entity Too Large, to the viewer, and then terminates the TCP connection to the viewer\.

### OCSP stapling<a name="request-custom-ocsp-stapling"></a>

When a viewer submits an HTTPS request for an object, either your distribution or the viewer must confirm with the certificate authority \(CA\) that the SSL certificate for the domain has not been revoked\. OCSP stapling speeds up certificate validation by allowing your distribution to validate the certificate and to cache the response from the CA, so the client doesn't need to validate the certificate directly with the CA\.

The performance improvement of OCSP stapling is more pronounced when your distribution receives numerous HTTPS requests for objects in the same domain\. Each server in a distribution edge location must submit a separate validation request\. When your distribution receives a lot of HTTPS requests for the same domain, every server in the edge location soon has a response from the CA that it can "staple" to a packet in the SSL handshake; when the viewer is satisfied that the certificate is valid, your distribution can serve the requested object\. If your distribution doesn't get much traffic in an edge location, new requests are more likely to be directed to a server that hasn't validated the certificate with the CA yet\. In that case, the viewer separately performs the validation step and the distribution server serves the object\. That distribution server also submits a validation request to the CA, so the next time it receives a request that includes the same domain name, it has a validation response from the CA\.

### Persistent connections<a name="request-custom-persistent-connections"></a>

When your distribution gets a response from your origin, it tries to maintain the connection for several seconds in case another request arrives during that period\. Maintaining a persistent connection saves the time required to re\-establish the TCP connection and perform another TLS handshake for subsequent requests\.

### Protocols<a name="RequestCustomProtocols"></a>

Your distribution forwards HTTP or HTTPS requests to the origin server based on value of the **Origin protocol policy** field in the Lightsail console \. In the Lightsail console, the options are **HTTP only**, and **HTTPS only**\. 

If you specify **HTTP Only** or **HTTPS Only**, your distribution forwards requests to your origin using the specified protocol, regardless of the protocol in the viewer request\.

**Important**  
If your distribution forwards a request to your origin using the HTTPS protocol, and if the origin server returns an invalid certificate or a self\-signed certificate, your distribution drops the TCP connection\.

### Query strings<a name="RequestCustomQueryStrings"></a>

You can configure whether your distribution forwards query string parameters to your origin\. 

### Origin connection timeout and attempts<a name="custom-origin-timeout-attempts"></a>

By default, your distribution waits as long as 30 seconds \(3 attempts of 10 seconds each\) before returning an error response to the viewer\.



### Origin response timeout<a name="request-custom-request-timeout"></a>

The *origin response timeout*, also known as the *origin read timeout* or *origin request timeout*, applies to both of the following:
+ The amount of time, in seconds, that your distribution waits for a response after forwarding a request to the origin\.
+ The amount of time, in seconds, that your distribution waits after receiving a packet of a response from the origin and before receiving the next packet\.

Your distribution's behavior depends on the HTTP method of the viewer request:
+ `GET` and `HEAD` requests – If the origin doesn’t respond or stops responding within the duration of the response timeout, your distribution drops the connection\. If the specified number of origin connection attempts is more than 1, your distribution tries again to get a complete response\. Your distribution tries up to 3 times, as determined by the value of the *origin connection attempts* setting\. If the origin doesn’t respond during the final attempt, your distribution doesn’t try again until it receives another request for content on the same origin\. 
+ `DELETE`, `OPTIONS`, `PATCH`, `PUT`, and `POST` requests – If the origin doesn’t respond within 30 seconds, your distribution drops the connection and doesn’t try again to contact the origin\. The client can resubmit the request if necessary\.

### Simultaneous requests for the same object \(traffic spikes\)<a name="request-custom-traffic-spikes"></a>

When a distribution edge location receives a request for an object and either the object isn't currently in the cache or the object has expired, your distribution immediately sends the request to your origin\. If there's a traffic spike—if additional requests for the same object arrive at the edge location before your origin responds to the first request—your distribution pauses briefly before forwarding additional requests for the object to your origin\. Typically, the response to the first request will arrive at the distribution edge location before the response to subsequent requests\. This brief pause helps to reduce unnecessary load on your origin server\. If additional requests are not identical because, for example, you configured your distribution to cache based on request headers or cookies, your distribution forwards all of the unique requests to your origin\.

### User\-agent header<a name="request-custom-user-agent-header"></a>

If you want your distribution to cache different versions of your objects based on the device that a user is using to view your content, we recommend that you configure your distribution to forward one or more of the following headers to your origin:
+ `CloudFront-Is-Desktop-Viewer`
+ `CloudFront-Is-Mobile-Viewer`
+ `CloudFront-Is-SmartTV-Viewer`
+ `CloudFront-Is-Tablet-Viewer`

Based on the value of the `User-Agent` header, your distribution sets the value of these headers to `true` or `false` before forwarding the request to your origin\. If a device falls into more than one category, more than one value might be `true`\. For example, for some tablet devices, your distribution might set both `CloudFront-Is-Mobile-Viewer` and `CloudFront-Is-Tablet-Viewer` to `true`\.

You can configure your distribution to cache objects based on values in the `User-Agent` header, but we don't recommend it\. The `User-Agent` header has many possible values, and caching based on those values would cause your distribution to forward significantly more requests to your origin\. 

If you do not configure your distribution to cache objects based on values in the `User-Agent` header, your distribution adds a `User-Agent` header with the following value before it forwards a request to your origin:

`User-Agent = Amazon CloudFront`

Your distribution adds this header regardless of whether the request from the viewer includes a `User-Agent` header\. If the request from the viewer includes a `User-Agent` header, your distribution removes it\.

## How your distribution processes responses from your origin<a name="distribution-process-responses"></a>

This section contains information about how your distribution processes responses from your origin\.

**Contents**
+ [100\-Continue responses](#Response100Continue)
+ [Caching](#ResponseCustomCaching)
+ [Canceled requests](#response-custom-canceled-requests)
+ [Content negotiation](#ResponseCustomContentNegotiation)
+ [Cookies](#ResponseCustomCookies)
+ [Dropped TCP connections](#ResponseCustomDroppedTCPConnections)
+ [HTTP response headers that your distribution removes or replaces](#ResponseCustomRemovedHeaders)
+ [Maximum file size](#ResponseCustomMaxFileSize)
+ [Origin unavailable](#ResponseCustomOriginUnavailable)
+ [Redirects](#ResponseCustomRedirects)
+ [Transfer encoding](#ResponseCustomTransferEncoding)

### 100\-Continue responses<a name="Response100Continue"></a>

Your origin cannot send more than one 100\-Continue response to your distribution\. After the first 100\-Continue response, your distribution expects an HTTP 200 OK response\. If your origin sends another 100\-Continue response after the first one, your distribution returns an error\.

### Caching<a name="ResponseCustomCaching"></a>
+ Ensure that your origin sets valid and accurate values for the `Date` and `Last-Modified` header fields\.
+ If requests from viewers include the `If-Match` or `If-None-Match` request header fields, set the `ETag` response header field\. If you do not specify an `ETag` value, your distribution ignores subsequent `If-Match` or `If-None-Match` headers\.
+ Your distribution normally respects a `Cache-Control: no-cache` header in the response from the origin\. For an exception, see [Simultaneous requests for the same object \(traffic spikes\)](#request-custom-traffic-spikes)\.

### Canceled requests<a name="response-custom-canceled-requests"></a>

If an object is not in the edge cache, and if a viewer terminates a session \(for example, closes a browser\) after your distribution gets the object from your origin but before it can deliver the requested object, your distribution does not cache the object in the edge location\.

### Content negotiation<a name="ResponseCustomContentNegotiation"></a>

If your origin returns `Vary:*` in the response, and if the value of **Minimum TTL** for the corresponding cache behavior is **0**, your distribution caches the object but still forwards every subsequent request for the object to the origin to confirm that the cache contains the latest version of the object\. Your distribution doesn't include any conditional headers, such as `If-None-Match` or `If-Modified-Since`\. As a result, your origin returns the object to your distribution in response to every request\. 

If your origin returns `Vary:*` in the response, and if the value of **Minimum TTL** for the corresponding cache behavior is any other value, CloudFront processes the `Vary` header as described in [HTTP response headers that your distribution removes or replaces](#ResponseCustomRemovedHeaders)\. 

### Cookies<a name="ResponseCustomCookies"></a>

If you enable cookies for a cache behavior, and if the origin returns cookies with an object, your distribution caches both the object and the cookies\. Note that this reduces cacheability for an object\.

### Dropped TCP connections<a name="ResponseCustomDroppedTCPConnections"></a>

If the TCP connection between your distribution and your origin drops while your origin is returning an object to your distribution, your distribution's behavior depends on whether your origin included a `Content-Length` header in the response:
+ **Content\-Length header** – Your distribution returns the object to the viewer as it gets the object from your origin\. However, if the value of the `Content-Length` header doesn't match the size of the object, your distribution doesn't cache the object\.
+ **Transfer\-Encoding: Chunked** – Your distribution returns the object to the viewer as it gets the object from your origin\. However, if the chunked response is not complete, your distribution does not cache the object\.
+ **No Content\-Length header** – Your distribution returns the object to the viewer and caches it, but the object may not be complete\. Without a `Content-Length` header, your distribution cannot determine whether the TCP connection was dropped accidentally or on purpose\.

We recommend that you configure your HTTP server to add a `Content-Length` header to prevent your distribution from caching partial objects\.

### HTTP response headers that your distribution removes or replaces<a name="ResponseCustomRemovedHeaders"></a>

Your distribution removes or updates the following header fields before forwarding the response from your origin to the viewer:
+ `Set-Cookie` – If you configure your distribution to forward cookies, it will forward the `Set-Cookie` header field to clients\.
+ `Trailer`
+ `Transfer-Encoding` – If your origin returns this header field, your distribution sets the value to `chunked` before returning the response to the viewer\.
+ `Upgrade`
+ `Vary` – Note the following:
  + If you configure your distribution to forward any of the device\-specific headers to your origin \(`CloudFront-Is-Desktop-Viewer`, `CloudFront-Is-Mobile-Viewer`, `CloudFront-Is-SmartTV-Viewer`, `CloudFront-Is-Tablet-Viewer`\) and you configure your origin to return `Vary:User-Agent` to your distribution, your distribution returns `Vary:User-Agent` to the viewer\.
  + If you configure your origin to include either `Accept-Encoding` or `Cookie` in the `Vary` header, Your distribution includes the values in the response to the viewer\.
  + If you configure your distribution to forward a whitelist of headers to your origin, and if you configure your origin to return the header names to your distribution in the `Vary` header \(for example, `Vary:Accept-Charset,Accept-Language`\), Your distribution returns the `Vary` header with those values to the viewer\.
  + For information about how your distribution processes a value of `*` in the `Vary` header, see [Content negotiation](#ResponseCustomContentNegotiation)\.
  + If you configure your origin to include any other values in the `Vary` header, your distribution removes the values before returning the response to the viewer\.
+ `Via` – Your distribution sets the value to the following in the response to the viewer:

  `Via: `*http\-version* *alphanumeric\-string*`.cloudfront.net (CloudFront)`

  For example, if the client makes a request over HTTP/1\.1, the value is something like the following:

  `Via: 1.1 1026589cc7887e7a0dc7827b4example.cloudfront.net (CloudFront)`

### Maximum file size<a name="ResponseCustomMaxFileSize"></a>

The maximum size of a response body that your distribution will return to the viewer is 20 GB\. This includes chunked transfer responses that don't specify the `Content-Length` header value\.

### Origin unavailable<a name="ResponseCustomOriginUnavailable"></a>

If your origin server is unavailable and your distribution gets a request for an object that is in the edge cache but that has expired \(for example, because the period of time specified in the `Cache-Control max-age` directive has passed\), your distribution either serves the expired version of the object or serves a custom error page\.

In some cases, an object that is seldom requested is evicted and is no longer available in the edge cache\. Your distribution can't serve an object that has been evicted\.

### Redirects<a name="ResponseCustomRedirects"></a>

If you change the location of an object on your origin server, you can configure your web server to redirect requests to the new location\. After you configure the redirect, the first time a viewer submits a request for the object, your distribution sends the request to the origin, and the origin responds with a redirect \(for example, `302 Moved Temporarily`\)\. Your distribution caches the redirect and returns it to the viewer\. Your distribution does not follow the redirect\.

You can configure your web server to redirect requests to one of the following locations:
+ The new URL of the object on the origin server\. When the viewer follows the redirect to the new URL, the viewer bypasses your distribution and goes straight to the origin\. As a result, we recommend that you not redirect requests to the new URL of the object on the origin\.
+ The new distribution URL for the object\. When the viewer submits the request that contains the new distribution URL, your distribution gets the object from the new location on your origin, caches it at the edge location, and returns the object to the viewer\. Subsequent requests for the object will be served by the edge location\. This avoids the latency and load associated with viewers requesting the object from the origin\. However, every new request for the object will incur charges for two requests to your distribution\.

### Transfer encoding<a name="ResponseCustomTransferEncoding"></a>

Lightsail distributions support only the `chunked` value of the `Transfer-Encoding` header\. If your origin returns `Transfer-Encoding: chunked`, your distribution returns the object to the client as the object is received at the edge location, and caches the object in chunked format for subsequent requests\.

If the viewer makes a `Range GET` request and the origin returns `Transfer-Encoding: chunked`, your distribution returns the entire object to the viewer instead of the requested range\.

We recommend that you use chunked encoding if the content length of your response cannot be predetermined\. For more information, see [Dropped TCP Connections](#ResponseCustomDroppedTCPConnections)\.

## Additional information<a name="distribution-request-and-response-additional-information"></a>

Here are some articles to help you manage distributions in Lightsail:
+ [Content delivery network distributions in Amazon Lightsail](amazon-lightsail-content-delivery-network-distributions.md)
+ [Creating Amazon Lightsail distributions](amazon-lightsail-creating-content-delivery-network-distribution.md)
+ [Understanding request and response behaviors of an Amazon Lightsail distribution](#amazon-lightsail-distribution-request-and-response)
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
+ [Viewing distribution metrics in Amazon Lightsail](amazon-lightsail-viewing-distribution-health-metrics.md)
+ [Deleting your Amazon Lightsail distribution](amazon-lightsail-deleting-distribution.md)
+ [SSL/TLS certificates in Amazon Lightsail](understanding-tls-ssl-certificates-in-lightsail-https.md)
+ [Creating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-create-a-distribution-certificate.md)
+ [Validating SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-validating-a-distribution-certificate.md)
+ [Viewing SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-viewing-distribution-certificates.md)
+ [Deleting SSL/TLS certificates for your Amazon Lightsail distribution](amazon-lightsail-deleting-distribution-certificates.md)