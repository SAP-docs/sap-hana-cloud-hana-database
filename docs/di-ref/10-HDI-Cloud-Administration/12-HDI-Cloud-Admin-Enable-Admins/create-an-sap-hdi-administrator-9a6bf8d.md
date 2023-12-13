<!-- loio9a6bf8dc816e4b128ecec7580686236e -->

# Create an SAP HDI Administrator

The HDI administrator is responsible for configuring general SAP HDI parameters, creating and dropping HDI container groups, moving HDI containers between groups, and managing the privileges of HDI container-group administrators.



<a name="loio9a6bf8dc816e4b128ecec7580686236e__prereq_gml_1zz_j1b"/>

## Prerequisites

-   The `DBADMIN` user has been reactivated and you have its credentials.
-   SAP HDI is enabled.

    > ### Tip:  
    > In an SAP HANA Cloud instance, the SAP HDI is enabled by default.




<a name="loio9a6bf8dc816e4b128ecec7580686236e__context_fky_kbf_l1b"/>

## Context

This method uses the predefined `_SYS_DI.T_DEFAULT_DI_ADMIN_PRIVILEGES` table, which contains the largest possible set of privileges that can be granted for a user of this type. It is also possible to reduce the set of privileges by explicitly specifying the desired set of privileges and not using this default table.

> ### Note:  
> A variant of this procedure,`_SYS_DI.GRANT_CONTAINER_GROUP_API_PRIVILEGES_WITH_GRANT_OPTION`, also exists; it grants the given privileges `WITH GRANT OPTION` to the target user. However, this variant procedure is only needed in special scenarios, for example, when building a custom SQL API by wrapping the HDI SQL API in SQLScript procedures.



## Procedure

1.  In an SQL console, connect to the database with the `DBADMIN` user.

2.  Optional: Create a new user by executing the following statement:

    ```sql
    CREATE USER <HDI_admin_username> PASSWORD <password> NO FORCE_FIRST_PASSWORD_CHANGE;
    ```

    > ### Note:  
    > For more information about setting the default user group, for example, to avoid errors if `DBADMIN` is the user-group operator of more than one user group, see *User Management with DBADMIN* in *Related Information* below.

3.  Grant the new HDI administrator user the required privileges by executing the following statement:

    > ### Sample Code:  
    > ```sql
    > CREATE LOCAL TEMPORARY TABLE #PRIVILEGES LIKE _SYS_DI.TT_API_PRIVILEGES;
    > INSERT INTO #PRIVILEGES (PRINCIPAL_NAME, PRIVILEGE_NAME, OBJECT_NAME) SELECT '<HDI_admin_username>', PRIVILEGE_NAME, OBJECT_NAME FROM _SYS_DI.T_DEFAULT_DI_ADMIN_PRIVILEGES;
    > CALL _SYS_DI.GRANT_CONTAINER_GROUP_API_PRIVILEGES('_SYS_DI', #PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > DROP TABLE #PRIVILEGES;
    > 
    > ```

4.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

5.  Confirm that the new HDI administrator user can call HDI API procedures in the`_SYS_DI` schema.




<a name="loio9a6bf8dc816e4b128ecec7580686236e__postreq_ckz_5d1_k1b"/>

## Next Steps

Deactivate the `DBADMIN` user:

`ALTER USER DBADMIN DEACTIVATE USER NOW`.

**Related Information**  


[Revoke the SAP HDI Administrator Privileges](revoke-the-sap-hdi-administrator-privileges-84b472a.md "Revoke the SAP HDI administrator privileges from a specified user.")

[User Management with the SAP HANA Database Administrator DBADMIN \(SAP HANA Cloud Admin Guide\)](https://help.sap.com/docs/HANA_CLOUD_DATABASE/f9c5015e72e04fffa14d7d4f7267d897/5b35402c47b344d882ac13c661aff1c0.html)

