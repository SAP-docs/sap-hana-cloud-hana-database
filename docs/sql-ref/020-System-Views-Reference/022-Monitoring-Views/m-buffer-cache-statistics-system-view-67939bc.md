<!-- loio67939bc3ace4409ea01ac9aaa1ec6407 -->

# M\_BUFFER\_CACHE\_STATISTICS System View

Provides a cache level overview of the configuration, cache status, and memory usage.



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

Displays the cache name: C/S or R/S.

</td>
</tr>
<tr>
<td valign="top">

STATE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the cache state: ENABLED, DISABLING, DISABLED, or SHRINKING.

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

IO\_READ\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the disk I/O reads size by the cache in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAX\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum buffer cache memory capacity in bytes.

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

ALLOCATED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the allocated memory for the buffer cache in bytes.

</td>
</tr>
<tr>
<td valign="top">

USED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the used memory in buffer cache in bytes.

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

Displays the number of times that a buffer is released for reuse by the cache.

</td>
</tr>
<tr>
<td valign="top">

HIT\_RATIO

</td>
<td valign="top">

FLOAT

</td>
<td valign="top">

Displays the ratio of pages found in the buffer cache to pages requested from the buffer cache.

</td>
</tr>
<tr>
<td valign="top">

PINNED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of pinned memory in the buffer cache in bytes.

</td>
</tr>
</table>

**Related Information**  


[M\_BUFFER\_CACHE\_POOL\_STATISTICS System View](m-buffer-cache-pool-statistics-system-view-4c417c7.md "Provides statistics for each buffer pool in a cache.")

[M\_BUFFER\_CACHE\_POOL\_STATISTICS\_RESET System View](m-buffer-cache-pool-statistics-reset-system-view-caf06b3.md "Provides statistics for each buffer pool in a cache since the last reset.")

[M\_BUFFER\_CACHE\_STATISTICS\_RESET System View](m-buffer-cache-statistics-reset-system-view-1d8ef9a.md "Provides a cache level overview of the configuration, cache status, and memory usage since the last reset.")

[M\_LOG\_BUFFERS System View](m-log-buffers-system-view-20b3e49.md "Provides information about log buffer statistics.")

[SAP HANA NSE Buffer Cache](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/8a35ce565c594c11bb785bea607213d8.html "The SAP HANA Native Storage Extension (NSE) buffer cache replaces the SAP HANA default page replacement and memory limit mechanism for the memory pages.") :arrow_upper_right:

