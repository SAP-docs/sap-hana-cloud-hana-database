<!-- loiod20e2e88d2951014a316e9e53d4a9381 -->

# M\_KERNEL\_PROFILER System View

Displays the state and provides information about Kernel Profilers in the system. You must have the RESOURCE ADMIN or TRACE ADMIN system privileges to use this view.



<a name="loiod20e2e88d2951014a316e9e53d4a9381___m__k_e_r_n_e_l__p_r_o_f_i_l_e_r_1struct_M_KERNEL_PROFILER"/>

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

APPLICATION\_USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the application user name to filter on.

</td>
</tr>
<tr>
<td valign="top">

USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the SQL user name to filter on.

</td>
</tr>
<tr>
<td valign="top">

MEMORY\_LIMIT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the limit for profiling data in bytes. This is not an exact limit, a heuristic approach is used to limit memory.

</td>
</tr>
<tr>
<td valign="top">

SAMPLING\_INTERVAL

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the sampling interval, in milliseconds.

</td>
</tr>
<tr>
<td valign="top">

CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the connection ID to filter on.

</td>
</tr>
<tr>
<td valign="top">

TRACEPROFILE\_NAME

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the user-specific trace profile name to filter on.

</td>
</tr>
<tr>
<td valign="top">

START\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time that profiling was started.

</td>
</tr>
<tr>
<td valign="top">

STOP\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time that profiling was stopped.

</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current size, in bytes, of the kernel profile.

</td>
</tr>
<tr>
<td valign="top">

SAMPLE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of samples stored for the profile.

</td>
</tr>
<tr>
<td valign="top">

STATUS

</td>
<td valign="top">



</td>
<td valign="top">

Displays the status of the profiler. Possible values are: STARTED, STOPPED

</td>
</tr>
</table>

**Related Information**  


[ALTER SYSTEM \{START | STOP | SAVE | CLEAR\} KERNEL PROFILER Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-start-stop-save-clear-kernel-profiler-statement-system-manageme-864e9b9.md "Manages the operation of the Kernel Profiler.")

[Kernel Profiler](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/bdd27500bb571014b7f7e61e7c4cda04.html "The kernel profiler is a sampling profiler built into the SAP HANA database. It can be used to analyze performance issues and it collects, for example, information about frequent and/or expensive execution paths during query processing.") :arrow_upper_right:

[Diagnostic Files and Logs](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/335e2374c20245e78c9c4c6ce5b0fec6.html "In the event of problems with the SAP HANA database, you can check diagnosis files for errors.") :arrow_upper_right:

