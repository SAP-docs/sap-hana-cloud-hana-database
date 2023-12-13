<!-- loiofee165a6ad61402d879d129b00b7d881 -->

# AGENT\_CONFIGURATION System View

Provides agent configuration information.



<a name="loiofee165a6ad61402d879d129b00b7d881__section_x5h_dvn_bhb"/>

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

KEY

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the agent property key.

</td>
</tr>
<tr>
<td valign="top">

VALUE

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the agent property value.

</td>
</tr>
</table>



<a name="loiofee165a6ad61402d879d129b00b7d881__section_sfn_xhc_bzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[AGENTS System View](agents-system-view-c4bec1f.md "Lists active data provisioning agents in the system.")

[AGENT\_GROUPS System View](agent-groups-system-view-efefb22.md "Lists active data provisioning agent groups in the system.")

[M\_AGENTS System View](../022-Monitoring-Views/m-agents-system-view-a866f34.md "Provides agent host information.")

