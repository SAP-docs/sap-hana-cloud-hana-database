<!-- loio20d12816751910149640d1e144741069 -->

# ALTER SYSTEM CLEAR TRACES Statement \(System Management\)

Clears \(removes\) trace files opened by SAP HANA.



<a name="loio20d12816751910149640d1e144741069__sql_alter_system_clear_traces_1sql_alter_system_clear_traces_syntax"/>

## Syntax

```
ALTER SYSTEM CLEAR TRACES ( <trace_type_list> ) [ UNTIL <timestamp> ] [ WITH BACKUP ]
```



<a name="loio20d12816751910149640d1e144741069__sql_alter_system_clear_traces_1sql_alter_system_clear_traces_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<trace\_type\_list\>*

</b></dt>
<dd>

Specifies a list of trace types to be cleared.

```
<trace_type_list> ::= <trace_type> [, <trace_type> [,…] ]
```


<dl>
<dt><b>

*<trace\_type\>*

</b></dt>
<dd>

Specifies the trace type.

```
<trace_type> ::= <string_literal>
```

You can selectively clear specific trace files by setting *<trace\_type\>* to one of the following types:


<table>
<tr>
<th valign="top">

 *<trace\_type\>* 



</th>
<th valign="top">

Trace Files



</th>
</tr>
<tr>
<td valign="top">

\*



</td>
<td valign="top">

all \*.trc files of services listed below



</td>
</tr>
<tr>
<td valign="top">

ALERT



</td>
<td valign="top">

\*alert\_\*.trc



</td>
</tr>
<tr>
<td valign="top">

BACKUP



</td>
<td valign="top">

backup.log



</td>
</tr>
<tr>
<td valign="top">

BACKINT



</td>
<td valign="top">

backint.log



</td>
</tr>
<tr>
<td valign="top">

CLIENT



</td>
<td valign="top">

localclient\_\*.trc



</td>
</tr>
<tr>
<td valign="top">

CRASHDUMP



</td>
<td valign="top">

\*.crashdump.\*



</td>
</tr>
<tr>
<td valign="top">

EMERGENCYDUMP



</td>
<td valign="top">

\*.emergencydump.\*



</td>
</tr>
<tr>
<td valign="top">

EXPENSIVESTATEMENT



</td>
<td valign="top">

\*.expensive\_statements.\*.trc



</td>
</tr>
<tr>
<td valign="top">

indexserver,nameserver,...,daemon



</td>
<td valign="top">

open \*.trc files of a single service type



</td>
</tr>
<tr>
<td valign="top">

ROWSTOREREORG



</td>
<td valign="top">

\*.row\_store\_reorg.\*.trc



</td>
</tr>
<tr>
<td valign="top">

RTEDUMP



</td>
<td valign="top">

\*.rtedump.\*.trc



</td>
</tr>
<tr>
<td valign="top">

SQLTRACE



</td>
<td valign="top">

sqltrace\*.py



</td>
</tr>
<tr>
<td valign="top">

TABLE PARTITION OPERATIONS



</td>
<td valign="top">

indexserver\_\*.\*.table\_partition\_operation.\*.trc



</td>
</tr>
<tr>
<td valign="top">

UNLOAD



</td>
<td valign="top">

\*.unloads.\*.trc



</td>
</tr>
</table>



</dd>
</dl>



</dd><dt><b>

*<timestamp\>*

</b></dt>
<dd>

Specifies that all trace files with a modification time before or equal to the timestamp are deleted.

```
<timestamp> ::= <string_literal>
```



</dd><dt><b>

WITH BACKUP

</b></dt>
<dd>

Specifies that trace files are compressed and saved instead of removed.



</dd>
</dl>



<a name="loio20d12816751910149640d1e144741069__sql_alter_system_clear_traces_1sql_alter_system_clear_traces_description"/>

## Description

When you use this statement, all trace files and compressed files \(like .gz\) that were opened by the SAP HANA database are removed, assuming WITH BACKUP is not specified.

On distributed systems, this command clears all trace files on all hosts.

Use this command to reduce disk space used by large trace files for example, when trace components are set to INFO or DEBUG.



<a name="loio20d12816751910149640d1e144741069__section_jdg_5lr_xrb"/>

## Permissions

To clear traces, you must have the TRACE ADMIN system privilege.



<a name="loio20d12816751910149640d1e144741069__sql_alter_system_clear_traces_1sql_alter_system_clear_traces_examples"/>

## Examples

Clear the alert trace file.

```
ALTER SYSTEM CLEAR TRACES('ALERT');
```

Clear the alert and client trace files.

```
ALTER SYSTEM CLEAR TRACES('ALERT', 'CLIENT');
```

Back up the alert and client trace files.

```
ALTER SYSTEM CLEAR TRACES('ALERT', 'CLIENT') WITH BACKUP;
```

Clear the alert and client trace files with a timestamp prior or equal to 2015-12-31 23:59:59.999.

```
ALTER SYSTEM CLEAR TRACES ('ALERT', 'CLIENT') UNTIL '2015-12-31 23:59:59';
```

Back up the indexserver trace files.

```
ALTER SYSTEM CLEAR TRACES('indexserver') WITH BACKUP;
```

**Related Information**  


[ALTER SYSTEM REMOVE TRACES Statement \(System Management\)](alter-system-remove-traces-statement-system-management-20d25bf.md "Deletes the trace files on a specified host to reduce the disk space used by large trace files.")

[M\_TRACEFILES System View](../../020-System-Views-Reference/022-Monitoring-Views/m-tracefiles-system-view-20c8f48.md "Provides information about all trace files.")

[ALTER SYSTEM \{START | STOP\} PERFTRACE Statement \(System Management\)](alter-system-start-stop-perftrace-statement-system-management-20d2d3e.md "Starts or stops performance tracing.")

[M\_TRACEFILE\_CONTENTS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-tracefile-contents-system-view-20c8d7f.md "Provides SAP HANA information from trace files.")

