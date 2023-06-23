<!-- loio4e9d59759b294124baa97c5b6d675072 -->

# Maintaining SAP HDI Container Groups

The administrator of an SAP HDI container group is responsible for managing the SAP HDI containers that are organized into one or more HDI container groups.

In SAP HANA Deployment Infrastructure \(HDI\), managing an HDI container group typically involves the following administrator tasks:

-   Grant and revoke container-group administrator privileges

-   Create and drop containers

-   Grant and revoke container administrator privileges

-   Grant and revoke container access


> ### Tip:  
> The APIs of a container group named “G” are in the schema `_SYS_DI#G`.



<a name="loio4e9d59759b294124baa97c5b6d675072__section_hzs_hfc_n1b"/>

## HDI Container Administration

The HDI container group administrator can perform the same administrative tasks as an HDI container administrator. For details about the functionality available to the HDI container administrator, see the section about HDI container administration in *Related Information* below. To perform container-related administration tasks, the container-group administrator calls the appropriate HDI container administration SQL procedures, not of the target container, but of the container **group schema** \(for example, `_SYS_DI#G`\) of the HDI container group administrator. The name of the target container is specified by means of an additional first parameter, as illustrated in the sample below.

> ### Sample Code:  
> ```sql
> CREATE LOCAL TEMPORARY COLUMN TABLE #PRIVILEGES LIKE _SYS_DI.TT_SCHEMA_PRIVILEGES; 
> INSERT INTO #PRIVILEGES ( PRIVILEGE_NAME, PRINCIPAL_SCHEMA_NAME, PRINCIPAL_NAME ) VALUES ( 'SELECT', '', 'U' ); 
> CALL _SYS_DI#G.GRANT_CONTAINER_SCHEMA_PRIVILEGES( 'C', #PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?); 
> DROP TABLE #PRIVILEGES; 
> ```

The example above shows how to grant a user “U” the privileges to access the run-time objects in the container “C”. The HDI container group administrator calls the SQL procedure `GRANT_CONTAINER_SCHEMA_PRIVILEGES` in the `_SYS_DI` schema, passing the container’s name “C” as the additional first parameter:

> ### Note:  
> Container-administration tasks should normally be performed by the container’s assigned administrator. The HDI container **group** administrator should only be used to perform every-day container administration tasks in exceptional circumstances. The only exception to this rule is the creation and dropping of containers, which can only be performed by the container **group** administrator.



<a name="loio4e9d59759b294124baa97c5b6d675072__section_u5p_sn1_m1b"/>

## Exporting and Importing Containers

In special cases, a container and its dependencies can be exported from the database and imported into a different database, for, example, when a container needs to be copied from one container to another. For more information about how to export and import containers for copy purposes, see *Related Information* below.

It is also possible to export and import a container for support purposes. However, it is not recommended and is not without risk, as described in the following caution note.

> ### Caution:  
> The API procedures `_SYS_DI#G.EXPORT_CONTAINER_FOR_SUPPORT` and `_SYS_DI#G.IMPORT_CONTAINER_FOR_SUPPORT` are available to the HDI container-group administrator but intended for use by SAP support, exclusively. The exported data might include private or confidential data from the container, and the container import could also compromise the integrity of the database.

**Related Information**  


[Maintaining SAP HDI Containers](../15-HDI-Cloud-Admin-Maintain-Containers/maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

[Maintaining the SAP HDI](../13-HDI-Cloud-Admin-Maintain-HDI/maintaining-the-sap-hdi-df043e3.md "Maintenance of the SAP HANA Deployment infrastructure (HDI) is the responsibility of the HDI administrator, who must set up and configure general HDI parameters.")

[SAP HANA Deployment Infrastructure in the Cloud](../../sap-hana-deployment-infrastructure-in-the-cloud-3ef0ee9.md "Understand the benefits of using the SAP HANA Deployment Infrastructure (HDI).")

[Export an SAP HDI Container for Copy Purposes](export-an-sap-hdi-container-for-copy-pur-36a5547.md "An HDI container can be exported to a table, which can then be used to import the container into a database.")

