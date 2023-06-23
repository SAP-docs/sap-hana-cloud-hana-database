<!-- loio71e6d97146b64d2595a6d3d8d520e6b9 -->

# M\_RESULT\_CACHE System View

Provides result cache information.



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

CACHE\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the unique ID for each result cache entry.



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

USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the user name.



</td>
</tr>
<tr>
<td valign="top">

DETAILS



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays the details.



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

Displays the size of memory occupied by the result cache entry in bytes.



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

Displays the number of records in the cache entry.



</td>
</tr>
<tr>
<td valign="top">

CREATE\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the timestamp the result cache entry is generated and stored.



</td>
</tr>
<tr>
<td valign="top">

LAST\_REFRESH\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the last refresh time of the result cache entry.



</td>
</tr>
<tr>
<td valign="top">

LAST\_REFRESH\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the time duration of the cache entry preparation in milliseconds.



</td>
</tr>
<tr>
<td valign="top">

REFRESH\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of refreshments on the cache entry.



</td>
</tr>
<tr>
<td valign="top">

LAST\_ACCESS\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the last time the result cache entry was accessed by a user.



</td>
</tr>
<tr>
<td valign="top">

ACCESS\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of accesses on the cache entry.



</td>
</tr>
<tr>
<td valign="top">

RUNTIME\_MISS\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of cache miss counts. This value is decided at runtime with parameter values.



</td>
</tr>
<tr>
<td valign="top">

EVICT\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total number of eviction counts due to budget limitations.



</td>
</tr>
<tr>
<td valign="top">

IS\_EVICTED



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether or not the cache entry is evicted: TRUE/FALSE.



</td>
</tr>
</table>

**Related Information**  


[M\_RESULT\_CACHE\_RESET System View](m-result-cache-reset-system-view-7a3e046.md "Provides information about result cache statistics.")

[M\_RESULT\_CACHE\_EXCLUSIONS System View](m-result-cache-exclusions-system-view-c9838b9.md "Provides information about result cache exclusions.")

[RESULT\_CACHE System View](../021-System-Views/result-cache-system-view-ae7b365.md "Provides information about objects available to use the result cache.")

[RESULT\_CACHE\_COLUMNS System View](../021-System-Views/result-cache-columns-system-view-6fa00dc.md "Provides information about columns available to use the result cache.")

[ALTER SYSTEM REFRESH RESULT CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-refresh-result-cache-statement-system-management-9d274fa.md "Refreshes all result cache entries related to the specified object with up-to-date results.")

[ALTER SYSTEM REFRESH RESULT CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-refresh-result-cache-entry-statement-system-management-1ab0dbb.md "Refreshes the specified result cache entry.")

[ALTER SYSTEM REMOVE RESULT CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-remove-result-cache-entry-statement-system-management-2124566.md "Removes the result cache entry for the specified cache ID.")

[ALTER SYSTEM CLEAR RESULT CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-result-cache-statement-system-management-97dca93.md "Removes all result cache entries from the system.")

[Procedure Result Cache](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/23bd07d4f4a1444ab64ca580373e8efc.html "Procedure Result Cache (PRC) is a server-wide in-memory cache that caches the output arguments of procedure calls using the input arguments as keys.") :arrow_upper_right:

[Deterministic Procedure Cache](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/8809a2a02e1b49d9a3fc68bb135f430d.html "") :arrow_upper_right:

