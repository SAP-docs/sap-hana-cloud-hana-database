<!-- loio20f8d0a175191014a7c192193b8645a9 -->

# MERGE DELTA Statement \(Data Manipulation\)

Merges the column store table delta storage to the table's main storage.



<a name="loio20f8d0a175191014a7c192193b8645a9__sql_merge_delta_1sql_merge_delta_syntax"/>

## Syntax

```
MERGE DELTA OF <table_name> [ PART <n> ]
   [ WITH PARAMETERS ( <parameter_list>, … ) ]
   [ FORCE REBUILD ]
```



<a name="loio20f8d0a175191014a7c192193b8645a9__sql_merge_delta_1sql_merge_delta_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

DELTA OF *<table\_name\>*

</b></dt>
<dd>

Specifies the table where the delta merge occurs, with the optional schema name.

```
<table_name> ::= [ <schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```



</dd><dt><b>

PART *<n\>*

</b></dt>
<dd>

Merges the delta of a specific table partition to the table's main storage.



</dd><dt><b>

WITH PARAMETERS

</b></dt>
<dd>

Specifies options that are specific to the column store.

```
<parameter_list> ::= <parameter> [, <parameter> [,…] ]

<parameter> ::= <parameter_name> = <parameter_setting>

<parameter_name> ::= 'SMART_MERGE' 

<parameter_setting> ::= 'ON' | 'OFF'
```

When SMART\_MERGE is ON, the database does a smart merge based on merge criteria configured in `indexserver.ini`.



</dd><dt><b>

FORCE REBUILD

</b></dt>
<dd>

Force a delta merge even if the delta storage is empty and no deleted rows exist in the main storage that could be discarded. Use this option to create a new main storage matching the latest table definition \(that is, reflecting current persistent memory preferences\).



</dd>
</dl>



<a name="loio20f8d0a175191014a7c192193b8645a9__sql_merge_delta_1sql_merge_delta_description"/>

## Description

As a column store table is read, optimized, and compressed, deltas are introduced to optimize insert or update operations. All insertions are passed to the delta storage. At a certain point in time the delta changes to a table can be merged into the table main storage.



<a name="loio20f8d0a175191014a7c192193b8645a9__section_zz2_fmm_wcb"/>

## Permissions

The UPDATE privilege on the column store table is required for performing a delta merge.



<a name="loio20f8d0a175191014a7c192193b8645a9__sql_merge_delta_1sql_merge_delta_examples"/>

## Examples

Merge the column store table delta storage to the tables main storage.

```
MERGE DELTA OF TableA;
```

Merge the column store table TableA using a smart merge.

```
MERGE DELTA OF TableA WITH PARAMETERS('SMART_MERGE' = 'ON');
```

Merge table TableA delta storage of partition 1 to the main storage of partition 1.

```
MERGE DELTA OF TableA PART 1;
```

Merge table TableA history-delta storage into its history-main storage.

```
MERGE DELTA OF TableA FORCE REBUILD;
```

