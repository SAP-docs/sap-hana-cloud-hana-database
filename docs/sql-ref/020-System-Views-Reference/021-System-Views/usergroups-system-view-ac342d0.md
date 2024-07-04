<!-- loioac342d0868b244b0b42e16b3dbb5d7bc -->

# USERGROUPS System View

Provides details on all user groups.



<a name="loioac342d0868b244b0b42e16b3dbb5d7bc___a_f_l__p_a_c_k_a_g_e_s_1struct_AFL_PACKAGES"/>

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

Displays the name of the user group.

</td>
</tr>
<tr>
<td valign="top">

USERGROUP\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the user group ID.

</td>
</tr>
<tr>
<td valign="top">

CREATOR

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the creator of the user group.

</td>
</tr>
<tr>
<td valign="top">

IS\_USER\_ADMIN\_ENABLED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether a user with the USER ADMIN system privilege can manage the specified user group: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_CLIENT\_CONNECT\_ENABLED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether a user in this user group is able to connect to the database: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

HAS\_CONNECT\_RESTRICTION

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether connect restrictions are defined for this user group: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

COMMENTS

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the description for the specified user group.

</td>
</tr>
</table>



<a name="loioac342d0868b244b0b42e16b3dbb5d7bc__section_qf1_hz1_x2b"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

Users see different values in this view depending on their privileges, as follows:

-   Users with one of the following privileges can see everything for all users:

    -   CATALOG READ system privilege
    -   OPERATOR object privilege on any user group

-   All other users see only information specific to their user group.


**Related Information**  


[USERS System View](users-system-view-2102609.md "Lists all users.")

[USERGROUP\_PARAMETERS System View](usergroup-parameters-system-view-365bd21.md "Provides the list of parameter sets defined for usergroups.")

[USERGROUP\_CONNECT\_RESTRICTIONS System View](usergroup-connect-restrictions-system-view-57d3364.md "Provides details on connection restrictions for all user groups.")

[USER\_PARAMETERS System View](user-parameters-system-view-2102244.md "Lists all parameters and their values, which have been assigned to users in the system (using CREATE USER ... SET PARAMETER or ALTER USER ... SET PARAMETER).")

[CREATE USERGROUP Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-usergroup-statement-access-control-9869125.md "Creates a usergroup.")

[ALTER USERGROUP Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-usergroup-statement-access-control-aa94ca8.md "Alters a usergroup.")

[DROP USERGROUP Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-usergroup-statement-access-control-6dc0ada.md "Removes a user group from the database.")

[SQL Statements and Authorization for User Group Administration (Reference)](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/bdc34546fcdf4d24b58b1235dda68ec8.html "Creating and configuring user groups requires different combinations of privileges.") :arrow_upper_right:

