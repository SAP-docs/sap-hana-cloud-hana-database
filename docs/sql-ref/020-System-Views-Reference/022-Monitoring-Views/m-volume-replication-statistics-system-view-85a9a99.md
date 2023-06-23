<!-- loio85a9a9985dd649b997fe5133d2c4ba8a -->

# M\_VOLUME\_REPLICATION\_STATISTICS System View

Shows volume replication statistics.



<a name="loio85a9a9985dd649b997fe5133d2c4ba8a___m__v_o_l_u_m_e__i_o__t_o_t_a_l__s_t_a_t_i_s_t_i_c_s_1struct_M_VOLUME_IO_TOTAL_STATISTICS"/>

## Structure


<table>
<tr>
<th valign="top">

 



</th>
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

 



</td>
<td valign="top">

SOURCE\_HOST



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the source host name.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

SOURCE\_PORT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the internal source port number.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

SOURCE\_VOLUME\_REPLICA\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the ID of the source volume replica.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

VOLUME\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the ID of the volume.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

TARGET\_HOST



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the target host name.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

TARGET\_PORT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the internal target port number.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

SOURCE\_VOLUME\_REPLICA\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the ID of the target volume replica.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

TARGET\_CONNECT\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the time the connection was established.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

TARGET\_RECONNECT\_COUNT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the number of reconnects to the target.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

TARGET\_FULLY\_RECOVERABLE



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the target is fully recoverable.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

REPLICATION\_MODE



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the replication mode.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

REPLICATION\_STATUS



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the replication status.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

REPLICATION\_STATUS\_DETAILS



</td>
<td valign="top">

NVARCHAR\(1024\)



</td>
<td valign="top">

Displays status details.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

LAST\_LOG\_POSITION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the last confirmed log position.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

LAST\_LOG\_POSITION\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the time of the last confirmed log position.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

SHIPPED\_LOG\_POSITION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the shipped log position.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

SHIPPED\_LOG\_POSITION\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the timestamp of the shipped log position.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

SHIPPED\_LOG\_BUFFERS\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the shipped log buffer count.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

SHIPPED\_LOG\_BUFFERS\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the shipped log buffers size in bytes.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

SHIPPED\_LOG\_BUFFERS\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the shipped log buffer duration in microseconds.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

BACKLOG\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the current backlog size in bytes.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

MAX\_BACKLOG\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the max size allowed for the backlog in bytes.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

BACKLOG\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the current replication backlog in microseconds.



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

MAX\_BACKLOG\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the max replication backlog in microseconds.



</td>
</tr>
</table>

