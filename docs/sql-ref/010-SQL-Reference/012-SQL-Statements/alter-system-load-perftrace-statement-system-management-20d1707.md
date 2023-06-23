<!-- loio20d170777519101493f4be280b8d0b45 -->

# ALTER SYSTEM LOAD PERFTRACE Statement \(System Management\)

Converts a `.tpt` file into tables.



<a name="loio20d170777519101493f4be280b8d0b45__sql_alter_system_load_perftrace_1sql_alter_system_load_perftrace_syntax"/>

## Syntax

```
ALTER SYSTEM LOAD PERFTRACE [FILE <file_name>]
   INTO TABLES <table_prefix> [WITH REPLACE]
```



<a name="loio20d170777519101493f4be280b8d0b45__sql_alter_system_load_perftrace_1sql_alter_system_load_perftrace_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

FILE *<file\_name\>*

</b></dt>
<dd>

Specifies the file that raw performance data is loaded from.

```
<file_name> ::= <string_literal>
```



</dd><dt><b>

INTO TABLES *<table\_prefix\>*

</b></dt>
<dd>

Specifies the table prefix to be used with optional schema name.

> ### Note:  
> The created tables are only to used in conjunction with SAP tools or support personnel; the format of the tables is intentionally not documented for end users.

```
<table_prefix> ::= [ <schema_name>. ]<identifier>
 
<schema_name> ::= <unicode_name>
```



</dd><dt><b>

WITH REPLACE

</b></dt>
<dd>

Specifies that previously existing tables are removed. If the REPLACE option is not specified, then an error is thrown if tables with the specified prefix already exist.



</dd>
</dl>



<a name="loio20d170777519101493f4be280b8d0b45__sql_alter_system_load_perftrace_1sql_alter_system_load_perftrace_description"/>

## Description

Tables beginning with *<table\_prefix\>*\_PERFTRACE\_... are created and filled with the content from the `.tpt` file. The `.tpt` file is loaded from the trace directory of your SAP HANA database instance. If you do not specify a file name, then `perftrace.tpt` is used.



<a name="loio20d170777519101493f4be280b8d0b45__section_ytd_24r_xrb"/>

## Permissions

To convert a `.tpt` file to tables, you must have the TRACE ADMIN system privilege.



<a name="loio20d170777519101493f4be280b8d0b45__sql_alter_system_load_perftrace_1sql_alter_system_load_perftrace_example"/>

## Example

Load performance trace data from the `mytrace.tpt` file into tables. The created tables include MYTRACE\_PERFTRACE\_INFO MYTRACE\_PERFTRACE\_SERVICES, and MYTRACE\_PERFTRACE\_CALLS.

```
ALTER SYSTEM LOAD PERFTRACE FILE 'mytrace.tpt' INTO TABLES mytrace WITH REPLACE;
```

