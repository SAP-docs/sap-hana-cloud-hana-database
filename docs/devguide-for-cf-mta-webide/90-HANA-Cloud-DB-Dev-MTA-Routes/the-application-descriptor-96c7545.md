<!-- loio96c7545f62504d55b669010d8fb9c41e -->

# The Application Descriptor

Understand the contents of the file used to configure the multitarget application router.

When a business application consists of several different apps \(microservices\), the application router is used to provide a single entry point to that business application. The application router is responsible for the following tasks:

-   Dispatch requests to back-end microservices \(reverse proxy\)

-   Authenticate users

-   Serve static content

-   In multi-tenancy scenarios, derive the tenant information from the URL and forward the information to the XS UAA service so that the authentication request is redirected to the appropriate tenant-specific Identity Provider \(IdP\), for example,using SAML “Bearer Assertions”.


The application descriptor is a file that contains the configuration information used by the application router. The file is named `xs-app.json` and its content is formatted according to JavaScript Object Notation \(JSON\) rules.

> ### Tip:  
> The different applications \(microservices\) are the destinations to which the incoming requests are forwarded. The rules that determine which request should be forwarded to which destination are called routes. For every destination there can be more than one route.



<a name="loio96c7545f62504d55b669010d8fb9c41e__section_k5x_xzr_s1b"/>

## User Authentication Services

User authentication is performed by the User Account and Authentication \(UAA\) server. In the application run-time environment in Cloud Foundry on SAP Business Technology Platform, a service is created for the UAA configuration; by using the standard service-binding mechanism, the content of this configuration is available in the *<VCAP\_SERVICES\>* environment variable, which the application router can access to read the configuration details.

> ### Note:  
> The UAA service should have `xsuaa` in its tags or the environment variable *<UAA\_SERVICE\_NAME\>* should be defined, for example, to specify the **exact** name of the UAA service to use.

A calling component accesses a target service by means of the application router only if there is no JSON Web Token \(JWT\) token available, for example, if a user invokes the application from a Web browser. If a JWT token is already available, for example, because the user has already been authenticated, or the calling component uses a JWT token for its own OAuth client, the calling component calls the target service directly; it does not need to use the application router.

> ### Note:  
> The application router does not “hide” the back-end microservices in any way; they remain directly accessible when bypassing the application router. So the back-end microservices must protect all their end points by validating the JWT token and implementing proper authorization scope checks.

The application router supports the use of the `$XSAPPNAME` placeholder, which you can use in your route configuration, for example, in the `scope` property for the specified route. The value of `$XSAPPNAME` is taken from the UAA configuration \(for example, the `xsappname` property\). For more information, see *Application Router Configuration Syntax* in *Related Information*.



<a name="loio96c7545f62504d55b669010d8fb9c41e__section_bv2_twv_3x"/>

## Headers

In many cases back-end nodes need to respond to client requests with URLs. Since micro services are accessed through the application router component, the clients always request the application router’s URL. The back end nodes need to know the actual request URL in order can build URLs that are accessible by the client. If back-end nodes respond to client requests with URLs, these URLs need to be accessible to the client. For this reason, the application router passes the following `x-forwarding-*` headers to the client:

-   `x-forwarded-host`

    Contains the **host** header value that was sent by the client to the application router

-   `x-forwarded-proto`

    Contains the **protocol** that was used by the client to connect to the application router

-   `x-forwarded-for`

    Contains the **address** of the client which connects to the application router

-   `x-forwarded-path`

    Contains the original **path** which was requested by the client from the approuter


> ### Caution:  
> When the application router forwards a request to a destination, it blocks the header `host`.

“Hop-by-hop” headers are meaningful only for a single transport-level connection; these headers are not forwarded by the application router. The following headers are classified as “Hop-By-Hop” headers:

-   Connection

-   Keep-Alive

-   Public

-   Proxy-Authenticate

-   Transfer-Encoding

-   Upgrade


You can configure the application router to send additional HTTP headers, for example, by using the `httpHeaders` environment variable.



<a name="loio96c7545f62504d55b669010d8fb9c41e__section_ahn_twv_3x"/>

## Sessions

The application router establishes a session with the client \(browser\) using a session cookie. The application router intercepts all session cookies sent by back-end services and stores them in its own session. To prevent collisions between the various session cookies, back-end session cookies are not sent to the client. On request, the application router sends the cookies back to the respective back-end services so the services can establish their own sessions.

> ### Note:  
> Non-session cookies from back-end services **are** forwarded to the client, which might cause collisions between cookies. Applications should be able to handle cookie collisions.



### Session Contents

A session established by the application router typically contains the following elements:

-   Redirect location

    The location to redirect to after login; if the request is redirected to a UAA login form, the original request URL is stored in the session so that, after successful authentication, the user is redirected back to it.

-   CSRF token

    The CSRF token value if it was requested by the clients. For more information about protection against Cross Site Request Forgery see [CSRF Protection](the-application-descriptor-96c7545.md#loio96c7545f62504d55b669010d8fb9c41e__section_xj4_pcg_2z) below.

-   OAuth token

    The JSON Web Token \(JWT\) fetched from the User Account and Authentication service \(UAA\) and forwarded to back-end services in the `Authorization` header. The client never receives this token. The application router refreshes the JWT automatically before it expires \(if the session is still valid\). By default, this routine is triggered 5 minutes before the expiration of the JWT, but it can also be configured with the *<JWT\_REFRESH\>* environment variable \(the value is set in minutes\). If *<JWT\_REFRESH\>* is set to 0, the refresh action is disabled.

-   OAuth scopes

    The scopes owned by the current user, which is used to check if the user has the authorizations required for each request

-   Back-end session cookies

    All session cookies sent by back-end services




<a name="loio96c7545f62504d55b669010d8fb9c41e__section_om5_twv_3x"/>

## Scaling

The application router keeps all established sessions in local memory, and if multiple instances of the application router are running, there is no synchronization between the sessions. To scale the application router for multiple instances, session stickiness must be enabled so that each HTTP session is handled by the same application router instance.



<a name="loio96c7545f62504d55b669010d8fb9c41e__section_npy_twv_3x"/>

## Sizing and Memory Configuration

The application-router process should run with at least 256MB memory. The amount of memory actually required depends on the application the router is serving. The following aspects have an influence on the application's memory usage:

-   Concurrent connections

-   Active sessions

-   Size of the Java Web Token

-   Back-end session cookies


You can use the start-up parameter `max-old-space-size` to restrict the amount of memory used by the JavaScript heap. The default value for `max-old-space-size` is less than 2GB. To enable the application to use all available resources, the value of `max-old-space-size` should be set to a number equal to the memory limit for the whole application. For example, if the application memory is limited to 2GB, set the heap limit as follows, in the application's `package.json` file:

> ### Sample Code:  
> Set Application Router Memory Usage in `package.json` File
> 
> ```
> "scripts": {
>   "start": "node --max-old-space-size=2048 node_modules/@sap/approuter/approuter.js"
> }
> ```

If the application router is running in an environment with limited memory, set the heap limit to about 75% of available memory. For example, if the application router memory is limited to 256MB, add the following command to your `package.json`:

> ### Sample Code:  
> ```
> "scripts": {
>   "start": "node --max-old-space-size=192 node_modules/@sap/approuter/approuter.js"
> }
> ```

> ### Tip:  
> For detailed information about memory consumption in different scenarios, see the Sizing Guide for the Application Router located in `approuter/approuter.js/doc/sizingGuide.md`



<a name="loio96c7545f62504d55b669010d8fb9c41e__section_xj4_pcg_2z"/>

## CSRF Protection

The application router enables CSRF protection for any HTTP method that is not `GET` or `HEAD` and the route is not public. A path is considered public, if it does not require authentication. This is the case for routes with `authenticationType: none` or if authentication is disabled completely via the top level property `authenticationMethod: none`.

To obtain a CSRF token one must send a `GET` or `HEAD` request with a `x-csrf-token: fetch` header to the application router. The application router will return the created token in a `x-csrf-token: <token>` header, where `<token>`

If a CSRF protected route is requested with any of the above mentioned methods, will be the value of the CSRF token.`x-csrf-token: <token>` header should be present in the request with the previously obtained token. This request must use the same session as the fetch token request. If the `x-csrf-token` header is not present or is invalid, the application router will return status code “403 - Forbidden”.



<a name="loio96c7545f62504d55b669010d8fb9c41e__section_fwp_44r_s1b"/>

## Cloud Connectivity

The application router supports integration with the SAP Connectivity service. The connectivity service enables you to manage proxy access to the Cloud Connector, which you can use to create tunnels for connections to systems located in private networks, for example, on-premise. To use the connectivity feature, you must create an instance of the connectivity service and bind it to the `Approuter` application.

In addition, the relevant destination configurations in the *<destinations\>* environment variable must have the proxy type `"onPremise"`, for example, `"proxyType": "onPremise"`. You must also ensure that you obtain a valid XSUAA login token for the User Account and Authentication service.

**Related Information**  


[Application Router Configuration Syntax](application-router-configuration-syntax-5f77e58.md "The application description defined in the xs-app.json file contains the configuration information used by the application router.")

[Application Router Environment Variables](application-router-environment-variables-0aac697.md "A list of environment variables that can be used to configure the application router.")

[Configure the Multitarget Application Router](configure-the-multitarget-application-router-6ba8959.md "The application routes to the available microservices are described in the xs-app.json file.")

[Application-Router Resource Files](application-router-resource-files-8dccaad.md "The routing configuration for an application is defined in one or more so-called &quot;destinations&quot; that are defined in a destinations configuration.")

