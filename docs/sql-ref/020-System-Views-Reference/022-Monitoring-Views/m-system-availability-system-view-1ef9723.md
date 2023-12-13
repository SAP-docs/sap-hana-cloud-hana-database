<!-- loio1ef9723a03214bd889c4fb8947765aa4 -->

# M\_SYSTEM\_AVAILABILITY System View

Monitors the availability of the system.



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

EVENT\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time that this event was originally traced.

</td>
</tr>
<tr>
<td valign="top">

GUID

</td>
<td valign="top">

NVARCHAR \(36\)

</td>
<td valign="top">

Displays the event guide.

</td>
</tr>
<tr>
<td valign="top">

IS\_ORIGIN

</td>
<td valign="top">

NVARCHAR \(5\)

</td>
<td valign="top">

Displays the original entry.

</td>
</tr>
<tr>
<td valign="top">

TRACE\_HOST

</td>
<td valign="top">

NVARCHAR \(64\)

</td>
<td valign="top">

Displays the host the trace file was read from.

</td>
</tr>
<tr>
<td valign="top">

EVENT\_NAME

</td>
<td valign="top">

NVARCHAR \(32\)

</td>
<td valign="top">

Displays the event name:

-   database\_add

-   database\_remove

-   failover\_begin

-   failover\_end

-   host\_remove\_prepare

-   host\_remove\_reorg

-   host\_remove\_abort

-   host\_remove

-   ping

-   recovery\_begin

-   recovery\_end

-   service\_remove

-   service\_remove\_abort

-   service\_remove\_prepare

-   service\_remove\_reorg

-   service\_started

-   service\_starting

-   service\_stopped

-   service\_stopping

-   service\_unknown




</td>
</tr>
<tr>
<td valign="top">

EVENT\_DETAIL

</td>
<td valign="top">

NVARCHAR \(256\)

</td>
<td valign="top">

Displays any additional information.

</td>
</tr>
<tr>
<td valign="top">

ERROR\_MESSAGE

</td>
<td valign="top">

NVARCHAR \(256\)

</td>
<td valign="top">

Displays the error message.

</td>
</tr>
<tr>
<td valign="top">

SYSTEM\_ACTIVE

</td>
<td valign="top">

NVARCHAR \(16\)

</td>
<td valign="top">

Displays the system active status: NO, YES, UNKNOWN, STARTING, or STOPPING.

</td>
</tr>
<tr>
<td valign="top">

SYSTEM\_STATUS

</td>
<td valign="top">

NVARCHAR \(16\)

</td>
<td valign="top">

Displays the system status:

-   ERROR

-   IGNORE

-   INFO

-   OK

-   WARNING




</td>
</tr>
<tr>
<td valign="top">

HOST

</td>
<td valign="top">

NVARCHAR \(64\)

</td>
<td valign="top">

Displays the host that traced the event.

</td>
</tr>
<tr>
<td valign="top">

HOST\_ACTIVE

</td>
<td valign="top">

NVARCHAR \(16\)

</td>
<td valign="top">

Displays the host active status.

</td>
</tr>
<tr>
<td valign="top">

HOST\_STATUS

</td>
<td valign="top">

NVARCHAR \(16\)

</td>
<td valign="top">

Displays the host status.

</td>
</tr>
<tr>
<td valign="top">

DATABASE\_NAME

</td>
<td valign="top">

NVARCHAR \(256\)

</td>
<td valign="top">

Displays the database name.

</td>
</tr>
<tr>
<td valign="top">

DATABASE\_ACTIVE

</td>
<td valign="top">

NVARCHAR \(16\)

</td>
<td valign="top">

Displays the database active status.

</td>
</tr>
<tr>
<td valign="top">

SERVICE\_NAME

</td>
<td valign="top">

NVARCHAR \(32\)

</td>
<td valign="top">

Displays the service name.

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

Displays the service port.

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

SERVICE\_ACTIVE

</td>
<td valign="top">

NVARCHAR \(16\)

</td>
<td valign="top">

Displays the service active status.

</td>
</tr>
<tr>
<td valign="top">

HOST\_CONFIG\_ROLES

</td>
<td valign="top">

NVARCHAR \(64\)

</td>
<td valign="top">

Displays the configured host roles.

</td>
</tr>
<tr>
<td valign="top">

HOST\_ACTUAL\_ROLES

</td>
<td valign="top">

NVARCHAR \(64\)

</td>
<td valign="top">

Displays the actual host roles.

</td>
</tr>
<tr>
<td valign="top">

STORAGE\_CONFIG\_PARTITION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the configured storage partition.

</td>
</tr>
<tr>
<td valign="top">

STORAGE\_ACTUAL\_PARTITION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the actual storage partition.

</td>
</tr>
<tr>
<td valign="top">

TARGET\_HOST

</td>
<td valign="top">

NVARCHAR \(64\)

</td>
<td valign="top">

Displays the failover target host.

</td>
</tr>
<tr>
<td valign="top">

TARGET\_HOST\_CONFIG\_ROLES

</td>
<td valign="top">

NVARCHAR \(64\)

</td>
<td valign="top">

Displays the target host configuration roles.

</td>
</tr>
<tr>
<td valign="top">

TARGET\_HOST\_ACTUAL\_ROLES

</td>
<td valign="top">

NVARCHAR \(64\)

</td>
<td valign="top">

Displays the target host actual roles.

</td>
</tr>
<tr>
<td valign="top">

TARGET\_STORAGE\_CONFIG\_PARTITION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the target storage configuration partition.

</td>
</tr>
<tr>
<td valign="top">

TARGET\_STORAGE\_ACTUAL\_PARTITION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the target storage actual partition.

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

Displays the system replication site ID.

</td>
</tr>
</table>

**Related Information**  


[M\_SYSTEM\_DATA\_STATISTICS System View](m-system-data-statistics-system-view-b354762.md "Lists data statistics generated by the server when you query a column and row store object.")

[M\_SYSTEM\_INFORMATION\_STATEMENTS System View](m-system-information-statements-system-view-20c5dfa.md "Provides system information statements.")

[M\_SYSTEM\_OVERVIEW System View](m-system-overview-system-view-20c61f0.md "Provides an overview of system status including important resource usage information and alerts.")

