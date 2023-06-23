<!-- loioa866f34db2f547ad87ef462ff9d352ec -->

# M\_AGENTS System View

Provides agent host information.




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

FREE\_PHYSICAL\_MEMORY



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the free physical memory on the agent host in bytes.



</td>
</tr>
<tr>
<td valign="top">

FREE\_SWAP\_SPACE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the free swap memory on the agent host in bytes.



</td>
</tr>
<tr>
<td valign="top">

LAST\_CONNECT\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the last successful connection time.



</td>
</tr>
<tr>
<td valign="top">

SYS\_TIMESTAMP



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the agent host timestamp in the agent host's local timezone.



</td>
</tr>
<tr>
<td valign="top">

USED\_PHYSICAL\_MEMORY



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the used physical memory on the agent host in bytes.



</td>
</tr>
<tr>
<td valign="top">

USED\_SWAP\_SPACE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the used swap memory on the agent host in bytes.



</td>
</tr>
<tr>
<td valign="top">

UTC\_TIMESTAMP



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the agent host timestamp in UTC.



</td>
</tr>
<tr>
<td valign="top">

AGENT\_VERSION



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the agent version.



</td>
</tr>
<tr>
<td valign="top">

AGENT\_STATUS



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the agent status.



</td>
</tr>
</table>

**Related Information**  


[AGENTS System View](../021-System-Views/agents-system-view-c4bec1f.md "Lists active data provisioning agents in the system.")

[AGENT\_CONFIGURATION System View](../021-System-Views/agent-configuration-system-view-fee165a.md "Provides agent configuration information.")

[AGENT\_GROUPS System View](../021-System-Views/agent-groups-system-view-efefb22.md "Lists active data provisioning agent groups in the system.")

