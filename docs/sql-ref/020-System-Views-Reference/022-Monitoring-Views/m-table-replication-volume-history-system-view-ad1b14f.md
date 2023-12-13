<!-- loioad1b14fecfce470f8a67c52f583ec718 -->

# M\_TABLE\_REPLICATION\_VOLUME\_HISTORY System View

Displays detailed information on the history of the table replication volume.




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

SOURCE\_VOLUME\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the volume ID of the source. If value is greater than 2048, it means it is in a remote location. This value is applicable to remote table replication only.

</td>
</tr>
<tr>
<td valign="top">

REPLICA\_VOLUME\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the volume ID of replica. If the value is greater than 2048, it means that it is a remote location.

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

Displays the remote source name of the source system. This value only appears if SOURCE\_VOLUME\_ID or REPLICA\_VOLUME\_ID is greater than 2048.

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

Displays the remote source schema name of the source system. This value only appears if SOURCE\_VOLUME\_ID or REPLICA\_VOLUME\_ID is greater than 2048.

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

Displays the remote source name of the replica system. This value only appears shown if SOURCE\_VOLUME\_ID or REPLICA\_VOLUME\_ID is greater than 2048.

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

Displays the remote source schema name of the replica system. This value only appears if SOURCE\_VOLUME\_ID or REPLICA\_VOLUME\_ID is greater than 2048.

</td>
</tr>
<tr>
<td valign="top">

REPLICATION\_STATUS\_CHANGE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time when the replication status was changed.

</td>
</tr>
<tr>
<td valign="top">

REPLICATION\_STATUS

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the replication status of the replica volume. Values are: DISABLED, ENABLING, ENABLED, ENABLED\_BUT\_UNAVAILABLE.

</td>
</tr>
<tr>
<td valign="top">

REPLICATION\_STATUS\_CHANGE\_REASON

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the reason for the change in replication status. Values are: EXCEPTION, EXCEPTION\_CLEANUP, COMMAND, RESTART, SHUTDOWN, INTERNAL, INITIAL

</td>
</tr>
<tr>
<td valign="top">

ERROR\_CODE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the error code in the event a replication volume related to the exception is turned off.

</td>
</tr>
<tr>
<td valign="top">

ERROR\_MESSAGE

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the error message in case the event a replication volume related to the exception is turned off.

</td>
</tr>
</table>

