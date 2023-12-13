<!-- loioea60f23498704b6ea225f44595151f61 -->

# INVALID\_CONNECT\_ATTEMPTS System View

Provides the number of invalid connection attempts for a user between two successful connections.



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

USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the user.

</td>
</tr>
<tr>
<td valign="top">

SUCCESSFUL\_CONNECT\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time the valid connection was attempted.

</td>
</tr>
<tr>
<td valign="top">

INVALID\_CONNECT\_ATTEMPTS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of invalid connection attempts for this user since the last successful connection.

</td>
</tr>
</table>



<a name="loioea60f23498704b6ea225f44595151f61__section_acl_srb_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[CONNECT Statement \(Session Management\)](../../010-SQL-Reference/012-SQL-Statements/connect-statement-session-management-20d3b9a.md "Connects to a database instance.")

[M\_CONNECTIONS System View](../022-Monitoring-Views/m-connections-system-view-20abcf1.md "Provides detailed information on connections between a client and a database. Information includes: connection status, client information, connection type, and resource utilization.")

[Session-Specific Information for Connections](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2023_4_QRC/en-US/d80b8d7ddf944f55801a534b3ce036e3.html "Set session-specific client information on SAP HANA remote source connections.") :arrow_upper_right:

