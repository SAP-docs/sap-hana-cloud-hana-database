<!-- loiod5bf65e64c85400a8efe7fa824301d4b -->

# Configuring the HDI Deployer

Set up and use the Node.js-based HDI Deployer in Cloud Foundry.

The SAP HANA Deployment Infrastructure Deployer \(HDI Deployer\) is a Node.js application \(`@sap/hdi-deploy`\) that is included in a Multi-Target Application \(MTA\) and is used to deploy HDI design-time artifacts to the respective HDI containers. When an MTA is deployed, the HDI Deployer application is pushed first so that it can “prepare” the SAP HANA persistence; by the time defined services are started in the application run-time environment, the HDI container is ready for use.

In the HDI setup, each module of the MTA \(for example `db/`, `js`, or `java`\) is assigned its own technical database user for accessing the run-time schema of the HDI container.

The HDI Deployer is packaged into the `db/` module of the MTA. Consequently, in order to use a new HDI Deployer, you need to reference a new version of the HDI Deployer in the `db/` module's `package.json` file. The HDI Deployer supports HANA 1.0 SPS11, HANA 1.0 SPS12, and the current HANA 2.0 development codeline.

> ### Note:  
> The HDI Deployer assumes ownership of the `src/`, `cfg/`, and `lib/` folders in the bound target HDI container. It is not possible to bind more than one \(1\) instance of the HDI Deployer to the same HDI container as the target container. For example, you cannot bind the `db/` modules of two different MTAs to the same HDI container as the target container; this results in undefined behavior.

**Related Information**  


[Integrate the HDI Deployer into a Mutlitarget Application's Database Module](integrate-the-hdi-deployer-into-a-mutlitarget-application-s-database-modul-0194390.md "Install the HDI Deployer for use by a Multi-Target Application (MTA).")

[Consume SAP Node.js Packages](https://help.sap.com/viewer/b9902c314aef4afb8f7a29bf8c5b37b3/2022_2_QRC/en-US/ddcff14e28384810a352bb6512cd3448.html "A selection of SAP-specific and ready-to-use Node.js packages is available on the public NPM registry.") :arrow_upper_right:

[Managing SAP HDI Containers and Artifacts](managing-sap-hdi-containers-and-artifacts-23f1f40.md "In SAP HANA Deployment Infrastructure (HDI), database development artifacts are deployed to so-called containers.")

