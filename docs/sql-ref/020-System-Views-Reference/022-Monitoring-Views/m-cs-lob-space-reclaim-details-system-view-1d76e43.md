<!-- loio1d76e4337d44442683e5c971f095b293 -->

# M\_CS\_LOB\_SPACE\_RECLAIM\_DETAILS System View

Provides detailed statistics per LOB owner for LOB garbage collection runs.



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

RECLAIM\_EXECUTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

 

</td>
<td valign="top">

Displays the unique ID of the garbage collection run.

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

Displays the schema name of the table the operation was run on.

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

Displays the name of the table the operation was run on.

</td>
</tr>
<tr>
<td valign="top">

COLUMN\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

 

</td>
<td valign="top">

Displays the column the operation was run on.

</td>
</tr>
<tr>
<td valign="top">

PART\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

 

</td>
<td valign="top">

Displays the table part ID the operation was run on.

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

Displays the start TIMESTAMP of the garbage collection operation.

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

Displays the end TIMESTAMP of the garbage collection operation.

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

Displays the number of file LOBs removed by the operation.

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

Displays the number of packed LOBs removed by the operation.

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



<a name="loio1d76e4337d44442683e5c971f095b293__section_r5q_zn1_rzb"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_CS\_LOB\_SPACE\_RECLAIMS System View](m-cs-lob-space-reclaims-system-view-439e847.md "Provides information regarding executed LOB garbage collection runs.")

[ALTER SYSTEM RECLAIM LOB SPACE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-reclaim-lob-space-statement-system-management-a0b7235.md "Runs LOB garbage collection and removes any non-referenced LOB files.")

[HOST_CS_LOB_SPACE_RECLAIMS View (Embedded Statistics Service)](https://help.sap.com/viewer/323c57a017234d47a0e7da3e22345822/2024_3_QRC/en-US/10897f1b23ce40b5b1aeadec9960f568.html "Aggregated LOB garbage collection statistics per volume. This view contains information only for the last 42 days. The collection interval is 43200 seconds.") :arrow_upper_right:

[M\_GARBAGE\_COLLECTION\_STATISTICS System View](m-garbage-collection-statistics-system-view-20b04b8.md "Provides garbage collection and history manager statistics.")

[Hybrid LOBs (Large Objects)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/61ab21a1972846e0aa0b9a989ce4867a.html "To save memory you can store LOB data on disk, in this case the data is only loaded into memory when it is needed. Alternatively, you can use the configurable Hybrid LOB feature which is flexible and stores LOBs either on disk or in memory depending on their size.") :arrow_upper_right:

