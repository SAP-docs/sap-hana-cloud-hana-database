<!-- loiocd5ef50762f246c38f610d1c1d05fa0b -->

# M\_SERVICE\_COMPONENTS System View

Displays all known components and their current status within an SAP HANA service.



<a name="loiocd5ef50762f246c38f610d1c1d05fa0b__section_kv2_3tm_ymb"/>

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

SERVICE\_COMPONENT

</td>
<td valign="top">

VARCHAR\(64\)

</td>
<td valign="top">



</td>
<td valign="top">

Displays the service component name.

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

IS\_ENABLED

</td>
<td valign="top">

VARCHAR\(5\)

</td>
<td valign="top">



</td>
<td valign="top">

Displays whether the component is enabled or not: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

LIFECYCLE\_PHASE

</td>
<td valign="top">

VARCHAR\(32\)

</td>
<td valign="top">



</td>
<td valign="top">

Displays the lifecycle phase of the component.

</td>
</tr>
<tr>
<td valign="top">

START\_THREAD\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">



</td>
<td valign="top">

Displays the ID of the thread that started the component.

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

Displays the timestamp when the component started.

</td>
</tr>
<tr>
<td valign="top">

START\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Microsecond

</td>
<td valign="top">

Displays the component start duration.

</td>
</tr>
<tr>
<td valign="top">

ASSIGN\_THREAD\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">



</td>
<td valign="top">

Displays the ID of the thread of the ASSIGN component.

</td>
</tr>
<tr>
<td valign="top">

ASSIGN\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">



</td>
<td valign="top">

Displays the timestamp of the beginning of the component ASSIGN.

</td>
</tr>
<tr>
<td valign="top">

ASSIGN\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Microsecond

</td>
<td valign="top">

Displays the duration of the ASSIGN component.

</td>
</tr>
<tr>
<td valign="top">

POST\_ASSIGN\_THREAD\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">



</td>
<td valign="top">

Displays the POST\_ASSIGN thread ID of the component.

</td>
</tr>
<tr>
<td valign="top">

POST\_ASSIGN\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">



</td>
<td valign="top">

Displays the timestamp of the start of the POST\_ASSIGN component.

</td>
</tr>
<tr>
<td valign="top">

POST\_ASSIGN\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Microsecond

</td>
<td valign="top">

Displays the duration of the POST\_ASSIGN component.

</td>
</tr>
<tr>
<td valign="top">

SHUTDOWN\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">



</td>
<td valign="top">

Displays the timestamp of the start of the component shutdown.

</td>
</tr>
<tr>
<td valign="top">

SHUTDOWN\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Microsecond

</td>
<td valign="top">

Displays the duration of the component shutdown.

</td>
</tr>
<tr>
<td valign="top">

LAST\_RECONFIG\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">



</td>
<td valign="top">

Displays the timestamp of the start of the last component reconfiguration.

</td>
</tr>
<tr>
<td valign="top">

RECONFIG\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Microsecond

</td>
<td valign="top">

Displays the duration of the last component reconfiguration.

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
</table>



<a name="loiocd5ef50762f246c38f610d1c1d05fa0b__section_vfs_bb3_ymb"/>

## Additional Information

Each component displays if it is enabled within the service and only then does it contain further information about the various phases \(start, assign, reconfiguration, and shutdown\). In case a service was assigned multiple times, only the latest assigned service is visible. The same goes for the other phases. Furthermore, a service is only represented in the view if it has a ComponentManager implemented, which should be the case for all services that are not used for test-only purposes. To give some insight into the accumulated various component-specific functionality that is not yet extracted into its own components, the monitoring view contains an additional row for each phase, which is marked as an *<other\>* component and adds up these remaining durations.

Another additional row for each phase, which is marked as an *<all\>* component, adds up all durations per phase.

The timestamp and the duration of the *<other\>* component cannot be used to calculate the exact end time of a phase, since it excludes some overhead that happens within the internal phases of a service.

**Related Information**  


[M\_SERVICE\_COMPONENT\_MEMORY System View](m-service-component-memory-system-view-20bed4f.md "Provides service-specific memory usage by logical component.")

[M\_SERVICES System View](m-services-system-view-20c4ef8.md "Provides the status of all services.")

