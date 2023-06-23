<!-- loioda9074a896e74274bee1193bf8f33e27 -->

# M\_SCHEDULER\_JOBS System View

Shows the status and the history of the status of the scheduled jobs.




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

USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the user who will execute, who is executing, or who has executed the job.



</td>
</tr>
<tr>
<td valign="top">

SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name of the job.



</td>
</tr>
<tr>
<td valign="top">

SCHEDULER\_JOB\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the job.



</td>
</tr>
<tr>
<td valign="top">

STATUS



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the status of the job. Valid statuses are:

-   SCHEDULED if the job is scheduled for execution in the future
-   RUNNING if the job is currently executing
-   SUCCESS if the job executed successfully
-   ERROR if an error occurred



</td>
</tr>
<tr>
<td valign="top">

ERROR\_MESSAGE



</td>
<td valign="top">

NVARCHAR\(2048\)



</td>
<td valign="top">

Displays an error message in the case where STATUS is ERROR.



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

Displays the time when the job is scheduled, if STATUS is SCHEDULED; otherwise, the time when the job execution started.



</td>
</tr>
<tr>
<td valign="top">

END\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the time when the job execution ended if STATUS is SUCCESS or ERROR; otherwise NULL.



</td>
</tr>
</table>



<a name="loioda9074a896e74274bee1193bf8f33e27__section_el4_mkv_b3b"/>

## Additional Information

Users see jobs that they created or on which they have been granted the ALTER or DROP object privilege. Users with the CATALOG READ system privilege see status and history for all jobs.

**Related Information**  


[SCHEDULER\_JOBS System View](../021-System-Views/scheduler-jobs-system-view-79e35f7.md "Shows existing jobs.")

[CREATE SCHEDULER JOB Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-scheduler-job-statement-data-definition-d7d43d8.md "Creates a scheduled job in the current or specified schema.")

[ALTER SCHEDULER JOB Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-scheduler-job-statement-data-definition-701e467.md "Alters a scheduled job in the current or specified schema.")

[DROP SCHEDULER JOB Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-scheduler-job-statement-data-definition-5a5f9f0.md "Drops a scheduled job in the current or specified schema.")

