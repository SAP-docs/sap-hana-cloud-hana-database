<!-- loiof4a7c5e74e254ed1bcae843ac3d5d188 -->

# M\_JOIN\_TRANSLATION\_TABLES System View

Provides column store join engine translation tables statistics.



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

SCHEMA\_NAME1

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the first schema name.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_NAME1

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the first table name.

</td>
</tr>
<tr>
<td valign="top">

COLUMN\_NAME1

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the first table's column name.

</td>
</tr>
<tr>
<td valign="top">

PART\_ID1

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the first table partition ID. Returns the following:

-   For partitioned tables, the part ID is equal to the sequential number of the partition, starting at 1.
-   In the case of replicated tables, the part ID is 1 for the original table and subsequent part IDs are assigned to replica tables.
-   The part ID is 0 for tables that are not partitioned.
-   A part ID value of -1 indicates that a modification of the table schema is in progress.



</td>
</tr>
<tr>
<td valign="top">

VERSION1

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the version information of the first table.

</td>
</tr>
<tr>
<td valign="top">

SCHEMA\_NAME2

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the second schema name.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_NAME2

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the second table name.

</td>
</tr>
<tr>
<td valign="top">

COLUMN\_NAME2

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the second table's column name.

</td>
</tr>
<tr>
<td valign="top">

PART\_ID2

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the second table partition ID. Returns the following:

-   For partitioned tables, the part ID is equal to the sequential number of the partition, starting at 1.
-   In the case of replicated tables, the part ID is 1 for the original table and subsequent part IDs are assigned to replica tables.
-   The part ID is 0 for tables that are not partitioned.
-   A part ID value of -1 indicates that a modification of the table schema is in progress.



</td>
</tr>
<tr>
<td valign="top">

VERSION2

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the version information of the second table.

</td>
</tr>
<tr>
<td valign="top">

IMPLEMENTATION\_TYPE

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays the implementation type.

</td>
</tr>
<tr>
<td valign="top">

IMPLEMENTATION\_TYPE\_CHANGE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last time that the implementation type was changed.

</td>
</tr>
<tr>
<td valign="top">

IMPLEMENTATION\_TYPE\_CHANGE\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of implementation type changes.

</td>
</tr>
<tr>
<td valign="top">

VALUE\_ID\_COUNT1

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of translated value IDs of the first table.

</td>
</tr>
<tr>
<td valign="top">

VALUE\_ID\_COUNT2

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of translated value IDs of the second table.

</td>
</tr>
<tr>
<td valign="top">

TRANSLATION\_TABLE\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the memory used by the translation table in bytes.

</td>
</tr>
<tr>
<td valign="top">

ESTIMATED\_HASHMAP\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the estimated memory used by the HASHMAP implementation in bytes.

</td>
</tr>
<tr>
<td valign="top">

ESTIMATED\_VECTOR\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the estimated memory used by the vector implementation in bytes.

</td>
</tr>
<tr>
<td valign="top">

LAST\_USED\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the counter to support LRU cache replacement algorithm.

</td>
</tr>
</table>

**Related Information**  


[M\_JOINENGINE\_STATISTICS System View](m-joinengine-statistics-system-view-c847a34.md "Provides statistics about join engine runtime objects used for column store join operations.")

[M\_JOIN\_DATA\_STATISTICS System View](m-join-data-statistics-system-view-528de29.md "Provides column store join engine join statistics.")

