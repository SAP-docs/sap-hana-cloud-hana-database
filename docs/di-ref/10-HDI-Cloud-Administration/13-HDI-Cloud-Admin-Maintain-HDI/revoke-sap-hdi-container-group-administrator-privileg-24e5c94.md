<!-- loio24e5c94998c744ccb0148723d5e42b6d -->

# Revoke SAP HDI Container-Group Administrator Privileges from a Container Group Administrator

An SAP HANA Deployment Infrastructure \(HDI\) administrator can revoke administration privileges on any HDI container group from a user.



## Procedure

1.  In an SQL console, connect to the database as the HDI administrator.

2.  Revoke the specified container-group administrator privileges.

    Insert the following SQL statement into the SQL console:

    ```sql
    CREATE LOCAL TEMPORARY COLUMN TABLE #PRIVILEGES LIKE _SYS_DI.TT_API_PRIVILEGES;
    INSERT INTO #PRIVILEGES (PRINCIPAL_NAME, PRIVILEGE_NAME, OBJECT_NAME) SELECT 'NEW_CONTAINER_GROUP_ADMIN', PRIVILEGE_NAME, OBJECT_NAME FROM _SYS_DI.T_DEFAULT_CONTAINER_GROUP_ADMIN_PRIVILEGES WHERE NOT (PRIVILEGE_NAME = 'SELECT' AND OBJECT_NAME LIKE '_SYS_DI.T%'); 
    CALL _SYS_DI.REVOKE_CONTAINER_GROUP_API_PRIVILEGES('G', #PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    DROP TABLE #PRIVILEGES; 
    ```

    > ### Tip:  
    > Replace the name of the user *<NEW\_CONTAINER\_GROUP\_ADMIN\>* in `INSERT` command in line 2 with the name of the user from whom the API privileges should be revoked, and replace the name of the container group *<G\>* in the `CALL` command in line 3 with the name of the desired container group name.

3.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

4.  Confirm that the container group administrator is no longer able to call HDI API procedures in the API schema \_SYS\_DI\#*<container\_group\_name\>*.


**Related Information**  


[Maintaining SAP HDI Container Groups](../14-HDI-Cloud-Admin-Maintain-Container-Groups/maintaining-sap-hdi-container-groups-4e9d597.md "The administrator of an SAP HDI container group is responsible for managing the SAP HDI containers that are organized into one or more HDI container groups.")

[Grant Container-Group Administrator Privileges to a User](../14-HDI-Cloud-Admin-Maintain-Container-Groups/grant-container-group-administrator-priv-97e6309.md "Container-group administrator privileges can be granted to another user at any time.")

