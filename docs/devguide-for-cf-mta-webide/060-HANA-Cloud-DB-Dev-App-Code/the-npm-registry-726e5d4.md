<!-- loio726e5d41462c4eb29eaa6cc83ff41e84 -->

# The NPM Registry

The public NPM registry includes SAP Node.js modules for use by application developers.



Whether you are using command-line tools or a graphical integrated development environment \(IDE\) to build your Node.js application, you can configure the build process to use the packages that are available in registries which make Node Package Modules available for public consumption, for example, `"registry.npmjs.org"`. SAP maintains a selection of SAP-specific features and functions \(for example, `@sap/package`\), which are available on the public NPM registry and which you can configure your build tools to consider at build time, as described below:

-   [NPM Registry Configuration for Command-Line and Build Tools](the-npm-registry-726e5d4.md#loio726e5d41462c4eb29eaa6cc83ff41e84__section_k13_skg_vz)

-   [NPM Registry Configuration for SAP Web IDE](the-npm-registry-726e5d4.md#loio726e5d41462c4eb29eaa6cc83ff41e84__section_bmv_5kg_vz)




<a name="loio726e5d41462c4eb29eaa6cc83ff41e84__section_k13_skg_vz"/>

## NPM Registry Configuration for Command-Line and Build Tools

If you are using command-line tools to build your Node.js applications, you can configure the tools to use a particular NPM registry to resolve the dependencies between resources specified in the deployment descriptors. To specify the NPM registry, add the `"@sap:registry="` property to the `.npmrc` resource-configuration file, as illustrated in the following example:

> ### Sample Code:  
> NPM Registry Configuration in the `.npmrc` File
> 
> ```
> ...
> @sap:registry=https://registry.npmjs.org
> ...
> ```

You can also use the `npm` command to configure the target registry for the current session:

```
$ npm config set @sap:registry https://registry.npmjs.org
$ npm install @sap/<node_package>
```

> ### Note:  
> The public SAP NPM registry is now enabled by default for the resolution of Node.js module dependencies in the `@sap` scope during the staging of Node.js applications in the Cloud Foundry environment.

If you publish Node.js applications to the Cloud Foundry environment without dependencies, it is no longer necessary to specify the SAP NPM registry by means of an environment variable or in the NPM configuration file \(`.npmrc`\). If, however, you want to run or test a Node.js application locally, you still need to configure the SAP NPM registry as described above.



<a name="loio726e5d41462c4eb29eaa6cc83ff41e84__section_bmv_5kg_vz"/>

## NPM Registry Configuration for SAP Web IDE Build Tools

If you are using the build tools included in SAP Web IDE to build your Node.js applications, you can configure SAP Web IDE to use one or more specific NPM registries to resolve the dependencies between the resources specified in the development and deployment descriptors.

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
>       UPSTREAM_LINK: "https://registry.npmjs.org"
> ...
> ```

> ### Tip:  
> For more information about configuring the SAP Web IDE, see *Customizing the Environment* in *Related Information* below.

**Related Information**  


[Consume SAP Node.js Packages](consume-sap-node-js-packages-ddcff14.md "A selection of SAP-specific and ready-to-use Node.js packages is available on the public NPM registry.")

[Standard SAP Node.js Packages](standard-sap-node-js-packages-5451327.md "A collection of Node.js packages developed by SAP is provided to help you develop Node.js applications for Cloud Foundry and SAP HANA Cloud.")

[Customizing the Environment \(SAP Web IDE for SAP HANA Install Guide\)](https://help.sap.com/viewer/1a8e7ab05a2e4119b02b702f211422f5/2.0.02/en-US/5fd9473b7e994e2aa66092da5a10c75a.html)

