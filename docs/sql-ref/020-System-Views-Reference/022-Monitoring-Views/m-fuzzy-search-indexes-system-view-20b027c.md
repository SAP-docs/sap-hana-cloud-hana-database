<!-- loio20b027ca75191014a424a892c83e9c8f -->

# M\_FUZZY\_SEARCH\_INDEXES System View

Provides runtime information of fuzzy search indexes of column tables.



<a name="loio20b027ca75191014a424a892c83e9c8f___m__f_u_z_z_y__s_e_a_r_c_h__i_n_d_e_x_e_s_1struct_M_FUZZY_SEARCH_INDEXES"/>

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

Displays the internal port number.

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

INDEX\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the index.

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

PART\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the partition ID. Returns the following:

-   For partitioned tables, the part ID is equal to the sequential number of the partition, starting at 1.
-   In the case of replicated tables, the part ID is 1 for the original table and subsequent part IDs are assigned to replica tables.
-   The part ID is 0 for tables that are not partitioned.
-   A part ID value of -1 indicates that a modification of the table schema is in progress.



</td>
</tr>
<tr>
<td valign="top">

FUZZY\_SEARCH\_MODE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the fuzzy index search mode.

</td>
</tr>
<tr>
<td valign="top">

MIME\_TYPE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the MIME type of the fuzzy search index \(with search mode TEXT only\).

</td>
</tr>
<tr>
<td valign="top">

TOKEN\_SEPARATORS

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the token separators of the fuzzy search index \(with search mode TEXT only\).

</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE\_IN\_TOTAL

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the sum of MEMORY\_SIZE\_IN\_MAIN and MEMORY\_SIZE\_IN\_DELTA in bytes.

</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE\_IN\_MAIN

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current size of the fuzzy search indexes in main in bytes. This value is 0 if not loaded.

</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE\_IN\_DELTA

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current size of the fuzzy search indexes in delta, in bytes. This value is 0 if not loaded.

</td>
</tr>
<tr>
<td valign="top">

LOADED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays a flag to indicate that tge column is loaded into memory: TRUE/FALSE.

</td>
</tr>
</table>



<a name="loio20b027ca75191014a424a892c83e9c8f__section_ljz_zkj_wbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.



<a name="loio20b027ca75191014a424a892c83e9c8f___m__f_u_z_z_y__s_e_a_r_c_h__i_n_d_e_x_e_s_1fulldesc_M_FUZZY_SEARCH_INDEXES"/>

## Additional Information

This view shows the memory usage of all fuzzy search indexes. A fuzzy search index has no name and is identified by its schema name, table name, and column name.

**Related Information**  


[INDEXES System View](../021-System-Views/indexes-system-view-20a7044.md "Provides information about indexes on tables.")

