<!-- loio4c417c702d7f4ec4ac39c4abcde5abfc -->

# M\_BUFFER\_CACHE\_POOL\_STATISTICS System View

Provides statistics for each buffer pool in a cache.



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

VOLUME\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the volume identifier for the index server.

</td>
</tr>
<tr>
<td valign="top">

CACHE\_NAME

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the cache name: C/S, R/S.

</td>
</tr>
<tr>
<td valign="top">

BUFFER\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of the buffer in the pool in bytes.

</td>
</tr>
<tr>
<td valign="top">

REPLACEMENT\_POLICY

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the type of replacement policy used by the cache.

</td>
</tr>
<tr>
<td valign="top">

GROWTH\_PERCENT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the rate, as a percentage, at which the buffer pool can grow:

```
TOTAL_BUFFER_COUNT = TOTAL_BUFFER_COUNT + GROWTH PERCENT / 100 * MAX_SIZE
```



</td>
</tr>
<tr>
<td valign="top">

TOTAL\_BUFFER\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of buffers allocated to the pool.

</td>
</tr>
<tr>
<td valign="top">

FREE\_BUFFER\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of free buffers for the pool.

</td>
</tr>
<tr>
<td valign="top">

LRU\_LIST\_BUFFER\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of buffers in the LRU chain for the pool.

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

HOT\_BUFFER\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of buffers in the hot buffer list for the pool.

</td>
</tr>
<tr>
<td valign="top">

IO\_READ\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the disk I/O reads size for the pool.

</td>
</tr>
<tr>
<td valign="top">

BUFFER\_REUSE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of buffers released from the LRU list for the pool so that a requested page can be cached.

</td>
</tr>
<tr>
<td valign="top">

OUT\_OF\_BUFFER\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of times that an out-of-buffer situation occurred while requesting buffers from the pool.

</td>
</tr>
<tr>
<td valign="top">

PINNED\_BUFFER\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of pinned memory in the pool in bytes.

</td>
</tr>
</table>

**Related Information**  


[M\_BUFFER\_CACHE\_POOL\_STATISTICS\_RESET System View](m-buffer-cache-pool-statistics-reset-system-view-caf06b3.md "Provides statistics for each buffer pool in a cache since the last reset.")

[M\_BUFFER\_CACHE\_STATISTICS System View](m-buffer-cache-statistics-system-view-67939bc.md "Provides a cache level overview of the configuration, cache status, and memory usage.")

[M\_BUFFER\_CACHE\_STATISTICS\_RESET System View](m-buffer-cache-statistics-reset-system-view-1d8ef9a.md "Provides a cache level overview of the configuration, cache status, and memory usage since the last reset.")

[M\_LOG\_BUFFERS System View](m-log-buffers-system-view-20b3e49.md "Provides information about log buffer statistics.")

[SAP HANA NSE Buffer Cache](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/8a35ce565c594c11bb785bea607213d8.html "The SAP HANA Native Storage Extension (NSE) buffer cache replaces the SAP HANA default page replacement and memory limit mechanism for the memory pages.") :arrow_upper_right:

