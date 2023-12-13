<!-- loio4790ff85fecc4656a72bf59895c8c8de -->

# DYNAMIC\_RESULT\_CACHE\_INDEX\_COLUMNS System View

Provides information about the indexes of dynamic result caches.



<a name="loio4790ff85fecc4656a72bf59895c8c8de__section_tlc_pn2_b1b"/>

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

OBJECT\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID.

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

Displays the name of the indexed column.

</td>
</tr>
</table>



<a name="loio4790ff85fecc4656a72bf59895c8c8de__section_lhc_f2q_bzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[DYNAMIC\_RESULT\_CACHE System View](dynamic-result-cache-system-view-47458ee.md "Provides information about metadata objects that are enabled for a dynamic result cache.")

[M\_DYNAMIC\_RESULT\_CACHE System View](../022-Monitoring-Views/m-dynamic-result-cache-system-view-01f8a85.md "Lists statistics for the dynamic result cache.")

[M\_DYNAMIC\_RESULT\_CACHE\_EXCLUSIONS System View](../022-Monitoring-Views/m-dynamic-result-cache-exclusions-system-view-e5a5b84.md "Lists cache exclusions of the dynamic result cache.")

[ALTER SYSTEM REMOVE RESULT CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-remove-result-cache-entry-statement-system-management-2124566.md "Removes the result cache entry for the specified cache ID.")

[ALTER SYSTEM CLEAR RESULT CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-result-cache-statement-system-management-97dca93.md "Removes all result cache entries from the system.")

