<!-- loio1b567b05e53c4cb9b130026cb2e7302d -->

# The SAP HDI Deployer

SAP HDI provides dedicated tools to enable the deployment of design-time database artifacts to the SAP HANA database.

For Cloud Foundry environments, the SAP HANA Deployment Infrastructure \(HDI\) includes a so-called "Deployer", which is a Node application that is included in a Multi-Target Application \(MTA\) for the purpose of deploying an application's HDI database-related **design-time** artifacts to the application's corresponding HDI containers. When an MTA is deployed to the target run-time platform, the HDI Deployer application `@sap/hdi-deploy` is deployed first so that it can “prepare” the SAP HANA persistence; by the time the services defined in the MTA's deployment descriptor are started in the application run-time environment, the HDI container is ready for use.

You can install the HDI Deployer by including the Node.js application “`@sap/hdi-deploy`” in the `package.json` file that defines the dependencies inside your multitarget application's `db/` module, as illustrated in the following example:

> ### Code Syntax:  
> `myApp/db/package.json`
> 
> ```json
> {
>   "name": "deploy",
>   "dependencies": {
>     "@sap/hdi-deploy": "3.9.1"
>   },
>   "scripts": {
>     "start": "node node_modules/@sap/hdi-deploy/"
>   }
> }
> ```

> ### Note:  
> Java applications also require the HDI Deployer `@sap/hdi-deploy` for the deployment to HDI of database-related design-time artifacts. However, after deployment Java applications typically connect to the run-time schema of the application's corresponding HDI container using JDBC. Access to the HDI run-time containers is also possible with the SAP SQL APIs for SAP HANA DI \(HDI\).

In addition to the stand-alone deployer application, HDI also provides an API that enables applications to create database objects at run time by generating design-time artifacts within the application and deploying them into their container with the HDI. In this way, it is possible to extend the persistence in run-time authoring scenarios, for example, field extensibility or dynamic rule generation.



<a name="loio1b567b05e53c4cb9b130026cb2e7302d__section_btj_g2v_xfb"/>

## Dynamic Deployment to HDI

The Node.js module `@sap/hdi-dynamic-deploy` provides a Node.js-based HTTP server that can be used to deploy database content to dynamically created HDI containers, for example, containers created by means of the Instance Manager. The HDI Dynamic Deployer is intended for use in both on-premise scenarios and in the Cloud Foundry \(CF\) run-time environment on SAP Business Technology Platform.

> ### Note:  
> `@sap/hdi-dynamic-deploy` is based on `@sap/hdi-deploy` which should be used if a static deployment at deployment time is sufficient.

Typically, `@sap/hdi-dynamic-deploy` is installed by including a dependency in the `package.json` file of your multitarget application's database module, as illustrated in the following example:

> ### Sample Code:  
> `myApp/db/package.json`
> 
> ```
> {
>   "name": "deploy",
>   "dependencies": { 
>      "@sap/hdi-dynamic-deploy": "1.5.0" 
>   }, 
>   "scripts": { 
>      "start": "node node_modules/@sap/hdi-dynamic-deploy/"
>   }
> } 
> ```

For more detailed information about using the `@sap/hdi-dynamic-deploy`, see the `README.md` file included in the application's corresponding NPM package.



<a name="loio1b567b05e53c4cb9b130026cb2e7302d__section_rkv_fz5_xfb"/>

## Run-time Access to HDI Containers

If multitarget applications need access to their HDI run-time containers outside the scope of the HDI deployer, they can use the SAP SQL APIs for SAP HANA DI, which include an API specifically intended for content development in HDI containers.

> ### Note:  
> When working with the SAP SQL API for HDI, the HDI Deployer “`@sap/hdi-deploy`” described above is **not** required.

For example, for Node.js applications that need to create database objects at run time, the Node.js module `@sap/hdi` provides an HDI client library that includes a selection of asynchronous methods which enable access to SAP HANA deployment infrastructure functionality, for example: `connect()` and `disconnect()`, `createContainer()` and `dropContainer()`, and `configureLibraries()`.

Similarly, the `sap-java-hdi` client library enables access to the SAP HANA Deployment Infrastructure \(HDI\) for Java applications that need to create database objects at run time. Version 2.0 of the SAP HANA DI \(HDI\) client library for Java applications wraps the HDI SQL APIs in Java classes and methods which enable access to the APIs that are provided for managing HDI, its containers, and any container groups. Assuming the `hdiUser` has the privileges required to access `_SYS_DI`, the `sap-java-hdi` client library can be used to connect to the SAP HANA database, configure HDI, create and drop HDI containers, configure container build plug-in libraries, and so on.

> ### Note:  
> For more information about the standard and additional Java and Node.js libraries that you can use in your multitarget applications, see *Related Information* below.

**Related Information**  


[Standard SAP Node.js Packages (Developer Guide)](https://help.sap.com/viewer/b9902c314aef4afb8f7a29bf8c5b37b3/2024_1_QRC/en-US/54513272339246049bf438a03a8095e4.html "A collection of Node.js packages developed by SAP is provided to help you develop Node.js applications for Cloud Foundry and SAP HANA Cloud.") :arrow_upper_right:

[Standard SAP Java Packages (Developer Guide)](https://help.sap.com/viewer/b9902c314aef4afb8f7a29bf8c5b37b3/2024_1_QRC/en-US/6511bc054b0e48369a625a8019fefd53.html "A collection of Java client libraries developed by SAP is provided to help you develop Java applications for Cloud Foundry.") :arrow_upper_right:

