<!-- loio20ccfa20751910149c2de2cb9ce26e78 -->

# REORG\_OVERVIEW System View

Provides an overview of landscape redistributions.



<a name="loio20ccfa20751910149c2de2cb9ce26e78___r_e_o_r_g__o_v_e_r_v_i_e_w_1struct_REORG_OVERVIEW"/>

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

Displays the unique identifier for the executed reorg plan.

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

Displays the status of the plan execution:

-   STARTED: The plan execution has started.

-   FINISHED: The plan execution finished successfully.

-   FAILED: The plan execution is treated as failed.




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

Displays the UTC timestamp when the plan execution started.

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

Displays the UTC timestamp when plan execution stopped. This field remains empty while the execution is running or in the case of reboots during plan execution.

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

Displays the user that executed the table redistribution.

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

Displays the ID of the algorithm for the table redistribution.

</td>
</tr>
<tr>
<td valign="top">

PARAMETERS

</td>
<td valign="top">

NVARCHAR\(1024\)

</td>
<td valign="top">

Displays the parameters given for the table redistribution call.

</td>
</tr>
</table>



<a name="loio20ccfa20751910149c2de2cb9ce26e78___r_e_o_r_g__o_v_e_r_v_i_e_w_1fulldesc_REORG_OVERVIEW"/>

## Additional Information

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

This view contains information about table redistribution executions on this system and stores every call to the REORG\_EXECUTE statement. You can use this view to determine execution durations and the status of each table redistribution on this system. Only executed plan information is stored and calls of REORG\_GENERATE without REORG\_EXECUTE are not displayed.

**Related Information**  


[REORG\_GENERATE\_OVERVIEW System View](reorg-generate-overview-system-view-176f257.md "Tracks automated and administrator calls to the REORG_GENERATE procedure.")

[REORG\_PLAN System View](reorg-plan-system-view-20cd4f1.md "Provides current plan information for landscape reorganization.")

[REORG\_PLAN\_INFOS System View](reorg-plan-infos-system-view-20cd27f.md "Provides additional information about the current landscape reorganization plan.")

[REORG\_STEPS System View](reorg-steps-system-view-20cd6dd.md "Contains the executed or to be executed table redistribution plan items.")

[M\_REORG\_ALGORITHMS System View](../022-Monitoring-Views/m-reorg-algorithms-system-view-20b9ec5.md "Provides information about landscape redistribution algorithms.")

