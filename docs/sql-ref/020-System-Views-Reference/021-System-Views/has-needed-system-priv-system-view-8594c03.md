<!-- loio8594c03c9fd0446da0229427e6c4e970 -->

# HAS\_NEEDED\_SYSTEM\_PRIV System View

Displays whether the user has the needed system privilege.



<a name="loio8594c03c9fd0446da0229427e6c4e970__section_jkx_1pw_shb"/>

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

HAS\_PRIV

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays whether the user has the privilege.

</td>
</tr>
</table>



<a name="loio8594c03c9fd0446da0229427e6c4e970__section_ac4_trb_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[PRIVILEGES System View](privileges-system-view-20cc29b.md "Provides information about available privileges.")

[System Privileges](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/cadbcfc38b084808b80b3551b1cd756e.html "System privileges control general system activities.") :arrow_upper_right:

