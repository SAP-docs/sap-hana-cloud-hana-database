<!-- loioa61db9d9086f4b8aab6484e2a487e7da -->

# Create an SAP HDI Container Group

In SAP HANA Deployment Infrastructure \(HDI\), an HDI container group is used for administrating a set of HDI containers. Each HDI container group can be managed by different \(HDI administrator\) users.



## Procedure

1.  In an SQL console, connect to the database as the HDI administrator.

2.  Insert the following SQL statement:

    ```sql
    CALL _SYS_DI.CREATE_CONTAINER_GROUP('<container_group_name>', _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    ```

    > ### Note:  
    > Replace the name of the container group *<container\_group\_name\>* in the SQL `CALL` statement with your container-group name

3.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

4.  Confirm that the new container group has been created.

    > ### Tip:  
    > The system view `_SYS_DI.M_ALL_CONTAINER_GROUPS` contains a list of **all** created HDI container groups. For more information, see *Related Information* below.


**Related Information**  


[M\_ALL\_CONTAINER\_GROUPS](m-all-container-groups-0f41f81.md "View all HDI container groups in the database.")

