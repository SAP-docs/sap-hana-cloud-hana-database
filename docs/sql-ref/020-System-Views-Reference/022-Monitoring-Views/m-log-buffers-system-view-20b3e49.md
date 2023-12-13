<!-- loio20b3e49975191014bca6e0456cf8152e -->

# M\_LOG\_BUFFERS System View

Provides information about log buffer statistics.



<a name="loio20b3e49975191014bca6e0456cf8152e___m__l_o_g__b_u_f_f_e_r_s_1struct_M_LOG_BUFFERS"/>

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

LOG\_MODE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the log mode.

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

Displays the size of one log buffer in memory in kilobytes.

</td>
</tr>
<tr>
<td valign="top">

BUFFER\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the count of log buffers in memory.

</td>
</tr>
<tr>
<td valign="top">

SEGMENT\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum size of one log segment in megabytes.

</td>
</tr>
<tr>
<td valign="top">

BACKUP\_ENABLED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the log segment backup is enabled: TRUE, FALSE \(FALSE on log backup history broken\).

</td>
</tr>
<tr>
<td valign="top">

BACKUP\_TIMEOUT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the log segment backup timeout in seconds.

</td>
</tr>
<tr>
<td valign="top">

SWITCH\_NOWAIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the count of buffer switches without blocking on buffer semaphore.

</td>
</tr>
<tr>
<td valign="top">

SWITCH\_WAIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the count of buffer switches with blocking on buffer semaphore.

</td>
</tr>
<tr>
<td valign="top">

SWITCH\_OPEN\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the count of ignored still-open buffer switches \(resolved races\).

</td>
</tr>
</table>



<a name="loio20b3e49975191014bca6e0456cf8152e___m__l_o_g__b_u_f_f_e_r_s_1fulldesc_M_LOG_BUFFERS"/>

## Additional Information

The current configuration of in-memory log buffers is shown in the BUFFER\_SIZE and BUFFER\_COUNT columns. This defines how much log information can be collected transiently in memory, before the log queue becomes full.

Counters for buffer switches indicate performance of the in-memory log buffers. Normally, buffer switching happens without any waits. In the case of buffer full, however, a wait is necessary. Then, SWITCH\_WAIT\_COUNT is incremented, otherwise SWITCH\_NOWAIT\_COUNT is incremented. If the wait ratio is higher than one percent, this indicates a possible misconfiguration of the system. In this case:

-   Check if regular peaks exceed current log buffer configuration and if so, increase log buffer size and/or count

-   Check if the I/O subsystem is performing poorly \(see the M\_VOLUME\_IO\_TOTAL\_STATISTICS system view\).


Due to the lock-free nature of the algorithm used, some race conditions can happen. These are properly detected and resolved. Additionally, a count of such races is recorded in SWITCH\_OPEN\_COUNT. Normally, the ratio of races to buffer switches should also be under one percent even for high workloads.

This view has a resettable counterpart; you can see the values since the last reset in the M\_LOG\_BUFFERS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_LOG_BUFFERS_RESET;`.

**Related Information**  


[M\_LOG\_BUFFERS\_RESET System View](m-log-buffers-reset-system-view-20b4089.md "Provides log buffer statistics since the last reset.")

[M\_VOLUME\_IO\_TOTAL\_STATISTICS System View](m-volume-io-total-statistics-system-view-20cadec.md "Shows information about basic I/O operations on I/O subsystems (paths).")

[M\_LOG\_PARTITIONS System View](m-log-partitions-system-view-20b42eb.md "Provides log partition statistics.")

[M\_LOG\_SEGMENTS System View](m-log-segments-system-view-20b475c.md "Provides log segment statistics.")

