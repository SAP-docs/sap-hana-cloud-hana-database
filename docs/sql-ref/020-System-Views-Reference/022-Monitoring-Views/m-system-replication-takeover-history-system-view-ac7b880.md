<!-- loioac7b8801620a4d2c86c2453f3a79768a -->

# M\_SYSTEM\_REPLICATION\_TAKEOVER\_HISTORY System View

Provides access to a history of HSR takeover executions.



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

TAKEOVER\_START\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the start time of the takeover command. This value matches akeovers that are executed within the same system takeover process.

</td>
</tr>
<tr>
<td valign="top">

TAKEOVER\_END\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the end time of the takeover command.

</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_START\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the execution start time for takeover of the transaction domain.

</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_END\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the execution end time for takeover of the transaction domain.

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

Displays the generated ID of the secondary site at takeover time.

</td>
</tr>
<tr>
<td valign="top">

SITE \_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the logical name provided by the site administrator at takeover time.

</td>
</tr>
<tr>
<td valign="top">

COORDINATOR\_NAMESERVER\_HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the coordinator nameserver host at takeover time.

</td>
</tr>
<tr>
<td valign="top">

VERSION

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the SAP HANA version for the site that is executing the takeover.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_SITE\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the generated ID of the source site at takeover time.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_SITE \_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the logical name for the source site provided by the site administrator at takeover time.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_COORDINATOR\_NAMESERVER\_HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the source site coordinator nameserver host at takeover time.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_VERSION

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the source site SAP HANA version.

</td>
</tr>
<tr>
<td valign="top">

TAKEOVER\_TYPE

</td>
<td valign="top">

NVARCHAR\(10\)

</td>
<td valign="top">

Displays how the system went online:

-   ONLINE: an online takeover
-   OFFLINE: an offline takeover
-   TIMETRAVEL: a timetravel takeover



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

Displays the replication mode at takeover time.

</td>
</tr>
<tr>
<td valign="top">

OPERATION\_MODE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the operation mode at takeover time.

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

Displays the replication status at takeover time.

</td>
</tr>
<tr>
<td valign="top">

LOG\_POSITION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the log position that has been reached by takeover.

</td>
</tr>
<tr>
<td valign="top">

LOG\_POSITION\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time reached by the takeover.

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

Displays the highest log position that has been shipped before executing takeover.

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

Displays the time of the last shipped log buffer before executing takeover.

</td>
</tr>
<tr>
<td valign="top">

COMMENTS

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays a comment for the remote subscription.

</td>
</tr>
</table>

**Related Information**  


[M\_SYSTEM\_OVERVIEW System View](m-system-overview-system-view-20c61f0.md "Provides an overview of system status including important resource usage information and alerts.")

[M\_SYSTEM\_REPLICATION System View](m-system-replication-system-view-4b263e6.md "Monitors system replication information.")

