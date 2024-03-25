<!-- loio36a5547af0304ee29e964abf27468f52 -->

# Export an SAP HDI Container for Copy Purposes

An HDI container can be exported to a table, which can then be used to import the container into a database.



<a name="loio36a5547af0304ee29e964abf27468f52__prereq_ux4_zbq_sqb"/>

## Prerequisites

-   If the exported HDI container has any dependencies to other HDI containers or normal database schemas, then the other containers and schemas must also be made available in the target database first.
-   If the exported HDI container has been granted privileges to other containers or schemas, the granted privileges must also be assigned in the database before you import the dependent HDI container.
-   The tables in the schema of the exported container must not be larger than 2GB.
-   You have the `CREATE ANY` privileges in the schema where you want to create the table that contains the exported data.

> ### Note:  
> While an export or import operation is running, it is not possible to run any other HDI API on the affected HDI container.



## Context

The export of a source container is performed by calling the built-in procedure <code>_SYS_DI#<i class="varname">&lt;container_group_name&gt;</i>.EXPORT_CONTAINER_FOR_COPY</code>.

The procedure expects as inputs the name of the source container, the schema, and the names of two tables: the table into which the export data will be written \(for example, *<EXPORT\_TABLE\>*\), and a table containing any parameters. After the export procedure has completed successfully, the specified table contains not only the objects of the source container’s API schema \(<code><i class="varname">&lt;source_container_name&gt;</i>#DI</code>\) but also the deployed objects of the source container’s run-time schema \(*<source\_container\_name\>*\), including all dependent data.

To export a container *<source\_container\_name\>* in container group *<container\_group\_name\>* for copy purposes, perform the following steps:



## Procedure

1.  Open an SQL console and connect to the SAP HANA database with the permissions of the administrator of the HDI container group *<container\_group\_name\>*.

2.  Open the SQL editor for this database.

3.  Paste the following SQL code into the SQL editor.

    If the exported container depends on other containers, you need to export those other containers, too.

    > ### Note:  
    > You need the `CREATE ANY` permission in the schema *<MySchema\>* where the `EXPORT_TABLE`, is created.

    ```sql
    CREATE COLUMN TABLE <MySchema>.EXPORT_TABLE LIKE _SYS_DI.TT_CONTAINER_EXPORT;
    GRANT INSERT ON <MySchema>.EXPORT_TABLE TO <source_container_name>#DI;
    GRANT SELECT ON <MySchema>.EXPORT_TABLE TO <source_container_name>#DI;
    CALL _SYS_DI#<container_group_name>.EXPORT_CONTAINER_FOR_COPY
      ('<source_container_name>', '<MySchema>', 'EXPORT_TABLE', _SYS_DI.T_NO_PARAMETERS, ?, ?, ?); 
    ```

    1.  Replace *<source\_container\_name\>* with the name of the source container you are exporting from.

    2.  If necessary, replace *<MySchema\>* and `EXPORT_TABLE` in the example above with the name of the schema and table that should receive the exported container. A check is performed to establish if `EXPORT_TABLE` exists. If it exists, has the correct format, and is empty, then the export operation runs. Otherwise, an error is returned.

        > ### Restriction:  
        > The target table cannot be a temporary table.


4.  Execute the SQL code, and check that the operation completed successfully \(HDI return code 0\).

5.  Confirm that the container has been exported to the <code><i class="varname">&lt;MySchema&gt;</i>.<code>EXPORT_TABLE</code></code>.


**Related Information**  


[Maintaining SAP HDI Container Groups](maintaining-sap-hdi-container-groups-4e9d597.md "The administrator of an SAP HDI container group is responsible for managing the SAP HDI containers that are organized into one or more HDI container groups.")

[Import an SAP HDI Container for Copy Purposes](import-an-sap-hdi-container-for-copy-pur-905a7b3.md "An HDI container can be imported into the same (or another) database from a table.")

