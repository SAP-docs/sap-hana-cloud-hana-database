<!-- loiob856cdd2d8bf44c1a79dac7976f10119 -->

# AUDIT\_ACTIONS System View

Provides information about all available audit actions.



<a name="loiob856cdd2d8bf44c1a79dac7976f10119__section_onv_rqf_rhb"/>

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

ACTION\_GROUP

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the ID of the group of audit actions.

</td>
</tr>
<tr>
<td valign="top">

ACTION\_GROUP\_DESCRIPTION

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the description for the group of audit actions.

</td>
</tr>
<tr>
<td valign="top">

ACTION\_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the audit action.

</td>
</tr>
<tr>
<td valign="top">

IS\_USER\_MANDATORY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the audit action needs a user specification: TRUE/FALSE

</td>
</tr>
<tr>
<td valign="top">

IS\_OBJECT\_MANDATORY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the audit action needs an object specification: TRUE/FALSE

</td>
</tr>
<tr>
<td valign="top">

IS\_DATABASE\_SUPPORTED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether this audit action can be used in an SAP-defined default audit policy: TRUE/FALSE

</td>
</tr>
<tr>
<td valign="top">

IS\_SCHEMA\_SUPPORTED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether this audit action can be specified for specific schemas: TRUE/FALSE

</td>
</tr>
</table>



<a name="loiob856cdd2d8bf44c1a79dac7976f10119__section_lky_sjc_bzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[AUDIT\_LOG System View](audit-log-system-view-d1fe124.md "Provides information about audit records, with the exception of XSA-auditing.")

[AUDIT\_POLICIES System View](audit-policies-system-view-209e4d3.md "Provides information about audit policies.")

[Auditing Activity in the SAP HANA Database](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/48fd6586304c4f859bf92d64d0cd8b08.html "Auditing allows you to monitor and record selected actions performed in the SAP HANA database, providing you with visibility on who did what in the database (or tried to do what) and when.") :arrow_upper_right:

