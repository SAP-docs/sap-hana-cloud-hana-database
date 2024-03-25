<!-- loio14905bf0250c4c019abf9dd6a32c7083 -->

# M\_CS\_COLUMNS\_PERSISTENCE System View

Provides column persistence information for column tables.



## Structure


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the host name.

</td>
</tr>
<tr>
<td valign="top">

PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the internal port.

</td>
</tr>
<tr>
<td valign="top">

SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the table name.

</td>
</tr>
<tr>
<td valign="top">

PART\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Returns the table partition ID:

-   For partitioned tables, the part ID is equal to the sequential number of the partition, starting at 1.
-   For replicated tables, the part ID is 1 for the original table and subsequent part IDs are assigned to replica tables.
-   The part ID is 0 for tables that are not partitioned.
-   A part ID value of -1 indicates that a modification of the table schema is currently in progress.



</td>
</tr>
<tr>
<td valign="top">

COLUMN\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the numeric column ID.

</td>
</tr>
<tr>
<td valign="top">

COLUMN\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the column name.

</td>
</tr>
<tr>
<td valign="top">

PERSISTENCE\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the type of column persistence: SINGLE, PAGED, VIRTUAL\_FILE, or VIRTUAL\_PAGED.

</td>
</tr>
<tr>
<td valign="top">

MAIN\_PHYSICAL\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the storage size, in bytes, used by the column.

</td>
</tr>
<tr>
<td valign="top">

MAIN\_PHYSICAL\_SIZE\_IN\_PAGE\_LOADABLE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total on-disk size stored in a page-loadable format for the table in bytes.

</td>
</tr>
</table>

**Related Information**  


[M\_CS\_COLUMNS System View](m-cs-columns-system-view-20ad197.md "Provides runtime information about columns in column tables.")

[M\_CS\_ALL\_COLUMNS System View](m-cs-all-columns-system-view-20acf4c.md "Provides runtime information for all columns in column tables, including internal column tables.")

[M\_CS\_ALL\_COLUMN\_STATISTICS System View](m-cs-all-column-statistics-system-view-2cb5b77.md "Provides information on how many scans and index searches were performed on any specified columns.")

[Memory Management in the Column Store](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/bd6e6be8bb5710149e34e14608e07b76.html "The column store is the part of the SAP HANA database that manages data organized in columns in memory. Tables created as column tables are stored here.") :arrow_upper_right:

