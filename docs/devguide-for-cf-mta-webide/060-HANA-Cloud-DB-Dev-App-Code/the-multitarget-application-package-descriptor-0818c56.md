<!-- loio0818c567204440e1861e3a664f75eec7 -->

# The Multitarget Application Package Descriptor

A file describing the prerequisites and dependencies that apply to a JavaScript multitarget application in Cloud Foundry on SAP Business Technology Platform.

The dependencies of a JavaScript application are described in the `package.json` file. The `package.json` file is mandatory for JavaScript applications and must be located in the JavaScript application’s source-file folder, for example, `/path/appname/js`.

Typically, the `package.json` file is created with the node.js command `npm init`, where you provide general information about the JavaScript application. Note that for legacy XS JavaScript applications, you must also provide the following additional information:

-   Dependency to XS JavaScript module \(the XS compatibility layer\)
-   Dependency to the application router \(see example below\)
-   Start command to specify node options

> ### Note:  
> For illustration purposes, the following example includes dependencies to a ficticious github account \(on “acme.com”\); you must adapt any URLs to suit the local development environment and dependencies. In addition, the <code>@sap/<i class="varname">&lt;pkg&gt;</i></code> modules available on the public NPM registry at `registry.npmjs.org`. For more details, see *NPM Registry* in *Related Information* below.

> ### Sample Code:  
> Application's Package Description \(`package.json`\)
> 
> ```
> {
>   "name": "<application_name>",
>   "description": "<application_description>",
>   "version": "<application_version>",
>   "repository": {
>     "url": "git@github.acme.com:xs-samples/nodejs-hello-world.git"
>   },
>   "dependencies": {
>     "@sap/xsjs": "^1.1.9"
>     "@sap/approuter": ">=1.0.1 <2.0.1"
>     "@sap/hdbext": "^1.0.2"
>     "@sap/xssec": "^1.0.5"
>   },
>   "engines": {
>     "node": ">=0.10.x <0.12"
>   },
>   "scripts": {
>     "start": "node --max-old-space-size=400 --expose-gc main.js"
>   }
> }
> 
> ```

A package description is required for both the `web/` and `db/` modules. In the `web/` module, the information in the `package.json` file is enable the startup of the application router; the contents of the `package.json` file located in the `db/` module are used to start the SAP HANA HDI deployment application.



## Connections to the SAP HANA Cloud Database

To establish a connection to the database, an application must first look up the connection properties from the bound services and create an “hdb” client. The easiest way to do this is to add a dependency to `@sap/hdbext` to the application's `package.json` file, as illustrated in the following example:

> ### Sample Code:  
> ```
> "dependencies": {
> "@sap/hdbext": "1.0.2"
>   },
> ```

Next, the application has to create a connection, as illustrated in the following example:

> ### Sample Code:  
> ```
> var xsConnection = require("@sap/hdbext");
> var hdbclient = xsConnection.createConnection(function(error) { ... });
> ```



### Connection Pools

The `@sap/hdbext` module includes a simple method for pooling connections. To use the connection-pool feature, you must first create the connection pool, as illustrated in the following example:

```
var pool = hdbext.getPool(hanaConfig, poolConfig);
```

Then you can acquire a connection client from the pool; the client is delivered in a callback, as illustrated in the following example:

```
pool.acquire(function(err, client) {}); 
```

If the connection client is no longer needed, it should be released back to the pool:

```
pool.release(client);
```



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

If a Node.js application needs to call external applications or services, it must do so by performing HTTP requests to the required services. The service can either be located in the same system or on an external system on the Internet. For connections to remote systems, it is recommended for Node.js applications to make use of the “`request`” module. For outbound connections, you need to consider the following:

-   Proxy connections

    If your Node.js applications runs behind an HTTP proxy, the details of the proxy connection must be provided to the `request` module. Request can discover this information either from environment variables set in the application's manifest file \(`manifest.yml` \) or directly from the options object of the HTTP request.

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

**Related Information**  


[Create the Multitarget Application Package Descriptor](create-the-multitarget-application-package-descriptor-0b0ed18.md "The package descriptor defines a JavaScript application's design-time and run-time dependencies in Cloud Foundry.")

[Multitarget Application Package Descriptor Configuration Syntax](multitarget-application-package-descriptor-configuration-syntax-a4a91b5.md "The package descriptor defines the prerequisites and dependencies that apply to packages in a JavaScript multitarget application deployed in the Cloud Foundry run time.")

[Maintaining Application Security in Cloud Foundry on SAP BTP](../100-HANA-Cloud-DB-Dev-Security/maintaining-application-security-in-cloud-foundry-on-sap-btp-35d910e.md "Set up the security components required in the context of multitarget applications on SAP BTP .")

[The NPM Registry](the-npm-registry-726e5d4.md "The public NPM registry includes SAP Node.js modules for use by application developers.")

