<!-- loio21a9831a3dc34ac79aad8df15aa10d5d -->

# Set up Authentication for an SAP Multitarget Application

Define the authentication model for your multitarget application.



<a name="loio21a9831a3dc34ac79aad8df15aa10d5d__prereq_t4y_pc2_jbb"/>

## Prerequisites

-   Ensure that Node.js and its package manager \(NPM\) is installed.

    -   For independent installations of Node.js or NPM:

        Open a command-line shell and run the following commands:

        `node --version`

        `npm --version`





## Context

In multitarget applications, the Node.js application router \(`approuter`\) is used to connect your service to the centrally provided User Account and Authentication \(UAA\) service. This means that you need to deploy an `approuter` as part of your Multi-Target Application \(MTA\) and configure the `approuter` to manage the user authentication process.



## Procedure

1.  Set up the application router as part of your Multi-Target Application.

    The `approuter` is a Node.js package which you can download from the publicly available NPM registry, for example by configuring the registry in your NPM resource-configuration file \(`.npmrc`\) as illustrated in the following example:

    > ### Sample Code:  
    > Sample NPM Registry Configuration \(`.npmrc`\)
    > 
    > ```
    > @sap:registry=https://registry.npmjs.org
    > ```

    Add a dependency to the `approuter` package in your application's `package.json` file.

    > ### Sample Code:  
    > Typical `approuter` declaration in the `package.json`
    > 
    > ```
    > { 
    >   "name": "approuter", 
    >   "dependencies": { 
    >      "@sap/approuter": "2.10.0" 
    >   },
    >   "scripts": { 
    >      "start": "node node_modules/@sap/approuter/approuter.js"
    >   },
    >   "engines": {
    >      "node": "6.11.1"
    >   }
    > }
    > ```

2.  Update the application's `manifest.yml` file.

    Since the `approuter` is a Node.js application, it must be added to the multitarget application's build and deployment manifest in the same way as any other application. This list and configuration is specified in the `manifest.yml` file, as illustrated in the following example:

    The `manifest.yml` file is formatted according to YAML rules, which requires strict and consistent adherence to indents. In the following example, the *<tenantID\>* is only required if the application is deployed in a multi-tenant scenario.

    > ### Sample Code:  
    > ```
    > applications:
    > - name: approuter 
    >   host: approuter-<tenantID> 
    >   path: <PATH>/approuter 
    >   buildpack: nodejs_buildpack 
    >   memory: 128M 
    >   env:
    >     XSAPPNAME: myApp-<tenantID> 
    >     TENANT_HOST_PATTERN: "^(.*)-approuter-<tenantID>.acme.com" 
    >     destinations: > 
    >       [ 
    >         {
    >          "name":"ads-destination",
    >          "url":"https://MyApp-ads-<tenantID>.acme.com", 
    >          "forwardAuthToken": true
    >         }
    >       ] 
    >   services: 
    >     - applogs-myApp
    >     - uaa-myApp
    > ```

    > ### Note:  
    > Since the `manifest.yml` contains multiple applications, it is necessary to specify the name of the `"host"` where the application is running. With multiple hosts, it is not possible to use other means to specify the host name, for example, during application deployment using the command <code>xs push -n <i class="varname">&lt;HOST&gt;</i></code>.

3.  Configure the application router.

    You must define `"routes"` for an application; the specified path is used to direct incoming requests to the correct destination, as illustrated in the following example:

    > ### Sample Code:  
    > Route Configuration in `xs-app.json`
    > 
    > ```
    > {
    >   "welcomeFile": "index.html",
    >   "routes": [{ 
    >     "source": "^/myApp", 
    >     "target": "/", 
    >     "destination": "myApp-destination"
    >   }]
    > }
    > ```

4.  Deploy the application router and the corresponding application to the desired target.

    Before deploying the application, it is necessary to ensure that a instance of the UAA service is available for use by the deployed application.

    1.  Create the UAA service instance for your application.

        ```
        cf create-service xsuaa application uaa-myApp -c '{"xsappname":"myApp"}' 
        ```

    2.  Deploy your application.

        ```
        cf push 
        ```

        > ### Note:  
        > The host names for the deployment targets are specified in the application manifest \(`manifest.yml`\).

    3.  Check the information available for the UAA service connection information in the *<VCAP\_SERVICES\>* environment variable.

        The UAA service broker generates the service-connection information when the `approuter` is bound to the corresponding UAA service instance. The JSON array following the string `"XSUAA":` contains the client credentials for the UAA service instance, which are used to establish a trusted relationship between the `approuter` and the UAA service. The client credentials string also contains the URL of the UAA service, which the `approuter` uses to redirect unauthenticated calls to the UAA service.

        ```
        cf env approuter
        ```

        > ### Note:  
        > Locate the property `xsappname`.

    4.  List the routes that are already mapped to the application.

        ```
        cf routes
        ```

        If the `approuter` is to be used for other tenants, you must specify a route for each additional tenant, for example, to `myAppTrial`.


5.  Access the application using the application router.

    1.  List the URL for the `approuter`.

        ```
        cf apps
        ```

    2.  Paste the URL for the `approuter` into a Web browser.

        `https://myAppTrial-approuter.acme.com`

        This should redirect you to XSUAA logon screen, where you can log on using the credentials required \(for example, e-mail address and password\). Both the authentication **method** \(`"route"`, or `"none"`\) and the authentication **type** \(`"xsuaa"`, `"basic"`, or `"none"`\) can be specified in the application router configuration \(`xs-app.json`\).

        > ### Tip:  
        > The application router can be configured to implement Cross-Site Request Forgery \(CSRF\) protection. It is also possible to configure the `approuter` to initiate an automatic central log out if a user session is inactive for a specified period of time. The amount of time to wait is defined in the `SESSION_TIMEOUT` environment variable. To prevent unexpected behavior, you must ensure that the timeout configuration for the application router and the XSUAA service are identical for **all** routes with the authentication type <code>“xsuaa”</code>.



**Related Information**  


[The NPM Registry](../060-HANA-Cloud-DB-Dev-App-Code/the-npm-registry-726e5d4.md "The public NPM registry includes SAP Node.js modules for use by application developers.")

[Application Router Configuration Syntax](../090-HANA-Cloud-DB-Dev-MTA-Routes/application-router-configuration-syntax-5f77e58.md "The application description defined in the xs-app.json file contains the configuration information used by the application router.")

[Set up Authentication for your JavaScript Multitarget Application](../060-HANA-Cloud-DB-Dev-App-Code/set-up-authentication-for-your-javascript-multitarget-application-1c16bb3.md "Instructions to help you set up user authentication for your JavaScript multitarget application in Cloud Foundry.")

[Configure Authentication and Authorization](../060-HANA-Cloud-DB-Dev-App-Code/configure-authentication-and-authorization-cc45f18.md "You configure authentication and authorization by using the integrated container authentication provided with the Java build pack or the Spring security library.")

[Set up Generic Authorization for a Multitarget Application](set-up-generic-authorization-for-a-multitarget-application-c8c578e.md "Define an authorization model for your multitarget application and configure generic authorization for any application end point (route path).")

