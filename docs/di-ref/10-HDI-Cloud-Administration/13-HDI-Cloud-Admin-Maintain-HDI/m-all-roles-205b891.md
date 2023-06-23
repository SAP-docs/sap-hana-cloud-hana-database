<!-- loio205b8918c2364e5ea44816cc9feb6e85 -->

# M\_ALL\_ROLES

Show all the container roles for any HDI container.



The `_SYS_DI` monitoring view `M_ALL_ROLES` shows all the container roles for any HDI container where the current user has `SELECT` permission on the view `M_ROLES` at either the container or the container-group level.



**M\_ROLES**


<table>
<tr>
<th valign="top">

Name



</th>
<th valign="top">

Data Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

CONTAINER\_NAME



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

The name of the container where the roles are deployed



</td>
</tr>
<tr>
<td valign="top">

ROLE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

The name of the role



</td>
</tr>
<tr>
<td valign="top">

ROLE\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

The role ID



</td>
</tr>
<tr>
<td valign="top">

ROLE\_MODE



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

The mode of the role: '`LOCAL`'



</td>
</tr>
<tr>
<td valign="top">

GLOBAL\_IDENTITY



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

The identity specified for role with `ROLE_MODE GLOBAL` 



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

The name of the user who created the role



</td>
</tr>
<tr>
<td valign="top">

CREATE\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

The time at which the role was created



</td>
</tr>
<tr>
<td valign="top">

CONTEXT



</td>
<td valign="top">

NVARCHAR\(2048\)



</td>
<td valign="top">

The context for which the role is valid



</td>
</tr>
</table>

