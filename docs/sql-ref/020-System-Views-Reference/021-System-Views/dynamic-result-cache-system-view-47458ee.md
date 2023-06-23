<!-- loio47458ee33b2548e1926de800935db464 -->

# DYNAMIC\_RESULT\_CACHE System View

Provides information about metadata objects that are enabled for a dynamic result cache.



<a name="loio47458ee33b2548e1926de800935db464__section_tlc_pn2_b1b"/>

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

CACHE\_TYPE



</td>
<td valign="top">

NVARCHAR\(44\)



</td>
<td valign="top">

Displays which type of cache is enabled for the object: FULL, PARTIAL \(SELECTED COLUMNS\), PARTIAL \(FILTERED\), PARTIAL \(SELECTED COLUMNS, FILTERED\).



</td>
</tr>
<tr>
<td valign="top">

CACHE\_FILTER



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays the filter condition specified to reduce the cache size.



</td>
</tr>
<tr>
<td valign="top">

CACHE\_LOCATIONS



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

Displays the cache entry locations.



</td>
</tr>
<tr>
<td valign="top">

IS\_VALID



</td>
<td valign="top">

NVARCHAR \(5\)



</td>
<td valign="top">

Specifies whether the dynamic result cache is valid or not. A result cache becomes invalid \(FALSE\) when its base objects are changed or dropped.



</td>
</tr>
</table>

**Related Information**  


[M\_DYNAMIC\_RESULT\_CACHE System View](../022-Monitoring-Views/m-dynamic-result-cache-system-view-01f8a85.md "Lists statistics for the dynamic result cache.")

[M\_DYNAMIC\_RESULT\_CACHE\_EXCLUSIONS System View](../022-Monitoring-Views/m-dynamic-result-cache-exclusions-system-view-e5a5b84.md "Lists cache exclusions of the dynamic result cache.")

[DYNAMIC\_RESULT\_CACHE\_INDEX\_COLUMNS System View](dynamic-result-cache-index-columns-system-view-4790ff8.md "Provides information about the indexes of dynamic result caches.")

[ALTER SYSTEM REMOVE RESULT CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-remove-result-cache-entry-statement-system-management-2124566.md "Removes the result cache entry for the specified cache ID.")

[ALTER SYSTEM CLEAR RESULT CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-result-cache-statement-system-management-97dca93.md "Removes all result cache entries from the system.")

