<!-- loio20b475c7751910149705a31072bd2c45 -->

# M\_LOG\_SEGMENTS System View

Provides log segment statistics.



<a name="loio20b475c7751910149705a31072bd2c45___m__l_o_g__s_e_g_m_e_n_t_s_1struct_M_LOG_SEGMENTS"/>

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

SEGMENT\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the log segment ID within the partition.

</td>
</tr>
<tr>
<td valign="top">

FILE\_NAME

</td>
<td valign="top">

NVARCHAR\(512\)

</td>
<td valign="top">

Displays the log segment file name.

</td>
</tr>
<tr>
<td valign="top">

FILE\_OFFSET

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the start position of the log segment in the file.

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

Displays the log segment state:


<dl>
<dt><b>

Formatting

</b></dt>
<dd>

The log segment is being formatted and not yet used.



</dd><dt><b>

Preallocated

</b></dt>
<dd>

The log segment has been preallocated but has never been used.



</dd><dt><b>

Writing

</b></dt>
<dd>

The log segment is currently being written.



</dd><dt><b>

Closed

</b></dt>
<dd>

The log segment is closed, not backed up and is still required for restart.



</dd><dt><b>

Truncated

</b></dt>
<dd>

The log segment is not required for restart, but has not been backed up.



</dd><dt><b>

BackedUp

</b></dt>
<dd>

The log segment has been backed up, but is still required for restart.



</dd><dt><b>

RetainedFree

</b></dt>
<dd>

The log segment has been backed up; it is not required for a restart but is needed to resynchronize the system replication sites.



</dd><dt><b>

Free

</b></dt>
<dd>

The log segment has been backed up, it is not required for restart and can be reused.



</dd><dt><b>

ClosedIncoplete

</b></dt>
<dd>

The log segment has been closed in an incomplete state on a system replication site. This is a temporary state that persists until system replication reconnects or a takeover occurs.



</dd><dt><b>

FreeIncomplete

</b></dt>
<dd>

The log segment has been designated as 'free' in an incomplete state, typically following scenarios like a system replication takeover or log corruption.



</dd>
</dl>



</td>
</tr>
<tr>
<td valign="top">

MIN\_POSITION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the first position contained in the log segment.

</td>
</tr>
<tr>
<td valign="top">

MAX\_POSITION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the position behind the last log record in the log segment. This value is for closed log segments only.

</td>
</tr>
<tr>
<td valign="top">

HOLE\_POSITION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the start position of the log hole before the log segment. This value is equal to MIN\_POSITION if there is no hole.

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

Displays the used log segment size in bytes.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total log segment size in bytes.

</td>
</tr>
<tr>
<td valign="top">

IN\_BACKUP

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates whether or not the flag for the log segment is in the backup: TRUE/FALSE

</td>
</tr>
<tr>
<td valign="top">

LAST\_COMMIT\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time stamp of the last commit in the log segment.

</td>
</tr>
<tr>
<td valign="top">

ENCRYPTION\_KEY\_HASH

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the hash of the key used for the log segment encryption.

</td>
</tr>
</table>



<a name="loio20b475c7751910149705a31072bd2c45___m__l_o_g__s_e_g_m_e_n_t_s_1fulldesc_M_LOG_SEGMENTS"/>

## Additional Information description

This view describes each allocated log segment and shows its current state and log position range that is currently contained in the segment.

This view has a resettable counterpart; you can see the values since the last reset in the M\_LOG\_SEGMENTS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_LOG_SEGMENTS_RESET;`.

**Related Information**  


[M\_LOG\_SEGMENTS\_RESET System View](m-log-segments-reset-system-view-20b4996.md "Provides log segment statistics since the last reset.")

[M\_LOG\_BUFFERS System View](m-log-buffers-system-view-20b3e49.md "Provides information about log buffer statistics.")

[M\_LOG\_PARTITIONS System View](m-log-partitions-system-view-20b42eb.md "Provides log partition statistics.")

[M\_VOLUME\_IO\_TOTAL\_STATISTICS System View](m-volume-io-total-statistics-system-view-20cadec.md "Shows information about basic I/O operations on I/O subsystems (paths).")

