<!-- loio2f40fd348d534ac6a0405a0addfa341b -->

# M\_HA\_DR\_PROVIDERS System View

Provides information about loaded HA/DR providers.



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

PROVIDER\_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the HA/DR provider name.

</td>
</tr>
<tr>
<td valign="top">

PROVIDER\_COMPANY

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the HA/DR provider company name.

</td>
</tr>
<tr>
<td valign="top">

PROVIDER\_DESCRIPTION

</td>
<td valign="top">

NVARCHAR\(2000\)

</td>
<td valign="top">

Displays the HA/DR provider description.

</td>
</tr>
<tr>
<td valign="top">

PROVIDER\_VERSION

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays theHA/DR provider version.

</td>
</tr>
<tr>
<td valign="top">

PROVIDER\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the HA/DR provider type.

</td>
</tr>
<tr>
<td valign="top">

PROVIDER\_PATH

</td>
<td valign="top">

NVARCHAR\(512\)

</td>
<td valign="top">

Displays the HA/DR provider path.

</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_ORDER

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the HA/DR provider execution order.

</td>
</tr>
</table>



<a name="loio2f40fd348d534ac6a0405a0addfa341b__section_dtn_5nj_wbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

