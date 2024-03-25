<!-- loio20cd6dd3751910149301cfd0bce9c079 -->

# REORG\_STEPS System View

Contains the executed or to be executed table redistribution plan items.



<a name="loio20cd6dd3751910149301cfd0bce9c079___r_e_o_r_g__s_t_e_p_s_1struct_REORG_STEPS"/>

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

REORG\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the reorg ID.

</td>
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

Displays the ID of the table redistribution group of steps that the item belongs to.

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

Indicates the preconditions that have to be fulfilled before the table redistribution step can be executed.

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

Displays the schema name.

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

Displays the table name.

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

Returns the new partition specification.

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

Returns the old partition specification.

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

Displays the host where the table/partition was located.

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

Displays the port where the table/partition was located.

</td>
</tr>
<tr>
<td valign="top">

STATUS

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the status message.

</td>
</tr>
<tr>
<td valign="top">

ERROR

</td>
<td valign="top">

NVARCHAR\(1024\)

</td>
<td valign="top">

Displays the error message.

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

Specifies the UTC timestamp when the plan execution started.

</td>
</tr>
<tr>
<td valign="top">

END\_DATE

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Specifies the UTC timestamp when the plan execution stopped.

</td>
</tr>
</table>



<a name="loio20cd6dd3751910149301cfd0bce9c079__section_kkf_31p_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[REORG\_GENERATE\_OVERVIEW System View](reorg-generate-overview-system-view-176f257.md "Tracks automated and administrator calls to the REORG_GENERATE procedure.")

[REORG\_OVERVIEW System View](reorg-overview-system-view-20ccfa2.md "Provides an overview of landscape redistributions.")

[REORG\_PLAN System View](reorg-plan-system-view-20cd4f1.md "Provides current plan information for landscape reorganization.")

[REORG\_PLAN\_INFOS System View](reorg-plan-infos-system-view-20cd27f.md "Provides additional information about the current landscape reorganization plan.")

[M\_REORG\_ALGORITHMS System View](../022-Monitoring-Views/m-reorg-algorithms-system-view-20b9ec5.md "Provides information about landscape redistribution algorithms.")

