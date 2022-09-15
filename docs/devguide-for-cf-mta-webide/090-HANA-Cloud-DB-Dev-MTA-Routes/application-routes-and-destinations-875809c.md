<!-- loio875809c7817c4633bcb5369f15f6864b -->

# Application Routes and Destinations

The application router is the single point of entry for an application.

The application router is used to serve static content, propagate user information, and act as a proxy to forward requests to other micro services. The routing configuration for an application is defined in one or more destinations. The application router configuration is responsible for the following tasks:

-   Act as the main user-entry point to an application service
-   Serve static content
-   Serve routes and destinations
-   Rewrite URLs
-   Forward requests to other services
-   Propagate user information
-   Handle authentication
-   Manage HTML5 application/browser sessions

> ### Note:  
> The application router does not manage server caching. The server cache must be set \(with e-tags\) in the server itself. The cache should contain not only static content but container resources, too, for example, relating to OData metadata.

In Cloud-based scenarios, a request is routed by means of domain names and a central router component. This requires a DNS wild card entry so that all requests are redirected to the "Cloud Router" which does dispatching and load balancing.



## Destinations

A destination defines the back-end connectivity. In its simplest form, a destination is a URL to which requests are forwarded.

Destinations are defined in an environment variable for the `approuter` application. The destinations are typically specified in the application manifest file \(`manifest.yml`\). The router information is added to the `env: destinations` section of the `manifest.yml` file, as illustrated in the following example:

> ### Sample Code:  
> Destinations Defined in the Application Manifest \(`manifest.yml`\)
> 
> ```
> ---
> applications:
> - name: node-hello-world
>   port: <approuter-port>  #the port used for the approuter
>   memory: 100M
>   path: web
>   env:
>     destinations: >
>       [
>         {
>           "name":"backend",
>           "url":"http://<hostname>:<node-port>",
>           "forwardAuthToken": true
>         }
>       ]
>   services:
>     - node-uaa
> 
> ```

> ### Note:  
> The <code>“name”</code> and <code>“url”</code> properties are mandatory.

The value of the destination “`name`” property \(<code>“name”:“backend”</code> in the example below\) must match the value of the `destinations` property configured for a route in the corresponding application-router configuration file \(`xs-app.json`\). It is also possible to define a logout path and method for the `destinations` property in the `xs-app.json` file. For more information, see the section describing the application-router configuration syntax in *Related Information*.

**Related Information**  


[Configure the Multitarget Application Router](configure-the-multitarget-application-router-6ba8959.md "The application routes to the available microservices are described in the xs-app.json file.")

[Application-Router Resource Files](application-router-resource-files-8dccaad.md "The routing configuration for an application is defined in one or more so-called &quot;destinations&quot; that are defined in a destinations configuration.")

[Application Router Configuration Syntax](application-router-configuration-syntax-5f77e58.md "The application description defined in the xs-app.json file contains the configuration information used by the application router.")

