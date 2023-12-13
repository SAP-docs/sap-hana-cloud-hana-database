<!-- loio864e9b9851bb467e9c0c4c1f285bef12 -->

# ALTER SYSTEM \{START | STOP | SAVE | CLEAR\} KERNEL PROFILER Statement \(System Management\)

Manages the operation of the Kernel Profiler.



<a name="loio864e9b9851bb467e9c0c4c1f285bef12__section_oxp_qf5_ncb"/>

## Syntax

```
ALTER SYSTEM { <start_profiler> 
 | <stop_profiler> 
 | <save_profiler> 
 | <clear_profiler> 
 } 
```



<a name="loio864e9b9851bb467e9c0c4c1f285bef12__section_pxp_qf5_ncb"/>

## Syntax Element


<dl>
<dt><b>

*<start\_profiler\>*

</b></dt>
<dd>

Starts the Kernel Profiler.

```
<start_profiler> ::= START KERNEL PROFILER 
 [ <location> ] 
 [ <profile_by> ]
 [ <memory_limit> ] 
 [ <sampling_interval> ]
```


<dl>
<dt><b>

*<location\>*

</b></dt>
<dd>

Restricts profiling to the specified location. See the definition of *<location\>* later in this list.



</dd><dt><b>

*<profile\_by\>*

</b></dt>
<dd>

Sets the scope of the profiling.

```
<profile_by> ::= { <user_name> 
 | <application_user_name> 
 | <connection_id>
 | <traceprofile_name> }
```


<dl>
<dt><b>

*<user\_name\>*

</b></dt>
<dd>

Restricts profiling to the specified SQL user name.

```
<user_name> ::= USER <simple_identifier>
```



</dd><dt><b>

*<application\_user\_name\>*

</b></dt>
<dd>

Restricts profiling to the specified application user name.

```
<application_user_name> ::= APPLICATIONUSER <string_literal>
```



</dd><dt><b>

*<connection\_id\>*

</b></dt>
<dd>

Restricts profling to the specified connection ID.

```
<connection_id> ::= SESSION <numeric_literal>
```



</dd><dt><b>

*<traceprofile\_name\>*

</b></dt>
<dd>

Restricts profiling to the specified user-specific trace profile.

```
<traceprofile_name> ::= TRACEPROFILE <string_literal>
```



</dd>
</dl>



</dd><dt><b>

*<memory\_limit\>*

</b></dt>
<dd>

Sets an approximate memory limit \(in bytes\) for the Kernel Profiler. If not specified, the default is 0 \(no limit\).

```
<memory_limit> ::= MEMORY LIMIT <numeric_literal>
```



</dd><dt><b>

*<sampling\_interval\>*

</b></dt>
<dd>

Periodically stores profiler samples, according to specified interval \(in milliseconds\). If not specified, the default is 1 millisecond.

```
<sampling_interval> ::= SAMPLING INTERVAL <numeric_literal>
```



</dd>
</dl>



</dd><dt><b>

*<stop\_profiler\>*

</b></dt>
<dd>

Stops the Kernel Profiler \(but does not free up the allocated memory\).

```
<stop_profiler> ::= STOP KERNEL PROFILER [ <location> ]
```

*<location\>* restricts profiling to the specified location. See the definition of *<location\>* later in this topic.



</dd><dt><b>

*<save\_profiler\>*

</b></dt>
<dd>

Stops the Kernel Profiler, if it is running, saves the data to the trace directory, and clears the allocated memory

```
<save_profiler> ::= SAVE KERNEL PROFILER [ <location> ] [ <filter_list> ] [ <into_files> ]

<filter_list> ::= FOR CALLSTACKS <string_literal> [, <string_literal> [, ... ] ] 

<into_files> ::= INTO { [ CPU FILE <file_name_cpu> ] [ WAIT FILE <file_name_wait> ] }
<file_name_cpu> ::= <string_literal>
<file_name_wait> ::= <string_literal>
```


<dl>
<dt><b>

*<location\>*

</b></dt>
<dd>

Restricts profiling to the specified location. See the definition of *<location\>* later in this topic.



</dd><dt><b>

*<filter\_list\>*

</b></dt>
<dd>

Filters the profiling output to the specified call stacks.



</dd><dt><b>

*<into\_files\>*

</b></dt>
<dd>

Writes Kernel Profiler output to the specified file\(s\) in the trace directory of your SAP HANA database instance.

If the INTO clause is not specified, then the default names of files it creates are `kernel_profiler_cpu.dot` and `kernel_profiler_wait.dot`. However, if only one file type is specified, only this file is created \(the other file is not created with its default file name\).

If you specify a file name without the prefix `kernel_profiler_` or suffix `_cpu.dot/_wait.dot`, these are added to the file name.

You cannot specify a path for the files. Also, files of the same name are overwritten.



</dd>
</dl>



</dd><dt><b>

*<clear\_profiler\>*

</b></dt>
<dd>

Stops the Kernel Profiler, and clears the allocated memory.

```
<clear_profiler> ::= CLEAR KERNEL PROFILER [ <location> ]
```

*<location\>* restricts profiling to the specified location. See the definition of *<location\>* later in this topic.



</dd><dt><b>

*<location\>*

</b></dt>
<dd>

Restricts the Kernel Profiler to the specified location.

```
<location> ::= AT [ LOCATION ] <host_and_port>
<host_and_port> ::= { ( <host> , <port> ) | '<host>:<port>' }
<host> ::= <string_literal>
<port> ::= <numeric_literal>
```



</dd>
</dl>



<a name="loio864e9b9851bb467e9c0c4c1f285bef12__section_qxp_qf5_ncb"/>

## Description

The Kernel Profiler is a tool which collects information about CPU consumption and wait times for SAP HANA's various internal processes. This information can be helpful in support scenarios.

Only one instance of the Kernel Profiler can be active at a time using the ALTER SYSTEM statement, which can be monitored with the M\_KERNEL\_PROFILER system view.



<a name="loio864e9b9851bb467e9c0c4c1f285bef12__section_b2j_dt2_n2b"/>

## Permissions

You must have the RESOURCE ADMIN or TRACE ADMIN system privilege to execute this statement.



<a name="loio864e9b9851bb467e9c0c4c1f285bef12__section_rxp_qf5_ncb"/>

## Examples

The following statement clears all previously collected Kernel Profiler data.

```
ALTER SYSTEM CLEAR KERNEL PROFILER;
```

The following statement starts profiling for the DBADMIN user, sets a memory limit of 1 GB, and sets a sampling interval of 2 milliseconds.

```
ALTER SYSTEM START KERNEL PROFILER USER DBADMIN MEMORY LIMIT 1073741824 SAMPLING INTERVAL 2;
```

The following statement stops profiling, saves the data for the specified call stacks into the trace directory, and then frees the memory that was used for the profiling data.

```
ALTER SYSTEM SAVE KERNEL PROFILER FOR CALLSTACK 'Execution::JobExecWatchdog::run','System::ProcessorInfo::getCurrentProcessorIndex' INTO CPU FILE 'cpu.dot' WAIT FILE 'wait.dot';
```

The following statement starts profiling at host:port `ab1234:30003` and filters for the user-specific trace \(database trace\) profile `MYTRACEPROFILE`.

```
ALTER SYSTEM START KERNEL PROFILER AT 'ab1234:30003' TRACEPROFILE 'MYTRACEPROFILE';
```

The following statement stops profiling and clears the profiling data for the specified location `ab1234:30003`. In this case, because the Kernel Profiler is being stopped, and the data cleared, no data will be saved.

```
ALTER SYSTEM CLEAR KERNEL PROFILER AT LOCATION 'ab1234:30003';
```

**Related Information**  


[M\_KERNEL\_PROFILER System View](../../020-System-Views-Reference/022-Monitoring-Views/m-kernel-profiler-system-view-d20e2e8.md "Displays the state and provides information about Kernel Profilers in the system. You must have the RESOURCE ADMIN or TRACE ADMIN system privileges to use this view.")

[Kernel Profiler](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/bdd27500bb571014b7f7e61e7c4cda04.html "The kernel profiler is a sampling profiler built into the SAP HANA database. It can be used to analyze performance issues and it collects, for example, information about frequent and/or expensive execution paths during query processing.") :arrow_upper_right:

[Diagnostic Files and Logs](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/335e2374c20245e78c9c4c6ce5b0fec6.html "In the event of problems with the SAP HANA database, you can check diagnosis files for errors.") :arrow_upper_right:

