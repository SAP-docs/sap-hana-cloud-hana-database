<!-- loio3447f9706b3a42fc9840a3dac389e426 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Enable and Disable Cross-Container Access for HDI in Cloud Foundry

Use an HDI container-group configuration parameter to enable access between HDI containers in the same HDI container group.



<a name="loio3447f9706b3a42fc9840a3dac389e426__prereq_mkk_w1t_ytb"/>

## Prerequisites

To complete the steps described in this task, the following prerequisites apply:

-   You have access to the Cloud Foundry run-time environment
-   You have access to **
-   You have access to an SQL console that is connected to SAP HANA
-   You have the privileges of an HDI container-group administrator



## Context

The HDI container-group administrator can use a function to set the container-group configuration parameter `enable_cross_container_access`, which enables DML access \(for example, `SELECT`, `EXECUTE`, etc.\) for each container in an HDI container group to all other containers in the same HDI container group. This feature is particularly useful in the following scenarios:

-   Creating HDI containers

    When a new HDI container is created, if the HDI container group to which the new container is assigned has the configuration parameter SAP Business Application Studio`enable_cross_container_access` set, then all other containers in the HDI container group are given DML access to the new container's schema, and the new container has the same access to all other containers in the container group.

-   Moving HDI containers

    When an HDI container is moved to another container group, DML schema access to other containers in the source container group is revoked from the moved container, and in the target container group, the same procedure is performed on the moved container as would be performed during the creation of a new container.


SAP BusinessTo enable access between containers in the same HDI container group, perform the following steps:



## Procedure

1.  In *SAP Business Application Studio*, open an SQL console.

    1.  Open the *SAP HANA Database Explorer* view in *SAP Business Application Studio*.

        > ### Note:  
        > To be able to see the list of databases that you want to explore, you must be logged on to Cloud Foundry; the databases are associated with a Cloud Foundry development space. If you are not logged into Cloud Foundry, *SAP Business Application Studio* prompts you to provide the required user credentials.

        In the views pane of *SAP Business Application Studio*, choose <span class="FPA-icons"></span> \(SAP HANA Database Explorer\).

    2.  Open the SQL console for SAP HANA as the HDI administrator.

        In the *DATABASE LIST* pane, locate the database that you want to explore, and choose <span class="FPA-icons"></span> \(Open SQL Console as HDI Admin\).

        > ### Tip:  
        > If you cannot find your database in the list, choose <span class="FPA-icons"></span> \(Refresh\) in the Database Explorer pane.

        If the connection succeeds, the tool bar in the SQL console for SAP HANA indicates the name of the database it is connected to and \(in brackets\) the name of the Cloud Foundry space to which the database is assigned, for example, *Myapp-hdidb-ws-ab1cd \(MyDevSpace\)*.


2.  In the SQL console, connect to the SAP HANA database as the administrator of the HDI container group, where you want to enable cross-container access.

3.  Open the SQL editor for this database.

4.  Enable access between containers in the chosen container group.

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

5.  Disable access between containers in the chosen HDI container group.

    The following code example shows how to use the configuration parameter `enable_cross_container_access` to disable access between containers in the container group 'G':

    ```sql
    CREATE LOCAL TEMPORARY COLUMN TABLE #CONFIG_GROUP_PARAMETERS LIKE _SYS_DI.TT_PARAMETERS; 
    INSERT INTO #CONFIG_GROUP_PARAMETERS (KEY, VALUE) VALUES ('enable_cross_container_access', ''); 
    CALL _SYS_DI#G.CONFIGURE_CONTAINER_GROUP_PARAMETERS(#CONFIG_GROUP_PARAMETERS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?); 
    DROP TABLE #CONFIG_GROUP_PARAMETERS; 
    ```

    In this example, no value \(`''`\) is provided for the parameter `enable_cross_container_access`, which revokes DML schema access between containers in the container group `'G'`, but you can also explicitly set the parameter to `'false'`.


**Related Information**  


[Enable Access to Objects in a Remote Classic Schema](enable-access-to-objects-in-a-remote-classic-schema-402944b.md "Use a synonym to enable access to objects in a remote schema that is not managed by your Cloud Foundry application (for example, ERP).")

[Enable Access to Objects in Another HDI Container](enable-access-to-objects-in-another-hdi-container-4adba34.md "Use a synonym to enable access to another HDI container.")

[SAP HDI Configuration Parameters \(SAP HDI Reference Guide for SAP HANA Cloud\)](https://help.sap.com/docs/HANA_CLOUD_DATABASE/c2cc2e43458d4abda6788049c58143dc/1d9582a464344b6c86bcd3489dca7554.html)

