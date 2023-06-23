<!-- loio20d2973275191014bafef616be15326a -->

# ALTER SYSTEM SAVE PERFTRACE Statement \(System Management\)

Collects raw performance trace data from `.prf` files and saves the information into a single `.tpt` file.



> ### Note:  
> Performance tracing is only to be used in conjunction with SAP Support personnel. The collected performance trace data cannot be analyzed by an end user.



<a name="loio20d2973275191014bafef616be15326a__sql_alter_system_save_perftrace_1sql_alter_system_save_perftrace_syntax"/>

## Syntax

```
ALTER SYSTEM SAVE PERFTRACE [INTO FILE <file_name>]
```



<a name="loio20d2973275191014bafef616be15326a__sql_alter_system_save_perftrace_1sql_alter_system_save_perftrace_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

INTO FILE *<file\_name\>*

</b></dt>
<dd>

Specifies the file where raw performance data is saved.

```
<file_name> ::= <string_literal>
```



</dd>
</dl>



<a name="loio20d2973275191014bafef616be15326a__sql_alter_system_save_perftrace_1sql_alter_system_save_perftrace_description"/>

## Description

The `.tpt` file is saved in the trace directory of your SAP HANA database instance. If you do not specify a file name, then `perftrace.tpt` is used.

Use the M\_JOB\_PROGRESS system view to monitor the saving of a trace file. The save job is shown as Save PerfTrace in the system view.

Saving a performance trace can take some time. You can cancel the job shown in M\_JOB\_PROGRESS system view by using the ALTER SYSTEM CANCEL \[WORK IN\] SESSION statement.



<a name="loio20d2973275191014bafef616be15326a__section_ex5_lqr_xrb"/>

## Permissions

To save performance trace data from `.prf` files, you must have the TRACE ADMIN system privilege.



<a name="loio20d2973275191014bafef616be15326a__sql_alter_system_save_perftrace_1sql_alter_system_save_perftrace_example"/>

## Example

Save raw performance trace data into the `mytrace.tpt` file.

```
ALTER SYSTEM SAVE PERFTRACE INTO FILE 'mytrace.tpt';
```

**Related Information**  


[ALTER SYSTEM \{START | STOP\} PERFTRACE Statement \(System Management\)](alter-system-start-stop-perftrace-statement-system-management-20d2d3e.md "Starts or stops performance tracing.")

[M\_PERFTRACE System View](../../020-System-Views-Reference/022-Monitoring-Views/m-perftrace-system-view-20b70e8.md "Displays the state of the current performance trace. The performance trace provides detailed information about query execution.")

[M\_JOB\_PROGRESS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-job-progress-system-view-20b1b23.md "Provides information about current long running system operations.")

[ALTER SYSTEM LOAD PERFTRACE Statement \(System Management\)](alter-system-load-perftrace-statement-system-management-20d1707.md "Converts a .tpt file into tables.")

[ALTER SYSTEM CANCEL \[WORK IN\] SESSION Statement \(System Management\)](alter-system-cancel-work-in-session-statement-system-management-20d0eb2.md "Cancels the currently executing statement of a session.")

