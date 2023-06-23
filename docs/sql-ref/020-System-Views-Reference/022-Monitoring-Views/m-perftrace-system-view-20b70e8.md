<!-- loio20b70e8c75191014ad6ed82e6804355c -->

# M\_PERFTRACE System View

Displays the state of the current performance trace. The performance trace provides detailed information about query execution.



<a name="loio20b70e8c75191014ad6ed82e6804355c___m__p_e_r_f_t_r_a_c_e_1struct_M_PERFTRACE"/>

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

STATUS



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the status of the performance trace: STOPPED, STARTED, or SAVING.



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

Displays when the performance trace started.



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

Displays when the performance trace stopped.



</td>
</tr>
<tr>
<td valign="top">

FILE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size of the collected trace files in bytes. This value is only valid if tracing is stopped and not saved.



</td>
</tr>
<tr>
<td valign="top">

REMAINING\_SECONDS



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the remaining number of seconds until tracing stops automatically.



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

Displays the SQL user name filter.



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

Displays the application user name filter.



</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the application name filter.



</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_TRACELEVEL



</td>
<td valign="top">

NVARCHAR\(8\)



</td>
<td valign="top">

Displays the passport filter: MEDIUM/HIGH.



</td>
</tr>
<tr>
<td valign="top">

PLAN\_EXECUTION



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Indicates whether plan execution details are recorded.



</td>
</tr>
<tr>
<td valign="top">

FUNCTION\_PROFILER



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether or not the function profiler details are recorded: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

ROOT\_STATEMENT\_HASH



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the root statement hash filter.



</td>
</tr>
</table>

**Related Information**  


[ALTER SYSTEM \{START | STOP\} PERFTRACE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-start-stop-perftrace-statement-system-management-20d2d3e.md "Starts or stops performance tracing.")

[ALTER SYSTEM SAVE PERFTRACE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-save-perftrace-statement-system-management-20d2973.md "Collects raw performance trace data from .prf files and saves the information into a single .tpt file.")

