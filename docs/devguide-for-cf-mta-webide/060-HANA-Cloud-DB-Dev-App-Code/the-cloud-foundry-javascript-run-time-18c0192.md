<!-- loio18c01923b738416d8ec2eaa3eae2a4bf -->

# The Cloud Foundry JavaScript Run Time

Cloud Foundry on SAP Business Technology Platform provides a JavaScript run time environment to which you can deploy your Node.js and JavaScript applications.

Cloud Foundry enables you to build and deploy applications on Node.js. Although no assumptions are made about the frameworks you are using, it is recommended to connect to \(and use\) the SAP HANA Cloud's deployment infrastructure \(HDI\) container, and validate using JSON Web Tokens \(JWT\).

Authentication for Node.js applications relies on a special usage of the OAuth 2.0 protocol by the User Account and Authentication service \(UAA\). The UAA vouches for the authenticated user's identity using a JSON web token \(JWT\) as OAuth 2.0 token. This is a signed text-based token in JSON syntax. For more information, see the README.md file of the `@sap/xssec` module in the Container Security API, for example, for your Node.js application.



## Node.js Modules for Download

A collection of Node.js packages developed by SAP is provided for use in Cloud Foundry; the Node.js packages are available on the NPM public registry at `https://registry.npmjs.org`. Packages include, among other things, an application router, a job scheduler, logging tools, text mining and analysis tools, and so on. The following list shows a selection of the more commonly used packages available on the NPM Registry:

-   `@sap/approuter`
-   `@sap/hdbext`
-   `@sap/hana-client`
-   `@sap/hdi`
-   `@sap/hdi-deploy`
-   `@sap/jobs-client`
-   `@sap/logging`
-   `@sap/xsenv`
-   `@sap/xsjs`
-   `@sap/xssec`
-   `@sap/xss-secure`

> ### Tip:  
> For more information about configuring and using the NPM Registry, see *Related Links*.

To install an `npm` module use the following command:

```
npm install --save @sap/xsenv
```

To use a module, for example `@sap/xsenv`:

```
var xsenv = require('@sap/xsenv');
```



## SAP HANA Cloud Database Connections

To establish a connection to the SAP HANA Cloud database, a JavaScript application must first look up the connection properties from the bound services and create a database client object. For Node.js applications, the easiest way to do this is to add a dependency to `@sap/hdbext` to the application's `package.json` file, as illustrated in the following example:

> ### Note:  
> You might need to modify the version of `@sap/hdbext` to reflect the version required by your application.

> ### Sample Code:  
> ```
> "dependencies": {
> "@sap/hdbext": "^5.0.0"
>   },
> ```

Next, the application has to create a connection, as illustrated in the following example:

> ### Sample Code:  
> ```
> var hdbext = require('@sap/hdbext'); 
> var hanaConfig = { ... }; 
> hdbext.createConnection(hanaConfig, function(error, client) { 
>   if (error) { 
>   	return console.error(error); 
>   } 
> 
>   client.exec(...); 
> }); 
> ```



### Connection Pools

SAP HANA Cloud multitarget applications can use the connection pooling functionality provided by the `@sap/hana-client` package. Connection pooling is enabled by adding the property `pooling` with value `true` \(JavaScript boolean\) in the `hanaConfig` object.



## Security

For Node.js, the client security library is an `npm` module called `@sap/xssec`. If you want your application to use the security library `@sap/xssec`, you must add the dependency to `@sap/xssec` in the `dependencies` section of your application's package description file, `package.json`, as illustrated in the following example:

> ### Sample Code:  
> ```
> "dependencies": {
>     "@sap/xssec": "^1.0.5"
>   },
> 
> ```



## Outbound Connectivity

If a Node.js application needs to call external applications or services, it must do so by performing HTTP requests to the required services. The service can either be located in the same system or on an external system on the Internet. For connections to remote systems, Node.js applications can make use of the “`request`” module. For outbound connections, you need to consider the following:

-   Proxy connections

    If your Node.js applications runs behind an HTTP proxy, the details of the proxy connection must be provided to the `request` module. Request can discover this information either from environment variables set in the application's manifest file or directly from the options object of the HTTP request.

-   Authentication

    If the application needs to call a service that performs authentication by means of Security Assertion Markup Language \(SAML\) and JWT \(authentication\), and the calling service does so as well, then the SAML token can be taken from the incoming request and attached to the outgoing request.


> ### Sample Code:  
> ```
> var options = {
>     url: remoteURL,
>     headers: {
>         'authorization': req.headers.authorization
>     }
> };
> 
> ```

> ### Note:  
> For this so called “principal propagation” to work, both the calling and the called application must be bound to the same User Account and Authentication \(UAA\) service. Otherwise the SAML token attached to the request will not be recognized and the request cannot be authenticated.



<a name="loio18c01923b738416d8ec2eaa3eae2a4bf__section_bn1_15b_ygb"/>

## Optimizing Application Memory Usage

To define a limit for the memory used by your JavaScript application, set the *<OPTIMIZE\_MEMORY\>* environment variable to `true`. If the memory property is not specified in the `manifest.yml` file, the default memory limit is 1GB.

> ### Note:  
> The memory-limit feature works only for applications with Node.js version 6.12.x or higher. For versions of Node.js older than 6.12.x, you have to manually set the property `--max_old_space_size` in the `start` command of the Node.js application, as illustrated in the following example. The recommended value is 75% of the memory limit you want to add to your application.

> ### Sample Code:  
> ```
> node --max_old_space_size=96 server.js
> ```

**Related Information**  


[Writing the Multitarget Application Code](writing-the-multitarget-application-code-32e9590.md "Add business logic to your multitarget application to enable it to work with the database artifacts.")

[The Cloud Foundry Java Run Time](the-cloud-foundry-java-run-time-2b5a9a4.md "SAP Business Technology Platform provides a Cloud Foundry Java run time to which you can deploy your Java applications.")

[Standard SAP Node.js Packages](standard-sap-node-js-packages-5451327.md "A collection of Node.js packages developed by SAP is provided to help you develop Node.js applications for Cloud Foundry and SAP HANA Cloud.")

[The NPM Registry](the-npm-registry-726e5d4.md "The public NPM registry includes SAP Node.js modules for use by application developers.")

