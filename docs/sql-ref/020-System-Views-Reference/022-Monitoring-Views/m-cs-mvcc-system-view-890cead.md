<!-- loio890cead73dd24116ab40041b05123365 -->

# M\_CS\_MVCC System View

Provides column store MVCC information.



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

Displays the port number.

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

Displays the partition ID. Returns the following:

-   For partitioned tables, the part ID is equal to the sequential number of the partition, starting at 1.
-   In the case of replicated tables, the part ID is 1 for the original table and subsequent part IDs are assigned to replica tables.
-   The part ID is 0 for tables that are not partitioned.
-   A part ID value of -1 indicates that a modification of the table schema is in progress.



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

Indicates if the MVCC data is loaded into the memory.

</td>
</tr>
<tr>
<td valign="top">

FRAGMENT\_TYPE

</td>
<td valign="top">

NVARCHAR\(7\)

</td>
<td valign="top">

Displays the fragment type: DELTA1, DELTA2, or MAIN.

</td>
</tr>
<tr>
<td valign="top">

RECORD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of visible records in the table.

</td>
</tr>
<tr>
<td valign="top">

RAW\_RECORD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of physical records in the table.

</td>
</tr>
<tr>
<td valign="top">

ROWSTATE\_BLOCK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of active rowstate blocks.

</td>
</tr>
<tr>
<td valign="top">

CTS\_BLOCK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of blocks used to store creation timestamps \(CTS\).

</td>
</tr>
<tr>
<td valign="top">

DTS\_BLOCK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of blocks used to store deletion timestamps \(DTS\).

</td>
</tr>
<tr>
<td valign="top">

ROWSTATE\_STUB\_BLOCK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of stub blocks, both visible and invisible, present in the MVCC layer associated with the fragment.

</td>
</tr>
<tr>
<td valign="top">

VISIBLE\_ROWSTATE\_STUB\_BLOCK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of visible stub blocks present in the MVCC layer associated with the fragment.

</td>
</tr>
<tr>
<td valign="top">

CTS\_STUB\_BLOCK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of active CTS stub blocks.

</td>
</tr>
<tr>
<td valign="top">

DTS\_STUB\_BLOCK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of active DTS stub blocks.

</td>
</tr>
<tr>
<td valign="top">

FREE\_ROWSTATE\_BLOCK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of free row-state blocks available for successive operations.

</td>
</tr>
<tr>
<td valign="top">

FREE\_TS\_BLOCK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of free CTS/DTS blocks.

</td>
</tr>
<tr>
<td valign="top">

FREE\_TS\_STUB\_BLOCK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of free CTS/DTS stub blocks.

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

Displays the number of pages in the MVCC page chain.

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

If MVCC data is loaded, then it displays the total memory size of MVCC structures in bytes.

</td>
</tr>
<tr>
<td valign="top">

PAGE\_CHAIN\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

If MVCC data is loaded, then it displays the memory size of the pinned MVCC page chain in bytes.

</td>
</tr>
<tr>
<td valign="top">

PAGE\_CHAIN\_ACTIVE\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the memory size of the active part of the MVCC page chain in bytes.

</td>
</tr>
<tr>
<td valign="top">

ROWSTATE\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

If MVCC data is loaded, then it displays the memory size of transient rowstate structures in bytes.

</td>
</tr>
<tr>
<td valign="top">

CTS\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the amount of memory used to store CTS blocks in bytes.

</td>
</tr>
<tr>
<td valign="top">

DTS\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the amount of memory used to store DTS blocks in bytes.

</td>
</tr>
<tr>
<td valign="top">

MISC\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

If MVCC data is loaded, then it displays the memory size of miscellaneous MVCC related structures in bytes.

</td>
</tr>
<tr>
<td valign="top">

SPARSE\_DTS\_BLOCK\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of DTS blocks that are sparse timestamp blocks.

</td>
</tr>
<tr>
<td valign="top">

SPARSE\_DTS\_MEMORY\_SIZE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the memory size of the sparse block in bytes.

</td>
</tr>
<tr>
<td valign="top">

FREE\_SPARSE\_TS\_BLOCK\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of available sparse timestamp blocks for successive operations.

</td>
</tr>
</table>

**Related Information**  


[CURRENT\_MVCC\_SNAPSHOT\_TIMESTAMP Function \(Datetime\)](../../010-SQL-Reference/011-SQL-Functions/current-mvcc-snapshot-timestamp-function-datetime-f15c8a4.md "Returns the timestamp of the current MVCC snapshot in SSSS format (seconds past midnight).")

[M\_MVCC\_SNAPSHOTS System View](m-mvcc-snapshots-system-view-b41f6b2.md "Provides detailed snapshot information of the Multiversion Concurrency Control (MVCC) manager.")

[M\_MVCC\_OVERVIEW System View](m-mvcc-overview-system-view-f405b73.md "Provides an overview of the row-store Multiversion Concurrency Control (MVCC) manager.")

[HOST_MVCC_OVERVIEW View (Embedded Statistics Service)](https://help.sap.com/viewer/323c57a017234d47a0e7da3e22345822/2024_1_QRC/en-US/4ea7cb57d6954278ab2eee175705d144.html "Specifies the MVCC overview per host.") :arrow_upper_right:

[M\_MVCC\_TABLES System View](m-mvcc-tables-system-view-20b5e31.md "Provides statistics for the row-store Multiversion Concurrency Control (MVCC) manager.")

