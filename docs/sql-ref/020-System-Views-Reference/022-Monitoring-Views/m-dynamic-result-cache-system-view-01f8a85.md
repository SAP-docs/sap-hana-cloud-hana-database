<!-- loio01f8a85aafd148d98e4a90431b694887 -->

# M\_DYNAMIC\_RESULT\_CACHE System View

Lists statistics for the dynamic result cache.



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

CACHE\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the unique ID for each dynamic result cache entry.

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

OBJECT\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the object type that the dynamic result cache entry belongs to.

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

Displays the details of all of the constituents of the cache key.

</td>
</tr>
<tr>
<td valign="top">

LAST\_MVCC\_SNAPSHOT\_TIMESTAMP

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last cached MVCC snapshot timestamp.

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

Displays the size, in bytes, of the memory occupied by the dynamic result cache entry.

</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE\_IN\_INDEX

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size, in bytes, of the memory occupied by the dynamic result cache entry's indexes.

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

DELTA\_RECORD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of records in the cache entry created by a delta refresh.

</td>
</tr>
<tr>
<td valign="top">

IS\_REFRESHING

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays the status of the asynchronous cache entry refresh job. The result is TRUE if the refresh job is currently running and FALSE otherwise.

</td>
</tr>
<tr>
<td valign="top">

CURRENT\_REFRESH\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the duration, in milliseconds, of the currently running cache entry refresh job. The value is 1 when IS\_REFRESHING is FALSE.

</td>
</tr>
<tr>
<td valign="top">

CURRENT\_REFRESH\_REASON

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the reason why the refresh job was triggered. The value is empty when IS\_REFRESHING is FALSE.

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

Displays the timestamp when the dynamic result cache entry was created.

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

Displays the timestamp when the last cache entry refresh job finished.

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

Displays the duration, in milliseconds, of the last cache entry refresh job.

</td>
</tr>
<tr>
<td valign="top">

LAST\_REFRESH\_REASON

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the reason why the last refresh job was triggered.

</td>
</tr>
<tr>
<td valign="top">

LAST\_DELTA\_REFRESH\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the timestamp when the last delta refresh on the cache entry finished.

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

Displays the timestamp of the last cache entry access.

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

Displays the number of refreshes on the cache entry.

</td>
</tr>
<tr>
<td valign="top">

DELTA\_REFRESH\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of delta refreshes on the cache entry.

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

Displays the number of read accesses on the cache entry.

</td>
</tr>
<tr>
<td valign="top">

MISS\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of cache miss read accesses on the cache entry.

</td>
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
</table>

**Related Information**  


[DYNAMIC\_RESULT\_CACHE System View](../021-System-Views/dynamic-result-cache-system-view-47458ee.md "Provides information about metadata objects that are enabled for a dynamic result cache.")

[M\_DYNAMIC\_RESULT\_CACHE\_EXCLUSIONS System View](m-dynamic-result-cache-exclusions-system-view-e5a5b84.md "Lists cache exclusions of the dynamic result cache.")

[DYNAMIC\_RESULT\_CACHE\_INDEX\_COLUMNS System View](../021-System-Views/dynamic-result-cache-index-columns-system-view-4790ff8.md "Provides information about the indexes of dynamic result caches.")

[Results Caching for Virtual Tables and Linked Database](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/7dc806a729c64cd589f0d58d3b77aae1.html "Only view results caching is supported for virtual tables and linked database.") :arrow_upper_right:

