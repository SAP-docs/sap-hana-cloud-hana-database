<!-- loioca1a943bb6524233b7766ae399f062fd -->

# Introducing SAP HANA Cloud

A short overview of SAP HANA Cloud



<a name="loioca1a943bb6524233b7766ae399f062fd__section_overview"/>

## Overview

SAP HANA Cloud provides a single place to access, store, and process all enterprise data in real time. It is a cloud-native platform that reduces the complexity of multi-cloud or hybrid system landscapes. SAP HANA Cloud provides all of the advanced SAP HANA technologies for multi-model data processing either in-memory or on disk. You can benefit from cloud qualities such as automatic software updates, elasticity, and low total cost of ownership by using SAP HANA Cloud either as a stand-alone solution or as an extension to your existing on-premise environment.

The SAP HANA Cloud allows you to consume the SAP HANA database from applications running on SAP Business Technology Platform \(BTP\), as well as from applications running on-premise or other Cloud services using the standard SAP HANA clients. The SAP HANA Cloud provides simplified data access to connect all your information without the need to have all data loaded into a single storage solution.

If you are familiar with multiple tenant databases in SAP HANA on-premise systems, note that every SAP HANA Cloud database instance is equivalent to a single tenant database. For multiple databases, create multiple SAP HANA Cloud database instances. Using SAP BTP cockpit or the Cloud Foundry command-line interface \(`cf` CLI\), you can create and manage SAP HANA Cloud instances in your space.

Developers can bind any applications deployed in the same space to database instances. SAP multitarget applications are bound to HDI containers; every application has a dedicated HDI container. The SAP HANA Deployment Infrastructure \(HDI\) provides a service that enables you to deploy database development artifacts to so-called containers. This service includes a family of consistent design-time artifacts for all key SAP HANA database features, which describe the target \(run-time\) state of SAP HANA database artifacts, for example: tables, views, or procedures. These artifacts are modeled, staged \(uploaded\), built, and deployed into SAP HANA. Using HDI is not a strict requirement, schemas and database artifacts can be created at run-time using SQL database definition language in the SQL console. For more information about HDI in SAP HANA Cloud, see *Related Information* below.

To administer an SAP HANA Cloud database, use the SAP HANA cockpit, which provides a range of tools for administration and monitoring. For more information, see *Related Information* below .

To query information about an SAP HANA Cloud database and view information about your database's catalog objects, use the SAP HANA Database Explorer. For more information, see *Related Information* below.

All access to SAP HANA Cloud instances is via secure connections on SQL ports.

> ### Tip:  
> It is also possible to open the Database Explorer from *SAP Business Application Studio*.

**Related Information**  


[SAP HANA Cloud, SAP HANA Database Deployment Infrastructure Reference](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2023_2_QRC/en-US/4077972509f5437c85d6a03e01509417.html "Set up and maintain the deployment infrastructure for the SAP HANA Cloud, SAP HANA database service.") :arrow_upper_right:

