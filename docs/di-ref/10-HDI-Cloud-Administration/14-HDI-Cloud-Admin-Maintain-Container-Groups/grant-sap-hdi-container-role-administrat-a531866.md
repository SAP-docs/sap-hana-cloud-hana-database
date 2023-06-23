<!-- loioa531866596e04f3a8d8500b6df51f1c4 -->

# Grant SAP HDI-Container Role-Administrator Privileges to a User

In SAP HANA Deployment Infrastructure \(HDI\), role-administrator privileges for HDI containers can be granted to another user at any time.



<a name="loioa531866596e04f3a8d8500b6df51f1c4__context_pqc_v5x_k1b"/>

## Context

Each HDI container can have its own set of administrators. Role-administrative privileges for a container must be explicitly granted or revoked either by an HDI container-group administrator or an HDI-container administrator with the necessary privileges.

The predefined table `_SYS_DI.T_DEFAULT_CONTAINER_ROLE_ADMIN_PRIVILEGES` used in this task contains the largest possible set of privileges that can be granted for a user of this type. The predefined table specifies privileges for the `GRANT_CONTAINER_SCHEMA_ROLES` and `REVOKE_CONTAINER_SCHEMA_ROLES` container APIs, the container's `M_ROLES` view, as well as any related objects needed for granting \(or revoking\) roles from the container to another user.

> ### Note:  
> It is not mandatory to use the predefined table `_SYS_DI.T_DEFAULT_CONTAINER_ROLE_ADMIN_PRIVILEGES`. To reduce the set of privileges granted during this operation, you can explicitly specify the set of privileges that are required for your scenario.



<a name="loioa531866596e04f3a8d8500b6df51f1c4__steps_nxw_fsx_k1b"/>

## Procedure

1.  In an SQL console, connect to the database as the administrator of the target HDI container group \(for example, “G”\).

2.  Open the SQL editor for this database.

3.  Grant the HDI-container, role-administrator privileges.

    Insert the following SQL code into the editor:

    > ### Sample Code:  
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #PRIVILEGES LIKE _SYS_DI.TT_API_PRIVILEGES; 
    > INSERT INTO #PRIVILEGES (PRINCIPAL_NAME, PRIVILEGE_NAME, OBJECT_NAME) SELECT 'NEW_CONTAINER_ADMIN', PRIVILEGE_NAME, OBJECT_NAME FROM _SYS_DI.T_DEFAULT_CONTAINER_ROLE_ADMIN_PRIVILEGES; 
    > CALL _SYS_DI#G.GRANT_CONTAINER_API_PRIVILEGES('C', #PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?); 
    > DROP TABLE #PRIVILEGES
    > 
    > ```

4.  Adjust the name of the user `NEW_CONTAINER_ADMIN` in the `INSERT` statement in line 2 to reflect the name of the user to whom the API privileges should be granted. You will also have to change the name of the container group “G” in the API schema `_SYS_DI#G` and the name of the container “C” to reflect the names in your landscape.

5.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

6.  \(Optional\) Confirm that the `NEW_CONTAINER_ADMIN` user is now able to call HDI container API procedures in the container C's API schema `C#DI`.


**Related Information**  


[Maintaining SAP HDI Container Groups](maintaining-sap-hdi-container-groups-4e9d597.md "The administrator of an SAP HDI container group is responsible for managing the SAP HDI containers that are organized into one or more HDI container groups.")

