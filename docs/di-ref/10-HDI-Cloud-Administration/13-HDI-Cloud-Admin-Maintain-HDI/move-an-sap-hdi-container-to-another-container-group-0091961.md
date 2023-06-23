<!-- loio00919612198f4f1898f0ec01875d052f -->

# Move an SAP HDI Container to Another Container Group

The SAP HANA Deployment Infrastructure \(HDI\) administrator can move an HDI container to another container group.



## Procedure

1.  In an SQL console, connect to the database as the HDI administrator.

2.  Move the specified container to the new target container group.

    Insert the following SQL statement into the SQL console:

    ```sql
    CALL _SYS_DI.MOVE_CONTAINER_TO_GROUP('<container_to_be_moved>', '<target_container_group>', _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    ```

3.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

4.  Using the `M_ALL_CONTAINERS` monitoring view, check that *<container\_group\_to\_be\_moved\>* has the container group *<target\_container\_group\>* assigned in the CONTAINER\_GROUP\_NAME column.


