<!-- loio5ed997a6deb14be0844483f8e7aa368a -->

# M\_VISIBLE\_CONTAINER\_GROUPS

Shows all HDI container groups in the database that the user is allowed to see.



The `_SYS_DI` monitoring view `M_VISIBLE_CONTAINER_GROUPS` shows all HDI container groups in the database, which are visible to the user. A container group is considered visible, if the user has any privilege on the group’s API schema or if he is allowed to access `M_ALL_CONTAINER_GROUPS` in the `_SYS_DI` schema.

> ### Note:  
> The view is public.

**M\_VISIBLE\_CONTAINER\_GROUPS**


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

**Related Information**  


[M\_ALL\_CONTAINER\_GROUPS](m-all-container-groups-0f41f81.md "View all HDI container groups in the database.")

[M\_VISIBLE\_CONTAINERS](m-visible-containers-7972902.md "Shows all HDI containers in the database that the user is allowed to see and the container groups to which the visible containers.")

