<!-- loio8bad1a8605b343ababf821350b160714 -->

# Grant SAP HDI Container Administrator Privileges to a User

Enable administrator access to an SAP HDI container.



## Context

In SAP HANA Deployment Infrastructure \(HDI\), administrator privileges for an HDI container are initially granted to a user by an administrator of the container group that the HDI container belongs to. If these privileges have been granted "with grant option", the HDI container administrator can also grant these privileges to another user as described below:

> ### Note:  
> The predefined table `_SYS_DI.T_DEFAULT_CONTAINER_ADMIN_PRIVILEGES` used in this task contains the largest possible set of privileges that can be granted for a user of this type. You can reduce the set of privileges granted by explicitly specifying the desired set of privileges and not using this default table.



## Procedure

1.  In an SQL console, connect to the database with an administrator of the HDI container “C”.

2.  Open the SQL editor for this database.

3.  Insert the following SQL code into the editor:

    > ### Sample Code:  
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #PRIVILEGES LIKE _SYS_DI.TT_API_PRIVILEGES;
    > INSERT INTO #PRIVILEGES (PRINCIPAL_NAME, PRIVILEGE_NAME, OBJECT_NAME) SELECT 'NEW_CONTAINER_ADMIN', PRIVILEGE_NAME, OBJECT_NAME FROM _SYS_DI.T_DEFAULT_CONTAINER_ADMIN_PRIVILEGES; 
    > CALL C#DI.GRANT_CONTAINER_API_PRIVILEGES(#PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?); 
    > DROP TABLE #PRIVILEGES; 
    > ```

    1.  Adjust the name of the user “`NEW_CONTAINER_ADMIN`” in line 2 to reflect the name of the user to whom the API privileges should be granted.

    2.  Adjust the name of the container's API schema `C#DI` to suit your needs.

    3.  If the target user should also be able to grant another user the container administration privileges, replace the procedure `C#DI.GRANT_CONTAINER_API_PRIVILEGES` in the SQL statement above with the procedure `C#DI.GRANT_CONTAINER_API_PRIVILEGES_WITH_GRANT_OPTION`.

        > ### Note:  
        > The procedure `C#DI.GRANT_CONTAINER_API_PRIVILEGES_WITH_GRANT_OPTION` should only be used in special scenarios, for example, when building a custom SQL API by wrapping the HDI SQL API in SQLScript procedures.


4.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

5.  \(Optional\) Confirm that the `NEW_CONTAINER_ADMIN` user is now able to call HDI container API procedures in the containers API schema \(for example, `C#DI` in container “C”\).


**Related Information**  


[Revoke SAP HDI Container Administrator Privileges from a User](revoke-sap-hdi-container-administrator-privile-7c7b430.md "Disable administrator access to an SAP HDI container.")

[Maintaining SAP HDI Containers](maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

