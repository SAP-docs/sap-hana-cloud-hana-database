<!-- loio3cbd0818857a483dbfc21e6802a6f148 -->

# M\_LOG\_REPLAY\_QUEUE\_STATISTICS System View

Provides information about log replay queue statistics.



<a name="loio3cbd0818857a483dbfc21e6802a6f148__M_LOG_REPLAY_QUEUE_STATISTICS"/>

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

LOG\_REPLAY\_QUEUE\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the ID of the log replay queue.



</td>
</tr>
<tr>
<td valign="top">

LOG\_RECORD\_TYPE



</td>
<td valign="top">

NVARCHAR\(40\)



</td>
<td valign="top">

Displays the type of redo log record.



</td>
</tr>
<tr>
<td valign="top">

TOTAL\_LOG\_RECORD\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total number of replayed log entries.



</td>
</tr>
<tr>
<td valign="top">

TOTAL\_EXECUTION\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the accumulated execute time to replay log entries in microseconds.



</td>
</tr>
<tr>
<td valign="top">

TOTAL\_WAIT\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the accumulated local wait time during replay of log entries in microseconds.



</td>
</tr>
<tr>
<td valign="top">

TOTAL\_LOG\_RECORD\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the accumulated log size of replayed log entries.



</td>
</tr>
</table>

**Related Information**  


[M\_LOG\_REPLAY\_QUEUE\_STATISTICS\_RESET System View](m-log-replay-queue-statistics-reset-system-view-2382dd1.md "Provides information about log replay queue statistics.")

[HOST_SERVICE_REPLICATION View (Embedded Statistics Service)](https://help.sap.com/viewer/323c57a017234d47a0e7da3e22345822/2023_2_QRC/en-US/7df5ea067be947e7b0b09a13234f1d80.html "Specifies the service replication statistics per host.") :arrow_upper_right:

