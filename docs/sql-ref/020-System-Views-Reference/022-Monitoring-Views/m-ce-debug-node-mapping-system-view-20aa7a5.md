<!-- loio20aa7a5b751910148e10f97a350b0f7f -->

# M\_CE\_DEBUG\_NODE\_MAPPING System View

Provides information about node mapping between calculation nodes and Runtime nodes after execution.



<a name="loio20aa7a5b751910148e10f97a350b0f7f___m__c_e__d_e_b_u_g__n_o_d_e__m_a_p_p_i_n_g_1struct_M_CE_DEBUG_NODE_MAPPING"/>

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

STATEMENT\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the statement ID.

</td>
</tr>
<tr>
<td valign="top">

SCENARIO\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the scenario name.

</td>
</tr>
<tr>
<td valign="top">

NODE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the calculation node name.

</td>
</tr>
<tr>
<td valign="top">

NODE\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the calculation node type \(ROOT, TEMPLATE, or CALC\_DS\).

</td>
</tr>
<tr>
<td valign="top">

SUCC\_SCENARIO\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the successor scenario name.

</td>
</tr>
<tr>
<td valign="top">

SUCC\_NODE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the successor calculation node name.

</td>
</tr>
<tr>
<td valign="top">

RUNTIME\_NODE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the runtime calculation node name.

</td>
</tr>
<tr>
<td valign="top">

RUNTIME\_NODE\_JSON

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the JSON string representing the calculation node.

</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the execution timestamp.

</td>
</tr>
</table>

**Related Information**  


[M\_CE\_DEBUG\_INFOS System View](m-ce-debug-infos-system-view-20aa1f2.md "Provides debug information after the execution of a calculation scenario.")

[M\_CE\_DEBUG\_JSONS System View](m-ce-debug-jsons-system-view-20aa4be.md "Provides all available JSONS (original, instantiated, or optimized) of a scenario for a concrete query.")

[M\_DEBUG\_SESSIONS System View](m-debug-sessions-system-view-20aeae8.md "Provides an overview of debug sessions and their properties.")

[M\_DEBUG\_CONNECTIONS System View](m-debug-connections-system-view-20ae867.md "Provides an overview of connections used per debug session.")

[SQLScript Debugger](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/77b84f65439d4ead97c88b7452476674.html "") :arrow_upper_right:

