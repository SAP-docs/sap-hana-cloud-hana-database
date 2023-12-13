<!-- loio6498399c829b441696a4fa9b49886091 -->

# M\_CS\_LOG\_REPLAY\_QUEUE\_STATISTICS System View

Provides information about column store log replay queue statistics.



<a name="loio6498399c829b441696a4fa9b49886091__M_CS_LOG_REPLAY_QUEUE_STATISTICS"/>

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

Displays the name of the host.

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

LOG\_REPLAY\_QUEUE\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the ID of the recovery queue.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_CS\_LOG\_RECORD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of redo records that were processed in this queue.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_DML\_LOG\_RECORD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of column store DML redo records that were processed in this queue.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_DDL\_LOG\_RECORD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of column store DDL redo records that were processed in this queue.

</td>
</tr>
<tr>
<td valign="top">

LAST\_CS\_LOG\_RECORD\_TYPE

</td>
<td valign="top">

NVARCHAR\(40\)

</td>
<td valign="top">

Displays the last column store log record type in this queue.

</td>
</tr>
<tr>
<td valign="top">

LAST\_LOG\_REPLAY\_POSITION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last log replay position that was processed in this queue.

</td>
</tr>
<tr>
<td valign="top">

LAST\_SAVEPOINT\_POSITION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last savepoint position that was passed in this queue.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_SAVEPOINT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of savepoints that were passsed in this queue.

</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_TABLE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of tables that are currently handled in this queue.

</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_DELTA\_MERGE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of delta merges that are currently ongoing for tables that are handled in this queue.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_DELTA\_MERGE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of delta merges that were started on this queue.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_SUCCESSFUL\_DELTA\_MERGE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of successful merges.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_DELTA\_FUSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of delta fusions that were made in this queue.

</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_OPTIMIZE\_COMPRESSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of optimize compressions that are currently ongoing for tables that are handled in this queue.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_OPTIMIZE\_COMPRESSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of successful optimize compressions.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_SUCCESSFUL\_OPTIMIZE\_COMPRESSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of successful optimize compressions.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_DML\_CONTEXT\_CREATE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of expensive creations of DML contexts.

</td>
</tr>
</table>

**Related Information**  


[M\_CS\_LOG\_REPLAY\_QUEUE\_STATISTICS\_RESET System View](m-cs-log-replay-queue-statistics-reset-system-view-415dc16.md "Provides information about column store log replay queue statistics since the last reset.")

[HOST_SERVICE_REPLICATION View (Embedded Statistics Service)](https://help.sap.com/viewer/323c57a017234d47a0e7da3e22345822/2023_4_QRC/en-US/7df5ea067be947e7b0b09a13234f1d80.html "Specifies the service replication statistics per host.") :arrow_upper_right:

