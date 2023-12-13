<!-- loio20b5e315751910149709b4e5e7ad9f2c -->

# M\_MVCC\_TABLES System View

Provides statistics for the row-store Multiversion Concurrency Control \(MVCC\) manager.



<a name="loio20b5e315751910149709b4e5e7ad9f2c___m__m_v_c_c__t_a_b_l_e_s_1struct_M_MVCC_TABLES"/>

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

NAME

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

VALUE

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the value.

</td>
</tr>
</table>

**Related Information**  


[M\_MVCC\_OVERVIEW System View](m-mvcc-overview-system-view-f405b73.md "Provides an overview of the row-store Multiversion Concurrency Control (MVCC) manager.")

[M\_MVCC\_SNAPSHOTS System View](m-mvcc-snapshots-system-view-b41f6b2.md "Provides detailed snapshot information of the Multiversion Concurrency Control (MVCC) manager.")

[M\_TRANS\_TOKENS System View](m-trans-tokens-system-view-f760316.md "Provides information about all active transaction tokens.")

[Managing Tables](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/68554490aee94885ba31611489a04992.html "The SAP HANA database stores data in memory in tables, organized in columns, and partitions, distributed among multiple servers.") :arrow_upper_right:

