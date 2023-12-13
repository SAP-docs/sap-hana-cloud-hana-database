<!-- loioc3c34fdeccae423ea2071fd61acba787 -->

# Enable and Disable Cross-Container Access

Use an HDI container-group configuration parameter to enable access between HDI containers in the same HDI container group.



<a name="loioc3c34fdeccae423ea2071fd61acba787__prereq_mkk_w1t_ytb"/>

## Prerequisites

To complete the steps described in this task, the following prerequisites apply:

-   You have the privileges of an HDI container-group administrator
-   You have access to an SQL console that is connected to SAP HANA



## Context

The HDI container-group administrator can use a function to set the container-group configuration parameter `enable_cross_container_access`, which enables DML access \(for example, `SELECT`, `EXECUTE`, etc.\) for each container in an HDI container group to all other containers in the same HDI container group. This feature is particularly useful in the following scenarios:

-   Creating new HDI containers

    If the HDI container group to which a new container is assigned has the configuration parameter `enable_cross_container_access` set to "true", then all other containers in the HDI container group are given DML access to the new container's schema, and the new container has the same access to all other containers in the container group.

-   Moving existing HDI containers

    When an HDI container is moved to another container group, DML schema access to other containers in the source container group is revoked from the moved container, and in the target container group, the same procedure is performed on the moved container as would be performed during the creation of a new container.


> ### Note:  
> The cross-container access you configure in this task provides privileges for the container object owner; these privileges include the `GRANT OPTION` and allow the container object owner to create objects that depend on objects in another container even in situations when the `SELECT WITH GRANT` privilege is required, for example, when creating calculation views.
> 
> Cross-container access only provides the privileges required to access other containers; it does not provide direct access to objects in other containers. To work with objects from other HDI containers, you need to use synonyms.

To enable access between containers in the same HDI container group, perform the following steps:



## Procedure

1.  In an SQL console, connect to the database as the administrator of the HDI container group, where you want to enable cross-container access.

2.  Open the SQL editor for this database.

3.  Enable access between containers in the chosen container group.

    Execute the following code, which shows how to use the configuration parameter `enable_cross_container_access` to enable access between containers assigned to container group `'G'`:

    ```sql
    CREATE LOCAL TEMPORARY COLUMN TABLE #CONFIG_GROUP_PARAMETERS LIKE _SYS_DI.TT_PARAMETERS; 
    INSERT INTO #CONFIG_GROUP_PARAMETERS (KEY, VALUE) VALUES ('enable_cross_container_access', 'true'); 
    CALL _SYS_DI#G.CONFIGURE_CONTAINER_GROUP_PARAMETERS(#CONFIG_GROUP_PARAMETERS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?); 
    DROP TABLE #CONFIG_GROUP_PARAMETERS; 
    ```

    With the configuration parameter `enable_cross_container_access` set to `'true'` for the specified container group \(`'G'`\), any containers already in group `'G'` are granted DML schema access to all other containers in container group `'G'`.

    > ### Note:  
    > The same access is also granted to any new containers which are subsequently added \(or moved\) to the HDI container group where the configuration parameter is set to `'true'`.

4.  Disable access between containers in the chosen container group.

    The following code example shows how to use the configuration parameter `enable_cross_container_access` to disable access between containers in the container group 'G':

    ```sql
    CREATE LOCAL TEMPORARY COLUMN TABLE #CONFIG_GROUP_PARAMETERS LIKE _SYS_DI.TT_PARAMETERS; 
    INSERT INTO #CONFIG_GROUP_PARAMETERS (KEY, VALUE) VALUES ('enable_cross_container_access', ''); 
    CALL _SYS_DI#G.CONFIGURE_CONTAINER_GROUP_PARAMETERS(#CONFIG_GROUP_PARAMETERS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?); 
    DROP TABLE #CONFIG_GROUP_PARAMETERS; 
    ```

    In this example, no value \(`''`\) is provided for the parameter `enable_cross_container_access`, which revokes DML schema access between containers in the container group `'G'`, but you can also explicitly set the parameter to `'false'`.


**Related Information**  


[Enable and Disable Access to all Containers in a Container Group for Application Users](enable-and-disable-access-to-all-contain-9dd2703.md "Use a group configuration parameter to enable and disable access to all containers in a container group for an application run-time user.")

[SAP HDI Configuration Parameters](../13-HDI-Cloud-Admin-Maintain-HDI/sap-hdi-configuration-parameters-1d9582a.md "Configuration parameters are used to configure the behavior of SAP HANA Deployment Infrastructure (HDI).")

[Maintaining SAP HDI Container Groups](maintaining-sap-hdi-container-groups-4e9d597.md "The administrator of an SAP HDI container group is responsible for managing the SAP HDI containers that are organized into one or more HDI container groups.")

[Using Synonyms to Access External Schemas and Objects \(Developer Guide for SAP HANA XS Advanced\)](https://help.sap.com/docs/SAP_HANA_PLATFORM/4505d0bdaf4948449b7f7379d24d0f0d/bdc9f7ae66134c279a5f3683bba9b361.html)

[Using Synonyms to Access External Schemas and Objects \(SAP HANA Cloud Database Developer Guide for Busines App Studio\)](https://help.sap.com/docs/HANA_CLOUD_DATABASE/c2b99f19e9264c4d9ae9221b22f6f589/bdc9f7ae66134c279a5f3683bba9b361.html)

