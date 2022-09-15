<!-- loioddcff14e28384810a352bb6512cd3448 -->

# Consume SAP Node.js Packages

A selection of SAP-specific and ready-to-use Node.js packages is available on the public NPM registry.



## Context

A Node.js application often depends on packages that are present in the public `npm` registry or on specific SAP modules. A selection of SAP packages for Node.js is available for use in your Node.js applications. If your Node.js application depends on any of the SAP NPM packages, you need to configure a source to resolve the dependencies.

All the standard SAP NPM packages can be found in the public NPM registry at [https://registry.npmjs.org](https://registry.npmjs.org).

> ### Tip:  
> For information about how to configure your Node.js application to use the NPM registry at `https://registry.npmjs.org` to resolve package requirements and dependencies, see *The NPM Registry* in *Related Information* below.

The following instructions explain how to configure the use of the NPM Registry to resolve NPM package dependencies when building and deploying Node.js applications:



## Procedure

1.  Configure command-line tools to use the NPM Registry to resolve package dependencies.

    If you are using command-line tools to build your Node.js applications, you can configure the tools to use a particular NPM registry to resolve the dependencies between resources specified in the deployment descriptors. To specify the NPM registry, add the `"@sap:registry="` property to the `.npmrc` resource-configuration file, as illustrated in the following example:

    > ### Sample Code:  
    > NPM Registry Configuration in the `.npmrc` File
    > 
    > ```
    > ...
    > @sap:registry=https://registry.npmjs.org
    > ...
    > ```

    You can also use the `npm` command to configure the target registry for the current console session:

    ```
    $ npm config set @sap:registry https://registry.npmjs.org
    $ npm install @sap/<node_package>
    ```

    > ### Note:  
    > This is configured by default during application staging, but for local development you still have to set the registry manually.

2.  Configure the SAP Web IDE to use the NPM Registry to resolve package dependencies.

    To specify a specific NPM registry that will be used for the resolution of dependency requirements when developing and building applications with SAP Web IDE, add the `"UPSTREAM_LINK"` and \(or\) `"SAPUPSTREAM_LINK"` properties to the `di-local-npm-registry` module in the MTA **extension** descriptor \(for example, `sapwebide.mtaext`\) that is used when deploying SAP Web IDE, as illustrated in the following example:

    > ### Note:  
    > If a suitable MTA extension descriptor does not already exist for the deployment of SAP Web IDE, you must create one and add the suggested configuration details for the NPM registries.

    > ### Sample Code:  
    > MTA Extension Descriptor: NPM Registry Configuration for SAP Web IDE Deployment
    > 
    > ```
    > ...
    > modules:
    >   - name: di-local-npm-registry
    >     properties:
    >       UPSTREAM_LINK: "http://registry.npmjs.org"
    > ...
    > ```


**Related Information**  


[Standard SAP Node.js Packages](standard-sap-node-js-packages-5451327.md "A collection of Node.js packages developed by SAP is provided to help you develop Node.js applications for Cloud Foundry and SAP HANA Cloud.")

[The NPM Registry](the-npm-registry-726e5d4.md "The public NPM registry includes SAP Node.js modules for use by application developers.")

[The Cloud Foundry JavaScript Run Time](the-cloud-foundry-javascript-run-time-18c0192.md "Cloud Foundry on SAP Business Technology Platform provides a JavaScript run time environment to which you can deploy your Node.js and JavaScript applications.")

[SAP Software Download Center \(Logon required\)](http://help.sap.com/disclaimer?site=https://launchpad.support.sap.com/#/softwarecenter)

