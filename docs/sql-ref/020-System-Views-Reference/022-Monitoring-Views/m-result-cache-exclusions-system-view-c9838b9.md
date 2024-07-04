<!-- loioc9838b90a48a46cc92db1c18fa7bcb98 -->

# M\_RESULT\_CACHE\_EXCLUSIONS System View

Provides information about result cache exclusions.



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

Displays the name of the results cache.

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

REASON

</td>
<td valign="top">

NVARCHAR\(1024\)

</td>
<td valign="top">

Displays the reason why the object cannot use result cache.

</td>
</tr>
<tr>
<td valign="top">

EXCLUDE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the timestamp when disabling the result cache was decided.

</td>
</tr>
</table>

**Related Information**  


[M\_RESULT\_CACHE System View](m-result-cache-system-view-71e6d97.md "Provides result cache information.")

[RESULT\_CACHE System View](../021-System-Views/result-cache-system-view-ae7b365.md "Provides information about objects available to use the result cache.")

[RESULT\_CACHE\_COLUMNS System View](../021-System-Views/result-cache-columns-system-view-6fa00dc.md "Provides information about columns available to use the result cache.")

[ALTER SYSTEM REFRESH RESULT CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-refresh-result-cache-statement-system-management-9d274fa.md "Refreshes all result cache entries related to the specified object with up-to-date results.")

[ALTER SYSTEM REFRESH RESULT CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-refresh-result-cache-entry-statement-system-management-1ab0dbb.md "Refreshes the specified result cache entry.")

[ALTER SYSTEM REMOVE RESULT CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-remove-result-cache-entry-statement-system-management-2124566.md "Removes the result cache entry for the specified cache ID.")

[ALTER SYSTEM CLEAR RESULT CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-result-cache-statement-system-management-97dca93.md "Removes all result cache entries from the system.")

[Procedure Result Cache](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/23bd07d4f4a1444ab64ca580373e8efc.html "Procedure Result Cache (PRC) is a server-wide in-memory cache that caches the output arguments of procedure calls using the input arguments as keys.") :arrow_upper_right:

[Deterministic Procedure Cache](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/8809a2a02e1b49d9a3fc68bb135f430d.html "") :arrow_upper_right:

[M\_RESULT\_CACHE\_RESET System View](m-result-cache-reset-system-view-7a3e046.md "Provides information about result cache statistics.")

