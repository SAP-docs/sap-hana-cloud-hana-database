<!-- loio20af4e6e75191014ba7da5b7c4c5da60 -->

# M\_EVENTS System View

Provides information about internal events.



<a name="loio20af4e6e75191014ba7da5b7c4c5da60___m__e_v_e_n_t_s_1struct_M_EVENTS"/>

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

HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the host.

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

Displays the port.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the original host if the event was created via another host.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the original port if the event was created via another host.

</td>
</tr>
<tr>
<td valign="top">

TYPE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the type of event.

</td>
</tr>
<tr>
<td valign="top">

ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the ID of the event.

</td>
</tr>
<tr>
<td valign="top">

INFOTEXT

</td>
<td valign="top">

NVARCHAR\(2000\)

</td>
<td valign="top">

Displays additional information in free text.

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

Displays the time that the event was created.

</td>
</tr>
<tr>
<td valign="top">

UPDATE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time that the event was updated.

</td>
</tr>
<tr>
<td valign="top">

HANDLE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time that the event was handled.

</td>
</tr>
<tr>
<td valign="top">

STATE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the state of the event.

</td>
</tr>
<tr>
<td valign="top">

ACKNOWLEDGED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates whether the event is acknowledged: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

FAILED\_HANDLES

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of failed handle attempts.

</td>
</tr>
</table>



<a name="loio20af4e6e75191014ba7da5b7c4c5da60___m__e_v_e_n_t_s_1fulldesc_M_EVENTS"/>

## Additional Information

Important events \(for example, DiskFull\) reported by the database are shown in this view. The state of an event can be either NEW or HANDLED. CREATE TIME shows the time the event was created \(and reported\) and HANDLE time shows the time the event was handled \(that is, cleared\). Handled events are removed periodically by the StatisticsServer

**Related Information**  


[GLOBAL_INTERNAL_EVENTS View (Embedded Statistics Service)](https://help.sap.com/viewer/323c57a017234d47a0e7da3e22345822/2024_1_QRC/en-US/449bb507ab944d5f8702e812e751bd28.html "Specifies global internal event information.") :arrow_upper_right:

