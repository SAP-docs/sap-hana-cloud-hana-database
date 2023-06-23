<!-- loio20bf9c0575191014a72084d40b3ba448 -->

# M\_SERVICE\_NETWORK\_IO System View

Provides service network I/O statistics.



<a name="loio20bf9c0575191014a72084d40b3ba448___m__s_e_r_v_i_c_e__n_e_t_w_o_r_k__i_o_1struct_M_SERVICE_NETWORK_IO"/>

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

SENDER\_HOST



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the host name of the sending service.



</td>
</tr>
<tr>
<td valign="top">

SENDER\_PORT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the port that the sending service listens on.



</td>
</tr>
<tr>
<td valign="top">

RECEIVER\_HOST



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the host name of the receiving service.



</td>
</tr>
<tr>
<td valign="top">

RECEIVER\_PORT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the port that the receiving service listens on.



</td>
</tr>
<tr>
<td valign="top">

SEND\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of bytes sent.



</td>
</tr>
<tr>
<td valign="top">

RECEIVE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of bytes received.



</td>
</tr>
<tr>
<td valign="top">

SEND\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the time spent sending in microseconds.



</td>
</tr>
<tr>
<td valign="top">

RECEIVE\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the time spent receiving in microseconds.



</td>
</tr>
<tr>
<td valign="top">

REQUEST\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of requests handled.



</td>
</tr>
</table>



<a name="loio20bf9c0575191014a72084d40b3ba448__section_x5d_2b4_x2b"/>

## Additional Information

This view has a resettable counterpart; you can see the values since the last reset in the M\_SERVICE\_NETWORK\_IO\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_SERVICE_NETWORK_IO_RESET;`.

**Related Information**  


[M\_SERVICE\_NETWORK\_IO\_RESET System View](m-service-network-io-reset-system-view-20c0429.md "Provides the service network I/O statistics since the last reset.")

