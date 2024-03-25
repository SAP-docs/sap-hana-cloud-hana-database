<!-- loio00919612198f4f1898f0ec01875d052f -->

# Move an SAP HDI Container to Another Container Group

The SAP HANA Deployment Infrastructure \(HDI\) administrator can move an HDI container to another container group.



<a name="loio00919612198f4f1898f0ec01875d052f__context_okg_1b3_m1c"/>

## Context

HDI administrators and container-group administrators can move HDI containers between HDI container groups for which they are responsible.

> ### Caution:  
> It is not recommended to change the default container-group assignment of an HDI container that is managed by an SAP BTP service instance. For example, containers created by or in the SAP BTP Cockpit should not be moved from the default container group to which they are assigned on creation.



## Procedure

1.  In an SQL console, connect to the database as the HDI administrator.

2.  Move the specified container to the new target container group.

    Insert the following SQL statement into the SQL console:

    ```sql
    CALL _SYS_DI.MOVE_CONTAINER_TO_GROUP('<container_to_be_moved>', '<target_container_group>', _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    ```

    > ### Tip:  
    > Replace *<container\_to\_be\_moved\>* and *<target\_container\_group\>* in the `CALL` command with the name of the container you want to move and the name of the target container group to move it to, respectively.

3.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

4.  Using the `M_ALL_CONTAINERS` monitoring view, check that *<container\_to\_be\_moved\>* has the container group *<target\_container\_group\>* assigned in the CONTAINER\_GROUP\_NAME column.

    > ### Tip:  
    > For more information, see *Related Information* below.


**Related Information**  


[M\_ALL\_CONTAINERS](m-all-containers-61ce5ab.md "Shows all HDI containers that are assigned to an HDI container group.")

