<!-- loio97e6309d643d4423869b95b71bf93cf8 -->

# Grant Container-Group Administrator Privileges to a User

Container-group administrator privileges can be granted to another user at any time.



## Context

Each container group can have its own set of administrators. Administrative privileges for a container group must be explicitly granted by an HDI administrator, or the container group's administrator. Unlike the HDI administrator, the container-group administrator can only grant another user the container group administrator privileges for their own container groups.

This method uses the predefined `_SYS_DI.T_DEFAULT_CONTAINER_GROUP_ADMIN_PRIVILEGES` table, which contains the largest possible set of privileges that can be granted for a user of this type. However, it is possible to reduce the set of privileges granted by specifying the desired set of privileges explicitly and not using this default table.

> ### Tip:  
> The procedure `_SYS_DI#G.GRANT_CONTAINER_GROUP_API_PRIVILEGES_WITH_GRANT_OPTION` can also be used; it grants the given privileges “`WITH GRANT OPTION`” to the target user. This procedure is only needed in special scenarios, for example, when building a custom SQL API by wrapping the HDI SQL API in SQLScript procedures.



<a name="loio97e6309d643d4423869b95b71bf93cf8__steps_nxw_fsx_k1b"/>

## Procedure

1.  In an SQL console, connect to the database with an HDI administrator user.

2.  Open the SQL editor for this database.

3.  Insert the following SQL code into the SQL editor:

    > ### Sample Code:  
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #PRIVILEGES LIKE _SYS_DI.TT_API_PRIVILEGES;
    > INSERT INTO #PRIVILEGES (PRINCIPAL_NAME, PRIVILEGE_NAME, OBJECT_NAME) SELECT '<container_group_admin_username>', PRIVILEGE_NAME, OBJECT_NAME FROM _SYS_DI.T_DEFAULT_CONTAINER_GROUP_ADMIN_PRIVILEGES;
    > CALL _SYS_DI#<container_group_name>.GRANT_CONTAINER_GROUP_API_PRIVILEGES(#PRIVILEGES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?); 
    > DROP TABLE #PRIVILEGES; 
    > ```

4.  Replace the name of the user *<container\_group\_admin\_username\>* in the `INSERT` command in line 2 with the name of the user to whom the container-group admin API privileges should be granted, and in line 3 replace *<container\_group\_name\>* with the name of the container group for which you want to grant administrator privileges.

5.  Execute the SQL code.

6.  \(Optional\) Confirm that the *<container\_group\_admin\_username\>* user is now able to call HDI API procedures in the container group *<container\_group\_name\>*'s API schema <code>_SYS_DI#<i class="varname">&lt;container_group_name&gt;</i></code>, where *<container\_group\_name\>* is replaced with the name of your HDI container group.


**Related Information**  


[Maintaining SAP HDI Container Groups](maintaining-sap-hdi-container-groups-4e9d597.md "The administrator of an SAP HDI container group is responsible for managing the SAP HDI containers that are organized into one or more HDI container groups.")

[Revoke SAP HDI Container-Group Administrator Privileges from an Administrator User](revoke-sap-hdi-container-group-administr-f4c000c.md "In SAP HANA Deployment Infrastructure (HDI), HDI container-group administration privileges can be revoked from a user at any time.")

