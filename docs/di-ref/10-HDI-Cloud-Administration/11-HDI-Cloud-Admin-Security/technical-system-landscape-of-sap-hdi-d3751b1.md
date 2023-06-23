<!-- loiod3751b1d135b454e8f0606b9f1e22b70 -->

# Technical System Landscape of SAP HDI

An overview of the architecture of SAP HDI.

HDI clients such as the client libraries for Java and JavaScript use the HDI SQL API to manage containers and their content.

The HDI API is based on SQL and database procedures. For example, the application programming interface \(API\) for system-wide, HDI-container management includes procedures for creating and dropping HDI containers. Each container has its own container API consisting of container-specific procedures for uploading \(`WRITE`\), listing \(`READ`\), and retrieving \(`LIST`\) design-time objects, for deploying uploaded design time objects \(`MAKE`\), and for granting \(or revoking\) access to \(or from the container’s schemas and API \(grant, revoke\).

It is possible to assign HDI containers to container groups where a corresponding group-level management API restricts the management operations \(for example, create/drop, configure, etc.\) to the set of containers included in the specific group.

 ![](images/SAP_HDI_Architecture_9dee975.png) 



<a name="loiod3751b1d135b454e8f0606b9f1e22b70__section_t4q_2vt_ngb"/>

## Users and Clients

Users and applications interact with SAP HDI by means of one of the available clients, which use the SAP HDI's SQL application-programming interface to manage HDI containers and the corresponding content.

-   HDI client

    HDI provides client libraries for Node.js \(`@sap/hdi`\) and Java \(`sap-java-hdi`\) which include a selection of methods that can be used to connect to the HDI and access HDI functionality.

-   The development environment

    The HDI's API is based on a library of SQL procedures, which can be used \(among other things\) to create and drop containers; upload design-time objects to the virtual file system of the HDI container; deploy uploaded objects \(make\) to the container run time; and grant \(or revoke\) the permissions required to access HDI containers.


**Related Information**  


[SAP HDI Security](sap-hdi-security-d9e5051.md "An overview of the tools used to configure and ensure security in the SAP HANA Deployment Infrastructure (HDI).")

