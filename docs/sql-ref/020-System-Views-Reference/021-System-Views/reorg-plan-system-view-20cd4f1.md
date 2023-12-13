<!-- loio20cd4f11751910148df8d7b88529c921 -->

# REORG\_PLAN System View

Provides current plan information for landscape reorganization.



<a name="loio20cd4f11751910148df8d7b88529c921___r_e_o_r_g__p_l_a_n_1struct_REORG_PLAN"/>

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

STEP\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the step ID.

</td>
</tr>
<tr>
<td valign="top">

STEP\_GROUP

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the step group.

</td>
</tr>
<tr>
<td valign="top">

PRECONDITION

</td>
<td valign="top">

NVARCHAR\(1024\)

</td>
<td valign="top">

Displays the precondition of the specified step.

</td>
</tr>
<tr>
<td valign="top">

SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the table name.

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

Displays the schema name.

</td>
</tr>
<tr>
<td valign="top">

NEW\_PARTITION\_SPEC

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the new partition specification.

</td>
</tr>
<tr>
<td valign="top">

OLD\_PARTITION\_SPEC

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the old partition specification.

</td>
</tr>
<tr>
<td valign="top">

PARTITION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the partition ID.

</td>
</tr>
<tr>
<td valign="top">

NEW\_HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the host where the table/partition is moved to.

</td>
</tr>
<tr>
<td valign="top">

NEW\_PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the port where the table/partition is moved to.

</td>
</tr>
<tr>
<td valign="top">

OLD\_HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the host where the table/partition is located.

</td>
</tr>
<tr>
<td valign="top">

OLD\_PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the port where the table/partition is located.

</td>
</tr>
</table>



<a name="loio20cd4f11751910148df8d7b88529c921___r_e_o_r_g__p_l_a_n_1fulldesc_REORG_PLAN"/>

## Additional Information

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

This view contains the last table redistribution plan generated with this database connection. The contents of the session are stored temporarily and are deleted when the connection is closed.

**Related Information**  


[REORG\_GENERATE\_OVERVIEW System View](reorg-generate-overview-system-view-176f257.md "Tracks automated and administrator calls to the REORG_GENERATE procedure.")

[REORG\_OVERVIEW System View](reorg-overview-system-view-20ccfa2.md "Provides an overview of landscape redistributions.")

[REORG\_PLAN\_INFOS System View](reorg-plan-infos-system-view-20cd27f.md "Provides additional information about the current landscape reorganization plan.")

[REORG\_STEPS System View](reorg-steps-system-view-20cd6dd.md "Contains the executed or to be executed table redistribution plan items.")

[M\_REORG\_ALGORITHMS System View](../022-Monitoring-Views/m-reorg-algorithms-system-view-20b9ec5.md "Provides information about landscape redistribution algorithms.")

