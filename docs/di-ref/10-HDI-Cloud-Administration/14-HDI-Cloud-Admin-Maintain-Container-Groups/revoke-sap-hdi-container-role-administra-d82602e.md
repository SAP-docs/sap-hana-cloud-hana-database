<!-- loiod82602e6e8054c79be8f418430fd411f -->

# Revoke SAP HDI-Container Role-Administrator Privileges from a User

In SAP HANA Deployment Infrastructure \(HDI\), role-administrator privileges for HDI containers can be revoked from a user at any time.



## Context

Each container can have its own set of administrators. Role-administrative privileges for a container must be explicitly granted or revoked by an HDI container group administrator, or an HDI container administrator with the necessary privileges.

The predefined table `_SYS_DI.T_DEFAULT_CONTAINER_ROLE_ADMIN_PRIVILEGES` used in this task contains the largest possible set of privileges that can be granted for a user of this type. The predefined table specifies privileges for the `GRANT_CONTAINER_SCHEMA_ROLES` and `REVOKE_CONTAINER_SCHEMA_ROLES` container APIs, the container's `M_ROLES` view, as well as any related objects needed for granting \(or revoking\) roles from the container to another user.

> ### Note:  
> It is not mandatory to use the predefined table `_SYS_DI.T_DEFAULT_CONTAINER_ROLE_ADMIN_PRIVILEGES`. To reduce the set of privileges granted during this operation, you can explicitly specify the set of privileges that are required for your scenario.



<a name="loiod82602e6e8054c79be8f418430fd411f__steps_nxw_fsx_k1b"/>

## Procedure

1.  In an SQL console, connect to the database as the administrator of the HDI container group *<container\_group\_name\>*.

2.  Open the SQL editor for this database.

3.  Insert the following SQL code into the editor:

    > ### Sample Code:  
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #PRIVILEGES LIKE _SYS_DI.TT_API_PRIVILEGES;
    > INSERT INTO #PRIVILEGES (PRINCIPAL_NAME, PRIVILEGE_NAME, OBJECT_NAME) SELECT '<container_admin_username>', PRIVILEGE_NAME, OBJECT_NAME FROM _SYS_DI.T_DEFAULT_CONTAINER_ROLE_ADMIN_PRIVILEGES WHERE NOT (PRIVILEGE_NAME = 'SELECT' AND OBJECT_NAME LIKE '_SYS_DI.T%');
    > CALL _SYS_DI#<container_group_name>.REVOKE_CONTAINER_API_PRIVILEGES('<container_name>', #PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > DROP TABLE #PRIVILEGES; 
    > ```

4.  Replace *<container\_admin\_username\>* in the `INSERT` statement in line 2 with the name of the user from whom the API privileges should be revoked. In the `CALL` statement in line 3, you will also have to change the name of the container group *<container\_group\_name\>* in the API schema <code>_SYS_DI#<i class="varname">&lt;container_group_name&gt;</i></code> and the name of the container *<container\_name\>* to reflect the group and container names in your landscape.

5.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

6.  \(Optional\) Confirm that the privileges have been successfully revoked and the *<container\_admin\_username\>* user is no longer able to call HDI container API procedures in the container *<container\_name\>*'s API schema <code><i class="varname">&lt;container_name&gt;</i>#DI</code>.


**Related Information**  


[Grant SAP HDI-Container Role-Administrator Privileges to a User](grant-sap-hdi-container-role-administrat-a531866.md "In SAP HANA Deployment Infrastructure (HDI), role-administrator privileges for HDI containers can be granted to another user at any time.")

[Maintaining SAP HDI Container Groups](maintaining-sap-hdi-container-groups-4e9d597.md "The administrator of an SAP HDI container group is responsible for managing the SAP HDI containers that are organized into one or more HDI container groups.")

