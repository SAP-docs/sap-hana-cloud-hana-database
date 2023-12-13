<!-- loio20cadec8751910148bab98528e3634a9 -->

# M\_VOLUME\_IO\_TOTAL\_STATISTICS System View

Shows information about basic I/O operations on I/O subsystems \(paths\).



<a name="loio20cadec8751910148bab98528e3634a9___m__v_o_l_u_m_e__i_o__t_o_t_a_l__s_t_a_t_i_s_t_i_c_s_1struct_M_VOLUME_IO_TOTAL_STATISTICS"/>

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

Displays the internal port number.

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

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the configuration parameters.

</td>
</tr>
<tr>
<td valign="top">

BLOCKED\_WRITE\_REQUESTS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of blocked write requests.

</td>
</tr>
<tr>
<td valign="top">

MAX\_BLOCKED\_WRITE\_REQUESTS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum number of blocked write requests.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_READS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of synchronous reads.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_TRIGGER\_ASYNC\_READS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of triggered asynchronous reads.

</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_ASYNC\_READS\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of active asynchronous reads

</td>
</tr>
<tr>
<td valign="top">

TRIGGER\_READ\_RATIO

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the trigger-ratio of asynchronous reads.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_SHORT\_READS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of reads that read fewer bytes than requested.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_FULL\_RETRY\_READS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of full retry reads.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_FAILED\_READS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of failed reads.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_READ\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of read data in bytes.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_READ\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total read time in microseconds.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_APPENDS

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

TOTAL\_WRITES

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of synchronous writes.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_TRIGGER\_ASYNC\_WRITES

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of triggered asynchronous writes.

</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_ASYNC\_WRITES\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of active asynchronous writes

</td>
</tr>
<tr>
<td valign="top">

TRIGGER\_WRITE\_RATIO

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the trigger-ratio of asynchronous writes.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_SHORT\_WRITES

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of writes that wrote less bytes than requested.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_FULL\_RETRY\_WRITES

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of full retry writes.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_FAILED\_WRITES

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of failed writes.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_WRITE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of written data in bytes.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_WRITE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total write time in microseconds.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_IO\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total IO time in microseconds.

</td>
</tr>
</table>



<a name="loio20cadec8751910148bab98528e3634a9___m__v_o_l_u_m_e__i_o__t_o_t_a_l__s_t_a_t_i_s_t_i_c_s_1fulldesc_M_VOLUME_IO_TOTAL_STATISTICS"/>

## Additional Information

Throughput of file I/O can generally be calculated by \(TOTAL\_READ\_SIZE + TOTAL\_WRITE\_SIZE\) / TOTAL\_IO\_TIME.

For TOTAL\_IO\_TIME, note that reads and writes can happen in parallel. For example, assume there is a 20 MB read operation and, in parallel, a 20 MB write operation. The read operation starts at 0.0 sec, the write operation starts at 0.5 sec, and both operations last exactly 2 seconds. TOTAL\_IO\_TIME is calculated as:

```
TOTAL_READ_SIZE  = 20,971,520 Bytes
TOTAL_WRITE_SIZE = 20,971,520 Bytes
TOTAL_READ_TIME  =  2,000,000 Microsecond (timeframe: 0.0 – 2.0 sec)
TOTAL_WRITE_TIME =  2,000,000 Microsecond (timeframe: 0.5 – 2.5 sec)
TOTAL_IO_TIME    =  2,500,000 Microsecond (timeframe: 0.0 – 2.5 sec)
```

Refer to the M\_VOLUME\_IO\_DETAILED\_STATISTICS and M\_VOLUME\_IO\_RETRY\_STATISTICS system views for detailed information about read/write performance on various buffer sizes.

This view has a resettable counterpart; you can see the values since the last reset in the M\_VOLUME\_IO\_TOTAL\_STATISTICS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_VOLUME_IO_TOTAL_STATISTICS_RESET;`.

Resetting this view implicitly resets the dependent child views M\_VOLUME\_IO\_DETAILED\_STATISTICS and M\_VOLUME\_IO\_RETRY\_STATISTICS.

**Related Information**  


[M\_VOLUME\_IO\_DETAILED\_STATISTICS System View](m-volume-io-detailed-statistics-system-view-20c9e76.md "Provides detailed statistics about file access.")

