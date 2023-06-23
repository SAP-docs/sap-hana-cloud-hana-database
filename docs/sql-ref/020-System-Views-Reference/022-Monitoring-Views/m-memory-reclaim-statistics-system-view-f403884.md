<!-- loiof40388456f5b1014a291dab0fe47d95b -->

# M\_MEMORY\_RECLAIM\_STATISTICS System View

Provides statistics for reclaiming memory \(for example, defragmentation, unloading of memory objects, and so on\).



<a name="loiof40388456f5b1014a291dab0fe47d95b___m__m_e_m_o_r_y__r_e_c_l_a_i_m__s_t_a_t_i_s_t_i_c_s_1struct_M_MEMORY_RECLAIM_STATISTICS"/>

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

STATISTICS\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the statistics object unique ID.



</td>
</tr>
<tr>
<td valign="top">

MEMORY\_RECLAIM\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of memory reclaims.



</td>
</tr>
<tr>
<td valign="top">

LAST\_MEMORY\_RECLAIM\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the time needed in milliseconds to reclaim memory for the last allocation.



</td>
</tr>
<tr>
<td valign="top">

MAX\_MEMORY\_RECLAIM\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the longest time needed in milliseconds to reclaim memory for the allocation.



</td>
</tr>
<tr>
<td valign="top">

MIN\_MEMORY\_RECLAIM\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the shortest time needed in milliseconds to reclaim memory for the allocation.



</td>
</tr>
<tr>
<td valign="top">

SUM\_MEMORY\_RECLAIM\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total time needed in milliseconds to reclaim memory for all allocations.



</td>
</tr>
<tr>
<td valign="top">

AVG\_MEMORY\_RECLAIM\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average time needed in milliseconds to reclaim memory for the allocation.



</td>
</tr>
<tr>
<td valign="top">

LAST\_SYNCHRONIZATION\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the last wait time in milliseconds while other thread/process reclaims memory.



</td>
</tr>
<tr>
<td valign="top">

MAX\_SYNCHRONIZATION\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the longest wait time in milliseconds while other thread/process reclaims memory.



</td>
</tr>
<tr>
<td valign="top">

MIN\_SYNCHRONIZATION\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the shortest wait time in milliseconds while other thread/process reclaims memory.



</td>
</tr>
<tr>
<td valign="top">

SUM\_SYNCHRONIZATION\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total wait time in milliseconds while other thread/process reclaims memory.



</td>
</tr>
<tr>
<td valign="top">

AVG\_SYNCHRONIZATION\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average wait time in milliseconds while other thread/process reclaims memory.



</td>
</tr>
<tr>
<td valign="top">

LAST\_DEFRAGMENTATION\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the duration in milliseconds of the last defragmentation.



</td>
</tr>
<tr>
<td valign="top">

MAX\_DEFRAGMENTATION\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the longest duration in milliseconds of defragmentation.



</td>
</tr>
<tr>
<td valign="top">

MIN\_DEFRAGMENTATION\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the shortest duration in milliseconds of defragmentation.



</td>
</tr>
<tr>
<td valign="top">

SUM\_DEFRAGMENTATION\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total duration in milliseconds of defragmentation.



</td>
</tr>
<tr>
<td valign="top">

AVG\_DEFRAGMENTATION\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average duration in milliseconds of defragmentation.



</td>
</tr>
<tr>
<td valign="top">

LAST\_DEFRAGMENTATION\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size in bytes freed by the last defragmentation.



</td>
</tr>
<tr>
<td valign="top">

MAX\_DEFRAGMENTATION\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the largest size in bytes freed by defragmentation.



</td>
</tr>
<tr>
<td valign="top">

MIN\_DEFRAGMENTATION\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the smallest size in bytes freed by defragmentation.



</td>
</tr>
<tr>
<td valign="top">

SUM\_DEFRAGMENTATION\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total size freed in bytes by defragmentation\).



</td>
</tr>
<tr>
<td valign="top">

AVG\_DEFRAGMENTATION\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average size in bytes freed by defragmentation.



</td>
</tr>
<tr>
<td valign="top">

LAST\_MEMORY\_OBJECT\_UNLOAD\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the duration in milliseconds of the last unload. Also see view M\_MEMORY\_OBJECTS.



</td>
</tr>
<tr>
<td valign="top">

MAX\_MEMORY\_OBJECT\_UNLOAD\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the longest duration in milliseconds of all unloads. Also see view M\_MEMORY\_OBJECTS.



</td>
</tr>
<tr>
<td valign="top">

MIN\_MEMORY\_OBJECT\_UNLOAD\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the shortest duration in milliseconds of all unloads. Also see view M\_MEMORY\_OBJECTS.



</td>
</tr>
<tr>
<td valign="top">

SUM\_MEMORY\_OBJECT\_UNLOAD\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total duration in milliseconds of all unloads. Also see view M\_MEMORY\_OBJECTS.



</td>
</tr>
<tr>
<td valign="top">

AVG\_MEMORY\_OBJECT\_UNLOAD\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average duration in milliseconds of all unloads. Also see view M\_MEMORY\_OBJECTS.



</td>
</tr>
<tr>
<td valign="top">

LAST\_MEMORY\_OBJECT\_UNLOAD\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size in bytes freed by the last unloading of memory objects. Also see view M\_MEMORY\_OBJECTS.



</td>
</tr>
<tr>
<td valign="top">

MAX\_MEMORY\_OBJECT\_UNLOAD\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the largest size in bytes freed by unloading memory objects. Also see view M\_MEMORY\_OBJECTS.



</td>
</tr>
<tr>
<td valign="top">

MIN\_MEMORY\_OBJECT\_UNLOAD\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the smallest size in bytes freed by unloading memory objects. Also see view M\_MEMORY\_OBJECTS.



</td>
</tr>
<tr>
<td valign="top">

SUM\_MEMORY\_OBJECT\_UNLOAD\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total size in bytes freed by unloading memory objects. Also see view M\_MEMORY\_OBJECTS.



</td>
</tr>
<tr>
<td valign="top">

AVG\_MEMORY\_OBJECT\_UNLOAD\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average size in bytes freed by unloading memory objects. also see view M\_MEMORY\_OBJECTS.



</td>
</tr>
</table>



<a name="loiof40388456f5b1014a291dab0fe47d95b__section_d1d_klh_x2b"/>

## Additional Information

This view has a resettable counterpart; you can see the values since the last reset in the M\_MEMORY\_RECLAIM\_STATISTICS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_MEMORY_RECLAIM_STATISTICS_RESET;`.

**Related Information**  


[M\_MEMORY\_RECLAIM\_STATISTICS\_RESET System View](m-memory-reclaim-statistics-reset-system-view-f404081.md "Provides statistics for reclaiming memory (for example, defragmentation, unloading of memory objects, and so on) since the last reset.")

