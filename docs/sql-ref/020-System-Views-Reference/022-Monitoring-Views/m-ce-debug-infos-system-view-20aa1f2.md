<!-- loio20aa1f2f751910149013f00b156fc9d1 -->

# M\_CE\_DEBUG\_INFOS System View

Provides debug information after the execution of a calculation scenario.



<a name="loio20aa1f2f751910149013f00b156fc9d1___m__c_e__d_e_b_u_g__i_n_f_o_s_1struct_M_CE_DEBUG_INFOS"/>

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

Displays the internal port number.



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

DEBUG\_TYPE\_MASK



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the bit mask indicating the type of debug information.



</td>
</tr>
<tr>
<td valign="top">

TABLE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the table name \(temporary intermediate result table\).



</td>
</tr>
<tr>
<td valign="top">

COLUMN\_NAMES



</td>
<td valign="top">

CLOB



</td>
<td valign="top">

Displays the column names.



</td>
</tr>
<tr>
<td valign="top">

TABLE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the table size in bytes \(temporary intermediate result table\).



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
<tr>
<td valign="top">

APPLICATION\_QUERY\_ID



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the application query ID.



</td>
</tr>
</table>

**Related Information**  


[M\_CE\_DEBUG\_JSONS System View](m-ce-debug-jsons-system-view-20aa4be.md "Provides all available JSONS (original, instantiated, or optimized) of a scenario for a concrete query.")

[M\_CE\_DEBUG\_NODE\_MAPPING System View](m-ce-debug-node-mapping-system-view-20aa7a5.md "Provides information about node mapping between calculation nodes and Runtime nodes after execution.")

[M\_DEBUG\_SESSIONS System View](m-debug-sessions-system-view-20aeae8.md "Provides an overview of debug sessions and their properties.")

[M\_DEBUG\_CONNECTIONS System View](m-debug-connections-system-view-20ae867.md "Provides an overview of connections used per debug session.")

[SQLScript Debugger](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/77b84f65439d4ead97c88b7452476674.html "") :arrow_upper_right:

