<!-- loio707639b4b6b8427ba54985dc75369f0e -->

# M\_SERVICE\_COMPONENT\_DETAILS System View

Allows closer monitoring of service components.



<a name="loio707639b4b6b8427ba54985dc75369f0e__section_sjn_tr5_ymb"/>

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

Unit

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

DATABASE\_NAME

</td>
<td valign="top">

VARCHAR\(256\)

</td>
<td valign="top">



</td>
<td valign="top">

Displays the database name.

</td>
</tr>
<tr>
<td valign="top">

HOST

</td>
<td valign="top">

VARCHAR\(64\)

</td>
<td valign="top">



</td>
<td valign="top">

Displays the host name.

</td>
</tr>
<tr>
<td valign="top">

PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">



</td>
<td valign="top">

Displays the internal port.

</td>
</tr>
<tr>
<td valign="top">

SERVICE\_NAME

</td>
<td valign="top">

VARCHAR\(32\)

</td>
<td valign="top">



</td>
<td valign="top">

Displays the service name. See M\_SERVICE\_TYPES for all known service names.

</td>
</tr>
<tr>
<td valign="top">

SERVICE\_COMPONENT

</td>
<td valign="top">

VARCHAR\(64\)

</td>
<td valign="top">



</td>
<td valign="top">

Displays the component name. See See M\_SERVICE\_COMPONENTS for all known component names.

</td>
</tr>
<tr>
<td valign="top">

SERVICE\_COMPONENT\_ACTION

</td>
<td valign="top">

VARCHAR\(64\)

</td>
<td valign="top">



</td>
<td valign="top">

Displays the name of the component action.

</td>
</tr>
<tr>
<td valign="top">

PROGRESS\_DETAILS

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">



</td>
<td valign="top">

Displays the status details and progress information.

</td>
</tr>
<tr>
<td valign="top">

START\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">



</td>
<td valign="top">

Displays the timestamp of the start of the component action or lifecycle phase.

</td>
</tr>
<tr>
<td valign="top">

DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Microsecond

</td>
<td valign="top">

Displays the duration of the component action or lifecycle phase. The value is -1 as long as progress is ongoing.

</td>
</tr>
</table>

**Related Information**  


[M\_SERVICES System View](m-services-system-view-20c4ef8.md "Provides the status of all services.")

[M\_SERVICE\_COMPONENT\_MEMORY System View](m-service-component-memory-system-view-20bed4f.md "Provides service-specific memory usage by logical component.")

