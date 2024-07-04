<!-- loio20c527c67519101488b3c64dadb9afdd -->

# M\_SHARED\_MEMORY System View

Provides shared memory usage information for the SAP HANA indexserver.



<a name="loio20c527c67519101488b3c64dadb9afdd___m__s_h_a_r_e_d__m_e_m_o_r_y_1struct_M_SHARED_MEMORY"/>

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

Displays the allocated shared memory size on the module in bytes.

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

Displays the used shared memory size on the module in bytes.

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

Displays the free shared memory size on the module in bytes.

</td>
</tr>
</table>

**Related Information**  


[M\_SERVICE\_MEMORY System View](m-service-memory-system-view-20bf33c.md "Displays detailed memory utilization information by services.")

[Memory Sizing](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/bdf26308bb571014b7bcd3bcd586aecd.html "Memory sizing is the process of estimating in advance the amount of memory that will be required to run a certain workload on an SAP HANA database. To understand memory sizing, several questions need to be answered.") :arrow_upper_right:

[SAP HANA Used Memory](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/8d277dcc98a94784a4375c029d19d088.html "The total amount of memory used by SAP HANA is referred to as used memory. It includes program code and stack, all data and system tables, and the memory required for temporary computations.") :arrow_upper_right:

