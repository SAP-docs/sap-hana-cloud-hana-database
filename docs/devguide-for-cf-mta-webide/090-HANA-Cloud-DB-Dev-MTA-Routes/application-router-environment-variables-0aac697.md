<!-- loio0aac697f0cf7444193ed5eb0fc6e5bd0 -->

# Application Router Environment Variables

A list of environment variables that can be used to configure the application router.



The following table lists the environment variables that you can use to configure the application router. The table also provides a short description of each variable and, where appropriate, an example of the configuration data.

**Application Router Configuration Variables**


<table>
<tr>
<th valign="top">

Variable

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

[`CJ_PROTECT_WHITELIST`](application-router-environment-variables-0aac697.md#loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_nrz_hgn_mv) 

</td>
<td valign="top">

A list of allowed server or domain origins to use when checking for click-jacking attacks

</td>
</tr>
<tr>
<td valign="top">

[`COMPRESSION`](application-router-environment-variables-0aac697.md#loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_vsq_xch_wx) 

</td>
<td valign="top">

Configure the compression of resources before a response to the client.

</td>
</tr>
<tr>
<td valign="top">

[`CORS`](application-router-environment-variables-0aac697.md#loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_nt3_t4k_sz) 

</td>
<td valign="top">

Provide support for cross-origin requests, for example, by allowing the modification of the request header.

</td>
</tr>
<tr>
<td valign="top">

[`destinations`](application-router-environment-variables-0aac697.md#loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_upn_qhr_s1b) 

</td>
<td valign="top">

Provide information about the available application \(microservice\) destinations.

</td>
</tr>
<tr>
<td valign="top">

[`httpHeaders`](application-router-environment-variables-0aac697.md#loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_rhz_hgn_mv) 

</td>
<td valign="top">

Configure the application router to return additional HTTP headers in its responses to client requests

</td>
</tr>
<tr>
<td valign="top">

[`INCOMING_CONNECTION_TIMEOUT`](application-router-environment-variables-0aac697.md#loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_owp_xch_wx) 

</td>
<td valign="top">

Specify the maximum time \(in milliseconds\) for a client connection. If the specified time is exceeded, the connection is closed.

</td>
</tr>
<tr>
<td valign="top">

[`JWT_REFRESH`](application-router-environment-variables-0aac697.md#loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_x5z_hgn_mv) 

</td>
<td valign="top">

Configures the automatic refresh of the JSON Web Token \(JWT\) provided by the User Account and Authentication \(UAA\) service to prevent expiry \(default is 5 minutes\).

</td>
</tr>
<tr>
<td valign="top">

[`REQUEST_TRACE`](application-router-environment-variables-0aac697.md#loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_s1p_qvj_2z) 

</td>
<td valign="top">

Enable additional traces of the incoming and outgoing requests

</td>
</tr>
<tr>
<td valign="top">

[`SECURE_SESSION_COOKIE`](application-router-environment-variables-0aac697.md#loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_wpy_yfg_2z) 

</td>
<td valign="top">

Configure the enforcement of the `Secure` flag of the application router's session cookie.

</td>
</tr>
<tr>
<td valign="top">

[`SEND_XFRAMEOPTIONS`](application-router-environment-variables-0aac697.md#loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_d4z_hgn_mv) 

</td>
<td valign="top">

Set or change the `X-Frame-Options` header

</td>
</tr>
<tr>
<td valign="top">

[`SESSION_TIMEOUT`](application-router-environment-variables-0aac697.md#loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_blz_hgn_mv) 

</td>
<td valign="top">

Set the time to trigger an automatic central log out from the User Account and Authentication \(UAA\) server.

</td>
</tr>
<tr>
<td valign="top">

[`TENANT_HOST_PATTERN`](application-router-environment-variables-0aac697.md#loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_zhq_xch_wx) 

</td>
<td valign="top">

Define a regular expression to use when resolving tenant host names in the request’s host name.

</td>
</tr>
<tr>
<td valign="top">

[`UAA_SERVICE_NAME`](application-router-environment-variables-0aac697.md#loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_wf1_lgn_mv) 

</td>
<td valign="top">

Specify the **exact** name of the UAA service to bind to an application.

</td>
</tr>
<tr>
<td valign="top">

[`WS_ALLOWED_ORIGINS`](application-router-environment-variables-0aac697.md#loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_ijs_5fm_4v) 

</td>
<td valign="top">

A list of the allowed server \(or domain\) origins that the application router uses to verify requests

</td>
</tr>
</table>



<a name="loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_rhz_hgn_mv"/>

## httpHeaders

If configured, the application router sends additional HTTP headers in its responses to a client request. You can set the additional HTTP headers in the *<httpHeaders\>* environment variable. The following example configuration shows how to configure the application router to send two additional headers in the responses to the client requests from the application *<myApp\>*:

<code>xs set-env <i class="varname">&lt;myApp&gt;</i> httpHeaders "[ { \"X-Frame-Options\": \"ALLOW-FROM http://acme.com\" }, { \"Test-Additional-Header\": \"1\" } ]"</code>

or

<code>xs set-env <i class="varname">&lt;myApp&gt;</i> httpHeaders '[{ "X-Frame-Options": "ALLOW-FROM http://acme.com" }, { "Test-Additional-Header": "1" }]'</code>

> ### Tip:  
> To improve security in your application, set the `Content-Security-Policy` response header, which can be used to provide those Web browsers capable of interpreting it with information about the trusted sources from which an application can load resources.

The content-security-policy mechanism allows the client to detect and block any attempts to inject malicious scripts into the application. A value can be set for the security policy by using the *<httpHeaders\>* environment variable in the additional headers configuration. The value set represents a security policy which contains directive-value pairs. The value set for directive takes the form of an allow list of trusted sources. You can use the `Content-Security-Policy` to define a default source \(`default-src`\) or define individual settings, for example, to restrict connections \(`connect-src`\), limit the type of plug-ins that can be run \(`plugin-types`\), or ensure that scripts are only loaded from a permitted origin \(`script-src`\).

> ### Note:  
> The `Content-Security-Policy` header is seen as a second line of defense; applications should always provide and ensure suitable input validation and output encoding.



<a name="loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_upn_qhr_s1b"/>

## destinations

The destinations configuration is an array of objects that is defined in the `destinations` environment variable. A destination is required for every application \(microservice\) that is part of the business application. The following table lists the properties that can be used to describe the destination:

**Destination Environment Variable Properties**


<table>
<tr>
<th valign="top">

Property

</th>
<th valign="top">

Type

</th>
<th valign="top">

Mandatory

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`name` 

</td>
<td valign="top">

String

</td>
<td valign="top">

Yes

</td>
<td valign="top">

A unique indentifier for the destination

</td>
</tr>
<tr>
<td valign="top">

`url` 

</td>
<td valign="top">

String

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The Unique Resource Locator for the application \(microservice\)

</td>
</tr>
<tr>
<td valign="top">

`proxyHost` 

</td>
<td valign="top">

String

</td>
<td valign="top">

No

</td>
<td valign="top">

The host of the proxy server used in case the request should go through a proxy to reach the destination.

> ### Tip:  
> Mandatory if `proxyPort` is defined.



</td>
</tr>
<tr>
<td valign="top">

`proxyPort` 

</td>
<td valign="top">

String

</td>
<td valign="top">

No

</td>
<td valign="top">

The port of the proxy server used in case the request should go through a proxy to reach the destination.

> ### Tip:  
> Mandatory if `proxyHost` is defined.



</td>
</tr>
<tr>
<td valign="top">

`forwardAuthToken` 

</td>
<td valign="top">

Boolean

</td>
<td valign="top">

No

</td>
<td valign="top">

If true, the OAuth token will be sent to the destination. The default value is “false”. This token contains the user identity, scopes, and some other attributes. The token is signed by the User Account and Authentication \(UAA\) service so that the token can be used for user-authentication and authorization purposed by back-end services.

</td>
</tr>
<tr>
<td valign="top">

`strictSSL` 

</td>
<td valign="top">

Boolean

</td>
<td valign="top">

No

</td>
<td valign="top">

Configures whether the application router should reject untrusted certificates. The default value is “true”.

> ### Caution:  
> For testing purposes only. Do **not** use this property in production environments!



</td>
</tr>
<tr>
<td valign="top">

`timeout` 

</td>
<td valign="top">

Number

</td>
<td valign="top">

No

</td>
<td valign="top">

A positive integer representing the maximum amount of time to wait for a response \(in milliseconds\) from the specified destination. The default is 30000ms.

> ### Tip:  
> The timeout specified here also applies to the logout path, `logoutPath`, if the logout path is defined, for example, in the application's descriptor file `xs-app.json`.



</td>
</tr>
<tr>
<td valign="top">

`proxyType` 

</td>
<td valign="top">

String

</td>
<td valign="top">

No

</td>
<td valign="top">

Indicates if the destination is used to access applications in private networks \(for example, on-premise\) or publicly available on the Internet. Possible value: `onPremise`. If `proxyType` is not specified, the default \(Internet access\) is assumed.

> ### Tip:  
> In Cloud environments, if you set the application's destination `proxyType` to `onPremise`, a binding to the SAP Connectivity service is required, and the `forwardAuthToken` property must not be set.



</td>
</tr>
</table>

The following example shows a simple configuration for the *<destinations\>* environment variable:

> ### Sample Code:  
> ```
> [
>  {
>    "name" : "ui5",
>    "url" : "https://sapui5.acme.com",
>    "proxyHost" : "proxy",
>    "proxyPort" : "8080",
>    "forwardAuthToken" : false,
>    "timeout" : 1200
>  }
> ]
> ```

It is also possible to include the destinations in the `manifest.yml` file, as illustrated in the following example:

> ### Sample Code:  
> ```
> 
> - name: node-hello-world 
>   memory: 100M 
>   path: web 
>   env: destinations: > 
>        [
>         {"name":"ui5", "url":"https://sapui5.acme.com"} 
>        ]
> ```



### The Destination Service

It is also possible to read a “destination” configuration from the `destination service` in Cloud Foundry. For this configuration scenario, however, some restrictions apply regarding where the service can be used and what properties and options are recognized by the application router.

> ### Restriction:  
> The destination service is only available in Cloud Foundry; it is not available for use in on-premise environments.
> 
> If a destination with the same name is defined in both an environment destination **and** a destination service, the environment destination configuration takes precedence and will be loaded and used.

**AppRouter Limitations for the Destination Service in Cloud Foundry**


<table>
<tr>
<th valign="top">

Property

</th>
<th valign="top">

Optional

</th>
<th valign="top">

Destination Service Restrictions

</th>
</tr>
<tr>
<td valign="top">

`type` 

</td>
<td valign="top">

No

</td>
<td valign="top">

Supported protocol type: `HTTP` only

</td>
</tr>
<tr>
<td valign="top">

`Authentication` 

</td>
<td valign="top">

No

</td>
<td valign="top">

Supported authentication types:

-   `none`
-   `basic authentication`

    `User` and `Password` are mandatory

-   `principal propagation`

    `ProxyType` must be “`on-premise`”




</td>
</tr>
<tr>
<td valign="top">

`ProxyType` 

</td>
<td valign="top">

No

</td>
<td valign="top">

Supported proxy types:

-   `on-premise`

    A binding to the SAP Connectivity service is required.

-   `internet`



</td>
</tr>
<tr>
<td valign="top">

`ForwardAuthToken` 

</td>
<td valign="top">

Yes

</td>
<td valign="top">

If set to `true`, the OAuth token is sent to the specified destination. The default value is `false`. The OAuth token contains the user identity, authorization scopes, and other attributes. Since the token is signed by the UAA, it can be used for user authentication and authorization with back-end services.

> ### Note:  
> If `ProxyType` is set to `on-premise`, the `ForwardAuthToken` property cannot be set.



</td>
</tr>
<tr>
<td valign="top">

`Timeout`

</td>
<td valign="top">

Yes

</td>
<td valign="top">

A positive integer representing the maximum amount of time \(in milliseconds\) to wait for a response from the destination. The default value is 30000ms.

> ### Note:  
> The timeout specified here also applies to the destination's `logout path` \(if one is set\).



</td>
</tr>
</table>



<a name="loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_blz_hgn_mv"/>

## SESSION\_TIMEOUT

You can configure the triggering of an automatic central log-out from the User Account and Authentication \(UAA\) service if an application session is inactive for a specified time. A session is considered to be inactive if no requests are sent to the application router. The following command shows how to set the environment variable *<SESSION\_TIMEOUT\>* to 40 \(forty\) minutes for the application *<myApp1\>*:

<code>xs set-env <i class="varname">&lt;myApp1&gt;</i> SESSION_TIMEOUT 40</code>

> ### Note:  
> You can also set the session timeout value in the application's `manifest.yml` file, as illustrated in the following example:

> ### Sample Code:  
> ```
> - name: myApp1 
>   memory: 100M
>   path: web
>   env:
>     SESSION_TIMEOUT: 40
> ```

> ### Tip:  
> If the authentication type for a route is set to `"xsuaa"` \(for example, `"authenticationType": "xsuaa"`\), the application router depends on the UAA server for user authentication, and the UAA server might have its own session timeout defined. To avoid problems caused by unexpected timeouts, it is recommended that the session timeout values configured for the application router and the UAA are identical."



<a name="loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_d4z_hgn_mv"/>

## SEND\_XFRAMEOPTIONS

By default, the application router sends the `X-Frame-Options` header with the value “`SAMEORIGIN`”. You can change this behavior either by disabling the sending of the default header value \(for example, by setting SEND\_XFRAMEOPTIONS environment variable to false\) or by overriding the value, for example, by configuring additional headers \(with the *<httpHeaders\>* environment variable.

The following example shows how to disable the sending of the `X-Frame-Options` for a specific application, `myApp1`:

<code>xs set-env <i class="varname">&lt;myApp1&gt;</i> SEND_XFRAMEOPTIONS false</code>



<a name="loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_nrz_hgn_mv"/>

## CJ\_PROTECT\_WHITELIST

The *<CJ\_PROTECT\_WHITELIST\>* specifies a list of origins \(for example, host or domain names\) that do not need to be protected against click-jacking attacks. This list of allowed host names and domains are used by the application router's allow-list service to protect applications against click-jacking attacks. When an HTML page needs to be rendered in a frame, a check is done by calling the allow-list service to validate if the parent frame is allowed to render the requested content in a frame. The check itself is provided by the allow-list service

The following example shows how to add a host name to the click-jacking protection allow list for the application, `myApp1`:

<code>xs set-env <i class="varname">&lt;myApp1&gt;</i> CJ_PROTECT_WHITELIST {<i class="varname">&lt;protocol&gt;</i>, <i class="varname">&lt;hostname&gt;</i>, <i class="varname">&lt;portNr&gt;</i>}</code>

The content is a JSON list of objects with the properties listed in the following table:

**Allowed Host and Domain Names**


<table>
<tr>
<th valign="top">

Property

</th>
<th valign="top">

Type

</th>
<th valign="top">

Mandatory

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`protocol` 

</td>
<td valign="top">

String

</td>
<td valign="top">

No

</td>
<td valign="top">

URI scheme, for example “HTTP”.

</td>
</tr>
<tr>
<td valign="top">

`host` 

</td>
<td valign="top">

String

</td>
<td valign="top">

Yes

</td>
<td valign="top">

A valid host name, for example, `acme.com.hostname`, or a domain name defined with an asterisk \(\*\) `*.acme.com`.

</td>
</tr>
<tr>
<td valign="top">

`port` 

</td>
<td valign="top">

String/Number

</td>
<td valign="top">

No

</td>
<td valign="top">

Port string or number containing a valid port.

</td>
</tr>
</table>

> ### Note:  
> Matching is done against the properties provided. For example, if only the host name is provided, the allow-list service matches all schemata and protocols.

<code>xs set-env <i class="varname">&lt;myApp1&gt;</i> CJ_PROTECT_WHITELIST {<i class="varname">&lt;*.acme.com&gt;</i>}</code>



<a name="loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_ijs_5fm_4v"/>

## WS\_ALLOWED\_ORIGINS

When the application router receives an upgrade request, it verifies that the `origin` header includes the URL of the application router. If this is not the case, then an HTTP response with status 403 is returned to the client. This origin verification can be further configured with the environment variable *<WS\_ALLOWED\_ORIGINS\>*, which defines a list of the allowed origins the application router uses in the verification process.

> ### Note:  
> The structure of the *<WS\_ALLOWED\_ORIGINS\>* variable is the same as the variable *<CJ\_PROTECT\_WHITELIST\>*.

<code>xs set-env <i class="varname">&lt;myApp1&gt;</i> WS_ALLOWED_ORIGINS</code> \{*<\*.acme.com\>*\}



<a name="loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_x5z_hgn_mv"/>

## JWT\_REFRESH

The `JWT_REFRESH` environment variable is used to configure the application router to refresh a JSON Web Token \(JWT\) for an application, by default, 5 minutes before the JWT expires, if the session is active.

<code>xs set-env <i class="varname">&lt;myApp1&gt;</i> JWT_REFRESH 1</code>

If the JWT is close to expiration and the session is still active a JWT refresh will be triggered *<JWT\_REFRESH\>* minutes before expiration. The default value is 5 minutes. To disable the automatic refresh, set the value of *<JWT\_REFRESH\>* to 0 \(zero\).



<a name="loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_wf1_lgn_mv"/>

## UAA\_SERVICE\_NAME

The `UAA_SERVICE_NAME` environment variable enables you to configure an instance of the User Account and Authentication service for a specific application, as illustrated in the following example:

<code>xs set-env <i class="varname">&lt;myApp1&gt;</i> UAA_SERVICE_NAME <i class="varname">&lt;myUAAServiceName&gt;</i></code>

> ### Note:  
> The details of the service configuration is defined in the *<VCAP\_SERVICES\>* environment variable, which is not configured by the user.



<a name="loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_owp_xch_wx"/>

## INCOMING\_CONNECTION\_TIMEOUT

The `INCOMING_CONNECTION_TIMEOUT` environment variable enables you to set the maximum time \(in milliseconds\) allowed for a client connection, as illustrated in the following example:

<code>xs set-env <i class="varname">&lt;myApp1&gt;</i> INCOMING_CONNECTION_TIMEOUT 60,000</code>

If the specified time is exceeded, the connection is closed. If `INCOMING_CONNECTION_TIMEOUT` is set to zero \(0\), the connection-timeout feature is disabled. The default value for `INCOMING_CONNECTION_TIMEOUT` is 120,000 ms \(2 min\).



<a name="loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_zhq_xch_wx"/>

## TENANT\_HOST\_PATTERN

The `TENANT_HOST_PATTERN` environment variable enables you to specify a string containing a regular expression with a capturing group. The requested host is matched against this regular expression. The value of the first capturing group is used as the tenant Id., as illustrated in the following example:

<code>xs set-env <i class="varname">&lt;myApp1&gt;</i> TENANT_HOST_PATTERN</code>



<a name="loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_vsq_xch_wx"/>

## COMPRESSION

The `COMPRESSION` environment variable enables you to configure the compression of resources before a response to the client, as illustrated in the following example:

<code>xs set-env <i class="varname">&lt;myApp1&gt;</i> COMPRESSION</code>



<a name="loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_wpy_yfg_2z"/>

## SECURE\_SESSION\_COOKIE

The `SECURE_SESSION_COOKIE` can be set to *true* or *false*. By default, the `Secure` flag of the session cookie is set depending on the environment the application router runs in. For example, when the application router is running behind a router that is configured to serve HTTPS traffic, then this flag will be present. During local development the flag is not set.

> ### Note:  
> If the `Secure` flag is enforced, the application router will reject requests sent over unencrypted connections.

The following example illustrates how to set the `SECURE_SESSION_COOKIE` environment variable:

<code>xs set-env <i class="varname">&lt;myApp1&gt;</i> SECURE_SESSION_COOKIE true</code>



<a name="loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_s1p_qvj_2z"/>

## REQUEST\_TRACE

You can enable additional traces of the incoming and outgoing requests by setting the environment variable *<REQUEST\_TRACE\>* to “`true`”. If enabled, basic information is logged for every incoming and outgoing request to the application router.

The following example illustrates how to set the `REQUEST_TRACE` environment variable:

<code>xs set-env <i class="varname">&lt;myApp1&gt;</i> REQUEST_TRACE true</code>

> ### Tip:  
> This is in addition to the information generated by the Node.js package `@sap/logging` that is used by the application router.



<a name="loio0aac697f0cf7444193ed5eb0fc6e5bd0__section_nt3_t4k_sz"/>

## CORS

The `CORS` environment variable enables you to provide support for cross-origin requests, for example, by allowing the modification of the request header. Cross-origin resource sharing \(CORS\) permits Web pages from other domains to make HTTP requests to your application domain, where normally such requests would automatically be refused by the Web browser's security policy.

Cross-origin resource sharing \(CORS\) is a mechanism that allows restricted resources on a Web page to be requested from another domain \(protocol and port\) outside the domain \(protocol and port\) from which the first resource was served. The CORS configuration enables you to define details to control access to your application resource from other Web browsers. For example, you can specify where requests can originate from or what is allowed in the request and response headers. The following example illustrates a basic CORS configuration:

```
[
  {
      "uriPattern": "^\route1$",
      "allowedMethods": [
        "GET"
      ],
      "allowedOrigin": [
        {
          "host": "host.acme.com",
          "protocol": "https",
          "port": 345
        }
      ],
      "maxAge": 3600,
      "allowedHeaders": [
        "Authorization",
        "Content-Type"
      ],
      "exposeHeaders": [
        "customHeader1",
        "customHeader2"
      ],
      "allowedCredentials": true
    }
]
```

The CORS configuration includes an array of objects with the following properties, some of which are mandatory:

**Available Settings for CORS Options**


<table>
<tr>
<th valign="top">

CORS Property

</th>
<th valign="top">

Type

</th>
<th valign="top">

Mandatory

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`uriPattern`

</td>
<td valign="top">

String

</td>
<td valign="top">

Yes

</td>
<td valign="top">

A regular expression \(RegExp\) representing the source routes to which the CORS configuration applies. To ensure that the RegExp matches the complete path, surround it with ^ and $,f or example, `"uriPattern": "^\route1$"`. Defaults: none

</td>
</tr>
<tr>
<td valign="top">

`allowedOrigin`

</td>
<td valign="top">

Array

</td>
<td valign="top">

Yes

</td>
<td valign="top">

A comma-separated list of objects each of which contains a host name, port and protocol that are allowed by the server, for example: `[{“host”: "www.acme.com"}]` or `[{“host”: “.acme.com”}]`.

> ### Note:  
> Matching is case-sensitive. In addition, if no port or protocol is specified, the default is `“*”`.

The defaults configuration is: `[{“host”: "*"}]`, which means that the server allows **any** origin to access the resource.

</td>
</tr>
<tr>
<td valign="top">

`allowedMethods`

</td>
<td valign="top">

Array

</td>
<td valign="top">

No

</td>
<td valign="top">

A comma-separated list of HTTP methods that are allowed by the server, for example, <code>“GET”, “POST”</code>. If `allowMethods` is defined but no method is specified, the default <code>“GET”, “POST”, “HEAD”, “OPTIONS”</code> \(all\) applies.

> ### Tip:  
> The specified methods must be upper-case, for example,`GET`. Matching of the method type is case-sensitive.



</td>
</tr>
<tr>
<td valign="top">

`allowedHeaders`

</td>
<td valign="top">

Array

</td>
<td valign="top">

No

</td>
<td valign="top">

A comma-separated list of request headers that are allowed by the server. the default values are as follows: `[“Origin”, “Accept”, “X-Requested-With”, “Content-Type”, “Access-Control-Request-Method”, “Access-Control-Request-Headers”]`.

</td>
</tr>
<tr>
<td valign="top">

`maxAge`

</td>
<td valign="top">

String

</td>
<td valign="top">

No

</td>
<td valign="top">

A single value specifying the length of time \(in seconds\) a preflight request should be cached for. A negative value the prevents CORS filter from adding this response header to the pre-flight response. If `maxAge` is defined but no value is specified, the default time of “1800” seconds applies.

</td>
</tr>
<tr>
<td valign="top">

`exposeHeaders`

</td>
<td valign="top">

Array

</td>
<td valign="top">

No

</td>
<td valign="top">

A comma-separated list of **response** headers that are allowed to be exposed. If `exposeHeaders` is defined but no response header is specified for exposure, no default value is supplied.

</td>
</tr>
<tr>
<td valign="top">

`allowedCredentials` 

</td>
<td valign="top">

Boolean

</td>
<td valign="top">

No

</td>
<td valign="top">

A flag that indicates if the specified resource supports user credentials. The default setting is “true”.

</td>
</tr>
</table>

It is also possible to include the CORS configuration in either the `manifest.yml` or the `manifest-op.yml` file. The code in the following example enables the CORS configuration for any route with a source URI pattern that matches the RegExp “`^\route1$`”:

> ### Sample Code:  
> CORS Configuration in the `manifest.yml` File
> 
> ```
> - name: node-hello-world
>   memory: 100M
>   path: web
>   env:
>     CORS: >
>       [
>         {
>           "allowedOrigin":[
>                             {
>                                 "host":"my_host",
>                                 "protocol":"https"
>                             }
>                           ],
>           "uriPattern":"^/route1$"
>         }
> ```

**Related Information**  


[Configure the Multitarget Application Router](configure-the-multitarget-application-router-6ba8959.md "The application routes to the available microservices are described in the xs-app.json file.")

[Application Router Configuration Syntax](application-router-configuration-syntax-5f77e58.md "The application description defined in the xs-app.json file contains the configuration information used by the application router.")

[The Application Descriptor](the-application-descriptor-96c7545.md "Understand the contents of the file used to configure the multitarget application router.")

