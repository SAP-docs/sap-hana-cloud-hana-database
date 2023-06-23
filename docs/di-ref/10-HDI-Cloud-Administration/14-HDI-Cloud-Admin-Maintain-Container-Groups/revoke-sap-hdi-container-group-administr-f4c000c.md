<!-- loiof4c000ceb39841d891a170db17bd2397 -->

# Revoke SAP HDI Container-Group Administrator Privileges from an Administrator User

In SAP HANA Deployment Infrastructure \(HDI\), HDI container-group administration privileges can be revoked from a user at any time.



## Context

Each container group can have its own set of administrators. Administrative privileges for a container group must be explicitly granted and revoked by an HDI administrator, or a container-group's own administrator. Unlike the HDI administrator, the container-group administrator can only revoke container-group administrator privileges from another user for their own container groups.

> ### Tip:  
> This method uses the predefined table `_SYS_DI.T_DEFAULT_CONTAINER_GROUP_ADMIN_PRIVILEGES`, which contains the largest possible set of privileges that can be granted for a user of this type. However, it is possible to reduce the set of privileges granted by specifying the desired set of privileges individually and explicitly instead.



<a name="loiof4c000ceb39841d891a170db17bd2397__steps_nxw_fsx_k1b"/>

## Procedure

1.  In an SQL console, connect to the database with an HDI administrator user.

2.  Open the SQL editor for this database.

3.  Revoke the container-group administrator privileges.

    Insert the following SQL code into the SQL editor:

    > ### Sample Code:  
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #PRIVILEGES LIKE _SYS_DI.TT_API_PRIVILEGES;
    > INSERT INTO #PRIVILEGES (PRINCIPAL_NAME, PRIVILEGE_NAME, OBJECT_NAME) SELECT 'OTHER_CONTAINER_GROUP_ADMIN', PRIVILEGE_NAME, OBJECT_NAME FROM _SYS_DI.T_DEFAULT_CONTAINER_GROUP_ADMIN_PRIVILEGES WHERE NOT (PRIVILEGE_NAME = 'SELECT' AND OBJECT_NAME LIKE '_SYS_DI.T%');
    > CALL _SYS_DI#G.REVOKE_CONTAINER_GROUP_API_PRIVILEGES(#PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > DROP TABLE #PRIVILEGES; 
    > ```

    1.  Adjust the name of the user `OTHER_CONTAINER_GROUP_ADMIN` in the `INSERT` statement in line 2 to reflect the name of the user from whom the API privileges should be revoked, and the name of the container group “G” in the `CALL` statement in line 3 to correspond with the name of your container group.


4.  Execute the SQL code.

    Check that the code completes successfully with the HDI return code 0.

5.  \(Optional\) Confirm that the `OTHER_CONTAINER_GROUP_ADMIN` user is no longer able to call HDI API procedures in the container group “G”'s API schema `_SYS_DI#G`, where “G” is replaced with the name of your HDI container group.


**Related Information**  


[Maintaining SAP HDI Container Groups](maintaining-sap-hdi-container-groups-4e9d597.md "The administrator of an SAP HDI container group is responsible for managing the SAP HDI containers that are organized into one or more HDI container groups.")

[Grant Container-Group Administrator Privileges to a User](grant-container-group-administrator-priv-97e6309.md "Container-group administrator privileges can be granted to another user at any time.")

