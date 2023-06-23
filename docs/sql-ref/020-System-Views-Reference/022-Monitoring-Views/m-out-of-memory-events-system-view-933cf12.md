<!-- loio933cf12f60f840868bd1224063416253 -->

# M\_OUT\_OF\_MEMORY\_EVENTS System View

Provides a list of the last 20 out-of-memory \(OOM\) events.



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

NVARCHAR \(64\)



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

TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the time of the OOM event.



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

Displays the connection ID.



</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_ID



</td>
<td valign="top">

NVARCHAR \(20\)



</td>
<td valign="top">

Displays the statement ID.



</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_HASH



</td>
<td valign="top">

NVARCHAR \(32\)



</td>
<td valign="top">

Displays the identifier for an SQL string.



</td>
</tr>
<tr>
<td valign="top">

WORKLOAD\_CLASS\_NAME



</td>
<td valign="top">

NVARCHAR \(256\)



</td>
<td valign="top">

Displays the name of the effective workload class



</td>
</tr>
<tr>
<td valign="top">

HEAP\_MEMORY\_CATEGORY



</td>
<td valign="top">

NVARCHAR \(128\)



</td>
<td valign="top">

Displays the allocator name in case of a heap memory failure.



</td>
</tr>
<tr>
<td valign="top">

MEMORY\_REQUEST\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size, in bytes, of the failed memory allocation.



</td>
</tr>
<tr>
<td valign="top">

MEMORY\_USED\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size, in bytes, currently allocated. This value depends on the EVENT\_REASON.



</td>
</tr>
<tr>
<td valign="top">

EVENT\_REASON



</td>
<td valign="top">

NVARCHAR \(32\)



</td>
<td valign="top">

Displays the reason for the OOM event: GLOBAL ALLOCATION LIMIT, PROCESS ALLOCATION LIMIT, or STATEMENT MEMORY LIMIT.



</td>
</tr>
<tr>
<td valign="top">

MEMORY\_LIMIT\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size of the limit in bytes. This value depends on the EVENT\_REASON.



</td>
</tr>
<tr>
<td valign="top">

TRACEFILE\_NAME



</td>
<td valign="top">

NVARCHAR \(256\)



</td>
<td valign="top">

Displays the OOM trace file name.



</td>
</tr>
</table>

**Related Information**  


[SAP HANA Used Memory](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/8d277dcc98a94784a4375c029d19d088.html "The total amount of memory used by SAP HANA is referred to as used memory. It includes program code and stack, all data and system tables, and the memory required for temporary computations.") :arrow_upper_right:

