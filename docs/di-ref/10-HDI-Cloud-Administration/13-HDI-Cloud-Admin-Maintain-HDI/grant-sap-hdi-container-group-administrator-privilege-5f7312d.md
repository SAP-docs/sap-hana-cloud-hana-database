<!-- loio5f7312d58b944e16a7e093f6ca0e8021 -->

# Grant SAP HDI Container-Group Administrator Privileges to Another User

An SAP HANA Deployment Infrastructure \(HDI\) administrator or a container-group administrator must explicitly grant administrative privileges for a container group.



## Context

Every HDI container group can have its own set of administrators. An HDI administrator can grant another user administrator privileges for **any** HDI container group, whereas an HDI container-group administrator can only grant another user the container-group administrator privileges for his \(or her\) own HDI container group. This method uses the predefined `_SYS_DI.T_DEFAULT_CONTAINER_GROUP_ADMIN_PRIVILEGES` table, which contains the largest possible set of privileges that can be granted for a user of this type. You can reduce the set of privileges granted by explicitly specifying the desired set of privileges and not using this default table.

> ### Note:  
> A variant of this procedure, `_SYS_DI.GRANT_CONTAINER_GROUP_API_PRIVILEGES_WITH_GRANT_OPTION`, also exists; it grants the specified privileges `WITH GRANT OPTION` to the target user. This variant is only needed in special scenarios, for example, when building a custom SQL API by wrapping the HDI SQL API in SQLScript procedures.



## Procedure

1.  In an SQL console, connect to the database as the HDI administrator.

2.  Grant container-group administrator privileges to a specified user.

    Insert the following SQL statement into the SQL console:

    ```sql
    CREATE LOCAL TEMPORARY COLUMN TABLE #PRIVILEGES LIKE _SYS_DI.TT_API_PRIVILEGES;
    INSERT INTO #PRIVILEGES (PRINCIPAL_NAME, PRIVILEGE_NAME, OBJECT_NAME) SELECT '<container_group_admin_username>', PRIVILEGE_NAME, OBJECT_NAME FROM _SYS_DI.T_DEFAULT_CONTAINER_GROUP_ADMIN_PRIVILEGES;
    CALL _SYS_DI.GRANT_CONTAINER_GROUP_API_PRIVILEGES('<container_group_name>', #PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    DROP TABLE #PRIVILEGES;
    
    ```

    > ### Tip:  
    > Replace the name of the user *<container\_group\_admin\_username\>* in the `INSERT` command in line 2 with the name of the user to whom the API privileges should be granted, and replace the name of the container group *<container\_group\_name\>* in the `CALL` command in line 3 with the name of the desired container group name.

3.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

4.  Confirm that the new container group administrator is able to call HDI API procedures in the API schema \_SYS\_DI\#*<container\_group\_name\>*.


