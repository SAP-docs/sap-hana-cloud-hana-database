<!-- loiof405b73d6f5b10148407c80ee0de62bb -->

# M\_MVCC\_OVERVIEW System View

Provides an overview of the row-store Multiversion Concurrency Control \(MVCC\) manager.



<a name="loiof405b73d6f5b10148407c80ee0de62bb___m__m_v_c_c__o_v_e_r_v_i_e_w_1struct_M_MVCC_OVERVIEW"/>

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

VERSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of all versions in the host.

</td>
</tr>
<tr>
<td valign="top">

DATA\_VERSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of data versions per service.

</td>
</tr>
<tr>
<td valign="top">

METADATA\_VERSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of metadata versions per service.

</td>
</tr>
<tr>
<td valign="top">

MIN\_MVCC\_SNAPSHOT\_TIMESTAMP

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum MVCC timestamp which at least one transaction holds.

</td>
</tr>
<tr>
<td valign="top">

GLOBAL\_MVCC\_TIMESTAMP

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current global MVCC timestamp.

</td>
</tr>
<tr>
<td valign="top">

MIN\_READ\_TRANSACTION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Indicates that all active transactions can see the changes of TRANSACTION IDs less than or equal to MIN\_READ\_TRANSACTION\_ID.

</td>
</tr>
<tr>
<td valign="top">

MIN\_WRITE\_TRANSACTION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Indicates that all write transactions with a TRANSACTION ID less than or equal to MIN\_WRITE\_TRANSACTION\_ID are closed.

</td>
</tr>
<tr>
<td valign="top">

NEXT\_WRITE\_TRANSACTION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum TRANSACTION ID which is assigned to the next write transaction.

</td>
</tr>
<tr>
<td valign="top">

ACQUIRED\_LOCK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of acquired records locks.

</td>
</tr>
<tr>
<td valign="top">

MAX\_VERSIONS\_PER\_PARTITION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the max number of versions per partition.

</td>
</tr>
</table>

**Related Information**  


[M\_MVCC\_SNAPSHOTS System View](m-mvcc-snapshots-system-view-b41f6b2.md "Provides detailed snapshot information of the Multiversion Concurrency Control (MVCC) manager.")

[M\_MVCC\_TABLES System View](m-mvcc-tables-system-view-20b5e31.md "Provides statistics for the row-store Multiversion Concurrency Control (MVCC) manager.")

[M\_SYSTEM\_REPLICATION\_MVCC\_HISTORY System View](m-system-replication-mvcc-history-system-view-73bc68f.md "Displays the global multi-version concurrency control (MVCC) timestamp history in the secondary site for system replication. The global MVCC timestamp of the secondary site is updated after a chunk of logs from the primary site is replayed on the secondary site.")

[CURRENT\_MVCC\_SNAPSHOT\_TIMESTAMP Function \(Datetime\)](../../010-SQL-Reference/011-SQL-Functions/current-mvcc-snapshot-timestamp-function-datetime-f15c8a4.md "Returns the timestamp of the current MVCC snapshot in SSSS format (seconds past midnight).")

