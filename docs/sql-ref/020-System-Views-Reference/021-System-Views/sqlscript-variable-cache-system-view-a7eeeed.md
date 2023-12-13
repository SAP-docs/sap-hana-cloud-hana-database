<!-- loioa7eeeedda0764a2d94b793880b14a5b6 -->

# SQLSCRIPT\_VARIABLE\_CACHE System view

Provides information about procedures and functions that have variable caches defined.



<a name="loioa7eeeedda0764a2d94b793880b14a5b6___q_u_e_r_y__p_l_a_n_s_1struct_QUERY_PLANS"/>

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

SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema of the target object.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the target object name.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the target object type: PROCEDURE/FUNCTION.

</td>
</tr>
<tr>
<td valign="top">

VARIABLE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the variable to be cached.

</td>
</tr>
<tr>
<td valign="top">

VARIABLE\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the type of variable.

</td>
</tr>
<tr>
<td valign="top">

ENABLE\_MODE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the activation mode: ENABLED, DISABLED, or AUTOMATIC.

</td>
</tr>
</table>



<a name="loioa7eeeedda0764a2d94b793880b14a5b6__section_yg2_rvz_2zb"/>

## Additional Information

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_SQLSCRIPT\_VARIABLE\_CACHE System view](../022-Monitoring-Views/m-sqlscript-variable-cache-system-view-9fb8ca5.md "Provides runtime information about procedures and functions that have variable caches defined.")

[Procedure Result Cache](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/23bd07d4f4a1444ab64ca580373e8efc.html "Procedure Result Cache (PRC) is a server-wide in-memory cache that caches the output arguments of procedure calls using the input arguments as keys.") :arrow_upper_right:

[Deterministic Procedure Cache](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/8809a2a02e1b49d9a3fc68bb135f430d.html "") :arrow_upper_right:

