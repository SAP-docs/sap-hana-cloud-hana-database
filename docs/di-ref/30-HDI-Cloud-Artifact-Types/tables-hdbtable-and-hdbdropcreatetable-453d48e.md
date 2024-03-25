<!-- loio453d48e28f6747799546236b4b432e58 -->

# Tables \(.hdbtable and .hdbdropcreatetable\)

Transforms a design-time table resource into a table database object.



The table plug-ins transform a design-time table resource \(defined in `.hdbtable` or `.hdbdropcreatetable` artifacts\) into a table database object.

The Table plug-in uses a data migration component which transforms an already deployed version of the table into the new structure of the table. The necessary migration steps for the table structure are determined automatically based on changes to the design-time definition of the table. This transformation always uses a temporary shadow table into which the existing data is copied to match the new structure. For the duration of the copy operation, the source table is protected by means of an exclusive lock that prevents access by any other user until the lock is released again, which could in some situtations lead to a lock-wait time-out. Since the copy operation can be very costly for tables that contain a lot of data, the use of the migration-table \(`.hdbmigrationtable`\) plug-in should be considered. For smaller tables containing, for example, configuration data, this cost is usually negligible.

> ### Note:  
> It is possible to switch from `.hdbmigrationtable` to `.hdbtable`. For more information about how to switch formats, see *Switching from `.hdbmigrationtable` to `.hdbtable`* below.

The drop-create-table plug-in does not provide any data migration. A changed table definition will drop an already deployed version of the table on deployment and then recreate the table. If the table contains any data, this is not allowed, since the data would be lost.

The file format required for the `.hdbtable` and `.hdbdropcreatetable` artifacts uses a DDL-style syntax that is equivalent to the SQL syntax in the corresponding SQL command `CREATE TABLE`, without the leading “`CREATE`”, as illustrated in the following example.

> ### Note:  
> **Virtual** tables defined in the `.hdbvirtualtable` design-time artifact, which is handled by the virtual table build plug-in. Constraints on foreign keys are defined in the `.hdbconstraint` design-time artifacts, which are handled by the constraint build plug-in. In addition, these plug-ins cannot be used to set up a “system-versioned” table or application-time table. A separate plug-in is available for this purpose.

Partitioning of the table should only be specified or changed in the design-time table resource, since changes applied to the run-time table object would be lost each time the design-time table is redeployed.



### Switching from `.hdbmigrationtable` to `.hdbtable`

The following high-level steps show how to switch from `.hdbmigrationtable` to `.hdbtable`:

1.  Add a new design-time table artifact \(`hdbtable`\) to your database application project.
2.  Ensure that the new table artifact \(`hdbtable`\) has the same content as the existing `hdbmigrationtable` artifact in the application project.
3.  Add the name of \(and path to\) the `hdbmigrationtable` artifact to the undeploy allow list \(`undeploy.json`\).
4.  Delete the old design-time `hdbmigrationtable` artifact from the application project.
5.  Deploy the application.

For more information about the undeploy allow list \(`undeploy.json`\), see *Related Information* below.



<a name="loio453d48e28f6747799546236b4b432e58__section_ftw_523_1hb"/>

## Example Artifact Code

The following code shows a simple example of a table definition for SAP HDI:

> ### Code Syntax:  
> `/src/CUSTOMERS.hdbtable`
> 
> ```sql
> COLUMN TABLE "com.sap.hana.example::CUSTOMERS" ( 
>    "ID" INTEGER, 
>    "NAME" NVARCHAR(256),
>    "ACTIVE" TINYINT,
>    "COUNTRY" NVARCHAR(256),
>    PRIMARY KEY ("ID") )
> ```



### Example Artifact Code with Comments

Table and column comments can be defined in-place using the COMMENT keyword, as illustrated in the following code example:

> ### Code Syntax:  
> `/src/CUSTOMERS.hdbtable`
> 
> ```sql
> COLUMN TABLE "com.sap.hana.example::CUSTOMERS" ( 
>    "ID" INTEGER                COMMENT 'Customer ID',
>    "NAME" NVARCHAR(256)        COMMENT 'Customer Name',
>    "ACTIVE" TINYINT            COMMENT 'Currently active?',
>    "COUNTRY" NVARCHAR(256)     COMMENT 'Customer Country',
>    PRIMARY KEY ("ID") 
> )
> COMMENT 'Table with Customer data'
> ```



### Example Artifact Code with Associations

Tables support forward declarations for database-level associations using the `WITH ASSOCIATIONS` clause.

The table plug-ins create an additional intermediate “validate” artifact as part of the deployment. This “validate” artifact inserts itself between the table artifact, the artifacts which are referenced in the `WITH ASSOCIATIONS` clause, and the artifacts that consume the table artifact. The “validate” artifact validates the forward-declared associations and issues a warning in the event that an association is not valid.

The following code shows an example of a table definition with associations:

> ### Code Syntax:  
> `/src/CUSTOMERS.hdbtable`
> 
> ```sql
> COLUMN TABLE "com.sap.hana.example::CUSTOMERS" ( 
>    "ID" INTEGER, 
>    "NAME" NVARCHAR(256),
>    "ACTIVE" TINYINT,
>    "COUNTRY" NVARCHAR(256),
>    PRIMARY KEY ("ID") )
> 
> WITH ASSOCIATIONS 
> ( 
>   JOIN OTHER_TABLE 
>   AS 
>   TO_OTHER_TABLE 
>   ON ID = TO_OTHER_TABLE.ID 
> )
> ```



<a name="loio453d48e28f6747799546236b4b432e58__section_mbb_523_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbtable" : { 
>     "plugin_name" : "com.sap.hana.di.table"
> }, 
> "hdbdropcreatetable" : {
>     "plugin_name" : "com.sap.hana.di.dropcreatetable"
> }
> ```



<a name="loio453d48e28f6747799546236b4b432e58__section_x4v_s23_1hb"/>

## General Limitations

The following restrictions apply to the `.hdbtable` or `.hdbdropcreatetable` plug-ins:

-   You must specify the table **type**; permitted table types are `ROW` and `COLUMN`. The drop-create-table plug-ins also support global temporary tables with the types `GLOBAL TEMPORARY ROW` and `GLOBAL TEMPORARY COLUMN.` 

-   A table cannot reference another table:

    -   It is not possible to define a table by using another table \(for example, `TABLE A LIKE B`\)

    -   It is not possible to define a table based on a query \(for example, `TABLE A AS SELECT […] FROM B`\)


-   Flexible tables \(for example, using the `WITH SCHEMA FLEXIBILITY` clause\) and `HISTORY` tables are not supported.

-   Virtual tables are handled by the virtual-table build plug-in \(`.hdbvirtualtable`\).

-   Named constraints are not supported.

    Foreign-key constraints are handled by the constraint build plug-in \(`.hdbconstraint`\).

-   Client-side encryption \(`CLIENTSIDE ENCRYPTION`\) is not supported.

-   Table and column comments can be defined in-place using the `COMMENT` keyword.

-   Tables also support forward declarations for database-level associations via the `WITH ASSOCIATIONS` clause. The table plug-ins create an additional intermediate "validate" artifact as part of the deployment. This "validate" artifact will position itself between the table artifact, the artifacts which are referenced in the `WITH ASSOCIATIONS` clause, and the artifacts which consume the table artifact. The "validate" artifact attempts to validate the forward declared associations and will issue a warning if the association is not valid.

    > ### Note:  
    > The `.hdbtable` and `.hdbdropcreatetable` plug-ins cannot be used to set up either a system-versioned table or an application-time table. A separate plug-in is available for these purposes.




<a name="loio453d48e28f6747799546236b4b432e58__section_e2x_tqz_2wb"/>

## Fast Migration

To avoid the time and performance overheads involved when creating a shadow table, which can be extremely expensive when migrating larger tables, it is possible to migrate an `hdbtable` artifact by comparing source and target tables and automatically generating the `ALTER` statements required to transform the existing table to the new table definition. This fast migration is intended for simple changes such as those specified in the following list:

-   Changing the data type of a column
-   Changing the nullable or default value of a column
-   Adding or removing columns
-   Adding, removing, or changing partitioning
-   Adding, removing, or changing associations

For more complex changes, the migration falls back to the standard methog using data copy.

> ### Note:  
> The fast migration of an `hdbtable` artifact is only possible if the build parameter `try_fast_table_migration` for the HDI build plug-in `com.sap.hana.di.table` is set to "true". For more informartion, see *SAP HDI Parameters* in *Related Information* below.



### Special Handling and Limitations

When making use of the fast-migration feature for hdbtable artifacts, bear in mind the following information:

-   Changes to columns
    -   Cannot add a NOT NULL or primary key column without a default value
    -   Cannot add a unique column with a default value
    -   Cannot alter a column to `NOT NULL` 

-   Changes to data types:
    -   Character string data types, binary data types, and numeric data types:

        The following table shows which conversions are supported between character string data types, binary data types, and numeric data types:

        **HDI Data Type: Numeric Conversion in SAP HANA Cloud**


        <table>
        <tr>
        <th valign="top" align="right">

        Target type
        
        </th>
        <th valign="top" rowspan="2">

        TINYINT
        
        </th>
        <th valign="top" rowspan="2">

        SMALLINT
        
        </th>
        <th valign="top" rowspan="2">

        INTEGER
        
        </th>
        <th valign="top" rowspan="2">

        BIGINT
        
        </th>
        <th valign="top" rowspan="2">

        DECIMAL
        
        </th>
        <th valign="top" rowspan="2">

        DECIMAL\(*<p\>*,*<s\>*\)

        P: 1~38, S: 0~p
        
        </th>
        <th valign="top" rowspan="2">

        SMALLDECIMAL
        
        </th>
        <th valign="top" rowspan="2">

        REAL
        
        </th>
        <th valign="top" rowspan="2">

        DOUBLE
        
        </th>
        <th valign="top" rowspan="2">

        Character string type, or binary type
        
        </th>
        <th valign="top" rowspan="2">

        LOB
        
        </th>
        </tr>
        <tr>
        <th valign="top">

        Source type
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        TINYINT
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table: if p - s \>= 3
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table: if length \>= 3
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        SMALLINT
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table: if p - s \>= 5
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table: if length \>= 6
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        INTEGER
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table: if p - s \>= 10
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table: if length \>= 11
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        BIGINT
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table: if p - s \>= 19
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table: if length \>= 20
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        DECIMAL
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        DECIMAL\(*<p\>*,*<s\>*\)
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        Column table: if p'-s' \>= p-s && p'\>=p && s'\>=s \(p,s: source, p',s': target\)
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        Column table: if length \>= 41
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        SMALLDECIMAL
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        Column table: if length \>= 395
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        REAL
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table: if length \>= 20
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        DOUBLE
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table: if length \>= 24
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Character string type
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Binary type
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        

        
        </td>
        <td valign="top">
        

        
        </td>
        </tr>
        </table>
        
    -   Date and time data types

        The following table shows which conversions are supported between date and time data types:

        **HDI Data Type: Date and Time Conversion in SAP HANA Cloud**


        <table>
        <tr>
        <th valign="top" align="right">

        Target type
        
        </th>
        <th valign="top" rowspan="2">

        TIME
        
        </th>
        <th valign="top" rowspan="2">

        DATE
        
        </th>
        <th valign="top" rowspan="2">

        SECONDDATE
        
        </th>
        <th valign="top" rowspan="2">

        SECONDTIME
        
        </th>
        <th valign="top" rowspan="2">

        TIMESTAMP
        
        </th>
        <th valign="top" rowspan="2">

        Character string type, or binary type
        
        </th>
        <th valign="top" rowspan="2">

        LOB
        
        </th>
        </tr>
        <tr>
        <th valign="top">

        Source type
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        TIME
        
        </td>
        <td valign="top">
        
        Column table / Row table
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        Column table / Row table
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        Column table: if length \>= 8
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        DATE
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        Column table / Row table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table: if length \>= 10
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        SECONDDATE
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table / Row table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table: if length \>= 19
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        SECONDTIME
        
        </td>
        <td valign="top">
        
        Column table / Row table
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        Column table / Row table
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        Column table: if length \>= 8
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        TIMESTAMP
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table
        
        </td>
        <td valign="top">
        
        Column table / Row table
        
        </td>
        <td valign="top">
        
        Column table: if length \>= 27
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Character string type, or binary type
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        </tr>
        </table>
        
    -   Character-string data types:

        The following table shows which conversions are supported between character-string data types:

        **HDI Data Type: Character-string Conversion in SAP HANA Cloud**


        <table>
        <tr>
        <th valign="top" align="right">

        Target type
        
        </th>
        <th valign="top" rowspan="2">

        VARBINARY
        
        </th>
        <th valign="top" rowspan="2">

        CHAR or NCHAR
        
        </th>
        <th valign="top" rowspan="2">

        VARCHAR or NVARCHAR
        
        </th>
        <th valign="top" rowspan="2">

        NCLOB
        
        </th>
        <th valign="top" rowspan="2">

        BLOB
        
        </th>
        </tr>
        <tr>
        <th valign="top">

        Source type
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        VARBINARY
        
        </td>
        <td valign="top">
        
        Column table: if target length \>= source length
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        <td valign="top">
        
        Column table / Row table
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        CHAR or NCHAR
        
        </td>
        <td valign="top">
        
        Column table: if target length \>= \(source length \* 3\)
        
        </td>
        <td valign="top">
        
        Column table: if target length \>= source length
        
        </td>
        <td valign="top">
        
        Column table: if target length \>= source length
        
        </td>
        <td valign="top">
        
        Column table / Row table
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        VARCHAR or NVARCHAR
        
        </td>
        <td valign="top">
        
        Column table: if target length \>= \(source length \* 3\)
        
        </td>
        <td valign="top">
        
        Column table: if target length \>= source length
        
        </td>
        <td valign="top">
        
        if target\_length \>= source\_length
        
        </td>
        <td valign="top">
        
        Column table / Row table
        
        </td>
        <td valign="top">
        
        \-
        
        </td>
        </tr>
        </table>
        
    -   It is not possible to convert the LOB data type to any other data type.
    -   Supported conversions of multi-valued data types:
        -   Lower bound:

            The target type's lower bound should be lower than or equal to the source's type.

        -   Upper bound:

            The target type's upper bound should be higher than or equal to the source's type.

        -   It is not possible to alter 'with duplicates' to 'without duplicates'.
        -   For type conversion, the same rules apply as for the other data types.

    -   It is not possible to convert the spatial data types \(`ST_GEOMETRY`/`ST_POINT`\) to \(or from\) any other data type.

        It is not possible to modify the Spatial Reference System ID.

    -   It is not possible to convert the Boolean data type to \(or from\) any other data type.


**Related Information**  


[Table Data \(.hdbtabledata\)](table-data-hdbtabledata-35c4dd8.md "Insert data from other files (for example, CSV, .properties, or .tags files) into database tables.")

[Table Types \(.hdbtabletype\)](table-types-hdbtabletype-83275bd.md "Transforms a design-time table type resource into a table type database object.")

[Application Time-Period Tables \(.hdbapplicationtime \)](application-time-period-tables-hdbapplicationtime-73c7b80.md "Transforms a design-time application time-period table into a database table object with application-time period.")

[System Versioning Tables \(.hdbsystemversioning\)](system-versioning-tables-hdbsystemversioning-5794b34.md "Transforms a design-time, system-versioned table that refers to a current and history table into a system-versioned table database object.")

[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

[HDI Delta Deployment and Undeploy Allow List \(SAP HANA Cloud Database Developer Guide for Business App Studio\)](https://help.sap.com/docs/HANA_CLOUD_DATABASE/c2b99f19e9264c4d9ae9221b22f6f589/ebb0a1d1d41e4ab0a06ea951717e7d3d.html)

[SAP HDI Parameters](../10-HDI-Cloud-Administration/13-HDI-Cloud-Admin-Maintain-HDI/sap-hdi-parameters-e2d3e54.md "An overview of the parameters available for the SAP HANA Deployment Infrastructure (HDI) and the corresponding build plug-ins.")

