<!-- loio5f77e58ec01b46f6b64ee1e2afe3ead7 -->

# Application Router Configuration Syntax

The application description defined in the `xs-app.json` file contains the configuration information used by the application router.



The following example of an `xs-app.json` application descriptor shows the JSON-compliant syntax required and the properties that either must be set or can be specified as an additional option.

> ### Code Syntax:  
> ```
> {
>   "welcomeFile": "index.html",
>   "authenticationMethod": "route",
>   "sessionTimeout": 10,
>   "pluginMetadataEndpoint": "/metadata",
>   "routes": [
>     {
>       "source": "^/sap/ui5/1(.*)$",
>       "target": "$1",
>       "destination": "ui5",
>       "csrfProtection": false
>     },
>     {
>       "source": "/employeeData/(.*)",
>       "target": "/services/employeeService/$1",
>       "destination": "employeeServices",
>       "authenticationType": "xsuaa",
>       "scope": ["$XSAPPNAME.viewer", "$XSAPPNAME.writer"],
>       "csrfProtection": true
>     },
>     {
>       "source": "^/(.*)$",
>       "target": "/web/$1",
>       "localDir": "static-content",
>       "replace": {
>         "pathSuffixes": ["/abc/index.html"],
>         "vars": ["NAME"]
>       }
>     }
>   ],
>   "login": {
>      "callbackEndpoint": "/custom/login/callback"
>   },
>   "logout": {
>      "logoutEndpoint": "/my/logout",
>      "logoutPage": "/logout-page.html"
>   },
>   "destinations": {
>      "employeeServices": {
>        "logoutPath": "/services/employeeService/logout",
>        "logoutMethod": "GET"
>      }
>   }, 
>   "compression": { 
>      "minSize": 2048
>   },
>   "whitelistService": {
>      "endpoint": "/whitelist/service"
>   },
>   "websockets": {
>     "enabled": true
>   },
>   "errorPage": [
>     {"status": [400,401,402], "file": "/custom-err-4xx.html"},
>     {"status": 501, "file": "/custom-err-501.html"}
>   ] 
> }
> ```



<a name="loio5f77e58ec01b46f6b64ee1e2afe3ead7__section_cpm_hfr_xs"/>

## welcomeFile

The Web page served by default if the HTTP request does not include a specific path, for example, `index.html`.

<a name="loio5f77e58ec01b46f6b64ee1e2afe3ead7__table_xh1_p2r_xs"/>Application-Router Parameters


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

Values



</th>
</tr>
<tr>
<td valign="top">

 `welcomeFile` 



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

HTML page, for example, `index.html`



</td>
</tr>
</table>

> ### Code Syntax:  
> ```
> 
> "welcomeFile": "index.html", 
> 
> ```



<a name="loio5f77e58ec01b46f6b64ee1e2afe3ead7__section_rss_hfr_xs"/>

## authenticationMethod

The method used to authenticate user requests, for example: “route” or “none” \(no authentication\).

> ### Code Syntax:  
> ```
>  
> "authenticationMethod" : "route",
> 
> ```


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

Values



</th>
</tr>
<tr>
<td valign="top">

 `authenticationMethod` 



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

The following authentication methods are allowed:

-   `route`

    Authentication type is defined in the route configuration

-   `none`

    Disables authentication for all routes




</td>
</tr>
</table>

> ### Caution:  
> If `authenticationMethod` is set to “`none`”, logon with User Account and Authentication \(UAA\) is disabled.



<a name="loio5f77e58ec01b46f6b64ee1e2afe3ead7__section_qbz_hfr_xs"/>

## routes

Defines all route objects, for example: `source`, `target`, and, `destination`.

<a name="loio5f77e58ec01b46f6b64ee1e2afe3ead7__table_mlp_p2r_xs"/>Application Router: Routes Properties


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

 `source` 



</td>
<td valign="top">

RegEx



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Regular expression that matches an incoming request path. To ensure the RegEx matches the complete path, wrap it with ^ and $, for example, `"^/sap/ui5/1(.*)$"`. A request matches a particular route if its `path` contains the specified regular expression.

> ### Tip:  
> -   Use <code>“matchCase”</code> to specify if the regular expression defined in `path` is matched in a case-sensitive \(`true`\) way or not \(`false`\). Default is `true`.



</td>
</tr>
<tr>
<td valign="top">

 `httpMethods` 



</td>
<td valign="top">

Array of uppercase HTTP methods



</td>
<td valign="top">

No



</td>
<td valign="top">

HTTP methods that will be served by this route; the supported methods are: `DELETE`, `GET`, `HEAD`, `OPTIONS`, `POST`, `PUT`, `TRACE`, and `PATCH`.

> ### Tip:  
> If this option is not specified, the route will serve any HTTP method.



</td>
</tr>
<tr>
<td valign="top">

 `target` 



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

The incoming request path is rewritten to this target



</td>
</tr>
<tr>
<td valign="top">

 `destination` 



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

The destination to which the incoming request should be forwarded. This must match one of the `name` properties defined in the destinations environment variable..



</td>
</tr>
<tr>
<td valign="top">

 `scope` 



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

The authorization scope required to access the target path. The scope itself is defined in the application's security descriptor \(`xs-security.json`\), for example, <code>“$XSAPPNAME.Display”</code> or <code>“$XSAPPNAME.Create”</code>.



</td>
</tr>
<tr>
<td valign="top">

 `localDir` 



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

The directory from which application router serves static content \(for example, from the application's `web/` module\)



</td>
</tr>
<tr>
<td valign="top">

 `replace` 



</td>
<td valign="top">

Object



</td>
<td valign="top">

No



</td>
<td valign="top">

An object that contains the configuration for replacing placeholders with values from the environment. It is only relevant for static resources.



</td>
</tr>
<tr>
<td valign="top">

 `csrfProtection` 



</td>
<td valign="top">

Boolean



</td>
<td valign="top">

No



</td>
<td valign="top">

Toggle whether this route needs CSRF token protection. The default value is “true”. The application router enforces CSRF protection for any HTTP request that changes state on the server side, for example: PUT, POST, or DELETE.



</td>
</tr>
<tr>
<td valign="top">

 `authenticationType` 



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

The value can be “`xsuaa`”, “`basic`” or “`none`”. The default value is “`xsuaa`”. When “`xsuaa`” is used the specified UAA server will handle the authentication \(the user is redirected to the UAA's login form\). The basic mechanism works with SAP HANA users. If “`none`” is used then no authentication is needed for this route.



</td>
</tr>
<tr>
<td valign="top">

 `cacheControl` 



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

A string representing the value of the Cache-Control header, which is set on the response when serving static resources. By default the Cache-Control header is not set.

> ### Note:  
> This value is relevant only for static resources.



</td>
</tr>
</table>

> ### Code Syntax:  
> ```
> "routes": [ 
>   { 
>     "source": "^/sap/ui5/1(.*)$", 
>     "target": "$1", 
>     "destination": "ui5", 
>     "scope": "$XSAPPNAME.viewer",
>     "authenticationType": "xsuaa"
>     "csrfProtection": true
>   } 
> ]
> ```

> ### Note:  
> The properties `target`, `destination`, and `localDir` are optional. However, at least one of them **must** be defined.
> 
> The properties `destination` and `localDir` cannot be used together in the same route.

If there is no route defined for serving static content via `localDir`, a default route is created for “`resources`” directory as follows:

> ### Sample Code:  
> ```
> {
>   "routes": [
>     {
>       "source": " ^/(.*)$",
>       "localDir": "resources"
>     }
>   ]
> }
> ```

> ### Note:  
> If there is at least one route using `localDir`, the default route is not added.

The `httpMethods` option allows you to split the same path across different targets depending on the HTTP method. For example:

> ### Sample Code:  
> ```
> "routes": [ 
>   { 
> 	"source": "^/app1/(.*)$",
> 	"target": "/before/$1/after",
> 	"httpMethods": ["GET", "POST"]
>   } 
> ]
> ```

This route will be able to serve only GET and POST requests. Any other method \(including extension ones\) will get a ***405 Method Not Allowed*** response. The same endpoint can be split across multiple destinations depending on the HTTP method of the requests:

> ### Sample Code:  
> ```
> "routes": [ 
> {
>   "source": "^/app1/(.*)$",
>   "destination" : "dest-1",
>   "httpMethods": ["GET"]
> },
> {
>   "source": "^/app1/(.*)$",
>   "destination" : "dest-2",
>   "httpMethods": ["DELETE", "POST", "PUT"]
> } 
> ]
> ```

The sample code above will route GET requests to the target `dest-1`, DELETE, POST and PUT to `dest-2`, and any other method receives a ***405 Method Not Allowed*** response. It is also possible to specify `catchAll` routes, namely those that do not specify `httpMethods` restrictions:

> ### Sample Code:  
> ```
> "routes": [ 
> {
>   "source": "^/app1/(.*)$",
>   "destination" : "dest-1",
>   "httpMethods": ["GET"]
> },
> {
>   "source": "^/app1/(.*)$",
>   "destination" : "dest-2"
> }} 
> ]
> ```

In the sample code above, GET requests will be routed to `dest-1`, and all the rest to `dest-2`.



### replace

The `replace` object configures the placeholder replacement in static text resources.

> ### Sample Code:  
> ```
> {
>  "replace": {
>    "pathSuffixes": ["index.html"],
>    "vars": ["escaped_text", "NOT_ESCAPED"]
>  }
> }
> ```

The `replace` keyword requires the following properties:

<a name="loio5f77e58ec01b46f6b64ee1e2afe3ead7__table_qgd_34y_lv"/>Replacement Properties for Static Resource URLs


<table>
<tr>
<th valign="top">

Property



</th>
<th valign="top">

Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `pathSuffixes` 



</td>
<td valign="top">

Array



</td>
<td valign="top">

An array defining the path suffixes that are relative to `localDir`. Only files with a path ending with any of these suffixes will be processed.



</td>
</tr>
<tr>
<td valign="top">

 `vars` 



</td>
<td valign="top">

Array



</td>
<td valign="top">

An allow list with the environment variables that will be replaced in the files matching the suffix specified in `pathSuffixes`.



</td>
</tr>
</table>

The supported tags for replacing environment variables are: `{{ENV_VAR}}` and `{{{ENV_VAR}}}` . If there such an environment variable is defined, it will be replaced, otherwise it will be just an empty string.

> ### Note:  
> Any variable that is replaced using two-brackets syntax `{{ENV_VAR}}` will be HTML-escaped; the triple brackets syntax `{{{ENV_VAR}}}` is used when the replaced values do not need to be escaped and all values will remain unchanged. For example, if the value of the environment variable is `ab"cd` the result will be `ab&amp;quot;cd`.

If your application descriptor `xs-app.json` contains a route like the one illustrated in the following example,

```
{
 "source": "^/get/home(.*)",
 "target": "$1",
 "localDir": "resources",
 "replace": {
   "pathSuffixes": ["index.html"],
   "vars": ["escaped_text", "NOT_ESCAPED"]
 }
}
```

And your application uses the following `index.html` start file:

> ### Sample Code:  
> ```
> <html>
>  <head>
>   <title>{{escaped_text}}</title>
>   <script src="{{{NOT_ESCAPED}}}/index.js"/>
>  </head>
> </html>
> ```

Then, in `index.html`, `{{escaped_text}}` and `{{{NOT_ESCAPED}}}` will be replaced with the value defined in the environment variables *<escaped\_text\>* and *<NOT\_ESCAPED\>*.

> ### Note:  
> **All** `index.html` files are processed; if you want to apply the replacement only to specific files, you must set the path relative to `localDir`. In addition, all files should comply with the UTF-8 encoding rules.

The content type returned by a request is based on the file extension specified in the route. The application router support the following file types:

-   .json \(application/json\)

-   .txt \(text/plain\)

-   .html \(text/html\) **default**

-   .js \(application/javascript\)

-   .css \(test/css\)


The following table illustrates some examples of the `pathSuffixes` properties:

<a name="loio5f77e58ec01b46f6b64ee1e2afe3ead7__table_hgz_3ry_lv"/>Examples of the pathSuffixes Property


<table>
<tr>
<th valign="top">

Example



</th>
<th valign="top">

Result



</th>
</tr>
<tr>
<td valign="top">

 `{ "pathSuffixes": [".html"] }` 



</td>
<td valign="top">

All files with the extension `.html` under `localDir` and its subfolders will be processed.



</td>
</tr>
<tr>
<td valign="top">

 `{ "pathSuffixes": ["/abc/main.html", "some.html"] }` 



</td>
<td valign="top">

For the suffix `/abc/main.html`, all files named main.html which are inside a folder named `abc` will be processed.

For the suffix `some.html`, all files with a name that ends with “`some.html`” will be processed, for example:`some.html`, `awesome.html`.



</td>
</tr>
<tr>
<td valign="top">

 `{ "pathSuffixes": [".html"] }` 



</td>
<td valign="top">

All files with the name “`some.html`” will be processed. For example: `some.html` , `/abc/some.html`.



</td>
</tr>
</table>



<a name="loio5f77e58ec01b46f6b64ee1e2afe3ead7__section_imh_gsy_lv"/>

## sessionTimeout

Define the amount of time \(in minutes\) for which a session can remain inactive before it closes automatically \(times out\); the default time out is 15 minutes.

> ### Note:  
> The `sessionTimeout` property is no longer available; to set the session time out value, use the environment variable *<SESSION\_TIMEOUT\>*.

> ### Sample Code:  
> ```
> {
>   "sessionTimeout": 40,
> }
> ```

With the configuration in the example above, a session timeout will be triggered after 40 minutes and involves central log out.



<a name="loio5f77e58ec01b46f6b64ee1e2afe3ead7__section_xx1_lty_lv"/>

## login

A redirect to the application router at a specific endpoint takes place during OAuth2 authentication with the User Account and Authentication service \(UAA\). This endpoint can be configured in order to avoid possible collisions, as illustrated in the following example:

> ### Sample Code:  
> Application Router “login” Property
> 
> ```
> "login": { 
>   "callbackEndpoint": "/custom/login/callback" 
> } 
> ```

> ### Tip:  
> The default endpoint is “`/login/callback`”.



<a name="loio5f77e58ec01b46f6b64ee1e2afe3ead7__section_bdm_zkn_tt"/>

## logout

Define any options that apply if you want your application to have central log out end point. In this object you can define an application's central log out end point by using the `logoutEndpoint` property, as illustrated in the following example:

> ### Sample Code:  
> ```
> "logout" {
>   "logoutEndpoint": "/my/logout"
> }
> ```

Making a `GET` request to “`/my/logout`” triggers a client-initiated central log out. Central log out can be initiated by a client or triggered due to a session timeout, with the following consequences:

-   Client-initiated central log out
    -   Deletes the user session
    -   Requests the log out paths for all your back-end services \(if you provided these paths in the `destinations` property\).
    -   Redirects to the User Account and Authentication service \(UAA\), if such a service is provided, and logs out from there.

        > ### Tip:  
        > It is not possible to redirect back to your application after logging out from UAA.


-   Session time out
    -   Deletes the user session
    -   Requests the log out paths for all your back-end services \(if you provided these paths in the `destinations` property\).


You can use the `logoutPage` property to specify the Web page in one of the following ways:

-   URL path

    The UAA service redirects the user back to the application router, and the path is interpreted according to the configured routes.

    > ### Note:  
    > The resource that matches the URL path specified in the property `logoutPage` should not require authentication; for this route, the property `authenticationType` must be set to “`none`”. If your application enables user logon with single sign-on authentication, a custom logout page is needed to prevent a login-logout loop. For more information see SAP Note [2699214](https://launchpad.support.sap.com/#/notes/2699214).

    In the following example, `my-static-resources` is a folder in the working directory of the application router; the folder contains the file `logout-page.html` along with other static resources.

    > ### Sample Code:  
    > ```
    > { 
    >   "authenticationMethod": "route", 
    >   "logout": { 
    >     "logoutEndpoint": "/my/logout", 
    >     "logoutPage": "/logout-page.html"
    >   }, 
    >   "routes": [ 
    >     {
    >       "source": "^/logout-page.html$", 
    >       "localDir": "my-static-resources", 
    >       "authenticationType": "none"
    >     }
    >   ]
    > } 
    > ```

-   Absolute HTTP\(S\) path

    The UAA will redirect the user to a page \(or application\) different from the application router.

    > ### Sample Code:  
    > ```
    > "logout": {
    >   "logoutEndpoint": "/my/logout",
    >   "logoutPage": "http://acme.com/employees.portal" 
    > } 
    > ```




<a name="loio5f77e58ec01b46f6b64ee1e2afe3ead7__section_bch_ksn_tt"/>

## destinations

Specify any additional options for your destinations. The destinations section in `xs-app.json` extends the destination configuration in the deployment manifest \(`manifest.yml`\), for example, with some static properties such as a logout path.

> ### Sample Code:  
> ```
> {
>   "destinations": {
>     "node-backend": {
>       "logoutPath": "/ui5logout",
>       "logoutMethod": "GET"
>     }
>   }
> }
> ```

The following syntax rules apply:

<a name="loio5f77e58ec01b46f6b64ee1e2afe3ead7__table_ddv_cnn_tt"/>Application Router: Destination Properties


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

 `logoutPath` 



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

The log out end point for your destination. The `logoutPath` will be called when central log out is triggered or a session is deleted due to a time out. The request to `logoutPath` contains additional headers, including the JWT token.



</td>
</tr>
<tr>
<td valign="top">

 `logoutMethod` 



</td>
<td valign="top">

String



</td>
<td valign="top">

No



</td>
<td valign="top">

The `logoutMethod` property specifies the HTTP method with which the `logoutPath` will be requested, for example, POST, PUT, GET; the default value is POST



</td>
</tr>
</table>



<a name="loio5f77e58ec01b46f6b64ee1e2afe3ead7__section_qmb_st5_yt"/>

## compression

The `compression` keyword enables you to define if the application router compresses text resources before sending them. By default, resources larger than 1KB are compressed. If you need to change the compression size threshold, for example, to “2048 bytes”, you can add the optional property <code>“minSize”</code>: *<size\_in\_KB\>*, as illustrated in the following example.

> ### Sample Code:  
> ```
> {
>   "compression": {
>       "minSize": 2048
>   }
> }
> ```

You can disable compression in the following ways:

-   Global

    Within the compression section add "enabled": false

-   Front end

    The client sends a header “`Accept-Encoding`” which does not include “`gzip`”.

-   Back end

    The application sends a header “`Cache-Control`” with the “`no-transform`” directive.


<a name="loio5f77e58ec01b46f6b64ee1e2afe3ead7__table_ikc_z2n_tx"/>Application Router: Compression Properties


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

 `minSize` 



</td>
<td valign="top">

Number



</td>
<td valign="top">

No



</td>
<td valign="top">

Text resources larger than this size will be compressed.



</td>
</tr>
<tr>
<td valign="top">

 `enabled` 



</td>
<td valign="top">

Boolean



</td>
<td valign="top">

No



</td>
<td valign="top">

Globally disables or enables compression. The default value is true.



</td>
</tr>
</table>

> ### Note:  
> If the *<COMPRESSION\>* environment variable is set it will overwrite any existing values.



<a name="loio5f77e58ec01b46f6b64ee1e2afe3ead7__section_stg_ssy_lv"/>

## pluginMetadataEndpoint

Adds an endpoint that serves a JSON string representing all configured plugins.

> ### Sample Code:  
> ```
> {
>   "pluginMetadataEndpoint": "/metadata"
> }
> ```

> ### Note:  
> If you request the relative path `/metadata` of your application, a JSON string is returned with the configured plug-ins.



<a name="loio5f77e58ec01b46f6b64ee1e2afe3ead7__section_lcf_5sy_lv"/>

## whitelistService

Enable the white\(allow\)-list service to help prevent against click-jacking attacks. Enabling the allow-list service opens an endpoint accepting GET requests at the relative path configured in the `endpoint` property, as illustrated in the following example:

> ### Sample Code:  
> ```
> {
>   "whitelistService": {
>     "endpoint": "/allowlist/service"
>   }
> }
> ```

If the allow-list service is enabled in the application router, each time an HTML page needs to be rendered in a frame, the allow-list service is used check if the parent frame is allowed to render the content in a frame.



### Host Names and Domain Names

The allow-list service reads a list of allowed host names and domains defined in the environment variable *<CJ\_PROTECT\_WHITELIST\>*; the content is a JSON list of objects with the following properties:

<a name="loio5f77e58ec01b46f6b64ee1e2afe3ead7__table_dhz_41z_lv"/>Allowed Host and Domain Names


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

The following snippet shows an example of the resulting JSON array:

> ### Sample Code:  
> ```
> [
>  {
>   "protocol": "http", 
>   "host": "*.acme.com", 
>   "port": 12345 
>  },
>  {
>   "host": "hostname.acme.com"
>  }
> ]
> ```

> ### Note:  
> Matching is done against the properties provided. For example, if only host name is provided, the allow-list service returns “`framing: true`” for all, and matching will be for all schemata and protocols.



### Return Value

The allow-list service accepts only `GET` requests, and returns a JSON object as the response. The allow-list service call uses the parent origin as URI parameter \(URL encoded\) as follows:

> ### Sample Code:  
> ```
> GET url/to/whitelist/service?parentOrigin=https://parent.domain.acme.com
> 
> ```

The response is a JSON object with the following properties; property <code>“active”</code> has the value `false` only if *<CJ\_PROTECT\_WHITELIST\>* is not provided:

> ### Sample Code:  
> ```
> {
>   "version" : "1.0",
>   "active" : true | false, 
>   "origin" : "<same as passed to service>", 
>   "framing" : true | false
> }
> ```

The <code>“active”</code> property enables framing control; the <code>“framing”</code> property specifies if framing should be allowed. By default, the Application Router \(`approuter.js`\) sends the `X-Frame-Options` header with value the `SAMEORIGIN`.

> ### Tip:  
> If the allow-list service is enabled, the header value probably needs to be changed, see the *X-Frame-Options* header section for details about how to change it.



<a name="loio5f77e58ec01b46f6b64ee1e2afe3ead7__section_thr_vsy_lv"/>

## websockets

The application router can forward web-socket communication. Web-socket communication must be enabled in the application router configuration, as illustrated in the following example. If the back-end service requires authentication, the upgrade request should contain a valid session cookie. The application router supports the destination schemata "`ws`", "`wss`", "`http`", and "`https`".

> ### Sample Code:  
> ```
> {
>   "websockets": {
>     "enabled": true
>   }
> }
> ```

> ### Restriction:  
> A web-socket ping is not forwarded to the back-end service.



<a name="loio5f77e58ec01b46f6b64ee1e2afe3ead7__section_lwz_jtf_2z"/>

## errorPage

Errors originating in the application router show the HTTP status code of the error. It is possible to display a custom error page using the `errorPage` property.

The property is an array of objects, each object can have the following properties:

<a name="loio5f77e58ec01b46f6b64ee1e2afe3ead7__table_h5m_nvf_2z"/>Application Router: errorPage Properties


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

 `status` 



</td>
<td valign="top">

Number/Array



</td>
<td valign="top">

Yes



</td>
<td valign="top">

HTTP status code.



</td>
</tr>
<tr>
<td valign="top">

 `file` 



</td>
<td valign="top">

String



</td>
<td valign="top">

Yes



</td>
<td valign="top">

File path relative to the working directory of the application router.



</td>
</tr>
</table>

In the following code example, errors with status code “400”, “401” and “402” will show the content of `./custom-err-4xx.html`; errors with the status code “501” will display the content of `./http_resources/custom-err-501.html`.

> ### Sample Code:  
> ```
> { "errorPage" : [
>     {"status": [400,401,402], "file": "./custom-err-40x.html"},
>     {"status": 501, "file": "./http_resources/custom-err-501.html"}
>   ]
> }
> ```

> ### Note:  
> The contents of the `errorPage` configuration section have no effect on errors that are not generated by the application router.

**Related Information**  


[Application Router Environment Variables](application-router-environment-variables-0aac697.md "A list of environment variables that can be used to configure the application router.")

[Application Security Descriptor Configuration Syntax](../100-HANA-Cloud-DB-Dev-Security/application-security-descriptor-configuration-syntax-6d3ed64.md "The syntax required to set the properties and values defined in the xs-security.json application-security description file.")

[The Application Descriptor](the-application-descriptor-96c7545.md "Understand the contents of the file used to configure the multitarget application router.")

[Configure the Multitarget Application Router](configure-the-multitarget-application-router-6ba8959.md "The application routes to the available microservices are described in the xs-app.json file.")

