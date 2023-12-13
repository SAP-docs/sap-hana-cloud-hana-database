<!-- loio20c47d7675191014a4268963083a16c1 -->

# M\_SERVICE\_THREAD\_CALLSTACKS System View

Provides stack frame information for service threads.



<a name="loio20c47d7675191014a4268963083a16c1___m__s_e_r_v_i_c_e__t_h_r_e_a_d__c_a_l_l_s_t_a_c_k_s_1struct_M_SERVICE_THREAD_CALLSTACKS"/>

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

SERVICE\_NAME

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the service name. See M\_SERVICE\_TYPES for all known service names.

</td>
</tr>
<tr>
<td valign="top">

THREAD\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the thread ID.

</td>
</tr>
<tr>
<td valign="top">

IS\_ACTIVE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the thread is active.

</td>
</tr>
<tr>
<td valign="top">

FRAME\_LEVEL

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the level of the stack frame.

</td>
</tr>
<tr>
<td valign="top">

FRAME\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of stack frame \(function, file, library, and so on\).

</td>
</tr>
</table>



<a name="loio20c47d7675191014a4268963083a16c1__section_qpy_h3h_3kb"/>

## Additional Information

While this view is publicly visible, its contents can only be seen by users with the DATABASE ADMIN privilege.

**Related Information**  


[M\_SERVICE\_TYPES System View](m-service-types-system-view-20c4d1d.md "Provides information about service types.")

[M\_SERVICE\_THREADS System View](m-service-threads-system-view-20c499a.md "Displays detailed information about threads created by services.")

[M\_SERVICE\_THREAD\_SAMPLES System View](m-service-thread-samples-system-view-d2176a6.md "Displays detailed information about locks held by threads.")

