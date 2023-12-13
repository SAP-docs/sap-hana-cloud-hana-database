<!-- loio425a15ebd5e942e09ac99763c6cee6ae -->

# M\_TABLE\_REPLICATION\_VOLUME\_STATISTICS System View

Provides detailed information on table replication volume statistics.




<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Data Type

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

Displays the persistence Volume ID.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_REMOTE\_SOURCE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the remote source name of source system.  If SOURCE\_REMOTE\_SOURCE\_NAME and REPLICA\_REMOTE\_SOURCE\_NAME are NULL, it means non-remote table replication \(RTR\).

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_REMOTE\_SOURCE\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the remote source schema name of source system.

</td>
</tr>
<tr>
<td valign="top">

REPLICA\_REMOTE\_SOURCE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the remote source name of replica system.

</td>
</tr>
<tr>
<td valign="top">

REPLICA\_REMOTE\_SOURCE\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the remote source schema name of replica system.

</td>
</tr>
<tr>
<td valign="top">

LAST\_SOURCE\_COMMIT\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last commit time of source system. The value in this column cannot be reset using the ALTER SYSTEM RESET MONITORING View statement.

</td>
</tr>
<tr>
<td valign="top">

TRANSACTION\_LOG\_QUEUE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current transaction log queue size. This is the log count in the queue. The value in this column cannot be reset using the ALTER SYSTEM RESET MONITORING View statement.

</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_TRANSACTION\_LOG\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the shipped transaction log count.

</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_TRANSACTION\_LOG\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the shipped transaction log size in bytes.

</td>
</tr>
<tr>
<td valign="top">

REPLAYED\_TRANSACTION\_LOG\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the replayed transaction log size in bytes.

</td>
</tr>
<tr>
<td valign="top">

REPLAYED\_PRECOMMIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the replayed precommit count.

</td>
</tr>
<tr>
<td valign="top">

REPLAYED\_COMMIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the replayed commit count. The count includes the replayed DDL/DML commit count.

</td>
</tr>
<tr>
<td valign="top">

REPLAYED\_ROLLBACK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the replayed rollback count.

</td>
</tr>
<tr>
<td valign="top">

REPLAYED\_DDL\_COMMIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the replayed DDL commit count. This is applicable to remote table replication only.

</td>
</tr>
<tr>
<td valign="top">

TRANSACTION\_REPLAY\_ERROR\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the transaction replay error count.

</td>
</tr>
<tr>
<td valign="top">

AVG\_PRECOMMIT\_PROPAGATION\_LATENCY

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average precommit propagation latency time, in microseconds.

</td>
</tr>
<tr>
<td valign="top">

AVG\_PROPAGATION\_LATENCY

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average commit propagation latency, in microseconds. Propagation latency is the sum of network latency, dispatch latency, and processing latency.

</td>
</tr>
<tr>
<td valign="top">

AVG\_PROCESSING\_LATENCY

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average processing latency, in microseconds, of the commit log.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_DML\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated DML wait time, in microseconds.

</td>
</tr>
</table>

