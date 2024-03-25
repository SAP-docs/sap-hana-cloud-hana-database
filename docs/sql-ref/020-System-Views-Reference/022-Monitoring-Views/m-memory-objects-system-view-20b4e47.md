<!-- loio20b4e478751910148c5abaf8e1260770 -->

# M\_MEMORY\_OBJECTS System View

Returns memory object statistics.



<a name="loio20b4e478751910148c5abaf8e1260770___m__m_e_m_o_r_y__o_b_j_e_c_t_s_1struct_M_MEMORY_OBJECTS"/>

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

Displays the internal port number.

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

Displays the persistence volume ID.

</td>
</tr>
<tr>
<td valign="top">

TYPE

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the object \(statistic\) type.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of objects currently in the memory object container.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of the objects that are currently in the memory object container in bytes.

</td>
</tr>
<tr>
<td valign="top">

NON\_SWAPPABLE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of the non-swappable objects that are currently in the memory object container in bytes.

</td>
</tr>
<tr>
<td valign="top">

SWAPPABLE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of the swappable objects that are currently in the memory object container in bytes.

</td>
</tr>
<tr>
<td valign="top">

PUT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of put objects.

</td>
</tr>
<tr>
<td valign="top">

PUT\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size of put objects in bytes.

</td>
</tr>
<tr>
<td valign="top">

PUT\_FAILURE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of objects not added to the memory object container, due to key conflicts.

</td>
</tr>
<tr>
<td valign="top">

GET\_HIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of successful get operations.

</td>
</tr>
<tr>
<td valign="top">

GET\_MISS\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of get operations that failed because the object was not found in the memory object container.

</td>
</tr>
<tr>
<td valign="top">

MOVE\_IN\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of objects moved in from a different statistic.

</td>
</tr>
<tr>
<td valign="top">

MOVE\_IN\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size of objects moved in from a different statistic in bytes.

</td>
</tr>
<tr>
<td valign="top">

MOVE\_OUT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of objects moved out to a different statistic.

</td>
</tr>
<tr>
<td valign="top">

MOVE\_OUT\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size of objects moved out to a different statistic in bytes.

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

Displays the total number of evicted objects.

</td>
</tr>
<tr>
<td valign="top">

EVICT\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size of evicted objects in bytes.

</td>
</tr>
<tr>
<td valign="top">

TEMP\_EVICT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of temp-evicted objects.

</td>
</tr>
<tr>
<td valign="top">

TEMP\_EVICT\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size of temp-evicted objects in bytes.

</td>
</tr>
<tr>
<td valign="top">

RESIZE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of resizes of objects.

</td>
</tr>
<tr>
<td valign="top">

RESIZE\_DELTA\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size delta changed by the resize of the objects in bytes.

</td>
</tr>
<tr>
<td valign="top">

SHRINK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of shrunken objects.

</td>
</tr>
<tr>
<td valign="top">

SHRINK\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size of shrunken objects in bytes.

</td>
</tr>
<tr>
<td valign="top">

RETENTION\_PERIOD\_SHRINK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of shrunken objects due to an unused retention period.

</td>
</tr>
<tr>
<td valign="top">

RETENTION\_PERIOD\_SHRINK\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size of shrunken objects due to an unused retention period in bytes.

</td>
</tr>
<tr>
<td valign="top">

PAGE\_LOADABLE\_COLUMNS\_LIMIT\_SHRINK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of shrunken objects due to a paged attribute limit violation.

</td>
</tr>
<tr>
<td valign="top">

PAGE\_LOADABLE\_COLUMNS\_LIMIT\_SHRINK\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size of shrunken objects due to paged attribute limit violation in bytes.

</td>
</tr>
<tr>
<td valign="top">

FAILED\_SHRINK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of the objects that the shrink failed to remove.

</td>
</tr>
<tr>
<td valign="top">

FAILED\_SHRINK\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size of the objects that the shrink failed to remove in bytes.

</td>
</tr>
<tr>
<td valign="top">

UPPER\_LIMIT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the effective upper size limit \(in bytes\) for objects of this memory object type. If the total memory usage for objects belonging to this memory object type exceeds the UPPER\_LIMIT, an automatic unload is triggered.

</td>
</tr>
<tr>
<td valign="top">

LOWER\_LIMIT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the effective lower size limit \(in bytes\) for objects of this memory object type. If an automatic unload has been triggered because the UPPER\_LIMIT was exceeded, the unload execution stops when the total memory usage falls below the LOWER\_LIMIT.

</td>
</tr>
<tr>
<td valign="top">

RESOURCE\_CATEGORY

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays the resource category. CACHE indicates that the object has been used as a cache.

</td>
</tr>
</table>



<a name="loio20b4e478751910148c5abaf8e1260770___m__m_e_m_o_r_y__o_b_j_e_c_t_s_1fulldesc_M_MEMORY_OBJECTS"/>

## Additional Information

This view provides information about the number and size of resources in the resource container and about the throughput of the resource container. One row in this view represents one resource type \(the type is specified by the resource statistic\). The resource statistics are kept in a tree data structure and this view represents this tree in a human-readable form. Each value \(except for HOST, PORT, VOLUME\_ID, and STATISTICS\_NAME\) is the AGGREGATED value of the subtree \(including the current node\).

This view has a resettable counterpart; you can see the values since the last reset in the M\_MEMORY\_OBJECTS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_MEMORY_OBJECTS_RESET;`.

**Related Information**  


[M\_MEMORY\_OBJECTS\_RESET System View](m-memory-objects-reset-system-view-20b508b.md "Provides values accumulated since the last reset of the main view M_MEMORY_OBJECTS.")

[M\_MEMORY\_OBJECT\_DISPOSITIONS System View](m-memory-object-dispositions-system-view-20b4bf9.md "Displays the disposition-specific memory object statistics.")

[Managing Memory by Object Usage](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/815fd19868d84c13962852faa3b1ee85.html "You can use the Unused Retention Period feature to automatically unload objects from memory which are not being used.") :arrow_upper_right:

