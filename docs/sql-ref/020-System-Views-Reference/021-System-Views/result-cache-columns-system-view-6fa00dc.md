<!-- loio6fa00dc34248473987f6241abd9ea454 -->

# RESULT\_CACHE\_COLUMNS System View

Provides information about columns available to use the result cache.



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

SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name.

</td>
</tr>
<tr>
<td valign="top">

CACHE\_NAME

</td>
<td valign="top">

NVARCHAR \(256\)

</td>
<td valign="top">

Displays the name of the result cache.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the object name.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the object type.

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

Displays the column name.

</td>
</tr>
<tr>
<td valign="top">

CACHE\_AGGREGATION\_TYPE

</td>
<td valign="top">

NVARCHAR\(20\)

</td>
<td valign="top">

Indicates the required aggregation type in a query to use cache or indicate an aggregation type for caching the column. Supported aggregation types: SUM, MIN, MAX, or COUNT.

</td>
</tr>
</table>



<a name="loio6fa00dc34248473987f6241abd9ea454__section_avm_j1p_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[RESULT\_CACHE System View](result-cache-system-view-ae7b365.md "Provides information about objects available to use the result cache.")

[M\_RESULT\_CACHE System View](../022-Monitoring-Views/m-result-cache-system-view-71e6d97.md "Provides result cache information.")

[M\_RESULT\_CACHE\_RESET System View](../022-Monitoring-Views/m-result-cache-reset-system-view-7a3e046.md "Provides information about result cache statistics.")

[M\_RESULT\_CACHE\_EXCLUSIONS System View](../022-Monitoring-Views/m-result-cache-exclusions-system-view-c9838b9.md "Provides information about result cache exclusions.")

[ALTER SYSTEM CLEAR RESULT CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-result-cache-statement-system-management-97dca93.md "Removes all result cache entries from the system.")

[ALTER SYSTEM REMOVE RESULT CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-remove-result-cache-entry-statement-system-management-2124566.md "Removes the result cache entry for the specified cache ID.")

[ALTER SYSTEM REFRESH RESULT CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-refresh-result-cache-entry-statement-system-management-1ab0dbb.md "Refreshes the specified result cache entry.")

[ALTER SYSTEM REFRESH RESULT CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-refresh-result-cache-statement-system-management-9d274fa.md "Refreshes all result cache entries related to the specified object with up-to-date results.")

[Results Caching for Virtual Tables and Linked Database](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_3_QRC/en-US/7dc806a729c64cd589f0d58d3b77aae1.html "Only view results caching is supported for virtual tables and linked database.") :arrow_upper_right:

[Procedure Result Cache](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/23bd07d4f4a1444ab64ca580373e8efc.html "Procedure Result Cache (PRC) is a server-wide in-memory cache that caches the output arguments of procedure calls using the input arguments as keys.") :arrow_upper_right:

[Deterministic Procedure Cache](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/8809a2a02e1b49d9a3fc68bb135f430d.html "") :arrow_upper_right:

