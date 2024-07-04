<!-- loio20aa4beb75191014b355de15abe3dd1c -->

# M\_CE\_DEBUG\_JSONS System View

Provides all available JSONS \(original, instantiated, or optimized\) of a scenario for a concrete query.



<a name="loio20aa4beb75191014b355de15abe3dd1c___m__c_e__d_e_b_u_g__j_s_o_n_s_1struct_M_CE_DEBUG_JSONS"/>

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

TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the JSON type: original, instantiated, optimized, or extrace.

</td>
</tr>
<tr>
<td valign="top">

MODEL\_JSON

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the JSON string representing the calculation scenario.

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



<a name="loio20aa4beb75191014b355de15abe3dd1c__section_knn_z1w_rbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_CE\_DEBUG\_INFOS System View](m-ce-debug-infos-system-view-20aa1f2.md "Provides debug information after the execution of a calculation scenario.")

[M\_CE\_DEBUG\_NODE\_MAPPING System View](m-ce-debug-node-mapping-system-view-20aa7a5.md "Provides information about node mapping between calculation nodes and Runtime nodes after execution.")

[M\_DEBUG\_SESSIONS System View](m-debug-sessions-system-view-20aeae8.md "Provides an overview of debug sessions and their properties.")

[M\_DEBUG\_CONNECTIONS System View](m-debug-connections-system-view-20ae867.md "Provides an overview of connections used per debug session.")

[SQLScript Debugger](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/77b84f65439d4ead97c88b7452476674.html "") :arrow_upper_right:

