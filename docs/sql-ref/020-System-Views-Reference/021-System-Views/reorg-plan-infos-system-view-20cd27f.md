<!-- loio20cd27f275191014b538ef5faa5b00a2 -->

# REORG\_PLAN\_INFOS System View

Provides additional information about the current landscape reorganization plan.



<a name="loio20cd27f275191014b538ef5faa5b00a2___r_e_o_r_g__p_l_a_n__i_n_f_o_s_1struct_REORG_PLAN_INFOS"/>

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

KEY

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the key.

</td>
</tr>
<tr>
<td valign="top">

VALUE

</td>
<td valign="top">

NVARCHAR\(1024\)

</td>
<td valign="top">

Displays the value.

</td>
</tr>
</table>



<a name="loio20cd27f275191014b538ef5faa5b00a2___r_e_o_r_g__p_l_a_n__i_n_f_o_s_1fulldesc_REORG_PLAN_INFOS"/>

## Additional Information

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

This view contains information about the last table redistribution plan generation with this database connection. The contents are stored for the current session and are deleted when the connection is closed. The following list describes the contents of the individual lines of this view \(***VALUE***\), as identified by ***KEY***:


<dl>
<dt><b>

MOVE\_PHYSICAL

</b></dt>
<dd>

Indicates that all move operations during plan execution are executed as physical moves. Possible values are 0 or 1.



</dd>
</dl>


<dl>
<dt><b>

ALGORITHM\_ID

</b></dt>
<dd>

Displays the ID of the reorg algorithm that is used for generating the corresponding table redistribution plan.



</dd>
</dl>


<dl>
<dt><b>

PARAMETERS

</b></dt>
<dd>

Displays the parameter information of the last table redistribution plan generation call.



</dd>
</dl>

**Related Information**  


[REORG\_GENERATE\_OVERVIEW System View](reorg-generate-overview-system-view-176f257.md "Tracks automated and administrator calls to the REORG_GENERATE procedure.")

[REORG\_OVERVIEW System View](reorg-overview-system-view-20ccfa2.md "Provides an overview of landscape redistributions.")

[REORG\_PLAN System View](reorg-plan-system-view-20cd4f1.md "Provides current plan information for landscape reorganization.")

[REORG\_STEPS System View](reorg-steps-system-view-20cd6dd.md "Contains the executed or to be executed table redistribution plan items.")

[M\_REORG\_ALGORITHMS System View](../022-Monitoring-Views/m-reorg-algorithms-system-view-20b9ec5.md "Provides information about landscape redistribution algorithms.")

