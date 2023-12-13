<!-- loiob41f6b2680e84a69bd57209860a7b0b1 -->

# M\_MVCC\_SNAPSHOTS System View

Provides detailed snapshot information of the Multiversion Concurrency Control \(MVCC\) manager.



<a name="loiob41f6b2680e84a69bd57209860a7b0b1___m__m_v_c_c__s_n_a_p_s_h_o_t_s_1struct_M_MVCC_SNAPSHOTS"/>

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

TRANSACTION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the associated transaction object ID.

</td>
</tr>
<tr>
<td valign="top">

MVCC\_SNAPSHOT\_TIMESTAMP

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the MVCC timestamp of the snapshot.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the associated logical statement ID.

</td>
</tr>
<tr>
<td valign="top">

RELATED\_TABLES

</td>
<td valign="top">

NVARCHAR\(1024\)

</td>
<td valign="top">

Displays the associated table object IDs.

</td>
</tr>
</table>

**Related Information**  


[CURRENT\_MVCC\_SNAPSHOT\_TIMESTAMP Function \(Datetime\)](../../010-SQL-Reference/011-SQL-Functions/current-mvcc-snapshot-timestamp-function-datetime-f15c8a4.md "Returns the timestamp of the current MVCC snapshot in SSSS format (seconds past midnight).")

[M\_MVCC\_OVERVIEW System View](m-mvcc-overview-system-view-f405b73.md "Provides an overview of the row-store Multiversion Concurrency Control (MVCC) manager.")

[M\_MVCC\_TABLES System View](m-mvcc-tables-system-view-20b5e31.md "Provides statistics for the row-store Multiversion Concurrency Control (MVCC) manager.")

[M\_SNAPSHOTS System View](m-snapshots-system-view-20c5439.md "Provides information about existing snapshots.")

[M\_TABLE\_SNAPSHOTS System View](m-table-snapshots-system-view-f413b69.md "Provides snapshot information for tables that are blocked by table-wise GC.")

[M\_TRANS\_TOKENS System View](m-trans-tokens-system-view-f760316.md "Provides information about all active transaction tokens.")

