<!-- loio176f2576a2094def8f7b5a444d461464 -->

# REORG\_GENERATE\_OVERVIEW System View

Tracks automated and administrator calls to the REORG\_GENERATE procedure.



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

GENERATE\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the generated ID. This is an increasing, unique number used to identify the call to the REORG\_GENERATE procedure.

</td>
</tr>
<tr>
<td valign="top">

START\_DATE

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the UTC timestamp when the call reached the engine.

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

Displays the connection ID that initiates the call to the REORG\_GENERATE procedure.

</td>
</tr>
<tr>
<td valign="top">

USER

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the user name.

</td>
</tr>
<tr>
<td valign="top">

ALGORITHM\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the table redistribution algorithm ID used the in the call.

</td>
</tr>
<tr>
<td valign="top">

REORG\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the reorganization ID used to select the corresponding executed table redistribution plan.

</td>
</tr>
<tr>
<td valign="top">

PARAMETERS

</td>
<td valign="top">

NVARCHAR\(4096\)

</td>
<td valign="top">

Displays the table redistribution parameters that are used in the call.

</td>
</tr>
<tr>
<td valign="top">

DETAIL

</td>
<td valign="top">

NVARCHAR\(1024\)

</td>
<td valign="top">

Displays the detailed text for additional information.

</td>
</tr>
</table>



<a name="loio176f2576a2094def8f7b5a444d461464__section_xmh_f1p_dzb"/>

## Additional Information

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[REORG\_OVERVIEW System View](reorg-overview-system-view-20ccfa2.md "Provides an overview of landscape redistributions.")

[REORG\_PLAN System View](reorg-plan-system-view-20cd4f1.md "Provides current plan information for landscape reorganization.")

[REORG\_PLAN\_INFOS System View](reorg-plan-infos-system-view-20cd27f.md "Provides additional information about the current landscape reorganization plan.")

[REORG\_STEPS System View](reorg-steps-system-view-20cd6dd.md "Contains the executed or to be executed table redistribution plan items.")

[M\_REORG\_ALGORITHMS System View](../022-Monitoring-Views/m-reorg-algorithms-system-view-20b9ec5.md "Provides information about landscape redistribution algorithms.")

[PROCEDURES System View](procedures-system-view-20cc87c.md "Provides information about available stored procedures.")

