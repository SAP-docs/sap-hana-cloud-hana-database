<!-- loio2d7c6952032940b8ae06bb60766094cf -->

# M\_TABLE\_PERSISTENCE\_LOCATION\_STATISTICS System View

Provides persistence storage statistics for tables partitions and services.



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

Displays the table partition ID:

-   For partitioned tables, the part ID is equal to the sequential number of the partition, starting at 1.
-   In the case of replicated tables, the part ID is 1 for the original table and subsequent part IDs are assigned to replica tables.
-   The part ID is 0 for tables that are not partitioned.
-   A part ID value of -1 indicates that the table schema is currently in being modified.



</td>
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

DISK\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total disk size, in bytes, of all table parts.



</td>
</tr>
<tr>
<td valign="top">

PAGE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total number of pages of all table parts.



</td>
</tr>
<tr>
<td valign="top">

BYTES\_WRITTEN



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of bytes written to the table.



</td>
</tr>
<tr>
<td valign="top">

BYTES\_APPENDED



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of bytes appended to the table.



</td>
</tr>
<tr>
<td valign="top">

BYTES\_READ



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of bytes read from the table.



</td>
</tr>
<tr>
<td valign="top">

BYTESTREAM\_WRITTEN



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of bytes written to the table via the streaming interface.



</td>
</tr>
<tr>
<td valign="top">

APPEND\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of times the table was appended to.



</td>
</tr>
<tr>
<td valign="top">

WRITE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of times the table was written to.



</td>
</tr>
<tr>
<td valign="top">

OPTIMIZE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of times the table was written to be optimized.



</td>
</tr>
<tr>
<td valign="top">

READ\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of times the table was read from.



</td>
</tr>
<tr>
<td valign="top">

TRUNCATE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of times the table was truncated.



</td>
</tr>
<tr>
<td valign="top">

COPY\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of times the table was copied.



</td>
</tr>
</table>

**Related Information**  


[M\_TABLE\_PERSISTENCE\_STATISTICS System View](m-table-persistence-statistics-system-view-20c6fa5.md "Provides persistence summary statistics for tables.")

[M\_EXPENSIVE\_STATEMENT\_EXECUTION\_LOCATION\_STATISTICS System View](m-expensive-statement-execution-location-statistics-system-view-80c32e9.md "Provides location statistics for expensive statements.")

