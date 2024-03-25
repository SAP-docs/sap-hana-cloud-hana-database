<!-- loioe5a5b8401be54a49a55f7799e59d564f -->

# M\_DYNAMIC\_RESULT\_CACHE\_EXCLUSIONS System View

Lists cache exclusions of the dynamic result cache.



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

Displays the schema name that the dynamic result cache entry belongs to.

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

Displays the object name that the dynamic result cache entry belongs to.

</td>
</tr>
<tr>
<td valign="top">

DETAILS

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Lists all constituents of the excluded cache key.

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

Displays the size, in bytes, of the memory occupied by the excluded cache entry.

</td>
</tr>
<tr>
<td valign="top">

RECORD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of records in the excluded cache entry.

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

Displays the timestamp when the dynamic result cache entry was decided.

</td>
</tr>
</table>



## Additional Information

Cache entries that exceed configurable size \(defined in the `.ini` file\) are automatically removed and added to M\_DYNAMIC\_RESULT\_CACHE\_EXCLUSION. If the view is marked to be excluded, then redefine the view definition rather than increasing the configurable size.

**Related Information**  


[M\_DYNAMIC\_RESULT\_CACHE System View](m-dynamic-result-cache-system-view-01f8a85.md "Lists statistics for the dynamic result cache.")

[DYNAMIC\_RESULT\_CACHE System View](../021-System-Views/dynamic-result-cache-system-view-47458ee.md "Provides information about metadata objects that are enabled for a dynamic result cache.")

[DYNAMIC\_RESULT\_CACHE\_INDEX\_COLUMNS System View](../021-System-Views/dynamic-result-cache-index-columns-system-view-4790ff8.md "Provides information about the indexes of dynamic result caches.")

[ALTER SYSTEM CLEAR RESULT CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-result-cache-statement-system-management-97dca93.md "Removes all result cache entries from the system.")

[ALTER SYSTEM REMOVE RESULT CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-remove-result-cache-entry-statement-system-management-2124566.md "Removes the result cache entry for the specified cache ID.")

[Results Caching for Virtual Tables and Linked Database](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/7dc806a729c64cd589f0d58d3b77aae1.html "Only view results caching is supported for virtual tables and linked database.") :arrow_upper_right:

