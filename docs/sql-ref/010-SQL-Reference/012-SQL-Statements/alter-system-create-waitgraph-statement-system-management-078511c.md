<!-- loio078511c1125a4235bbd09e3ea6ff04a8 -->

# ALTER SYSTEM CREATE WAITGRAPH Statement \(System Management\)

Create a waitgraph file that contains thread information about deadlocks.



<a name="loio078511c1125a4235bbd09e3ea6ff04a8__sql_alter_system_clear_traces_1sql_alter_system_clear_traces_syntax"/>

## Syntax

```
ALTER SYSTEM CREATE WAITGRAPH [ AT [ LOCATION ] <location_ref> ] [ ALL THREADS ] [ INTO FILE <file_name> ]

<file_name> ::= <string_literal>
```



<a name="loio078511c1125a4235bbd09e3ea6ff04a8__sql_alter_system_clear_traces_1sql_alter_system_clear_traces_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<location\_ref\>*

</b></dt>
<dd>

Specifies the location of the service.

```
<location_ref> ::= '<host>:<port>'
```

If no location is specified, then the trace folder of the specified service is used.



</dd><dt><b>

ALL THREADS

</b></dt>
<dd>

Includes details on all threads on the connected service, not just those that are part of the deadlock.



</dd><dt><b>

INTO FILE

</b></dt>
<dd>

Specifies the name for the dump file. If a filename is not specified, then the default file name <code><i class="varname">&lt;servicename&gt;</i>_<i class="varname">&lt;hostname&gt;</i>.<i class="varname">&lt;port&gt;</i>.waitgraph.<i class="varname">&lt;YYYYMMDD-HHMMSS&gt;</i>.<i class="varname">&lt;pid&gt;</i>.trc</code> is used.



</dd>
</dl>



<a name="loio078511c1125a4235bbd09e3ea6ff04a8__section_ncz_1b4_p3b"/>

## Permissions

You need the RESOURCE ADMIN system privilege to execute this statement.



<a name="loio078511c1125a4235bbd09e3ea6ff04a8__sql_alter_system_clear_traces_1sql_alter_system_clear_traces_description"/>

## Description

This syntax lets you create a dump file containing information about threads that may participate in deadlocks.



<a name="loio078511c1125a4235bbd09e3ea6ff04a8__sql_alter_system_clear_traces_1sql_alter_system_clear_traces_examples"/>

## Examples

Write the current waitgraph on service myhost:30003 to the file named `my_waitgraph.trc`.

```
ALTER SYSTEM CREATE WAITGRAPH AT LOCATION 'myhost:30003' INTO FILE 'my_waitgraph.trc';
```

Write the current waitgraph \(including all threads even if they do not participate on the deadlock\) on the connected service into the file named `my_waitgraph.trc`.

```
ALTER SYSTEM CREATE WAITGRAPH ALL THREADS INTO FILE 'my_waitgraph.trc';
```

**Related Information**  


[Deadlock Detection Using SQL](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/159f604867804450bdc60b355e156457.html "To help with diagnosis of system issues you can create a waitgraph file that contains thread information about deadlocks.") :arrow_upper_right:

