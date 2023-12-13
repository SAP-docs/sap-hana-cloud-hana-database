<!-- loio22320f76def3495d9f5efbe4f2ecb70b -->

# M\_CONTAINER\_VERSIONS

View all container versions in the HDI container group.



The HDI-container-group-specific monitoring view `M_CONTAINER_VERSIONS` shows the version history and status information of the HDI containers in an HDI container group. Note that there can be multiple entries per container.

**M\_CONTAINER\_VERSIONS**


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

