<!-- loio20d25bff75191014965ad9dcc606d225 -->

# ALTER SYSTEM REMOVE TRACES Statement \(System Management\)

Deletes the trace files on a specified host to reduce the disk space used by large trace files.



<a name="loio20d25bff75191014965ad9dcc606d225__sql_alter_system_remove_traces_1sql_alter_system_remove_traces_syntax"/>

## Syntax

```
ALTER SYSTEM REMOVE TRACES (<hostname>, <trace_file_list>)
```



<a name="loio20d25bff75191014965ad9dcc606d225__sql_alter_system_remove_traces_1sql_alter_system_remove_traces_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<hostname\>*

</b></dt>
<dd>

Specifies the name of the host where the traces are to be removed.

```
<hostname> ::= <string_literal>
```



</dd><dt><b>

*<trace\_file\_list\>*

</b></dt>
<dd>

Specifies the trace files to be removed.

```
<trace_file_list> ::= 
 <trace_file> [{, <trace_file>}...]
```

*<trace\_file\>* specifies the name of a file to be removed.



</dd>
</dl>



<a name="loio20d25bff75191014965ad9dcc606d225__sql_alter_system_remove_traces_1sql_alter_system_remove_traces_description"/>

## Description

Valid host name and file name combinations can be retrieved from the M\_TRACEFILES system view.

When a service has a trace file open, it cannot be deleted. In this case, clear the trace file by using the ALTER SYSTEM CLEAR TRACES statement.



<a name="loio20d25bff75191014965ad9dcc606d225__section_ygf_cqr_xrb"/>

## Permissions

To delete trace files, you must have the TRACE ADMIN system privilege.



<a name="loio20d25bff75191014965ad9dcc606d225__sql_alter_system_remove_traces_1sql_alter_system_remove_traces_examples"/>

## Example

This command deletes files on the host named HOST\_NAME.

```
ALTER SYSTEM REMOVE TRACES ('hananode01', 'extrace.py', 'extrace.py.old');
```

**Related Information**  


[M\_TRACEFILES System View](../../020-System-Views-Reference/022-Monitoring-Views/m-tracefiles-system-view-20c8f48.md "Provides information about all trace files.")

[ALTER SYSTEM CLEAR TRACES Statement \(System Management\)](alter-system-clear-traces-statement-system-management-20d1281.md "Clears (removes) trace files opened by SAP HANA.")

[ALTER SYSTEM \{START | STOP\} PERFTRACE Statement \(System Management\)](alter-system-start-stop-perftrace-statement-system-management-20d2d3e.md "Starts or stops performance tracing.")

