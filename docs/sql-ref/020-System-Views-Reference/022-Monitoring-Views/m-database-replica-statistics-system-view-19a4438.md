<!-- loio19a443885e2241c1a22581112f36a336 -->

# M\_DATABASE\_REPLICA\_STATISTICS System View

Provides statistics on databases involved in replication.



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

SOURCE\_DATABASE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the source database.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the source host name.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the source internal port.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_VOLUME\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the source volume ID.

</td>
</tr>
<tr>
<td valign="top">

TARGET\_DATABASE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the target database.

</td>
</tr>
<tr>
<td valign="top">

TARGET\_HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the target host name.

</td>
</tr>
<tr>
<td valign="top">

TARGET\_PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the target port.

</td>
</tr>
<tr>
<td valign="top">

TARGET\_ACTIVE\_STATUS

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the target active status.

</td>
</tr>
<tr>
<td valign="top">

TARGET\_CONNECT\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time that the connection was established from the target.

</td>
</tr>
<tr>
<td valign="top">

TARGET\_RECONNECT\_TIME

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the target reconnect count.

</td>
</tr>
<tr>
<td valign="top">

TARGET\_FAILOVER\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the target failover count.

</td>
</tr>
<tr>
<td valign="top">

TARGET\_FULLY\_RECOVERABLE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates if the target is fully recoverable.

</td>
</tr>
<tr>
<td valign="top">

REPLICATION\_MODE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the replication mode.

</td>
</tr>
<tr>
<td valign="top">

REPLICATION\_STATUS

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the replication status.

</td>
</tr>
<tr>
<td valign="top">

REPLICATION\_STATUS\_DETAILS

</td>
<td valign="top">

NVARCHAR\(1024\)

</td>
<td valign="top">

Displays the replication status details.

</td>
</tr>
<tr>
<td valign="top">

LAST\_LOG\_POSITION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current log position.

</td>
</tr>
<tr>
<td valign="top">

LAST\_LOG\_POSITION\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the current log position timestamp.

</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_LOG\_POSITION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the shipped log position.

</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_LOG\_POSITION\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the shipped log position timestamp.

</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_LOG\_BUFFERS\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the shipped log buffers count.

</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_LOG\_BUFFERS\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the shipped log buffers size in bytes.

</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_LOG\_BUFFERS\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the shipped log buffer duration in microseconds.

</td>
</tr>
<tr>
<td valign="top">

ASYNC\_BUFFER\_FULL\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of times the asynchronous replication buffer got full.

</td>
</tr>
<tr>
<td valign="top">

BACKLOG\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current replication backlog in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAX\_BACKLOG\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the max replication backlog in bytes.

</td>
</tr>
<tr>
<td valign="top">

BACKLOG\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current replication backlog in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MAX\_BACKLOG\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the max replication backlog in microseconds.

</td>
</tr>
</table>

**Related Information**  


[M\_DATABASE\_REPLICAS System View](m-database-replicas-system-view-b83afe7.md "Provides source and target information for databases involved in replication.")

[M\_DATABASE System View](m-database-system-view-20ae63a.md "Provides database information.")

[M\_DATABASES System View](m-databases-system-view-dbbdc0d.md "Provides information about all databases in the system. The full content of this view is only accessible from the system database.")

[M\_DATABASE\_HISTORY System View](m-database-history-system-view-20ae406.md "Provides installation version history.")

