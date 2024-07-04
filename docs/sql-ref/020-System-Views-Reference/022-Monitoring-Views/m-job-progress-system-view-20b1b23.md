<!-- loio20b1b238751910148e45c5be2837b57f -->

# M\_JOB\_PROGRESS System View

Provides information about current long running system operations.



<a name="loio20b1b238751910148e45c5be2837b57f___m__j_o_b__p_r_o_g_r_e_s_s_1struct_M_JOB_PROGRESS"/>

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

Displays the schema of the object.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the object.

</td>
</tr>
<tr>
<td valign="top">

JOB\_NAME

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the type of operation. See the table below for more detail.

</td>
</tr>
<tr>
<td valign="top">

CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the connection that triggered the operation.

</td>
</tr>
<tr>
<td valign="top">

START\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the start time of the operation.

</td>
</tr>
<tr>
<td valign="top">

CURRENT\_PROGRESS

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the steps of the operation that are already finished.

</td>
</tr>
<tr>
<td valign="top">

MAX\_PROGRESS

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the maximum operation progress.

</td>
</tr>
<tr>
<td valign="top">

PROGRESS\_DETAIL

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the detailed information about the operation.

</td>
</tr>
</table>



<a name="loio20b1b238751910148e45c5be2837b57f__section_e3f_zyz_xbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.



<a name="loio20b1b238751910148e45c5be2837b57f___m__j_o_b__p_r_o_g_r_e_s_s_1fulldesc_M_JOB_PROGRESS"/>

## Additional Information

The below table lists the possible types of job operations:


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

JOB\_NAME

</td>
<td valign="top">

-   Alter Column Load Unit: Convert/change load unit at the column level using NSE DDLs.

-   Alter Index Load Unit: Convert/change load unit at the index level using NSE DDLs.

-   Alter Partition Load Unit: Convert/change load unit at the partition level using NSE DDLs.

-   Alter Table Load Unit: Convert/change load unit at the table level using NSE DDLs.

-   BW F Fact Table Compression: fact table compression

-   Backup: data backup

-   Check Table Consistency: table consistency check

-   Column table reloading on startup: Column table reloading on startup

-   Create Index: index creation

-   DSO activation: dso activation

-   DSO conversion: dso conversion

-   DSO rollback: dso rollback

-   Data Statistics Autocreate: Automatic creation of data statistics

-   Export All: main export operation

-   Export Object: exporting data for an object invoked by 'Export All'

-   Import All: main import operation

-   Import Object: importing data for an object invoked by 'Import All'

-   Memory Profiler: load memory profiler data into tables

-   Move Table: table move

-   Online Repartitioning: allows DML workloads during DDL executions

-   Optimize Compression: optimize compression

-   Plan Stability: Execute all cached plans to capture

-   Re-partitioning: table split and merge operations

-   Row Store Reorganization: row storage reorganization

-   Runtimedump: Runtimedump

-   Save PerfTrace: saving performance trace

-   Savepoint Critical Phase: critical phase of savepoint

-   Savepoint: savepoint

-   Table Consistency Check: Table Consistency Checks \(Procedure CHECK\_TABLE\_CONSISTENCY\)

-   Table Redistribution Execute: table redistribution plan execution

-   Table Redistribution Generate: table redistribution plan generation

-   Table conversion \(Col to Row\): table type conversion from column to row store

-   Table conversion \(Row to Col\): table type conversion from row to column store




</td>
</tr>
</table>

**Related Information**  


[M\_JOB\_HISTORY\_INFO System View](m-job-history-info-system-view-6c9f04a.md "Provides a history of long running system operations.")

