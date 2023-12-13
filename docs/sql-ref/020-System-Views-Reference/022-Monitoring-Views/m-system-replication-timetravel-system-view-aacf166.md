<!-- loioaacf1660ac8144d38792a5760bef88bd -->

# M\_SYSTEM\_REPLICATION\_TIMETRAVEL System View

Provides information about the valid time travel range for each service on a secondary site.



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

START\_SNAPSHOT\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the snapshot ID of the oldest commit timestamp on which timetravel can start.

</td>
</tr>
<tr>
<td valign="top">

START\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the oldest commit timestamp on which timetravel can start.

</td>
</tr>
<tr>
<td valign="top">

START\_REDO\_LOG\_POSITION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the oldest log position on which timetravel can start.

</td>
</tr>
<tr>
<td valign="top">

END\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the newest commit timestamp which can be reached via timetravel.

</td>
</tr>
<tr>
<td valign="top">

END\_REDO\_LOG\_POSITION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the newest log position that can be reached via timetravel.

</td>
</tr>
<tr>
<td valign="top">

COORDINATOR\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the coordinator type: COORDINATOR if it is a transaction coordinator volume type or NONE if it is not a coordinator volume type.

</td>
</tr>
</table>

**Related Information**  


[M\_SYSTEM\_OVERVIEW System View](m-system-overview-system-view-20c61f0.md "Provides an overview of system status including important resource usage information and alerts.")

[M\_SYSTEM\_REPLICATION System View](m-system-replication-system-view-4b263e6.md "Monitors system replication information.")

[Application-Time Period Tables](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/2e37d6a82f7b48ccbfcc5a1a6ce490f5.html "Application-Time Period Tables allow you to manage and manipulate historical business data based on application-specific time periods which are independent of system time-stamps.") :arrow_upper_right:

