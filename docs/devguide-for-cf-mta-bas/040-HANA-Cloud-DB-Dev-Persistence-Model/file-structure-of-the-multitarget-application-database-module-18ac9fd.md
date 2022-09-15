<!-- loio18ac9fd93d08418ab8bf53582f45d40a -->

# File Structure of the Multitarget Application Database Module

The structure and hierarchy required in the database module of a multitarget application.

The HDI Deployer expects the following file system structure for your the HDI content in your `db/` module:

-   `src/`

    A folder containing the HDI source artifacts required by the application

-   `cfg/`

    An optional folder containing HDI configuration artifacts

-   `package.json`

    The configuration file used by the Node.js package manager \(`npm`\) to bootstrap and start the multitarget application


> ### Note:  
> All other files in the root directory of the database module \(`db/`\) are ignored by the HDI Deployer \(`@sap/hdi-deploy`\).

**Related Information**  


[Integrate the HDI Deployer into a Mutlitarget Application's Database Module](integrate-the-hdi-deployer-into-a-mutlitarget-application-s-database-modu-0194390.md "Install the HDI Deployer for use by a Multi-Target Application (MTA).")

[Configuring the HDI Deployer](configuring-the-hdi-deployer-d5bf65e.md "Set up and use the Node.js-based HDI Deployer in Cloud Foundry.")

[Managing SAP HDI Containers and Artifacts](managing-sap-hdi-containers-and-artifacts-23f1f40.md "In SAP HANA Deployment Infrastructure (HDI), database development artifacts are deployed to so-called containers.")

