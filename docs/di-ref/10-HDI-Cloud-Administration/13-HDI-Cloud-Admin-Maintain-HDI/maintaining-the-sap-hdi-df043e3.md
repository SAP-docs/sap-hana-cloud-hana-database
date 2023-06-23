<!-- loiodf043e30b4f3441fb5a0eb0b57ec3d00 -->

# Maintaining the SAP HDI

Maintenance of the SAP HANA Deployment infrastructure \(HDI\) is the responsibility of the HDI administrator, who must set up and configure general HDI parameters.

Managing the SAP HDI typically involves the following administrator tasks:

-   Configure the HDI

-   List plug-in libraries available to a container

-   Create and drop container groups

-   Grant and revoke container-group administration privileges

-   Maintain container groups

-   Move containers between container groups




<a name="loiodf043e30b4f3441fb5a0eb0b57ec3d00__section_u5p_sn1_m1b"/>

## Exporting and Importing Containers

In special cases, a container and its dependencies can be exported from the database and imported into a different database for support purposes.

> ### Caution:  
> The API procedures `_SYS_DI.EXPORT_CONTAINER_FOR_SUPPORT` and `_SYS_DI.IMPORT_CONTAINER_FOR_SUPPORT` are available to the HDI administrator but intended for use by SAP support, exclusively. Bear in mind that the exported data might include private or confidential data from the container, and the container import could also compromise the integrity of the database.

**Related Information**  


[Configure SAP HDI Parameters](configure-sap-hdi-parameters-7c989fa.md "The SAP HANA Deployment Infrastructure (HDI) administrator can configure some general aspects of the HDI with parameters, for example, how long an HDI operation waits for a locking conflict to clear or the default behavior of HDI containers.")

[Enabling the SAP HDI Administrators](../12-HDI-Cloud-Admin-Enable-Admins/enabling-the-sap-hdi-administrators-c248d55.md "Create the users required to adminstrate and maintain the SAP HANA Deployment Infrastructure (HDI) services.")

[Maintaining SAP HDI Container Groups](../14-HDI-Cloud-Admin-Maintain-Container-Groups/maintaining-sap-hdi-container-groups-4e9d597.md "The administrator of an SAP HDI container group is responsible for managing the SAP HDI containers that are organized into one or more HDI container groups.")

[Maintaining SAP HDI Containers](../15-HDI-Cloud-Admin-Maintain-Containers/maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

