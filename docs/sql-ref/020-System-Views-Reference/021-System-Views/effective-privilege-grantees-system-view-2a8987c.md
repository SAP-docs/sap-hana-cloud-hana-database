<!-- loio2a8987c66cdf4baeb299de52eedf88c9 -->

# EFFECTIVE\_PRIVILEGE\_GRANTEES System View

Provides information about who was granted \(explicitly or implicitly via roles\) a specified privilege.



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

GRANTEE\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name of role that has the privilege.



</td>
</tr>
<tr>
<td valign="top">

GRANTEE



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the user or role that has the privilege.



</td>
</tr>
<tr>
<td valign="top">

GRANTEE\_TYPE



</td>
<td valign="top">

NVARCHAR\(4\)



</td>
<td valign="top">

Displays the grantee type: USER/ROLE.



</td>
</tr>
<tr>
<td valign="top">

GRANTOR\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name of role that provided the privilege.



</td>
</tr>
<tr>
<td valign="top">

GRANTOR



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the user or role that provided the privilege.



</td>
</tr>
<tr>
<td valign="top">

GRANTOR\_TYPE



</td>
<td valign="top">

NVARCHAR\(10\)



</td>
<td valign="top">

Displays the grantor type: USER, ROLE or ROLEGROUP.



</td>
</tr>
<tr>
<td valign="top">

OBJECT\_TYPE



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the type of the granted object, for example, TABLE, SCHEMA, and so on.



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

Displays the schema name the object belongs to.



</td>
</tr>
<tr>
<td valign="top">

OBJECT\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the object name of granted object.



</td>
</tr>
<tr>
<td valign="top">

PRIVILEGE



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the privilege granted.



</td>
</tr>
<tr>
<td valign="top">

IS\_GRANTABLE



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the privilege was granted with WITH GRANT OPTION or WITH ADMIN OPTION: TRUE/FALSE.



</td>
</tr>
</table>



<a name="loio2a8987c66cdf4baeb299de52eedf88c9__section_jyc_vdk_h2b"/>

## Additional Information

This view requires an equals \(=\) predicate on PRIVILEGE and OBJECT\_TYPE.

**Related Information**  


[EFFECTIVE\_PRIVILEGES System View](effective-privileges-system-view-20a2f3e.md "Provides the privileges of the specified user.")

[PRIVILEGES System View](privileges-system-view-20cc29b.md "Provides information about available privileges.")

[System Views for Verifying Users&apos; Authorization](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/ddae823e3b27477ea4c949607eebc435.html "You can query several system views to get detailed information about exactly which privileges and roles users have and how they come to have them. This can help you to understand why a user is authorized to perform particular actions, access particular data, or not.") :arrow_upper_right:

[ROLEGROUPS System Views](rolegroups-system-views-5e2b4b9.md "Shows available role groups.")

