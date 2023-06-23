<!-- loiob36b4b60c9e44291ae02e520135fd898 -->

# SAP HDI Administration

An overview of the scope of the tasks required to maintain the SAP HANA Deployment Infrastructure \(HDI\).

HDI administrators are responsible for enabling and maintaining the HDI. Maintaining the HDI, its HDI containers, and container groups, involves the following high-level tasks:

-   Enabling the HDI

    A database administrator with `DBADMIN` privileges creates the necessary administrator users, and assigns the new users the access privileges required to administrate the HDI.

    > ### Note:  
    > In SAP HANA Cloud instances, HDI is enabled by default.

-   Maintaining the HDI

    An HDI administrator configures HDI, creates HDI container groups, and grants and revokes the access privileges required by the HDI container-group administrators.

-   Maintaining HDI containers groups

    HDI container-group administrators create and drop HDI containers, grant and revoke access privileges for containers and container groups, and import and export containers \(for support purposes\).

-   Maintaining HDI containers

    HDI container administrators grant and revoke container-based access privileges, configure libraries and parameters, and grant and revoke access to an HDI container's schemas.


**Related Information**  


[SAP HDI Administration in Context](sap-hdi-administration-in-context-b4b6a89.md "An overview of the SAP HANA Deployment Infrastructure (HDI) administration process including the administrator users who set up and maintain HDI and its components.")

[SAP HDI Administrator Roles](sap-hdi-administrator-roles-7fea650.md "The administration of SAP HANA Deployment Infrastructure (HDI) involves a number of tasks that must be performed by different administrator roles.")

[Enabling the SAP HDI Administrators](12-HDI-Cloud-Admin-Enable-Admins/enabling-the-sap-hdi-administrators-c248d55.md "Create the users required to adminstrate and maintain the SAP HANA Deployment Infrastructure (HDI) services.")

