<!-- loio20c43fc975191014b0ece11b47a86c10 -->

# M\_SERVICE\_REPLICATION System View

Provides information about replicated services.



<a name="loio20c43fc975191014b0ece11b47a86c10___m__s_e_r_v_i_c_e__r_e_p_l_i_c_a_t_i_o_n_1struct_M_SERVICE_REPLICATION"/>

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

INTEGER\(10\)



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

Displays the volume ID.



</td>
</tr>
<tr>
<td valign="top">

SITE\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the generated site ID.



</td>
</tr>
<tr>
<td valign="top">

SITE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the logical site name.



</td>
</tr>
<tr>
<td valign="top">

SECONDARY\_HOST



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the secondary host name.



</td>
</tr>
<tr>
<td valign="top">

SECONDARY\_PORT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the secondary port.



</td>
</tr>
<tr>
<td valign="top">

SECONDARY\_SITE\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the generated ID of the secondary site.



</td>
</tr>
<tr>
<td valign="top">

SECONDARY\_SITE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the secondary logical site name.



</td>
</tr>
<tr>
<td valign="top">

SECONDARY\_ACTIVE\_STATUS



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the secondary active status.



</td>
</tr>
<tr>
<td valign="top">

SECONDARY\_CONNECT\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the time the connection was established from the secondary site.



</td>
</tr>
<tr>
<td valign="top">

SECONDARY\_RECONNECT\_COUNT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the secondary reconnect count.



</td>
</tr>
<tr>
<td valign="top">

SECONDARY\_FAILOVER\_COUNT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the secondary failover count.



</td>
</tr>
<tr>
<td valign="top">

SECONDARY\_FULLY\_RECOVERABLE



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays that the secondary system can be fully recovered with a backup from the primary system.

If this value is FALSE, then the backup history is broken. If there is a takeover at that time, then start a new data backup once the takeover is finished.



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

NVARCHAR\(1.024\)



</td>
<td valign="top">

Displays the replication status details.



</td>
</tr>
<tr>
<td valign="top">

FULL\_SYNC



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the full sync status:

-   DISABLED: the full sync is not configured

-   ENABLED: the full sync is configured, but it is not yet active \(transactions do not block in this state\)

-   ACTIVE: the full sync mode is configured and active




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

LAST\_SAVEPOINT\_VERSION



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the current savepoint version.



</td>
</tr>
<tr>
<td valign="top">

LAST\_SAVEPOINT\_LOG\_POSITION



</td>
<td valign="top">

BIGINT\(19\)



</td>
<td valign="top">

Displays the current savepoint log position.



</td>
</tr>
<tr>
<td valign="top">

LAST\_SAVEPOINT\_START\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the current savepoint timestamp.



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

Displays the shipped log positon.



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

REPLAYED\_LOG\_POSITION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the log end position of the last known replayed log buffer on the secondary site.



</td>
</tr>
<tr>
<td valign="top">

REPLAYED\_LOG\_POSITION\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the timestamp of the last known replayed log buffer on the secondary site.



</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_SAVEPOINT\_VERSION



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the shipped savepoint version.



</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_SAVEPOINT\_LOG\_POSITION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the shipped savepoint log position.



</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_SAVEPOINT\_START\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the shipped savepoint start time.



</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_FULL\_REPLICA\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the shipped full replica count.



</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_FULL\_REPLICA\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the shipped full replica size in bytes.



</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_FULL\_REPLICA\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the shipped full replica duration in microseconds.



</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_LAST\_FULL\_REPLICA\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the shipped last full replica size in bytes.



</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_LAST\_FULL\_REPLICA\_START\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the shipped last full replica start time.



</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_LAST\_FULL\_REPLICA\_END\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the shipped last full replica end time.



</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_DELTA\_REPLICA\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the shipped delta replica count.



</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_DELTA\_REPLICA\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the shipped delta replica size in bytes.



</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_DELTA\_REPLICA\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the shipped delta replica duration in microseconds.



</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_LAST\_DELTA\_REPLICA\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the shipped last delta replica size in bytes.



</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_LAST\_DELTA\_REPLICA\_START\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the shipped last delta replica start time.



</td>
</tr>
<tr>
<td valign="top">

SHIPPED\_LAST\_DELTA\_REPLICA\_END\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the shipped last delta replica end time.



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

Displays the number of times the asynchronous replication buffer was full.



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

Displays the maximum replication backlog in bytes.



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

Displays the maximum replication backlog in microseconds.



</td>
</tr>
<tr>
<td valign="top">

REPLAY\_BACKLOG\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size, in bytes, of all log buffers that have been shipped to the secondary site but have not yet been replayed on the scondary site.



</td>
</tr>
<tr>
<td valign="top">

MAX\_REPLAY\_BACKLOG\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the maximumsize, in bytes, of the REPLAY\_BACKLOG\_SIZE since the system startup.



</td>
</tr>
<tr>
<td valign="top">

REPLAY\_BACKLOG\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the time difference, in microseconds, between the time of the last shipped log buffer and the last replayed log buffer on the secondary site.



</td>
</tr>
<tr>
<td valign="top">

MAX\_REPLAY\_BACKLOG\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the maximum time, in microseconds, of the REPLAY\_BACKLOG\_TIME since the system startup.



</td>
</tr>
</table>

