<!-- loiod20da56dd2951014b0ed84780bd84d7e -->

# M\_JOBEXECUTORS System View

Provides job executor statistics.



<a name="loiod20da56dd2951014b0ed84780bd84d7e___m__j_o_b_e_x_e_c_u_t_o_r_s_1fulldesc_M_JOBEXECUTORS"/>

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

MAX\_CONCURRENCY\_CONFIG

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the maximum limit configured for concurrently running worker threads.

If this limit is exceeded, a dynamic reduction in the concurrently running worker threads is automatically triggered, to prevent overload.

</td>
</tr>
<tr>
<td valign="top">

MAX\_CONCURRENCY

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the maximum number of concurrently running worker threads.

The job executor keeps MAX\_CONCURRENCY worker threads busy. As a result, more worker threads are started if some worker threads are in a wait state for some time. Even if these additional worker threads are terminated, some of them are kept for later use and counted in PARKED\_WORKER\_COUNT.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_WORKER\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the total number of worker threads, including one extra worker thread for emergency diagnostic purposes.

</td>
</tr>
<tr>
<td valign="top">

PARKED\_WORKER\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of parked worker threads.

</td>
</tr>
<tr>
<td valign="top">

FREE\_WORKER\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the total number of worker threads that are idle and may immediately take up a job to work on.

</td>
</tr>
<tr>
<td valign="top">

SYS\_WAITING\_WORKER\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of worker threads waiting in system. A worker thread may wait for any other kind of synchronization.

</td>
</tr>
<tr>
<td valign="top">

JOB\_WAITING\_WORKER\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of worker threads waiting for a job on another worker thread.

</td>
</tr>
<tr>
<td valign="top">

YIELD\_WAITING\_WORKER\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of worker threads waiting on a yield. Sometimes a job running on a worker thread yields execution to another job that is more important.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_WAITING\_JOB\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of all jobs waiting for execution.

</td>
</tr>
<tr>
<td valign="top">

QUEUED\_WAITING\_JOB\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of jobs queued for execution.

</td>
</tr>
<tr>
<td valign="top">

WORKER\_CREATE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of threads created.

</td>
</tr>
</table>



<a name="loiod20da56dd2951014b0ed84780bd84d7e__section_nnn_ryz_xbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.



<a name="loiod20da56dd2951014b0ed84780bd84d7e__section_bdz_gyg_x2b"/>

## Additional Information

This view has a resettable counterpart; you can see the values since the last reset in the M\_JOBEXECUTORS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_JOBEXECUTORS_RESET;`.

**Related Information**  


[M\_JOBEXECUTORS\_RESET System View](m-jobexecutors-reset-system-view-d20dec6.md "Provides values accumulated since the last reset of the main view M_JOBEXECUTORS.")

[Controlling Parallel Execution of SQL Statements](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/5c012ca1def64bceb5f29028325193bd.html "Job management takes place in the HANA worker framework and is handled by the JobExecutor which is a job queueing and dispatching subsystem.") :arrow_upper_right:

