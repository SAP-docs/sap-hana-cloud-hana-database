<!-- loio66f4caa7c21f4feb94980ac9c43efa58 -->

# M\_METADATA\_CACHE\_STATISTICS System View

Provides information regarding the efficiency and use of the metadata cache.



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

Displays the port number.

</td>
</tr>
<tr>
<td valign="top">

CACHE\_GROUP\_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the category name of the cache group.

</td>
</tr>
<tr>
<td valign="top">

ORIGIN\_DATABASE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the original database that the cache group belongs to.

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

Displays the access count of the cache group.

</td>
</tr>
<tr>
<td valign="top">

HIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the cache hit count of the cache group.

</td>
</tr>
<tr>
<td valign="top">

EMPTY\_HIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the empty cache hit count of the cache group.

</td>
</tr>
<tr>
<td valign="top">

LATE\_HIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the duplicated metadata request count to the coordinator node. This count only occurs in the race conditions of the thread.

</td>
</tr>
<tr>
<td valign="top">

NOT\_FOUND\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the empty result response count of the coordinator node.

</td>
</tr>
<tr>
<td valign="top">

REVALIDATION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the revalidation count of old cache items.

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

Displays the cache miss count of the cache group.

</td>
</tr>
<tr>
<td valign="top">

ENTRY\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of items in the cache group.

</td>
</tr>
<tr>
<td valign="top">

INVALID\_ENTRY\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of invalid cache items. These items are set to invalid and removed during the next garbage collection.

</td>
</tr>
<tr>
<td valign="top">

VALID\_ENTRY\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of valid cache items.

</td>
</tr>
<tr>
<td valign="top">

STALE\_ENTRY\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of stale cache items. These are set as expired by default at the expiration time. These items can be revalidated later or removed at the next garbage collection.

</td>
</tr>
<tr>
<td valign="top">

USED\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of the memory occupied by the cache group in bytes.

</td>
</tr>
</table>

**Related Information**  


[ALTER SYSTEM CLEAR CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-cache-statement-system-management-141ad67.md "Clears resources (entries) from one or more cache instances.")

[ALTER SYSTEM REFRESH RESULT CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-refresh-result-cache-entry-statement-system-management-1ab0dbb.md "Refreshes the specified result cache entry.")

[ALTER SYSTEM CLEAR RESULT CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-result-cache-statement-system-management-97dca93.md "Removes all result cache entries from the system.")

[ALTER SYSTEM REMOVE RESULT CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-remove-result-cache-entry-statement-system-management-2124566.md "Removes the result cache entry for the specified cache ID.")

[Function Metadata](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/98599d94ae4e440eaea23dfd740de41b.html "") :arrow_upper_right:

[Procedure Metadata](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/8c59aace1caf472ebe71e6592a06b27a.html "") :arrow_upper_right:

