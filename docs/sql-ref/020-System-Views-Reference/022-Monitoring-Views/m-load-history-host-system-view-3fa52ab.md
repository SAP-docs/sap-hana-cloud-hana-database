<!-- loio3fa52abf1d854edbb7342a69364bcb0e -->

# M\_LOAD\_HISTORY\_HOST System View

Host specific load history KPIs.



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

TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the KPI collection timestamp.



</td>
</tr>
<tr>
<td valign="top">

CPU



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the percent of CPU used by all processes.



</td>
</tr>
<tr>
<td valign="top">

MEMORY\_RESIDENT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the physical memory used for all SAP HANA processes in bytes.



</td>
</tr>
<tr>
<td valign="top">

MEMORY\_TOTAL\_RESIDENT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the physical memory used for all processes in bytes.



</td>
</tr>
<tr>
<td valign="top">

MEMORY\_USED



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the memory used for all SAP HANA processes in bytes.



</td>
</tr>
<tr>
<td valign="top">

MEMORY\_ALLOCATION\_LIMIT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the memory allocation limit for all processes of an SAP HANA instance in bytes.



</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the physical memory size in bytes.



</td>
</tr>
<tr>
<td valign="top">

DISK\_USED



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the amount of disk used in bytes.



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

Displays the disk size in bytes.



</td>
</tr>
<tr>
<td valign="top">

NETWORK\_IN



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the bytes read from network by all processes in bytes per sample.



</td>
</tr>
<tr>
<td valign="top">

NETWORK\_OUT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the bytes written to network by all processes in bytes per sample.



</td>
</tr>
<tr>
<td valign="top">

SWAP\_IN



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the bytes read from swap by all processes in bytes per sample.



</td>
</tr>
<tr>
<td valign="top">

SWAP\_OUT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the bytes written to swap by all processes in bytes per sample.



</td>
</tr>
</table>

**Related Information**  


[M\_LOAD\_HISTORY\_INFO System View](m-load-history-info-system-view-2148ede.md "Load history KPI description.")

[M\_LOAD\_HISTORY\_SERVICE System View](m-load-history-service-system-view-261022b.md "Lists service-specific load history KPIs.")

[LOAD Statement \(Data Manipulation\)](../../010-SQL-Reference/012-SQL-Statements/load-statement-data-manipulation-20f83c8.md "Explicitly loads column store table data into memory instead of upon first access.")

[PERSISTENCE\_HISTORY System View](../021-System-Views/persistence-history-system-view-a8cb93e.md "Records the database version history.")

