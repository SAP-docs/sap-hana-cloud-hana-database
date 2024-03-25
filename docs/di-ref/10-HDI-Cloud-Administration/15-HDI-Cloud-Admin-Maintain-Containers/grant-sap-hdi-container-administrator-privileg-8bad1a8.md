<!-- loio8bad1a8605b343ababf821350b160714 -->

# Grant SAP HDI Container Administrator Privileges to a User

Enable administrator access to an SAP HDI container.



## Context

In SAP HANA Deployment Infrastructure \(HDI\), administrator privileges for an HDI container are initially granted to a user by an administrator of the container group that the HDI container belongs to. If these privileges have been granted "with grant option", the HDI container administrator can also grant these privileges to another user as described below:

> ### Note:  
> The predefined table `_SYS_DI.T_DEFAULT_CONTAINER_ADMIN_PRIVILEGES` used in this task contains the largest possible set of privileges that can be granted for a user of this type. You can reduce the set of privileges granted by explicitly specifying the desired set of privileges and not using this default table.



## Procedure

1.  In an SQL console, connect to the database with an administrator of the HDI container *<container\_name\>*.

2.  Open the SQL editor for this database.

3.  Insert the following SQL code into the editor:

    > ### Sample Code:  
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #PRIVILEGES LIKE _SYS_DI.TT_API_PRIVILEGES;
    > INSERT INTO #PRIVILEGES (PRINCIPAL_NAME, PRIVILEGE_NAME, OBJECT_NAME) SELECT '<NEW_CONTAINER_ADMIN>', PRIVILEGE_NAME, OBJECT_NAME FROM _SYS_DI.T_DEFAULT_CONTAINER_ADMIN_PRIVILEGES; 
    > CALL <container_name>#DI.GRANT_CONTAINER_API_PRIVILEGES(#PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?); 
    > DROP TABLE #PRIVILEGES; 
    > ```

    1.  Replace *<NEW\_CONTAINER\_ADMIN\>* in line 2 with the name of the user to whom the API privileges should be granted.

    2.  Adjust the name of the container's API schema <code><i class="varname">&lt;container_name&gt;</i>#DI</code> to suit your needs.

    3.  If the target user should also be able to grant another user the container administration privileges, replace the procedure <code><i class="varname">&lt;container_name&gt;</i>#DI.GRANT_CONTAINER_API_PRIVILEGES</code> in the SQL statement above with the procedure <code><i class="varname">&lt;container_name&gt;</i>#DI.GRANT_CONTAINER_API_PRIVILEGES_WITH_GRANT_OPTION</code>.

        > ### Note:  
        > The procedure <code><i class="varname">&lt;container_name&gt;</i>#DI.GRANT_CONTAINER_API_PRIVILEGES_WITH_GRANT_OPTION</code> should only be used in special scenarios, for example, when building a custom SQL API by wrapping the HDI SQL API in SQLScript procedures.


4.  Run the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

5.  \(Optional\) Confirm that the *<NEW\_CONTAINER\_ADMIN\>* user is now able to call HDI container API procedures in the containers API schema \(for example, <code><i class="varname">&lt;container_name&gt;</i>#DI</code> in container *<container\_name\>*\).


**Related Information**  


[Revoke SAP HDI Container Administrator Privileges from a User](revoke-sap-hdi-container-administrator-privile-7c7b430.md "Disable administrator access to an SAP HDI container.")

[Maintaining SAP HDI Containers](maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

