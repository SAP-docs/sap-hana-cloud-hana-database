<!-- loio36a5547af0304ee29e964abf27468f52 -->

# Export an SAP HDI Container for Copy Purposes

An HDI container can be exported to a table, which can then be used to import the container into a database.



<a name="loio36a5547af0304ee29e964abf27468f52__prereq_ux4_zbq_sqb"/>

## Prerequisites

-   If the exported HDI container has any dependencies to other HDI containers or normal database schemas, then the other containers and schemas must also be made available in the target database first.
-   If the exported HDI container has been granted privileges to other containers or schemas, the granted privileges must also be assigned in the database before you import the dependent HDI container.
-   The tables in the schema of the exported container must not be larger than 2GB.
-   You have the `CREATE ANY` privileges in the schema where you want to create the `EXPORT_TABLE`.

> ### Note:  
> While an export or import operation is running, it is not possible to run any other HDI API on the affected HDI container.



## Context

The export of a source container, for example, `C1`, is performed by calling the built-in procedure `_SYS_DI#G.EXPORT_CONTAINER_FOR_COPY`, where "G" is the name of the HDI container group. The procedure expects as inputs the name of the source container, the schema, and the names of two tables: the table into which the export data will be written \(`EXPORT_TABLE`\), and a table containing any parameters. After the export procedure has completed successfully, the specified table contains not only the objects of the source container’s API schema \(`C1#DI`\) but also the deployed objects of the source container’s run-time schema \(`C1`\), including all dependent data.

To export a container `C1` in container group `G` for copy purposes, perform the following steps:



## Procedure

1.  Open an SQL console and connect to the SAP HANA database with the permissions of the administrator of the HDI container group `G`.

2.  Open the SQL editor for this database.

3.  Paste the following SQL code into the SQL editor.

    If the exported container depends on other containers, you need to export those other containers, too.

    > ### Note:  
    > You need the `CREATE ANY` permission in the schema *<MySchema\>* where the `EXPORT_TABLE`, is created.

    ```sql
    CREATE COLUMN TABLE <MySchema>.EXPORT_TABLE LIKE _SYS_DI.TT_CONTAINER_EXPORT;
    GRANT INSERT ON <MySchema>.EXPORT_TABLE TO C1#DI;
    GRANT SELECT ON <MySchema>.EXPORT_TABLE TO C1#DI;
    CALL _SYS_DI#G.EXPORT_CONTAINER_FOR_COPY
      ('C1', <MySchema>, 'EXPORT_TABLE', _SYS_DI.T_NO_PARAMETERS, ?, ?, ?); 
    ```

    1.  If necessary, modify the name of the container `C1` to the name of the source container you are exporting from.

    2.  If necessary, change the name of the target table \(“`EXPORT_TABLE`” in the example above\) to the name of the table that should receive the exported container. A check is performed to establish if `EXPORT_TABLE` exists. If it exists, has the correct format, and is empty, then the export operation runs. Otherwise, an error is returned.

        > ### Restriction:  
        > The target table cannot be a temporary table.


4.  Execute the SQL code, and check that the operation completed successfully \(HDI return code 0\).

5.  Confirm that the container has been exported to the <code><i class="varname">&lt;MySchema&gt;</i>.EXPORT_TABLE</code>.


**Related Information**  


[Maintaining SAP HDI Container Groups](maintaining-sap-hdi-container-groups-4e9d597.md "The administrator of an SAP HDI container group is responsible for managing the SAP HDI containers that are organized into one or more HDI container groups.")

[Import an SAP HDI Container for Copy Purposes](import-an-sap-hdi-container-for-copy-pur-905a7b3.md "An HDI container can be imported into the same (or another) database from a table.")

