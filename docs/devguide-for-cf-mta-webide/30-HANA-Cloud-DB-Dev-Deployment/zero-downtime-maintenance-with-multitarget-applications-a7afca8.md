<!-- loioa7afca80f35c444c8d2e4ab42f5ec06d -->

# Zero-Downtime Maintenance with Multitarget Applications

The deploy service supports application updates using zero-downtime maintenance \(ZDM\).



In SAP HANA Cloud, zero-downtime updates of multitarget applications is achieved by deploying database artifacts in separate schemas, for example a “data” schema and an “access” schema.

-   Data schema

    Contains all database objects that have persistence data, for example tables, sequences, and indexes.

-   Access schema

    Contains the interface to database objects such as projection views and synonyms as well as database logic such as calculation views, database procedures, and functions.


> ### Note:  
> Applications are indirectly bound to the access and data schemas. Only deployment and lifecycle management tools access the data schema directly.

The deploy-service supports the following operation modes:

-   Normal
-   ZDM

    Enables the update of applications using zero-downtime-maintenance. In this mode, the deploy service analyzes the application artifacts and deploys them into the `data` and `access` schemas by providing the corresponding roles in the `data` schema, granting any necessary permissions, and providing the corresponding interfaces to the `access` schema.


![](images/ZDM_84738e6.png)

Depending on where and how the HDI artifacts are modeled in the multitarget application's database `db/` module, the following methods are used to handle the ZDM deployment:

1.  Default handling

    The artifacts are modeled in the default folders \(`src/`, `cfg/`\) of the application's database \(`db/`\) module. In this case, the deploy service handles the artifacts using the default rules and deploys them to the relevant default schema according to artifact type.

    During zero-downtime maintenance, the default deployment has the following limitations:

    -   Some access schema objects \(for example, interfaces and logic\) are deployed in the `data` schema, which is unnecessary as this brings a performance reduction and violates the ZDM concept of schema separation.

        For example, CDS types should be separated: objects such as CDS entities should be used from the `data` schema and objects such as CDS views from the `access` schema. If these CDS types are defined in separate CDS files, all artifacts except the CDS view are deployed to both schemas.

        > ### Tip:  
        > It is not necessary to deploy `access` schema objects such as the CDS type used from the CDS view into the `data` schema.

    -   `hdbtable` artifacts are deployed into the `data` schema by default.

        In certain situations, it is acceptable to deploy `hdbtable` artifacts into the `access` schema, for example, if there are corresponding `hdbtabledata` artifacts containing data that is used to fill the table defined in the `hdbtable` artifacts and, in addition, the data includes language text that is incompatible between versions.

        The default handling of ZDM deployment does not permit you to deploy `hdbtable` artifacts into an `access` schema; `hdbtable` artifacts are deployed into the `data` schema by default.


2.  Separated handling using `data/` and `access/` folders.

    In this scenario the artifacts are modeled in the `data/` and `access/` folders within the `src/` and `cfg/` folders of the database module. The `data/` folder should contain the data-schema-related objects that have persistence data, for example, tables, sequences, or indexes. The `access/` folder should contain access-schema-related objects \(for example, interface-to-database objects such as projection views and synonyms\) and the database logic \(defined in calculation views, database procedures, and functions\).

    The deploy service deploys the artifacts from the `data/` folder to the `data` schema and generates the corresponding interface objects in the `access` schema. Artifacts from the `access/` folder are deployed only to the `access` schema. This type of \(separated\) handling resolves the limitations listed above for the following reasons:

    -   Limitation 1 \(objects in the `access` schema\)

        Separate handling resolves this limitation because the `access` schema objects such as the CDS type used from CDS view are modeled in the `access/` folder and are deployed only to the `access` schema.

    -   Limitation 2 \(`hdbtable` objects deployed by default to the `data` schema\)

        Separate handling resolves this limitation because the `hdbtable` artifacts that should be deployed to the `access` schema are modeled in the `access/` folder and, as a result, are deployed only to the `access` schema.


    Separated handling brings clarity to the database model as the location of database objects is more accurately defined. Separated handling also improves the separation of object types.

    > ### Note:  
    > 1.  Currently all CDS files modeled in the `data/` folder are deployed to both the `data` and `access` schemas.
    > 2.  Reusable database modules are supported.


To ensure that your applications support the ZDM update, follow the adoption guidelines described in *Database Artifacts and Changes Supported by ZDM* and model the HDI artifacts in `data/` and `access/` folders accordingly. ZDM is also supported with the default handling of HDI artifacts, but it has limitations when the data model is more complex. For more information about the database changes and database artifacts that are supported by ZDM in your multitarget application, see *Related Information*.



<a name="loioa7afca80f35c444c8d2e4ab42f5ec06d__section_c5x_ntp_fdb"/>

## Persistence in applications

ZDM deployment is possible for applications that use HDI containers for persistence. HDI containers are services that use the `hdi-shared` service plan.

> ### Note:  
> Applications should not use a hard-coded service name for the data source to the HDI service, as during ZDM deployment the applications are bound to a new access HDI service with generated name, which could be different from the hard-coded name in the application code.

1.  Java Applications

    Java applications can use dynamic data-source configuration in one of the following ways:

    1.  By using an SAP JAVA buildpack

        Java applications can use a dynamic data-source-configuration feature that allows bound services described in the `manifest.yml` to appear as data sources available for look up in the `JNDI` of the application.

    2.  By using the *Spring Cloud Spring Service Connector*

        For more details, see *Related Information*


2.  Node.js applications

    Should use `@sap/hana-client` for connection to the database.


**Related Information**  


[Deploy a Multitarget Application with Zero-Downtime Maintenance](deploy-a-multitarget-application-with-zero-downtime-maintenance-f33557b.md "Update an application that has database changes without any downtime.")

[HDI Artifacts and Database Changes Supported by ZDM](hdi-artifacts-and-database-changes-supported-by-zdm-58ff82e.md "Zero-downtime maintenance (ZDM) supports the HDI artifacts and database changes listed in this topic.")

[Spring Cloud Spring Service Connector](http://cloud.spring.io/spring-cloud-connectors/spring-cloud-spring-service-connector.html)

