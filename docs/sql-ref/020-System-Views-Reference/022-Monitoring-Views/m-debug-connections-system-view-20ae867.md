<!-- loio20ae867f751910148f5df1118bc68c4f -->

# M\_DEBUG\_CONNECTIONS System View

Provides an overview of connections used per debug session.



<a name="loio20ae867f751910148f5df1118bc68c4f___m__d_e_b_u_g__c_o_n_n_e_c_t_i_o_n_s_1struct_M_DEBUG_CONNECTIONS"/>

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

CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the connection that is used for communication.

</td>
</tr>
<tr>
<td valign="top">

CONNECTION\_USAGE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Indicates whether this connection is used for debugger communication or debugging.

</td>
</tr>
<tr>
<td valign="top">

OPERATION

</td>
<td valign="top">

NVARCHAR\(512\)

</td>
<td valign="top">

Displays the operation that is currently running within this connection.

</td>
</tr>
</table>

**Related Information**  


[M\_DEBUG\_SESSIONS System View](m-debug-sessions-system-view-20aeae8.md "Provides an overview of debug sessions and their properties.")

[M\_CE\_DEBUG\_INFOS System View](m-ce-debug-infos-system-view-20aa1f2.md "Provides debug information after the execution of a calculation scenario.")

[M\_CE\_DEBUG\_JSONS System View](m-ce-debug-jsons-system-view-20aa4be.md "Provides all available JSONS (original, instantiated, or optimized) of a scenario for a concrete query.")

[SQLScript Debugger](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/77b84f65439d4ead97c88b7452476674.html "") :arrow_upper_right:

