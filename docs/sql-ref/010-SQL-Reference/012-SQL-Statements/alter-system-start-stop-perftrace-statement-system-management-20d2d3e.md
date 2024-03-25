<!-- loio20d2d3ed75191014bb9c86ed27c378d8 -->

# ALTER SYSTEM \{START | STOP\} PERFTRACE Statement \(System Management\)

Starts or stops performance tracing.



> ### Note:  
> Performance tracing is only to be used in conjunction with SAP Support personnel. The collected performance trace data cannot be analyzed by an end user.



<a name="loio20d2d3ed75191014bb9c86ed27c378d8__sql_alter_system_start_perftrace_1sql_alter_system_start_perftrace_syntax"/>

## Syntax

```
ALTER SYSTEM START PERFTRACE [ <user_name> ] [ <application_user_name> ]
   [ <application_name> ] [ <passport_level> ] 
   [ PLAN_EXECUTION ] [ FUNCTION_PROFILER ] [ DURATION <duration_seconds> ]
   [ <root_statement_hash> ]

| ALTER SYSTEM STOP PERFTRACE
```



<a name="loio20d2d3ed75191014bb9c86ed27c378d8__sql_alter_system_start_perftrace_1sql_alter_system_start_perftrace_syntax_element"/>

## Syntax Element


<dl>
<dt><b>

*<user\_name\>*

</b></dt>
<dd>

Restricts performance trace collection to an SQL user name.

```
<user_name> ::= USER <simple_identifier>
```



</dd><dt><b>

*<application\_user\_name\>*

</b></dt>
<dd>

Restricts performance trace collection to the application user name.

```
<application_user_name> ::= APPLICATIONUSER <string_literal>
```



</dd><dt><b>

*<application\_name\>*

</b></dt>
<dd>

Restricts performance trace collection to the application name.

```
<application_name> ::= APPLICATION <string_literal>
```



</dd><dt><b>

*<passport\_level\>*

</b></dt>
<dd>

Specifies the level of trace data to be collected.

```
<passport_level> ::= PASSPORT_TRACELEVEL { MEDIUM | HIGH }
```

*<passport\_level\>* filters the amount of data collected in end-to-end scenarios.



</dd><dt><b>

PLAN\_EXECUTION

</b></dt>
<dd>

Specifies that plan execution details should be traced.



</dd><dt><b>

FUNCTION\_PROFILER

</b></dt>
<dd>

Specifies that function-level details should be traced.



</dd><dt><b>

*<duration\_seconds\>*

</b></dt>
<dd>

Specifies the number of seconds to run the performance trace for. If not specified, the trace runs until the ALTER SYSTEM STOP PERFTRACE statement is executed.

```
<duration_seconds> ::= <numeric_literal>
```

After this period expires, the performance trace is automatically stopped. If you do not specify this parameter, then you must stop the performance trace with the ALTER SYSTEM STOP PERFTRACE statement.



</dd><dt><b>

*<root\_statement\_hash\>*

</b></dt>
<dd>

Restricts performance trace collection to the statement identified by the root statement hash.

```
<root_statement_hash> ::= ROOT_STATEMENT_HASH <string_literal>
```

For statements in stored procedures, the root statement hash is the statement hash of the stored procedure call. The perftrace filter compares the given root statement hash with the root statement hash of the statements. This will also trace statements running within a stored procedure.



</dd>
</dl>



<a name="loio20d2d3ed75191014bb9c86ed27c378d8__sql_alter_system_start_perftrace_1sql_alter_system_start_perftrace_description"/>

## Description

Only one performance trace can be active at a time.

After stopping the trace, collect and save the performance trace data with the ALTER SYSTEM SAVE PERFTRACE statement.



<a name="loio20d2d3ed75191014bb9c86ed27c378d8__section_msh_gzq_xrb"/>

## Permissions

To stop or start performance tracing, you must have the TRACE ADMIN system privilege.



<a name="loio20d2d3ed75191014bb9c86ed27c378d8__sql_alter_system_stop_perftrace_1sql_alter_system_start_perftrace_example"/>

## Example

Start performance tracing for the user sql\_user on application user name app\_user for application app\_name, and specify that plan execution and function-level detail should be traced.

```
ALTER SYSTEM START PERFTRACE USER sql_user APPLICATIONUSER app_user APPLICATION app_name PLAN_EXECUTION FUNCTION_PROFILER;
```

Start performance tracing that is filtered by the statement hash 21db1b17968de7861e6c97645f72963b.

```
ALTER SYSTEM START PERFTRACE ROOT_STATEMENT_HASH '21db1b17968de7861e6c97645f72963b';
```

Stop an active performance trace.

```
ALTER SYSTEM STOP PERFTRACE;
```

**Related Information**  


[ALTER SYSTEM SAVE PERFTRACE Statement \(System Management\)](alter-system-save-perftrace-statement-system-management-20d2973.md "Collects raw performance trace data from .prf files and saves the information into a single .tpt file.")

[M\_PERFTRACE System View](../../020-System-Views-Reference/022-Monitoring-Views/m-perftrace-system-view-20b70e8.md "Displays the state of the current performance trace. The performance trace provides detailed information about query execution.")

[ALTER SYSTEM CLEAR TRACES Statement \(System Management\)](alter-system-clear-traces-statement-system-management-20d1281.md "Clears trace files opened by SAP HANA.")

[ALTER SYSTEM REMOVE TRACES Statement \(System Management\)](alter-system-remove-traces-statement-system-management-20d25bf.md "Removes the trace files from a specified host to reduce the disk space used by large trace files.")

[ALTER SYSTEM \{START | STOP\} PERFTRACE Statement \(System Management\)](alter-system-start-stop-perftrace-statement-system-management-20d2d3e.md "Starts or stops performance tracing.")

[M\_TRACEFILE\_CONTENTS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-tracefile-contents-system-view-20c8d7f.md "Provides SAP HANA information from trace files.")

[M\_TRACE\_CONFIGURATION System View](../../020-System-Views-Reference/022-Monitoring-Views/m-trace-configuration-system-view-20c89f0.md "Provides information about trace configuration statistics.")

