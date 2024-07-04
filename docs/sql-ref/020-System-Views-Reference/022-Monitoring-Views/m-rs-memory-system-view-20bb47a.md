<!-- loio20bb47a975191014b1e2f6bd0a685d7b -->

# M\_RS\_MEMORY System View

Provides RS memory statistics.



<a name="loio20bb47a975191014b1e2f6bd0a685d7b___m__r_s__m_e_m_o_r_y_1struct_M_RS_MEMORY"/>

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

CATEGORY

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the module name.

</td>
</tr>
<tr>
<td valign="top">

ALLOCATED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the allocated memory size of the module in bytes.

</td>
</tr>
<tr>
<td valign="top">

USED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the used memory size of the module in bytes.

</td>
</tr>
<tr>
<td valign="top">

FREE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the free memory size of the module in bytes

</td>
</tr>
</table>

**Related Information**  


[M\_RS\_INDEXES System View](m-rs-indexes-system-view-20bb03a.md "Provides the statistics for B-tree and CPB-tree indexes.")

[M\_RS\_TABLES System View](m-rs-tables-system-view-20bbc60.md "Provides information about row tables, including detailed table sizes and record count.")

[M\_RS\_TABLE\_VERSION\_STATISTICS System View](m-rs-table-version-statistics-system-view-20bb882.md "Provides information on row table versions: detailed version counts and used sizes.")

[Memory Sizing](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/bdf26308bb571014b7bcd3bcd586aecd.html "Memory sizing is the process of estimating in advance the amount of memory that will be required to run a certain workload on an SAP HANA database. To understand memory sizing, several questions need to be answered.") :arrow_upper_right:

[SAP HANA Used Memory](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/8d277dcc98a94784a4375c029d19d088.html "The total amount of memory used by SAP HANA is referred to as used memory. It includes program code and stack, all data and system tables, and the memory required for temporary computations.") :arrow_upper_right:

[Managing Memory by Object Usage](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/815fd19868d84c13962852faa3b1ee85.html "You can use the Unused Retention Period feature to automatically unload objects from memory which are not being used.") :arrow_upper_right:

