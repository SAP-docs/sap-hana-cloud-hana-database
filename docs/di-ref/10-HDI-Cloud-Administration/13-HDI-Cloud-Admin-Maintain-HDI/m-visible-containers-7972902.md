<!-- loio797290236c164bbf8c54daae96676cd4 -->

# M\_VISIBLE\_CONTAINERS

Shows all HDI containers in the database that the user is allowed to see and the container groups to which the visible containers.



The `_SYS_DI` monitoring view `M_VISIBLE_CONTAINERS` shows all HDI containers in the database and the container groups to which they are assigned, that are visible to the user. A container is considered visible, if the user has any privilege on the container’s API schema or is allowed to access `M_CONTAINERS` in the group, that the container belongs to, or if he is allowed to access `M_ALL_CONTAINERS` in the `_SYS_DI` schema.

> ### Note:  
> The view is public.

**M\_VISIBLE\_CONTAINERS**


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

NVARCHAR\(256\)

</td>
<td valign="top">

The name of the container

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

The name of the user who created the container

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

The name of the application user who created the container

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

The time at which the container was created

</td>
</tr>
<tr>
<td valign="top">

CONTAINER\_GROUP\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

The name of the container group to which a container is assigned

</td>
</tr>
<tr>
<td valign="top">

LAST\_API\_ACCESS\_TIMESTAMP\_UTC

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

The time when an API on the container was most recently called

</td>
</tr>
<tr>
<td valign="top">

LAST\_SUCCESSFUL\_MAKE\_TIMESTAMP\_UTC

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

The time of the most recent successful deployment to the container

</td>
</tr>
</table>

**Related Information**  


[M\_ALL\_CONTAINERS](m-all-containers-61ce5ab.md "Shows all HDI containers that are assigned to an HDI container group.")

[M\_VISIBLE\_CONTAINER\_GROUPS](m-visible-container-groups-5ed997a.md "Shows all HDI container groups in the database that the user is allowed to see.")

