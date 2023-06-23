<!-- loio20b42eb175191014b23ab468e3baee4f -->

# M\_LOG\_PARTITIONS System View

Provides log partition statistics.



<a name="loio20b42eb175191014b23ab468e3baee4f___m__l_o_g__p_a_r_t_i_t_i_o_n_s_1struct_M_LOG_PARTITIONS"/>

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

PARTITION\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the partition ID. Returns the following:

-   For partitioned tables, the part ID is equal to the sequential number of the partition, starting at 1.
-   In the case of replicated tables, the part ID is 1 for the original table and subsequent part IDs are assigned to replica tables.
-   The part ID is 0 for tables that are not partitioned.
-   A part ID value of -1 indicates that a modification of the table schema is in progress.



</td>
</tr>
<tr>
<td valign="top">

PATH



</td>
<td valign="top">

NVARCHAR\(512\)



</td>
<td valign="top">

Displays the log partition root path.



</td>
</tr>
<tr>
<td valign="top">

LAST\_BUFFER\_PREPARE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size in bytes of the last log buffer at prepare time \(actual log data size\).



</td>
</tr>
<tr>
<td valign="top">

MAX\_BUFFER\_PREPARE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size of the largest log buffer in bytes at prepare time \(actual log data size\).



</td>
</tr>
<tr>
<td valign="top">

MIN\_BUFFER\_PREPARE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size in bytes of the smallest log buffer at prepare time \(actual log data size\).



</td>
</tr>
<tr>
<td valign="top">

SUM\_BUFFER\_PREPARE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total size in bytes of the log buffer at prepare time \(actual log data size\).



</td>
</tr>
<tr>
<td valign="top">

AVG\_BUFFER\_PREPARE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average size in bytes of the log buffer at prepare time \(actual log data size\).



</td>
</tr>
<tr>
<td valign="top">

LAST\_BUFFER\_OVERHEAD\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size in bytes of the last log buffer alignment overhead at I/O time.



</td>
</tr>
<tr>
<td valign="top">

MAX\_BUFFER\_OVERHEAD\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the largest size in bytes of the log buffer alignment overhead at I/O time.



</td>
</tr>
<tr>
<td valign="top">

MIN\_BUFFER\_OVERHEAD\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the smallest size in bytes of the log buffer alignment overhead at I/O time.



</td>
</tr>
<tr>
<td valign="top">

SUM\_BUFFER\_OVERHEAD\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total size in bytes of the log buffer alignment overhead at I/O time \(total\).



</td>
</tr>
<tr>
<td valign="top">

AVG\_BUFFER\_OVERHEAD\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average size in bytes of the log buffer alignment overhead at I/O time.



</td>
</tr>
<tr>
<td valign="top">

LAST\_BUFFER\_IO\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size in bytes of the last log buffer at I/O time \(actual data plus alignment overhead\).



</td>
</tr>
<tr>
<td valign="top">

MAX\_BUFFER\_IO\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the largest size in bytes of the log buffer at I/O time \(actual data plus alignment overhead\).



</td>
</tr>
<tr>
<td valign="top">

MIN\_BUFFER\_IO\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the smallest size in bytes of the log buffer at I/O time \(actual data plus alignment overhead\).



</td>
</tr>
<tr>
<td valign="top">

SUM\_BUFFER\_IO\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total size in bytes of log buffer at I/O time \(actual data plus alignment overhead\).



</td>
</tr>
<tr>
<td valign="top">

AVG\_BUFFER\_IO\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average size in bytes of log buffer at I/O time \(actual data plus alignment overhead\).



</td>
</tr>
<tr>
<td valign="top">

LAST\_GROUP\_COMMIT\_FREQUENCY



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the count of the last group commit frequency \(callback count per buffer with sync callback\).



</td>
</tr>
<tr>
<td valign="top">

MAX\_GROUP\_COMMIT\_FREQUENCY



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the count of the largest group commit frequency \(callback count per buffer with sync callback\).



</td>
</tr>
<tr>
<td valign="top">

MIN\_GROUP\_COMMIT\_FREQUENCY



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the count of the smallest group commit frequency \(callback count per buffer with sync callback\).



</td>
</tr>
<tr>
<td valign="top">

SUM\_GROUP\_COMMIT\_FREQUENCY



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total count of the group commit frequency \(callback count per buffer with sync callback\).



</td>
</tr>
<tr>
<td valign="top">

AVG\_GROUP\_COMMIT\_FREQUENCY



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average count of the group commit frequency \(callback count per buffer with sync callback\).



</td>
</tr>
<tr>
<td valign="top">

LAST\_CALLBACK\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the last callback time per buffer with sync callback in microseconds.



</td>
</tr>
<tr>
<td valign="top">

MAX\_CALLBACK\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the longest callback time per buffer with sync callback in microseconds.



</td>
</tr>
<tr>
<td valign="top">

MIN\_CALLBACK\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the shortest callback time per buffer with sync callback in microseconds.



</td>
</tr>
<tr>
<td valign="top">

SUM\_CALLBACK\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total callback time per buffer with sync callback in microseconds.



</td>
</tr>
<tr>
<td valign="top">

AVG\_CALLBACK\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average callback time per buffer with sync callback in microseconds.



</td>
</tr>
<tr>
<td valign="top">

PREPARED\_BUFFERS



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of buffers prepared for I/O.



</td>
</tr>
<tr>
<td valign="top">

WRITTEN\_BUFFERS



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of completed and written buffers.



</td>
</tr>
<tr>
<td valign="top">

WRITTEN\_BUFFERS\_OOO



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of buffers written out-of-order.



</td>
</tr>
<tr>
<td valign="top">

NEW\_SEGMENT\_REQUEST\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of of new log segment requests.



</td>
</tr>
<tr>
<td valign="top">

FREE\_SEGMENTS



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of log segments currently free.



</td>
</tr>
<tr>
<td valign="top">

IN\_BACKUP\_SEGMENTS



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of current in-backup log segments.



</td>
</tr>
<tr>
<td valign="top">

IN\_BACKUP\_TRUNCATED\_SEGMENTS



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of current in-backup truncated log segments.



</td>
</tr>
<tr>
<td valign="top">

BACKED\_UP\_SEGMENTS



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of log segments backed up so far.



</td>
</tr>
<tr>
<td valign="top">

TOTAL\_SEGMENTS



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total number of log segment count in the partition.



</td>
</tr>
<tr>
<td valign="top">

RECOVERY\_SEGMENTS\_IN\_LOAD



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of in-load segments during recovery.



</td>
</tr>
<tr>
<td valign="top">

RECOVERY\_SEGMENTS\_WAITING\_FOR\_LOAD



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of segments waiting for load during recovery.



</td>
</tr>
<tr>
<td valign="top">

RECOVERY\_SEGMENTS\_IN\_PROCESS



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of segments in process during recovery.



</td>
</tr>
<tr>
<td valign="top">

RECOVERY\_SEGMENTS\_PROCESSED



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Count of segments processed during recovery.



</td>
</tr>
<tr>
<td valign="top">

COMMIT\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of commits.



</td>
</tr>
<tr>
<td valign="top">

LAST\_COMMIT\_IO\_LATENCY



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the last time in microseconds needed to synchronize the flush of commit log.



</td>
</tr>
<tr>
<td valign="top">

MAX\_COMMIT\_IO\_LATENCY



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the longest time in microseconds needed to synchronize the flush of commit log entries.



</td>
</tr>
<tr>
<td valign="top">

MIN\_COMMIT\_IO\_LATENCY



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the shortest time in microseconds needed in synchronize the flush of commit log entries.



</td>
</tr>
<tr>
<td valign="top">

SUM\_COMMIT\_IO\_LATENCY



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total time in microseconds needed to synchronize the flush of commit log entries.



</td>
</tr>
<tr>
<td valign="top">

AVG\_COMMIT\_IO\_LATENCY



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average time in microseconds needed to synchronize the flush of commit log entries.



</td>
</tr>
</table>



<a name="loio20b42eb175191014b23ab468e3baee4f___m__l_o_g__p_a_r_t_i_t_i_o_n_s_1fulldesc_M_LOG_PARTITIONS"/>

## Additional Information

This view collects various performance statistics for each log partition. The collected statistics can be used to optimize workload.

This view has a resettable counterpart; you can see the values since the last reset in the M\_LOG\_PARTITIONS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_LOG_PARTITIONS_RESET;`.

**Related Information**  


[M\_LOG\_PARTITIONS\_RESET System View](m-log-partitions-reset-system-view-20b4528.md "Provides log partition statistics since the last reset.")

[M\_LOG\_BUFFERS System View](m-log-buffers-system-view-20b3e49.md "Provides information about log buffer statistics.")

[M\_LOG\_SEGMENTS System View](m-log-segments-system-view-20b475c.md "Provides log segment statistics.")

[M\_VOLUME\_IO\_TOTAL\_STATISTICS System View](m-volume-io-total-statistics-system-view-20cadec.md "Shows information about basic I/O operations on I/O subsystems (paths).")

