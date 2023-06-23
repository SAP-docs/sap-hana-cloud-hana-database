<!-- loiobea716c9ad68444ca63485e3f92d6589 -->

# SAP HDI Container Content Development with the HDI API

SAP HDI includes an SQL API for the development of content in SAP HDI containers.

HDI container content developers can use the content development API to maintain design-time artifacts in the container's virtual file systems and to create database objects from them. HDI automatically takes care of the dependencies between artifacts and creates the database objects in the correct order. A variety of artifacts types are available from which database objects can be created by HDI. These artifacts are handled by specialized build plug-ins. For more information about HDI build plug-ins, see *HDI Artifact Types and Build Plug-ins* in *Related Information* below.

The content development API of an HDI container includes stored procedures and views located in the container's `#DI` schema \(for example, schema `C#DI` in container “`C`”\). Before this API of a container can be called by a content developer, an administrator of the container has to grant the necessary privileges to the developer. If you are the administrator of the container, you can find more information in *Related Information* under *Maintaining SAP HDI Containers*. The APIs provided enable developers, amongst other things, to create objects and their content in the HDI container's work file system and deploy the objects to the deployed file system.



<a name="loiobea716c9ad68444ca63485e3f92d6589__section_o5k_3sy_wfb"/>

## The HDI Container's Work File System

After a container administrator has configured the build and plug-in libraries for an HDI container and granted developers the required access privileges for content-development, developers can start to `WRITE` files and their content to the container's “work” file system. The `DELETE` API enables you to remove files from the HDI container's work file system, and the `LIST`, `READ`, and `STATUS` APIs enable access to the work file-system's content. For more information about the APIs that provide access to an HDI container's "work" file system, see *The HDI Container API* in *Related Information*.



<a name="loiobea716c9ad68444ca63485e3f92d6589__section_kwx_ssy_wfb"/>

## The HDI Container's Deployed File System

To create database objects from the files in the HDI container's work file system, one of the `MAKE` operations is used, which copies the affected files to the HDI container's deployed file system. You can display information about the content of the deployed file-system's content with the `LIST_DEPLOYED` and `READ_DEPLOYED` APIs, too. For more information about the APIs that provide access to an HDI container's "deployed" file system, see *The HDI Container API* in *Related Information*.



<a name="loiobea716c9ad68444ca63485e3f92d6589__section_dqg_mty_wfb"/>

## Container Access for Content Development

The APIs provided for administrative operations in the context of content development enable you to grant \(or revoke\) the roles and privileges that provide access the HDI container or the container's schema, for example, `GRANT_CONTAINER_SCHEMA_PRIVILEGES` and `GRANT_CONTAINER_SCHEMA_ROLES` and the listing of the build and plug-in libraries configured for an HDI container \(`LIST_CONFIGURED_LIBRARIES`\). For more information about the APIs that enable the management of access privileges for an HDI container, see *The HDI Container API* in *Related Information*.

> ### Note:  
> The HDI also includes views that can be used to display information about the currently running `MAKE` operations, recent messages and objects, or the deployed roles.

**Related Information**  


[The HDI Container API](the-hdi-container-api-40ba784.md "Maintain HDI containers and container content using the HDI container API.")

[HDI Container Views](hdi-container-views-2b3814d.md "Display information about calls made with the HDI container API.")

[SAP HDI Artifact Types and Build Plug-ins Reference](../30-HDI-Cloud-Artifact-Types/sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

[Maintaining SAP HDI Containers](../10-HDI-Cloud-Administration/15-HDI-Cloud-Admin-Maintain-Containers/maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

