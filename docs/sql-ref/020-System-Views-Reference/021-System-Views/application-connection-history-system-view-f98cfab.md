<!-- loiof98cfabb024c46f6873b4e82c4d4f1be -->

# APPLICATION\_CONNECTION\_HISTORY System View

Provides stored application connection history information.



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

APPLICATION\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the application name.

</td>
</tr>
<tr>
<td valign="top">

CLIENT\_IP

</td>
<td valign="top">

NVARCHAR\(45\)

</td>
<td valign="top">

Displays the IP address of the client.

</td>
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

CONNECT\_DATE

</td>
<td valign="top">

DAYDATE

</td>
<td valign="top">

Displays the established date of the connection.

</td>
</tr>
<tr>
<td valign="top">

CONNECT\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the count of connections established in a day.

</td>
</tr>
</table>



<a name="loiof98cfabb024c46f6873b4e82c4d4f1be__section_hc5_mjc_bzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[APPLICATION\_ENCRYPTION\_KEYS System View](application-encryption-keys-system-view-d2c58ec.md "Provides information about encryption keys used by applications.")

[CONNECT Statement \(Session Management\)](../../010-SQL-Reference/012-SQL-Statements/connect-statement-session-management-20d3b9a.md "Connects to a database instance.")

[M\_CONNECTIONS System View](../022-Monitoring-Views/m-connections-system-view-20abcf1.md "Provides detailed information on connections between a client and a database. Information includes: connection status, client information, connection type, and resource utilization.")

