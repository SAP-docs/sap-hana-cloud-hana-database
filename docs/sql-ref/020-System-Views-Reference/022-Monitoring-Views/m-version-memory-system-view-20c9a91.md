<!-- loio20c9a9107519101494baf9f078eada01 -->

# M\_VERSION\_MEMORY System View

Provides information about memory use of the row-store Multiversion Concurrency Control \(MVCC\) manager.



<a name="loio20c9a9107519101494baf9f078eada01___m__v_e_r_s_i_o_n__m_e_m_o_r_y_1struct_M_VERSION_MEMORY"/>

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

ALLOCATED\_MEMORY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size of memory allocated for row-store version space in bytes.



</td>
</tr>
<tr>
<td valign="top">

USED\_MEMORY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size of memory actually used by row-store versions in bytes.



</td>
</tr>
<tr>
<td valign="top">

RECLAIMED\_VERSION\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size of memory reclaimed by row-store version garbage collection in bytes.



</td>
</tr>
<tr>
<td valign="top">

FREE\_MEMORY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size of memory freed and reusable in row-store version space in bytes.



</td>
</tr>
</table>

**Related Information**  


[M\_SYSTEM\_REPLICATION\_MVCC\_HISTORY System View](m-system-replication-mvcc-history-system-view-73bc68f.md "Displays the global multi-version concurrency control (MVCC) timestamp history in the secondary site for system replication. The global MVCC timestamp of the secondary site is updated after a chunk of logs from the primary site is replayed on the secondary site.")

[CURRENT\_MVCC\_SNAPSHOT\_TIMESTAMP Function \(Datetime\)](../../010-SQL-Reference/011-SQL-Functions/current-mvcc-snapshot-timestamp-function-datetime-f15c8a4.md "Returns the timestamp of the current MVCC snapshot in SSSS format (seconds past midnight).")

[M\_CS\_MVCC System View](m-cs-mvcc-system-view-890cead.md "Provides column store MVCC information.")

[M\_MVCC\_SNAPSHOTS System View](m-mvcc-snapshots-system-view-b41f6b2.md "Provides detailed snapshot information of the Multiversion Concurrency Control (MVCC) manager.")

[M\_MVCC\_OVERVIEW System View](m-mvcc-overview-system-view-f405b73.md "Provides an overview of the row-store Multiversion Concurrency Control (MVCC) manager.")

[M\_MVCC\_TABLES System View](m-mvcc-tables-system-view-20b5e31.md "Provides statistics for the row-store Multiversion Concurrency Control (MVCC) manager.")

