<!-- loioc4bec1f4c1fd4eb38c738856e49c8177 -->

# AGENTS System View

Lists active data provisioning agents in the system.



<a name="loioc4bec1f4c1fd4eb38c738856e49c8177__section_ivh_1vn_bhb"/>

## Structure


<table>
<tr>
<th valign="top">

Column

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

AGENT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the agent name.

</td>
</tr>
<tr>
<td valign="top">

PROTOCOL

</td>
<td valign="top">

NVARCHAR\(4\)

</td>
<td valign="top">

Displays the protocol for communication with SAP HANA database: TCP/HTTP.

</td>
</tr>
<tr>
<td valign="top">

AGENT\_HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the agent host specified when using TCP.

</td>
</tr>
<tr>
<td valign="top">

AGENT\_PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the agent port number specified when using TCP.

</td>
</tr>
<tr>
<td valign="top">

IS\_SSL\_ENABLED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the agent listening on the TCP port uses SSL: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

AGENT\_GROUP\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the clustering group to which the agent belongs.

</td>
</tr>
</table>



<a name="loioc4bec1f4c1fd4eb38c738856e49c8177__section_eg3_phc_bzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[AGENT\_CONFIGURATION System View](agent-configuration-system-view-fee165a.md "Provides agent configuration information.")

[AGENT\_GROUPS System View](agent-groups-system-view-efefb22.md "Lists active data provisioning agent groups in the system.")

[M\_AGENTS System View](../022-Monitoring-Views/m-agents-system-view-a866f34.md "Provides agent host information.")

