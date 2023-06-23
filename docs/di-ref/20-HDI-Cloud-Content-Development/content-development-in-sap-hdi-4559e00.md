<!-- loio4559e002676d469980fa00f0b4fa5b38 -->

# Content Development in SAP HDI

Develop and deploy database content in the SAP HANA Deployment Infrastructure \(HDI\).

If you are planning to develop content for deployment to HDI, you need to read and understand the high-level information included in the following sections where you can also find links to more detailed information:

-   [Content Development with the SAP HDI API](content-development-in-sap-hdi-4559e00.md#loio4559e002676d469980fa00f0b4fa5b38__section_qvl_4fm_lgb)
-   [Container Configuration and Name-space Rules](content-development-in-sap-hdi-4559e00.md#loio4559e002676d469980fa00f0b4fa5b38__section_gcj_4km_lgb)

> ### Caution:  
> SAP HDI focuses strictly on deployment. HDI does not include version-control tools, nor does it provide any tools for life-cycle management.
> 
> In addition, HDI containers and their schemas are intended to be managed exclusively by HDI. Creating objects manually in an HDI container is highly likely to cause problems that can lead to loss of data.



<a name="loio4559e002676d469980fa00f0b4fa5b38__section_qvl_4fm_lgb"/>

## Content Development with the SAP HDI API

HDI container content developers can use the content development API to maintain design-time artifacts in the container's virtual file systems and to create database objects from them. HDI automatically takes care of the dependencies between artifacts and creates the database objects in the correct order. A variety of artifacts types are available from which database objects can be created by HDI. These artifacts are handled by specialized build plug-ins. For more information about developing content with the HDI APIs, see *SAP HDI Container Content Development with the HDI API* and *HDI Artifact Types and Build Plug-ins* in *Related Information* below.

The content development API of an HDI container consists of stored procedures and views located in the container's `#DI` schema \(for example, schema `C#DI` in container “`C`”\). Before this container API can be called by a content developer, the container administrator must first grant the required privileges to the developer requiring access. For more information about the roles and privileges used to control access to HDI containers, see *Maintaining SAP HDI Containers* in *Related Information*.



<a name="loio4559e002676d469980fa00f0b4fa5b38__section_gcj_4km_lgb"/>

## Container Configuration and Name-space Rules

In SAP HDI, to create run-time objects from the corresponding design-time files \(for example, a catalog object from a source definition of a stored procedure\), HDI uses so-called Build Plug-ins. It is not possible to create a catalog object from a design-time resource without having a plug-in which can read and transform this source definition. For this reason, each design-time resource type must be mapped to a build plug-in for each container that is created. This mapping is configured in an HDI container-configuration file: a file with no name but the mandatory file suffix `.hdiconfig`. For more information about the container-configuration file `.hdbconfig`, see *Related Information* below.

HDI allows developers to configure the naming of generated database objects; the rules for object names and \(if desired\) name spaces are configured in the `.hdbnamespace` file. The naming rules do not directly relate to the folder structure of the corresponding design-time files. Developers can put a name-space configuration file in a design-time folder, which specifies how the generated database objects are named in the folder where the configuration file is located and also in any sub-folders.

When configuring the name-space rules, you can choose to use the plain design-time object name or the object name with a common name-space prefix. You can also use the object name with a prefix that is a concatenation of a common name-space and the design-time folder path. Choosing a folder-independent naming rule gives you the freedom to change your design-time folder structure without causing incompatible changes to run-time names. For more information about the name-space configuration file `.hdbnamespace`, see *Related Information* below.

**Related Information**  


[Managing SAP HDI Containers and Artifacts](managing-sap-hdi-containers-and-artifacts-23f1f40.md "In SAP HANA Deployment Infrastructure (HDI), database development artifacts are deployed to so-called containers.")

[SAP HDI Container Content Development with the HDI API](sap-hdi-container-content-development-with-the-hdi-api-bea716c.md "SAP HDI includes an SQL API for the development of content in SAP HDI containers.")

[Maintaining SAP HDI Containers](../10-HDI-Cloud-Administration/15-HDI-Cloud-Admin-Maintain-Containers/maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

[The SAP HDI Container Configuration File](the-sap-hdi-container-configuration-file-6400400.md "Bind design-time file types to the corresponding build plug-in required in the SAP HANA Deployment Infrastructure (HDI).")

[The HDI Name-Space Configuration File](the-hdi-name-space-configuration-file-6188d22.md "The SAP HANA Deployment Infrastructure (HDI) uses a JSON resource to define naming rules for run-time objects.")

[SAP HANA Cloud, SAP HANA Database Developer Guide for Cloud Foundry Multitarget Applications \(SAP Business Application Studio\)](https://help.sap.com/docs/HANA_CLOUD_DATABASE/c2b99f19e9264c4d9ae9221b22f6f589/f8e431e3cdc14516b4ba8c9932afd1f4.html)

[SAP HANA Cloud, SAP HANA Database Developer Guide for Cloud Foundry Multitarget Applications \(SAP Web IDE Full-Stack\)](https://help.sap.com/docs/HANA_CLOUD_DATABASE/b9902c314aef4afb8f7a29bf8c5b37b3/1547c14105be409ebfc3a9e9634a7188.html)

