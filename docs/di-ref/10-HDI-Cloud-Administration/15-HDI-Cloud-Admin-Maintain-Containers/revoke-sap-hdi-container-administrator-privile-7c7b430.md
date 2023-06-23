<!-- loio7c7b430bca764f68bdc19fc9c3ce6674 -->

# Revoke SAP HDI Container Administrator Privileges from a User

Disable administrator access to an SAP HDI container.



## Context

In SAP HANA Deployment Infrastructure \(HDI\), each HDI container can have its own set of administrators, and administrative privileges for an HDI container must be explicitly granted or revoked either by an HDI container-group administrator or by an HDI container administrator with the necessary privileges.

> ### Note:  
> The predefined table `_SYS_DI.T_DEFAULT_CONTAINER_ADMIN_PRIVILEGES` used in this task contains the largest possible set of privileges that can be granted for a user of this type. You can reduce the set of privileges granted by explicitly specifying the desired set of privileges and not using this default table.



<a name="loio7c7b430bca764f68bdc19fc9c3ce6674__steps_osn_qhd_l1b"/>

## Procedure

1.  In an SQL console, connect to the database with an administrator of the HDI container “C” \(or the name of the container whose administrator privileges you want to change\).

2.  Open the SQL editor for this database.

3.  Revoke container-administrator privileges from a user.

    Insert the following SQL code into the SQL editor:

    > ### Sample Code:  
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #PRIVILEGES LIKE _SYS_DI.TT_API_PRIVILEGES;
    > INSERT INTO #PRIVILEGES (PRINCIPAL_NAME, PRIVILEGE_NAME, OBJECT_NAME) SELECT 'NEW_CONTAINER_ADMIN', PRIVILEGE_NAME, OBJECT_NAME FROM _SYS_DI.T_DEFAULT_CONTAINER_ADMIN_PRIVILEGES WHERE NOT (PRIVILEGE_NAME = 'SELECT' AND OBJECT_NAME LIKE '_SYS_DI.T%');
    > CALL C#DI.REVOKE_CONTAINER_API_PRIVILEGES(#PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > DROP TABLE #PRIVILEGES; 
    > ```

    1.  In the `INSERT` statement in line 2, adjust the name of the user “`NEW_CONTAINER_ADMIN`” to reflect the name of the user from whom the API privileges should be revoked.

    2.  In the `CALL` statement in line 3, adjust the name of the container's API schema `C#DI` to suit your needs.


4.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

5.  \(Optional\) Confirm that the `NEW_CONTAINER_ADMIN` user is no longer able to call HDI container API procedures in the containers API schema \(for example, `C#DI` in container “C”\).


**Related Information**  


[Maintaining SAP HDI Containers](maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

[Grant SAP HDI Container Administrator Privileges to a User](grant-sap-hdi-container-administrator-privileg-8bad1a8.md "Enable administrator access to an SAP HDI container.")

