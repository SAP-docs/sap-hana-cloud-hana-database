<!-- loioc59c1123811d4a4c8e81490de26b78df -->

# Revoke SAP HDI Container Administrator Privileges from a User

In SAP HANA Deployment Infrastructure \(HDI\), administrator privileges for HDI containers can be revoked from a user at any time.



## Context

Each container can have its own set of administrators. Administrative privileges for a container must be explicitly granted or revoked by an HDI container group administrator, or an HDI container administrator with the necessary privileges.

> ### Note:  
> This method uses the predefined table `_SYS_DI.T_DEFAULT_CONTAINER_ADMIN_PRIVILEGES`, which contains the largest possible set of privileges that can be granted for a user of this type. You can reduce the set of privileges granted to a user by explicitly specifying the desired set of privileges and not using this default table.



<a name="loioc59c1123811d4a4c8e81490de26b78df__steps_nxw_fsx_k1b"/>

## Procedure

1.  In an SQL console, connect to the database as the administrator of the HDI container group whose privileges you want to change.

    In this example, the container group name is “G”. You will have to change the name of the container group \(G\) and the name of the container \(C\) used in this example to reflect the names of the containers and container groups in your landscape.

2.  Open the SQL editor for this database.

3.  Insert the following SQL code into the editor:

    > ### Sample Code:  
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #PRIVILEGES LIKE _SYS_DI.TT_API_PRIVILEGES;
    > INSERT INTO #PRIVILEGES (PRINCIPAL_NAME, PRIVILEGE_NAME, OBJECT_NAME) SELECT 'NEW_CONTAINER_ADMIN', PRIVILEGE_NAME, OBJECT_NAME FROM _SYS_DI.T_DEFAULT_CONTAINER_ADMIN_PRIVILEGES WHERE NOT (PRIVILEGE_NAME = 'SELECT' AND OBJECT_NAME LIKE '_SYS_DI.T%');
    > CALL _SYS_DI#G.REVOKE_CONTAINER_API_PRIVILEGES('C', #PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > DROP TABLE #PRIVILEGES; 
    > ```

4.  Adjust the name of the user `NEW_CONTAINER_ADMIN` in the `INSERT` statement in line 2 to reflect the name of the user from whom the API privileges should be revoked. In the `CALL` statement in line 3, you will also have to change the name of the container group “G” in the API schema `_SYS_DI#G` and the name of the container “C” to reflect the names in your landscape.

5.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

6.  \(Optional\) Confirm that the `NEW_CONTAINER_ADMIN` user is no longer able to call HDI container API procedures in the container C's API schema `C#DI`.


**Related Information**  


[Maintaining SAP HDI Container Groups](maintaining-sap-hdi-container-groups-4e9d597.md "The administrator of an SAP HDI container group is responsible for managing the SAP HDI containers that are organized into one or more HDI container groups.")

[Grant SAP HDI Container Administrator Privileges to a User](grant-sap-hdi-container-administrator-pr-468d01d.md "In SAP HANA Deployment Infrastructure (HDI), administrator privileges for HDI containers can be granted to another user at any time.")

