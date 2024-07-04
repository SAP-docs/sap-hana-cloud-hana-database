<!-- loio03aa3adec2ba48ee9e2e25ba26df6cb7 -->

# M\_ABSTRACT\_SQL\_PLAN\_OVERVIEW System View

Provides the status of each Plan Stability Manager on every index server in SAP HANA.



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

STATE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the Plan Stability Manager state:

-   READY: plan stability is enabled.
-   CAPTURE: the abstract SQL plans are being captured.
-   APPLY: the captured abstract SQL plans are being applied for execution plan generation.
-   IMPORT: the abstract SQL plans are being imported.
-   MIGRATION: the abstract SQL plans are being migrated.
-   UPDATE\_LOCATION: the location information of the captured abstract SQL plans is being updated.



</td>
</tr>
<tr>
<td valign="top">

TOTAL\_PLAN\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of enabled and disabled loaded plans.

</td>
</tr>
<tr>
<td valign="top">

ENABLED\_PLAN\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of enabled plans.

</td>
</tr>
<tr>
<td valign="top">

DISABLED\_PLAN\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of disabled plans.

</td>
</tr>
<tr>
<td valign="top">

ALLOCATED\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the allocated memory size, in bytes, being used by plan stability.

</td>
</tr>
<tr>
<td valign="top">

LAST\_APPLY\_START\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last APPLY start time.

</td>
</tr>
<tr>
<td valign="top">

LAST\_APPLY\_STOP\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last APPLY stop time.

</td>
</tr>
<tr>
<td valign="top">

LAST\_CAPTURE\_START\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last CAPTURE start time.

</td>
</tr>
<tr>
<td valign="top">

LAST\_CAPTURE\_STOP\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last CAPTURE stop time.

</td>
</tr>
<tr>
<td valign="top">

FILTERS

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the application filters of the abstract SQL plan.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_RELATED\_OBJECT\_DEFINITION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of related object definitions.

</td>
</tr>
<tr>
<td valign="top">

INVALID\_RELATED\_OBJECT\_DEFINITION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of invalid related object definitions.

</td>
</tr>
<tr>
<td valign="top">

RELATED\_OBJECT\_TABLE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the allocated memory size of the table, in bytes, being used for related object definitions.

</td>
</tr>
<tr>
<td valign="top">

PLAN\_TABLE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the allocated memory size of the table, in bytes, being used for plans.

</td>
</tr>
</table>



<a name="loio03aa3adec2ba48ee9e2e25ba26df6cb7__section_nw3_zfh_4bc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[ABSTRACT\_SQL\_PLANS System View](../021-System-Views/abstract-sql-plans-system-view-ba830ef.md "Lists information about abstract SQL plans.")

[M\_ABSTRACT\_SQL\_PLAN\_STATISTICS System View](m-abstract-sql-plan-statistics-system-view-35af7f2.md "Provides SQL query runtime statistics.")

