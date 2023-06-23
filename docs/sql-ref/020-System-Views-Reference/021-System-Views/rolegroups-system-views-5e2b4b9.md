<!-- loio5e2b4b95879a408e91c64f85fae53485 -->

# ROLEGROUPS System Views

Shows available role groups.



<a name="loio5e2b4b95879a408e91c64f85fae53485___r_o_l_e_s_1struct_ROLES"/>

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

ROLEGROUP\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the role group.



</td>
</tr>
<tr>
<td valign="top">

ROLEGROUP\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the ID of the role group.



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

Displays the name of user who created the role group.



</td>
</tr>
<tr>
<td valign="top">

IS\_ROLE\_ADMIN\_ENABLED



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether a user granted the ROLE ADMIN system privilege can manage this role group. Valid values are: TRUE/FALSE.



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

Displays a description of the role group.



</td>
</tr>
</table>



<a name="loio5e2b4b95879a408e91c64f85fae53485__section_twp_3fl_qrb"/>

## Additional Information

Users with CATALOG READ or CREATE ROLEGROUP system privileges will see all role groups in the view.

Users with GRANTOR, DROP or OPERATOR object privileges granted on specific role groups will only see those role groups in the view.

**Related Information**  


[EFFECTIVE\_PRIVILEGE\_GRANTEES System View](effective-privilege-grantees-system-view-2a8987c.md "Provides information about who was granted (explicitly or implicitly via roles) a specified privilege.")

[EFFECTIVE\_PRIVILEGES System View](effective-privileges-system-view-20a2f3e.md "Provides the privileges of the specified user.")

