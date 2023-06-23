<!-- loio6954969bba544da190ca53c1bf367086 -->

# ALTER SYSTEM CREATE RUNTIMEDUMP Statement \(System Management\)

Creates a runtimedump \(RTE\) dump file containing information about specific sections and profiles.



<a name="loio6954969bba544da190ca53c1bf367086__sql_alter_system_clear_traces_1sql_alter_system_clear_traces_syntax"/>

## Syntax

```
ALTER SYSTEM CREATE RUNTIMEDUMP [ AT [ LOCATION ] <location_ref> ]
    [ { SECTION <section_ref> | PROFILE <profile_name> } ] [ INTO FILE '<file_name>' ]

<profile_name> ::= <string_literal>
<file_name> ::= <string_literal>
```



<a name="loio6954969bba544da190ca53c1bf367086__sql_alter_system_clear_traces_1sql_alter_system_clear_traces_syntax_elements"/>

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



</dd>
</dl>


<dl>
<dt><b>

SECTION

</b></dt>
<dd>

Specifies one of the section names defined in the runtimedump section in the `global.ini` file.

```
<section_ref> ::= ( '<section_name>' [, '<section_name>' , ... ]

<section_name> ::= <string_literal>
```

If no section is specified, then all sections are written.



</dd><dt><b>

PROFILE

</b></dt>
<dd>

Specifies the named subset of sections defined in the runtimedump section in the `global.ini` file.



</dd><dt><b>

INTO FILE

</b></dt>
<dd>

Specifies the name for the dump file. If a file name is not specified, then the default file name <code><i class="varname">&lt;servicename&gt;</i>_<i class="varname">&lt;hostname&gt;</i>.<i class="varname">&lt;port&gt;</i>.rtedump.<i class="varname">&lt;YYYYMMDD-HHMMSS&gt;</i>.<i class="varname">&lt;pid&gt;</i>.trc</code> is used.



</dd>
</dl>



<a name="loio6954969bba544da190ca53c1bf367086__section_ncz_1b4_p3b"/>

## Permissions

You need the RESOURCE ADMIN system privilege to execute this statement.



<a name="loio6954969bba544da190ca53c1bf367086__sql_alter_system_clear_traces_1sql_alter_system_clear_traces_description"/>

## Description

This syntax lets you create an RTE dump file containing information about specific sections and profiles.



<a name="loio6954969bba544da190ca53c1bf367086__sql_alter_system_clear_traces_1sql_alter_system_clear_traces_examples"/>

## Examples

Writes information relating to the STACK\_SHORT section only to a file named `my_rte_dump.trc` on myhost, port 30003.

```
ALTER SYSTEM CREATE RUNTIMEDUMP AT LOCATION 'myhost:30003' SECTIONS ('STACK_SHORT') INTO FILE 'my_rte_dump.trc';
```

Writes information relating to all sections defined by the profile named myRTEProfile on the connected service to the file named `my_rte_dump.trc`.

```
ALTER SYSTEM CREATE RUNTIMEDUMP PROFILE 'myRTEProfile' INTO FILE 'my_rte_dump.trc';
```

