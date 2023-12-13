<!-- loio20be163175191014b4a7cc89cbe84331 -->

# M\_SEMAPHORES System View

Provides semaphore statistics.



<a name="loio20be163175191014b4a7cc89cbe84331___m__s_e_m_a_p_h_o_r_e_s_1struct_M_SEMAPHORES"/>

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

Displays the internal port.

</td>
</tr>
<tr>
<td valign="top">

VOLUME\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the persistence volume ID.

</td>
</tr>
<tr>
<td valign="top">

STATISTICS\_NAME

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the statistics object name.

</td>
</tr>
<tr>
<td valign="top">

STATISTICS\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the statistics object unique ID.

</td>
</tr>
<tr>
<td valign="top">

WAIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of wait calls.

</td>
</tr>
<tr>
<td valign="top">

BLOCKING\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of blocking wait calls.

</td>
</tr>
<tr>
<td valign="top">

TIMEOUT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of timeouts.

</td>
</tr>
<tr>
<td valign="top">

WAIT\_RATE

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the wait rate percentage.

</td>
</tr>
<tr>
<td valign="top">

LAST\_BLOCKING\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last time of blocking wait calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MAX\_BLOCKING\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum time of blocking wait calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MIN\_BLOCKING\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum time of blocking wait calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

SUM\_BLOCKING\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total time of blocking wait calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

AVG\_BLOCKING\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time of blocking wait calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

CREATE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of semaphore creations \(for shared statistics only\).

</td>
</tr>
<tr>
<td valign="top">

DESTROY\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of semaphore destructions \(for shared statistics only\).

</td>
</tr>
<tr>
<td valign="top">

COMPONENT

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the component.

</td>
</tr>
</table>



<a name="loio20be163175191014b4a7cc89cbe84331___m__s_e_m_a_p_h_o_r_e_s_1fulldesc_M_SEMAPHORES"/>

## Additional Information

This view contains information about single semaphore objects or groups of semaphore objects. It does not contain information about all semaphores.

This view has a resettable counterpart; you can see the values since the last reset in the M\_SEMAPHORES\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_SEMAPHORES_RESET;`.

**Related Information**  


[M\_SEMAPHORES\_RESET System View](m-semaphores-reset-system-view-20be55f.md "Provides semaphore statistics since the last reset.")

