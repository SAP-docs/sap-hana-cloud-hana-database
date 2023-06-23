<!-- loio61ce5ab54b494591b14400cf17a5df2a -->

# M\_ALL\_CONTAINERS

Shows all HDI containers that are assigned to an HDI container group.



The `_SYS_DI` monitoring view `M_ALL_CONTAINERS` shows all HDI containers in the database and container groups to which they are assigned.

**M\_ALL\_CONTAINERS**


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

