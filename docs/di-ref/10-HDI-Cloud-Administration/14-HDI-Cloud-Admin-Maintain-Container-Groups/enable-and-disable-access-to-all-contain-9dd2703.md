<!-- loio9dd270383b4c4a5f8b4a1e6fd3c3b757 -->

# Enable and Disable Access to all Containers in a Container Group for Application Users

Use a group configuration parameter to enable and disable access to all containers in a container group for an application run-time user.



<a name="loio9dd270383b4c4a5f8b4a1e6fd3c3b757__prereq_mkk_w1t_ytb"/>

## Prerequisites

To complete the steps described in this task, the following prerequisites apply:

-   You have the privileges of an HDI container-group administrator
-   You have access to an SQL console that is connected to SAP HANA



## Context

The HDI container-group administrator can use a function that will assign an application user or run-time user to an HDI-container-group-specific role called `CONTAINERS_ACCESS`. The function sets the container group configuration parameter “`enable_cross_container_access`”. which grants DML access \(for example, `SELECT`, `EXECUTE`, etc\) for each container in the HDI container group to the role `CONTAINERS_ACCESS`. This feature is particularly useful in the following scenarios:

-   Creating new HDI containers

    If the HDI container group to which a new container is assigned has the configuration parameter `enable_cross_container_access` set to "true", then the application or run-time user is granted DML access to all containers in the HDI container group.

-   Moving existing HDI containers

    When an HDI container is moved to another container group, then the DML schema access to all the other containers in the previous group is revoked \(assuming the parameter for the previous group is set to "true"\) from the application/run-time user, and the same procedure is performed on this container as explained for the creation of a container.


> ### Note:  
> The cross-container access you configure in this task provides privileges for an application user; the privileges provided do not include the `GRANT OPTION`. An application user needs these privileges when accessing objects in containers of the container group.
> 
> Cross-container access provides application users with the privileges they require to access other HDI containers and the objects in those containers. To work with objects in other HDI containers, application users do not need to use synonyms.



## Procedure

1.  Locate the application/run-time user to \(or from\) whom you want to grant \(or revoke\) access to all containers in a container group.

    In this example, the name of the application or run-time user is `RT_USER`.

2.  Locate the target HDI container group where you want to enable cross-container access for the application or run-time user.

3.  Grant the user access to containers in the target container group \("G" in this example\).

    ```sql
    CALL _SYS_DI#G.GRANT_CONTAINERS_ACCESS_ROLE('', 'RT_USER', _SYS_DI.T_NO_PARAMETERS, ?, ?, ?); 
    ```

4.  Enable the configuration parameter “`enable_cross_container_access`” for container group "G".

    ```sql
    CREATE LOCAL TEMPORARY COLUMN TABLE #CONFIG_GROUP_PARAMETERS LIKE _SYS_DI.TT_PARAMETERS;
    INSERT INTO #CONFIG_GROUP_PARAMETERS (KEY, VALUE) VALUES ('enable_cross_container_access', 'True'); 
    CALL _SYS_DI.CONFIGURE_CONTAINER_GROUP_PARAMETERS('G', #CONFIG_GROUP_PARAMETERS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?); 
    DROP TABLE #CONFIG_GROUP_PARAMETERS;
    ```

    This enables DML access to all the containers in the HDI container group "G" for the run-time user "`RT_USER`". `RT_USER` is automatically granted DML access to any new containers which are added \(or moved\) to the HDI container group "G" after the group configuration parameter `enable_cross_container_access` is set to "True".

5.  Disable DML access to containers inside the container group "G" for the run-time user `RT_USER`.

    ```sql
    CREATE LOCAL TEMPORARY COLUMN TABLE #CONFIG_GROUP_PARAMETERS LIKE _SYS_DI.TT_PARAMETERS; 
    INSERT INTO #CONFIG_GROUP_PARAMETERS (KEY, VALUE) VALUES ('enable_cross_container_access', ''); 
    CALL _SYS_DI.CONFIGURE_CONTAINER_GROUP_PARAMETERS('G', #CONFIG_GROUP_PARAMETERS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?); 
    DROP TABLE #CONFIG_GROUP_PARAMETERS; 
    ```

    This revokes DML access to all the containers in the HDI container group "G" from the run-time user "`RT_USER`".

6.  Revoke the containers access role from the run-time user `RT_USER`.

    ```sql
    CALL _SYS_DI#G.REVOKE_CONTAINERS_ACCESS_ROLE('', 'RT_USER', _SYS_DI.T_NO_PARAMETERS, ?, ?, ?); 
    ```


**Related Information**  


[Enable and Disable Cross-Container Access](enable-and-disable-cross-container-acces-c3c34fd.md "Use an HDI container-group configuration parameter to enable access between HDI containers in the same HDI container group.")

[SAP HDI Configuration Parameters](../13-HDI-Cloud-Admin-Maintain-HDI/sap-hdi-configuration-parameters-1d9582a.md "Configuration parameters are used to configure the behavior of SAP HANA Deployment Infrastructure (HDI).")

