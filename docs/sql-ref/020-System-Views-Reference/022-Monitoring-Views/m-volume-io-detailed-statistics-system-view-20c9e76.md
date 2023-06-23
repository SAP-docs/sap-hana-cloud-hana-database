<!-- loio20c9e7677519101494089e1b516c0bc8 -->

# M\_VOLUME\_IO\_DETAILED\_STATISTICS System View

Provides detailed statistics about file access.



<a name="loio20c9e7677519101494089e1b516c0bc8___m__v_o_l_u_m_e__i_o__d_e_t_a_i_l_e_d__s_t_a_t_i_s_t_i_c_s_1struct_M_VOLUME_IO_DETAILED_STATISTICS"/>

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

PATH



</td>
<td valign="top">

NVARCHAR\(512\)



</td>
<td valign="top">

Displays the file system path.



</td>
</tr>
<tr>
<td valign="top">

FILESYSTEM\_TYPE



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the file system type.



</td>
</tr>
<tr>
<td valign="top">

TYPE



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the type of contained files.



</td>
</tr>
<tr>
<td valign="top">

CONFIGURATION



</td>
<td valign="top">

NVARCHAR\(128\)



</td>
<td valign="top">

Displays the configuration parameters.



</td>
</tr>
<tr>
<td valign="top">

MAX\_IO\_BUFFER\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the maximum I/O buffer size in bytes.



</td>
</tr>
<tr>
<td valign="top">

APPEND\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of appends.



</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_APPEND\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of active appends.



</td>
</tr>
<tr>
<td valign="top">

MIN\_APPEND\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the minimum size of the appended data in bytes.



</td>
</tr>
<tr>
<td valign="top">

AVG\_APPEND\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average size of the appended data in bytes.



</td>
</tr>
<tr>
<td valign="top">

MAX\_APPEND\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the maximum size of the appended data in bytes.



</td>
</tr>
<tr>
<td valign="top">

SUM\_APPEND\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total size of the appended data in bytes.



</td>
</tr>
<tr>
<td valign="top">

WRITE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of writes.



</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_WRITE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of active writes.



</td>
</tr>
<tr>
<td valign="top">

MIN\_WRITE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the minimum size of the written data in bytes.



</td>
</tr>
<tr>
<td valign="top">

AVG\_WRITE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average size of the written data in bytes.



</td>
</tr>
<tr>
<td valign="top">

MAX\_WRITE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the maximum size of the written data in bytes.



</td>
</tr>
<tr>
<td valign="top">

SUM\_WRITE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total size of written data.



</td>
</tr>
<tr>
<td valign="top">

TRIGGER\_ASYNC\_WRITE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of trigger asynchronous writes.



</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_TRIGGER\_ASYNC\_WRITE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of active trigger asynchronous writes.



</td>
</tr>
<tr>
<td valign="top">

MIN\_TRIGGER\_ASYNC\_WRITE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the minimum size of the trigger asynchronous write data in bytes.



</td>
</tr>
<tr>
<td valign="top">

AVG\_TRIGGER\_ASYNC\_WRITE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average size of the trigger asynchronous write data in bytes.



</td>
</tr>
<tr>
<td valign="top">

MAX\_TRIGGER\_ASYNC\_WRITE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the maximum size of the trigger asynchronous write data in bytes.



</td>
</tr>
<tr>
<td valign="top">

SUM\_TRIGGER\_ASYNC\_WRITE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total size of the trigger asynchronous write data in bytes.



</td>
</tr>
<tr>
<td valign="top">

READ\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of reads.



</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_READ\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of active reads.



</td>
</tr>
<tr>
<td valign="top">

MIN\_READ\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the minimum size of the read data in bytes.



</td>
</tr>
<tr>
<td valign="top">

AVG\_READ\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average size of the read data in bytes.



</td>
</tr>
<tr>
<td valign="top">

MAX\_READ\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the maximum size of the read data in bytes.



</td>
</tr>
<tr>
<td valign="top">

SUM\_READ\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total size of the read data in bytes.



</td>
</tr>
<tr>
<td valign="top">

TRIGGER\_ASYNC\_READ\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of trigger asynchronous reads.



</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_TRIGGER\_ASYNC\_READ\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of active trigger asynchronous reads.



</td>
</tr>
<tr>
<td valign="top">

MIN\_TRIGGER\_ASYNC\_READ\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the minimum size of the trigger asynchronous read data.



</td>
</tr>
<tr>
<td valign="top">

AVG\_TRIGGER\_ASYNC\_READ\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average size of the trigger asynchronous read data.



</td>
</tr>
<tr>
<td valign="top">

MAX\_TRIGGER\_ASYNC\_READ\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the maximum size of the trigger asynchronous read data.



</td>
</tr>
<tr>
<td valign="top">

SUM\_TRIGGER\_ASYNC\_READ\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total size of the trigger asynchronous read data.



</td>
</tr>
</table>



<a name="loio20c9e7677519101494089e1b516c0bc8___m__v_o_l_u_m_e__i_o__d_e_t_a_i_l_e_d__s_t_a_t_i_s_t_i_c_s_1fulldesc_M_VOLUME_IO_DETAILED_STATISTICS"/>

## Additional Information

This view shows detailed I/O statistics for various buffer sizes. Each buffer size is a maximum value. That is, a buffer of the size 4k actually means <= 4k and a buffer size o f16k means 4k < buffer size <= 16k. The I/O time is the total time from starting a request until it finishes, including enqueue time. All measured times are periods of time between enqueueing and finishing a request. The reported times contain wait times if the request cannot be started immediately. Enqueue time is measured separately to see how many requests are executed asynchronously and how many are synchronous or blocking. For overall I/O performance, see TOTAL\_READ/WRITE\_SIZE and TOTAL\_IO\_TIME in the M\_VOLUME\_IO\_TOTAL\_STATISTICS system view.

This view has a resettable counterpart; you can see the values since the last reset in the M\_VOLUME\_IO\_DETAILED\_STATISTICS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_VOLUME_IO_DETAILED_STATISTICS_RESET;`

**Related Information**  


[M\_VOLUME\_IO\_DETAILED\_STATISTICS\_RESET System View](m-volume-io-detailed-statistics-reset-system-view-20ca089.md "Provides detailed statistics about file access since the last reset.")

[M\_VOLUME\_IO\_TOTAL\_STATISTICS System View](m-volume-io-total-statistics-system-view-20cadec.md "Shows information about basic I/O operations on I/O subsystems (paths).")

