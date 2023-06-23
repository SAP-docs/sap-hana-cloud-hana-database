<!-- loio439e8471a8df46f090fbb16ec6cfcc5d -->

# M\_CS\_LOB\_SPACE\_RECLAIMS System View

Provides information regarding executed LOB garbage collection runs.



<a name="loio439e8471a8df46f090fbb16ec6cfcc5d___m__t_a_b_l_e__l_o_b__f_i_l_e_s_1struct_M_CS_LOB_SPACE_RECLAIMS"/>

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

Unit



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

 



</td>
<td valign="top">

Displays the name of the host.



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

 



</td>
<td valign="top">

Displays the internal port.



</td>
</tr>
<tr>
<td valign="top">

VOLUME\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

 



</td>
<td valign="top">

Displays the persistence volume ID.



</td>
</tr>
<tr>
<td valign="top">

COLLECTION\_SCOPE



</td>
<td valign="top">

NVARCHAR\(8\)



</td>
<td valign="top">

 



</td>
<td valign="top">

Displays the scope of the garbage collection run on either VOLUME, TABLES, or TABLE.



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

 



</td>
<td valign="top">

Displays the schema name of the scanned table if the scope is TABLE.



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

 



</td>
<td valign="top">

Displays the name of the scanned table if the scope is TABLE.



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

 



</td>
<td valign="top">

Displays the start TIMESTAMP of the garbage collection run.



</td>
</tr>
<tr>
<td valign="top">

END\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

 



</td>
<td valign="top">

Displays the end TIMESTAMP of the garbage collection run.



</td>
</tr>
<tr>
<td valign="top">

SCANNED\_COLUMNS\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Counter



</td>
<td valign="top">

Displays the number of overall scanned columns.



</td>
</tr>
<tr>
<td valign="top">

REMOVED\_FILE\_LOBS\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Counter



</td>
<td valign="top">

Displays the number of removed file LOBs.



</td>
</tr>
<tr>
<td valign="top">

REMOVED\_PACKED\_LOBS\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Counter



</td>
<td valign="top">

Displays the number of removed packed LOBs.



</td>
</tr>
<tr>
<td valign="top">

ERROR\_CODE



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

 



</td>
<td valign="top">

Displays the first error code if the execution fails. More details are available in the ERROR\_MESSAGE field.



</td>
</tr>
<tr>
<td valign="top">

ERROR\_MESSAGE



</td>
<td valign="top">

NVARCHAR\(2000\)



</td>
<td valign="top">

 



</td>
<td valign="top">

Displays the detailed error message.



</td>
</tr>
</table>

**Related Information**  


[ALTER SYSTEM RECLAIM LOB SPACE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-reclaim-lob-space-statement-system-management-a0b7235.md "Runs LOB garbage collection and removes any non-referenced LOB files.")

[HOST_CS_LOB_SPACE_RECLAIMS View (Embedded Statistics Service)](https://help.sap.com/viewer/323c57a017234d47a0e7da3e22345822/2023_2_QRC/en-US/10897f1b23ce40b5b1aeadec9960f568.html "Aggregated LOB garbage collection statistics per volume. This view contains information only for the last 42 days. The collection interval is 43200 seconds.") :arrow_upper_right:

[M\_GARBAGE\_COLLECTION\_STATISTICS System View](m-garbage-collection-statistics-system-view-20b04b8.md "Provides garbage collection and history manager statistics.")

[Hybrid LOBs (Large Objects)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/61ab21a1972846e0aa0b9a989ce4867a.html "To save memory you can store LOB data on disk, in this case the data is only loaded into memory when it is needed. Alternatively, you can use the configurable Hybrid LOB feature which is flexible and stores LOBs either on disk or in memory depending on their size.") :arrow_upper_right:

