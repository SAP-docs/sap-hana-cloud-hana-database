<!-- loio365bd214980f44bc91d39ca5f0135a2e -->

# USERGROUP\_PARAMETERS System View

Provides the list of parameter sets defined for usergroups.



<a name="loio365bd214980f44bc91d39ca5f0135a2e___a_f_l__p_a_c_k_a_g_e_s_1struct_AFL_PACKAGES"/>

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

USERGROUP\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the usergroup.

</td>
</tr>
<tr>
<td valign="top">

PARAMETER\_SET\_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the name of the parameter set the parameter belongs to.

</td>
</tr>
<tr>
<td valign="top">

IS\_PARAMETER\_SET\_ENABLED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays if the parameter set is enabled for the usergroup: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

PARAMETER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the parameter.

</td>
</tr>
<tr>
<td valign="top">

PARAMETER\_VALUE

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the value of the parameter.

</td>
</tr>
</table>



<a name="loio365bd214980f44bc91d39ca5f0135a2e__section_phz_dcb_x2b"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

Users see different values in this view depending on their privileges, as follows:

-   Users with one of the following privileges can see everything for all usergroups: CATALOG READ, or USERGROUP OPERATOR

-   All other users see only information specific to the usergroup they are in.


**Related Information**  


[USERGROUPS System View](usergroups-system-view-ac342d0.md "Provides details on all user groups.")

[USERS System View](users-system-view-2102609.md "Lists all users.")

[CREATE USERGROUP Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-usergroup-statement-access-control-9869125.md "Creates a usergroup.")

[ALTER USERGROUP Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-usergroup-statement-access-control-aa94ca8.md "Alters a usergroup.")

[DROP USERGROUP Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-usergroup-statement-access-control-6dc0ada.md "Removes a user group from the database.")

[SQL Statements and Authorization for User Group Administration (Reference)](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/bdc34546fcdf4d24b58b1235dda68ec8.html "Creating and configuring user groups requires different combinations of privileges.") :arrow_upper_right:

