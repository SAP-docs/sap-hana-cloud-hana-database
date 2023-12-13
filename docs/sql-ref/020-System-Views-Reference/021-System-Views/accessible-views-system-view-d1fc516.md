<!-- loiod1fc5168d2951014ae99845a73cf554b -->

# ACCESSIBLE\_VIEWS System View

Provides information about accessible views for a given user.



<a name="loiod1fc5168d2951014ae99845a73cf554b___a_c_c_e_s_s_i_b_l_e__v_i_e_w_s_1struct_ACCESSIBLE_VIEWS"/>

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

USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the user who is authorized to access the view.

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

Displays the schema name of the view.

</td>
</tr>
<tr>
<td valign="top">

VIEW\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the view.

</td>
</tr>
<tr>
<td valign="top">

ANALYTICAL\_PRIVILEGE\_NEEDED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether this view is secured by means of analytical privileges.

</td>
</tr>
</table>



<a name="loiod1fc5168d2951014ae99845a73cf554b__section_m5x_fdk_h2b"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

This view requires an equal predicate on USER\_NAME.

**Related Information**  


[System Views for Verifying Users' Authorization](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2023_4_QRC/en-US/ddae823e3b27477ea4c949607eebc435.html "You can query several system views to get detailed information about exactly which privileges and roles users have and how they come to have them. This can help you to understand why a user is authorized to perform particular actions, access particular data, or not.") :arrow_upper_right:

