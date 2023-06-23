<!-- loio9095f21eb0c840acb58bdc4ab9bcd05e -->

# Revoke SAP HDI-Container Role-Administrator Privileges from a User

Disable role-administrator privileges for an SAP HDI container.



## Context

In SAP HANA Deployment Infrastructure \(HDI\), each HDI container can have its own set of administrators, and role-administrator privileges for an HDI container must be explicitly granted or revoked either by an HDI container-group administrator or by an HDI container administrator with the necessary privileges.

The predefined table `_SYS_DI.T_DEFAULT_CONTAINER_ROLE_ADMIN_PRIVILEGES` used in this task contains the largest possible set of privileges that can be granted for a user of this type. The predefined table specifies privileges for the `GRANT_CONTAINER_SCHEMA_ROLES` and `REVOKE_CONTAINER_SCHEMA_ROLES` container APIs, the container's `M_ROLES` view, as well as any related objects needed for granting \(or revoking\) roles from the container to another user.

> ### Note:  
> It is not mandatory to use the predefined table `_SYS_DI.T_DEFAULT_CONTAINER_ROLE_ADMIN_PRIVILEGES`. To reduce the set of privileges granted during this operation, you can explicitly specify the set of privileges that are required for your scenario.



<a name="loio9095f21eb0c840acb58bdc4ab9bcd05e__steps_osn_qhd_l1b"/>

## Procedure

1.  In an SQL console, connect to the database with an administrator of the HDI container “C” \(or the name of the container whose administrator privileges you want to change\).

2.  Open the SQL editor for this database.

3.  Revoke role-administrator privileges from a user in a specific HDI container.

    Insert the following SQL code into the SQL editor:

    > ### Sample Code:  
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #PRIVILEGES LIKE _SYS_DI.TT_API_PRIVILEGES;
    > INSERT INTO #PRIVILEGES (PRINCIPAL_NAME, PRIVILEGE_NAME, OBJECT_NAME) SELECT 'NEW_CONTAINER_ADMIN', PRIVILEGE_NAME, OBJECT_NAME FROM _SYS_DI.T_DEFAULT_CONTAINER_ROLE_ADMIN_PRIVILEGES WHERE NOT (PRIVILEGE_NAME = 'SELECT' AND OBJECT_NAME LIKE '_SYS_DI.T%');
    > CALL C#DI.REVOKE_CONTAINER_API_PRIVILEGES(#PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > DROP TABLE #PRIVILEGES; 
    > ```

    1.  In the `INSERT` statement in line 2, adjust the name of the user “`NEW_CONTAINER_ADMIN`” to reflect the name of the user from whom the API privileges should be revoked.


4.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

5.  \(Optional\) Confirm that the privileges have been successfully revoked and the `NEW_CONTAINER_ADMIN` user is no longer able to call HDI container API procedures in the containers API schema \(for example, `C#DI` in container “C”\).


**Related Information**  


[Grant SAP HDI-Container Role-Administrator Privileges to a User](grant-sap-hdi-container-role-administrator-pri-932e605.md "Enable role-administrator access to an SAP HDI container.")

[Maintaining SAP HDI Containers](maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

