<!-- loiod4d64f38dc8e4028ba985f0d7848e3f1 -->

# M\_ALL\_CONTAINER\_VERSIONS

View all container versions in the HDI container group.



The `_SYS_DI` monitoring view `M_ALL_CONTAINER_VERSIONS` shows the version history and status information of all HDI containers in the database. Note that there can be multiple entries per container.

**M\_ALL\_CONTAINER\_VERSIONS**


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

VERSION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

The container version number

</td>
</tr>
<tr>
<td valign="top">

STATUS

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

The current status of the container, for example: `CREATED`, `MIGRATED`, `MIGRATION FAILED`, `IMPORTING`, or `IMPORTED` 

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
</table>

