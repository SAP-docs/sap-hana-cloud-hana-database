<!-- loio20aeae89751910148c86e4caa4b3eae8 -->

# M\_DEBUG\_SESSIONS System View

Provides an overview of debug sessions and their properties.



<a name="loio20aeae89751910148c86e4caa4b3eae8___m__d_e_b_u_g__s_e_s_s_i_o_n_s_1struct_M_DEBUG_SESSIONS"/>

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

DEBUG\_SESSION\_ID

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the landscape-wide unique identifier for debug session.

</td>
</tr>
<tr>
<td valign="top">

COMPILE\_MODE

</td>
<td valign="top">

NVARCHAR\(20\)

</td>
<td valign="top">

Displays the compilation handling of nested procedures.

</td>
</tr>
<tr>
<td valign="top">

TIMEOUT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the time in seconds after which the debug session will timeout and destroy itself.

</td>
</tr>
<tr>
<td valign="top">

ATTACH\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of debuggees the debugger is currently attached to.

</td>
</tr>
<tr>
<td valign="top">

ATTACH\_FILTER\_CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the connection ID the debugger is using to attach to connections.

</td>
</tr>
<tr>
<td valign="top">

ATTACH\_FILTER\_USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the connection user name the debugger is using to attach to connections.

</td>
</tr>
<tr>
<td valign="top">

ATTACH\_FILTER\_APPLICATION\_USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the application user name the debugger is using to attach to connections.

</td>
</tr>
<tr>
<td valign="top">

ATTACH\_FILTER\_DEBUG\_TOKEN

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the debug token the debugger is using to attach to connections.

</td>
</tr>
</table>



<a name="loio20aeae89751910148c86e4caa4b3eae8__section_nlf_s2n_vbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_DEBUG\_CONNECTIONS System View](m-debug-connections-system-view-20ae867.md "Provides an overview of connections used per debug session.")

[SQLScript Debugger](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/77b84f65439d4ead97c88b7452476674.html "") :arrow_upper_right:

