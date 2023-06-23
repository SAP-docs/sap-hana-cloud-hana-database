<!-- loio468d01d381644cc781185d568037ce93 -->

# Grant SAP HDI Container Administrator Privileges to a User

In SAP HANA Deployment Infrastructure \(HDI\), administrator privileges for HDI containers can be granted to another user at any time.



<a name="loio468d01d381644cc781185d568037ce93__context_pqc_v5x_k1b"/>

## Context

Each HDI container can have its own set of administrators. Administrative privileges for a container must be explicitly granted or revoked either by an HDI container-group administrator or an HDI-container administrator with the necessary privileges.

> ### Note:  
> This method uses the predefined table `_SYS_DI.T_DEFAULT_CONTAINER_ADMIN_PRIVILEGES`, which contains the largest possible set of privileges that can be granted for a user of this type. You can reduce the set of privileges granted to a user by explicitly specifying the desired set of privileges and not using this default table.



<a name="loio468d01d381644cc781185d568037ce93__steps_nxw_fsx_k1b"/>

## Procedure

1.  In an SQL console, connect to the database as the administrator of the target HDI container group \(for example, “G”\).

2.  Open the SQL editor for this database.

3.  Grant container-administrator privileges.

    Insert the following SQL code into the editor:

    > ### Sample Code:  
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #PRIVILEGES LIKE _SYS_DI.TT_API_PRIVILEGES; 
    > INSERT INTO #PRIVILEGES (PRINCIPAL_NAME, PRIVILEGE_NAME, OBJECT_NAME) SELECT 'NEW_CONTAINER_ADMIN', PRIVILEGE_NAME, OBJECT_NAME FROM _SYS_DI.T_DEFAULT_CONTAINER_ADMIN_PRIVILEGES; 
    > CALL _SYS_DI#G.GRANT_CONTAINER_API_PRIVILEGES('C', #PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?); 
    > DROP TABLE #PRIVILEGES;
    > ```

4.  Adjust the name of the user `NEW_CONTAINER_ADMIN` in the `INSERT` statement in line 2 to reflect the name of the user to whom the API privileges should be granted. You will also have to change the name of the container group “G” in the API schema `_SYS_DI#G` and the name of the container “C” to reflect the names in your landscape.

5.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

6.  \(Optional\) Confirm that the `NEW_CONTAINER_ADMIN` user is now able to call HDI container API procedures in the container C's API schema `C#DI`.


**Related Information**  


[Revoke SAP HDI Container Administrator Privileges from a User](revoke-sap-hdi-container-administrator-p-c59c112.md "In SAP HANA Deployment Infrastructure (HDI), administrator privileges for HDI containers can be revoked from a user at any time.")

[Maintaining SAP HDI Container Groups](maintaining-sap-hdi-container-groups-4e9d597.md "The administrator of an SAP HDI container group is responsible for managing the SAP HDI containers that are organized into one or more HDI container groups.")

