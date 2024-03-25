<!-- loio01943903839542e8b983a8f3591c1c07 -->

# Integrate the HDI Deployer into a Mutlitarget Application's Database Module

Install the HDI Deployer for use by a Multi-Target Application \(MTA\).



## Prerequisites

The following prerequisite apply for the installation and use of the SAP HANA HDI Deployer:

-   Node.js package manager \(`npm`\)

    Ensure that `npm` is configured appropriately, for example, with a working URL to the package registry




## Context

The HDI Deployer is an application that is included in a Multi-Target Application \(MTA\) and is used to deploy HDI design-time artifacts to the respective HDI containers. When an MTA is deployed, the HDI Deployer application is pushed first so that it can “prepare” the SAP HANA persistence; by the time the services defined in the MTA's deployment descriptor are started in Cloud Foundry, the HDI container is ready for use.



## Procedure

1.  Ensure that `npm` is configured appropriately.

    > ### Tip:  
    > For more information about how to include the public NPM Registry \(`https://registry.npmjs.org`\) as the upstream NPM registry, see *Related Information* below.

2.  Install the HDI Deployer for use by the multitarget application's database module \(`db/`\).

    You can install the HDI Deployer by including the Node.js application “`@sap/hdi-deploy`” in the `package.json` file that defines the dependencies inside your multitarget application's `db/` module, as illustrated in the following example:

    > ### Code Syntax:  
    > `db/package.json`
    > 
    > ```json
    > {
    >   "name": "deploy",
    >   "dependencies": {
    >     "@sap/hdi-deploy": "3.6.0"
    >   },
    >   "scripts": {
    >     "start": "node node_modules/@sap/hdi-deploy/"
    >   }
    > }
    > ```

    > ### Tip:  
    > For information about the package @sap/hdi-deploy, see *Related Information* below.


**Related Information**  


[Configuring the HDI Deployer](configuring-the-hdi-deployer-d5bf65e.md "Set up and use the Node.js-based HDI Deployer in Cloud Foundry.")

[Consume SAP Node.js Packages](https://help.sap.com/viewer/b9902c314aef4afb8f7a29bf8c5b37b3/2024_1_QRC/en-US/ddcff14e28384810a352bb6512cd3448.html "A selection of SAP-specific and ready-to-use Node.js packages is available on the public NPM registry.") :arrow_upper_right:

[The NPM Registry](https://help.sap.com/viewer/b9902c314aef4afb8f7a29bf8c5b37b3/2024_1_QRC/en-US/726e5d41462c4eb29eaa6cc83ff41e84.html "The public NPM registry includes SAP Node.js modules for use by application developers.") :arrow_upper_right:

[@sap/hdi-deploy README](https://www.npmjs.com/package/@sap/hdi-deployhttps://www.npmjs.com/package/@sap/hdi-deploy)

