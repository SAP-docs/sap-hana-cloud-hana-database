<!-- loio20b12419751910148afa9303eec370a0 -->

# M\_HOST\_RESOURCE\_UTILIZATION System View

Provides information about host resource utilization by all processes \(including non-SAP HANA processes\). CPU time is in milliseconds and added across all cores since system start.



<a name="loio20b12419751910148afa9303eec370a0___m__h_o_s_t__r_e_s_o_u_r_c_e__u_t_i_l_i_z_a_t_i_o_n_1struct_M_HOST_RESOURCE_UTILIZATION"/>

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

FREE\_PHYSICAL\_MEMORY

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the free physical memory on the host in bytes.

</td>
</tr>
<tr>
<td valign="top">

USED\_PHYSICAL\_MEMORY

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the used physical memory on the host in bytes.

</td>
</tr>
<tr>
<td valign="top">

FREE\_SWAP\_SPACE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the free swap memory on the host in bytes.

</td>
</tr>
<tr>
<td valign="top">

USED\_SWAP\_SPACE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the used swap memory on the host in bytes.

</td>
</tr>
<tr>
<td valign="top">

ALLOCATION\_LIMIT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the allocation limit for all processes in bytes.

</td>
</tr>
<tr>
<td valign="top">

INSTANCE\_TOTAL\_MEMORY\_USED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the amount of memory from the memory pool that is currently being used by SAP HANA processes in bytes.

</td>
</tr>
<tr>
<td valign="top">

INSTANCE\_TOTAL\_MEMORY\_PEAK\_USED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the peak memory from the memory pool used by SAP HANA processes since the instance started \(this is a sample-based value\) in bytes.

</td>
</tr>
<tr>
<td valign="top">

INSTANCE\_TOTAL\_MEMORY\_ALLOCATED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of the memory pool for all SAP HANA processes in bytes.

</td>
</tr>
<tr>
<td valign="top">

INSTANCE\_CODE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the code size, including shared libraries of SAP HANA processes in bytes.

</td>
</tr>
<tr>
<td valign="top">

INSTANCE\_SHARED\_MEMORY\_ALLOCATED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the shared memory size of SAP HANA processes in bytes.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_CPU\_USER\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the CPU time spent in the user mode in milliseconds.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_CPU\_SYSTEM\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the CPU time spent in the kernel mode in milliseconds.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_CPU\_WIO\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the CPU time spent in wait I/O in milliseconds. Linux only, Microsoft Windows is always 0.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_CPU\_IDLE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the CPU idle time in milliseconds.

</td>
</tr>
<tr>
<td valign="top">

SYS\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the host timestamp in the local time zone.

</td>
</tr>
<tr>
<td valign="top">

UTC\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the host timestamp in UTC.

</td>
</tr>
<tr>
<td valign="top">

OPEN\_FILE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of allocated file handles on the host. The Kernel parameter is `fs.file-nr`. For more information, see the OPEN\_FILE\_LIMIT key in the M\_HOST\_INFORMATION system view topic.

</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_ASYNC\_IO\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of asynchronous input and/or output requests on the host. The Kernel parameter is `fs.ai-nr`. For more information, see the ASYNC\_IO\_LIMIT key in the M\_HOST\_INFORMATION system view topic.

</td>
</tr>
<tr>
<td valign="top">

FAST\_RESTART\_MEMORY\_MAPPED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

FAST\_RESTART\_MEMORY\_FILE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

FAST\_RESTART\_MEMORY\_PEAK\_MAPPED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

FAST\_RESTART\_MEMORY\_PEAK\_FILE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

PERSISTENT\_MEMORY\_MAPPED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

PERSISTENT\_MEMORY\_FILE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

PERSISTENT\_MEMORY\_PEAK\_MAPPED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

PERSISTENT\_MEMORY\_PEAK\_FILE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

For internal use only.

</td>
</tr>
</table>

**Related Information**  


[HOST_RESOURCE_UTILIZATION_STATISTICS View (Embedded Statistics Service)](https://help.sap.com/viewer/323c57a017234d47a0e7da3e22345822/2024_1_QRC/en-US/fbd82f0303c44e35a6bbb12cb803f94c.html "Returns the host resource utilization for all processes (including non-SAP HANA processes).") :arrow_upper_right:

[M\_HOST\_INFORMATION System View](m-host-information-system-view-20b1002.md "Provides host information such as machine and OS configuration.")

[M\_HOST\_NETWORK\_STATISTICS System View](m-host-network-statistics-system-view-b589470.md "Provides information about the network statistics of a host.")

