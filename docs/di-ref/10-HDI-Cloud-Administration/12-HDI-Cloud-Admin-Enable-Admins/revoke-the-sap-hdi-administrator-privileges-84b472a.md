<!-- loio84b472a52cbb4e4588a2d309f44f44cf -->

# Revoke the SAP HDI Administrator Privileges

Revoke the SAP HDI administrator privileges from a specified user.



<a name="loio84b472a52cbb4e4588a2d309f44f44cf__prereq_gml_1zz_j1b"/>

## Prerequisites

-   The `DBADMIN` user has been reactivated and you have its credentials.
-   SAP HDI is enabled.

    > ### Tip:  
    > In an SAP HANA Cloud instance, the SAP HDI is enabled by default.




## Context

The database administrator `DBADMIN` can revoke the SAP HDI administrator privileges from a user.

> ### Note:  
> This method uses the predefined `_SYS_DI.T_DEFAULT_DI_ADMIN_PRIVILEGES` table, which contains the largest possible set of privileges that can be revoked from a user of this type. It is also possible to reduce the set of privileges by explicitly specifying the desired set of privileges and not using this default table.



## Procedure

1.  In an SQL console, connect to the database with the `DBADMIN` user.

2.  Open the SQL editor for this database.

3.  Revoke the HDI administrator privileges from the selected user.

    Insert the following SQL code into the SQL console:

    > ### Note:  
    > In the following code example, replace `NEW_HDI_ADMIN` with the name of the user from whom the HDI administrator privileges should be revoked.

    ```sql
    CREATE LOCAL TEMPORARY TABLE #PRIVILEGES LIKE _SYS_DI.TT_API_PRIVILEGES;
    INSERT INTO #PRIVILEGES (PRINCIPAL_NAME, PRIVILEGE_NAME, OBJECT_NAME) SELECT 'NEW_HDI_ADMIN', PRIVILEGE_NAME, OBJECT_NAME FROM _SYS_DI.T_DEFAULT_DI_ADMIN_PRIVILEGES WHERE NOT (PRIVILEGE_NAME = 'SELECT' AND OBJECT_NAME LIKE 'T%');
    CALL _SYS_DI.REVOKE_CONTAINER_GROUP_API_PRIVILEGES('_SYS_DI', #PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    DROP TABLE #PRIVILEGES; 
    ```

4.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

5.  \(Optional\) Confirm that the `NEW_HDI_ADMIN` user is no longer able to call HDI API procedures in the `_SYS_DI` schema.




<a name="loio84b472a52cbb4e4588a2d309f44f44cf__postreq_ckz_5d1_k1b"/>

## Next Steps

Deactivate the `DBADMIN` user, for example, with the following command in the SQL console:

`ALTER USER DBADMIN DEACTIVATE USER NOW`

**Related Information**  


[Enabling the SAP HDI Administrators](enabling-the-sap-hdi-administrators-c248d55.md "Create the users required to adminstrate and maintain the SAP HANA Deployment Infrastructure (HDI) services.")

[Create an SAP HDI Administrator](create-an-sap-hdi-administrator-9a6bf8d.md "The HDI administrator is responsible for configuring general SAP HDI parameters, creating and dropping HDI container groups, moving HDI containers between groups, and managing the privileges of HDI container-group administrators.")

