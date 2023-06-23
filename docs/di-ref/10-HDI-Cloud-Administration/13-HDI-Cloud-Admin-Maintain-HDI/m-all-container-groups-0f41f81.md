<!-- loio0f41f811e62d4deb8235e4bbcf471613 -->

# M\_ALL\_CONTAINER\_GROUPS

View all HDI container groups in the database.



The `_SYS_DI` monitoring view `M_ALL_CONTAINER_GROUPS` shows a list of all HDI container groups in the database.

**M\_ALL\_CONTAINER\_GROUPS**


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

CONTAINER\_GROUP\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

The name of the HDI container group



</td>
</tr>
<tr>
<td valign="top">

CONTAINER\_GROUP\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(264\)



</td>
<td valign="top">

The name of the schema that contains the HDI container group’s API



</td>
</tr>
<tr>
<td valign="top">

CONTAINER\_GROUP\_USERGROUP\_NAME



</td>
<td valign="top">

NVARCHAR\(264\)



</td>
<td valign="top">

The name of the user group that is associated with the HDI container group



</td>
</tr>
<tr>
<td valign="top">

CREATE\_USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

The name of the user who created the HDI container group



</td>
</tr>
<tr>
<td valign="top">

CREATE\_APPUSER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

The name of the application user who created the HDI container group



</td>
</tr>
<tr>
<td valign="top">

CREATE\_TIMESTAMP\_UTC



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

The time at which the HDI container group was created



</td>
</tr>
</table>

