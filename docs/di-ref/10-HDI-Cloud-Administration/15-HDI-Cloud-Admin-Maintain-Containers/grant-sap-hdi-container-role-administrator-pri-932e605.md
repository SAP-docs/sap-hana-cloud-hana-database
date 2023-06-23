<!-- loio932e6054e19044b48a2aa904b4079917 -->

# Grant SAP HDI-Container Role-Administrator Privileges to a User

Enable role-administrator access to an SAP HDI container.



## Context

In SAP HANA Deployment Infrastructure \(HDI\), role-administrator privileges for an HDI container are initially granted to a user by an administrator of the container group that the HDI container belongs to. If these privileges have been granted "`with grant option`", the HDI container administrator can also grant these privileges to another user as described below:

The predefined table `_SYS_DI.T_DEFAULT_CONTAINER_ROLE_ADMIN_PRIVILEGES` used in this task contains the largest possible set of privileges that can be granted for a user of this type. The predefined table specifies privileges for the `GRANT_CONTAINER_SCHEMA_ROLES` and `REVOKE_CONTAINER_SCHEMA_ROLES` container APIs, the container's `M_ROLES` view, as well as any related objects needed for granting \(or revoking\) roles from the container to another user.

> ### Note:  
> It is not mandatory to use the predefined table `_SYS_DI.T_DEFAULT_CONTAINER_ROLE_ADMIN_PRIVILEGES`. To reduce the set of privileges granted during this operation, you can explicitly specify the set of privileges that are required for your scenario.



## Procedure

1.  In an SQL console, connect to the database with an administrator of the target HDI container \(for example, “C”\).

2.  Open the SQL editor for this database.

3.  Insert the following SQL code into the editor:

    > ### Sample Code:  
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #PRIVILEGES LIKE _SYS_DI.TT_API_PRIVILEGES;
    > INSERT INTO #PRIVILEGES (PRINCIPAL_NAME, PRIVILEGE_NAME, OBJECT_NAME) SELECT 'NEW_CONTAINER_ADMIN', PRIVILEGE_NAME, OBJECT_NAME FROM _SYS_DI.T_DEFAULT_CONTAINER_ROLE_ADMIN_PRIVILEGES; 
    > CALL C#DI.GRANT_CONTAINER_API_PRIVILEGES(#PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?); 
    > DROP TABLE #PRIVILEGES; 
    > ```

    1.  Adjust the name of the user “`NEW_CONTAINER_ADMIN`” in line 2 to reflect the name of the user to whom the API privileges should be granted.

    2.  Adjust the name of the container's API schema `C#DI` to suit your needs.

    3.  If the target user should also be able to grant these container administration privileges to another user, replace the procedure `C#DI.GRANT_CONTAINER_API_PRIVILEGES` in the SQL statement above with the procedure `C#DI.GRANT_CONTAINER_API_PRIVILEGES_WITH_GRANT_OPTION`.

        > ### Note:  
        > The procedure `C#DI.GRANT_CONTAINER_API_PRIVILEGES_WITH_GRANT_OPTION` should only be used in special scenarios, for example, when building a custom SQL API by wrapping the HDI SQL API in SQLScript procedures.


4.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

5.  \(Optional\) Confirm that the `NEW_CONTAINER_ADMIN` user is now able to call HDI container API procedures in the containers API schema \(for example, `C#DI` in container “C”\).


**Related Information**  


[Maintaining SAP HDI Containers](maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

