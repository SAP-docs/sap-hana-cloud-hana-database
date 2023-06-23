<!-- loio4077972509f5437c85d6a03e01509417 -->

# SAP HANA Cloud, SAP HANA Database Deployment Infrastructure Reference

Set up and maintain the deployment infrastructure for the SAP HANA Cloud, SAP HANA database service.

The *SAP HANA Cloud, SAP HANA Database Deployment Infrastructure Reference* describes the tasks required to set up, maintain, grant access to, and use the SAP HANA Deployment Infrastructure \(HDI\) for SAP HANA Cloud instances of the SAP HANA database. It also describes the roles required to provide access to the HDI at the various levels and how the roles fit together to provide a secure deployment infrastructure. The information in the guide is organized as follows:

-   The SAP HANA Cloud, SAP HANA database deployment infrastructure

    This section provides an introduction to the SAP HANA Cloud, SAP HANA database deployment infrastructure, which is a service that enables you to deploy database development artifacts to so-called containers. These artifacts are modeled, staged \(uploaded\), built, and deployed into SAP HANA.

-   SAP HDI administration

    This section describes the roles, personas, and most common tasks involved in the administration of SAP HDI. There is also important information about the security considerations to bear in mind when setting up and running SAP HDI. It is important to note that differences may apply to the various roles, persona, and procedures, depending on the underlying version of the SAP HANA database.

-   SAP HDI content development

    This section describes how to use the HDI container SQL API not only to configure and control access to an HDI container but also to develop content in the HDI container. Developers creating content for HDI containers can use the content-development HDI SQL API to maintain design-time artifacts in the container's virtual file systems and, on build or deployment, create database objects from them.

-   HDI artifact types and build plug-ins

    This section includes a list of the database artifact types supported by the SAP HANA Cloud, SAP HANA database deployment infrastructure, for example, tables, types, views. It also provides examples of the syntax required to use the artifacts as well as the plug-in configuration required to activate the corresponding catalog objects.


**Related Information**  


[SAP HANA Deployment Infrastructure in the Cloud](sap-hana-deployment-infrastructure-in-the-cloud-3ef0ee9.md "Understand the benefits of using the SAP HANA Deployment Infrastructure (HDI).")

[SAP HDI Administration](10-HDI-Cloud-Administration/sap-hdi-administration-b36b4b6.md "An overview of the scope of the tasks required to maintain the SAP HANA Deployment Infrastructure (HDI).")

[Content Development in SAP HDI](20-HDI-Cloud-Content-Development/content-development-in-sap-hdi-4559e00.md "Develop and deploy database content in the SAP HANA Deployment Infrastructure (HDI).")

[SAP HDI Artifact Types and Build Plug-ins Reference](30-HDI-Cloud-Artifact-Types/sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

