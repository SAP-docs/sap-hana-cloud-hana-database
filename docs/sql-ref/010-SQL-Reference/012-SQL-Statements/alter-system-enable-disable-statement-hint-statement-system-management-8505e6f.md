<!-- loio8505e6f5023c4092901735116d03fdce -->

# ALTER SYSTEM \{ENABLE | DISABLE\} STATEMENT HINT Statement \(System Management\)

Enables or disables hints from a target query or statement hash.



<a name="loio8505e6f5023c4092901735116d03fdce__section_ndx_lsx_dz"/>

## Syntax

```
ALTER SYSTEM { ENABLE | DISABLE } STATEMENT HINT 
   { [ ON { PROCEDURE | FUNCTION } <proc_func_name> ] FOR <target_query> 
   | FOR STATEMENT HASH <statement_hash> 
   | FOR ALL };
```



<a name="loio8505e6f5023c4092901735116d03fdce__section_odx_lsx_dz"/>

## Syntax Elements


<dl>
<dt><b>

ON \{ PROCEDURE | FUNCTION \} *<proc\_func\_name\>*

</b></dt>
<dd>

If a statement is specified as the target with the corresponding procedure/function name, the given hint is implicitly applied to the statement inside the corresponding procedure/function.

```
<proc_func_name> ::= [ <schema_name>.]<identifier>
```



</dd><dt><b>

*<target\_query\>*

</b></dt>
<dd>

Specifies the target query.



</dd><dt><b>

*<statement\_hash\>*

</b></dt>
<dd>

Specifies the statement hash.



</dd><dt><b>

ALL

</b></dt>
<dd>

Applies the action to both user-defined hints and system hints that are associated with the specified statement. If ALL is not specified, then the action is only applied on the user-defined hints.



</dd>
</dl>



<a name="loio8505e6f5023c4092901735116d03fdce__section_pdx_lsx_dz"/>

## Description

Both statements \(ENABLE, DISABLE\) evict all cached plans for the target SQL statements from the SQL Plan Cache.



<a name="loio8505e6f5023c4092901735116d03fdce__section_az2_rth_l2b"/>

## Example

This example enables all statement hints.

```
ALTER SYSTEM ENABLE STATEMENT HINT FOR ALL;
```

This example disables statement hints for the SELECT query.

```
ALTER SYSTEM DISABLE STATEMENT HINT FOR SELECT * FROM AAA, BBB WHERE AAA.X = BBB.X;
```

This example enables statement hints for the statement hash 36896ef08346b8321f88449d5c5e97f8.

```
ALTER SYSTEM ENABLE STATEMENT HINT FOR STATEMENT HASH '36896ef08346b8321f88449d5c5e97f8';
```

This example disables statement hints for the statement hash 36896ef08346b8321f88449d5c5e97f8.

```
ALTER SYSTEM DISABLE STATEMENT HINT FOR STATEMENT HASH '36896ef08346b8321f88449d5c5e97f8';
```

This example disables the hint on procedure MY\_PROC using the target query SELECT \* FROM :TVAR AAA, BBB WHERE AAA.X = BBB.X.

```
ALTER SYSTEM DISABLE STATEMENT HINT ON PROCEDURE MY_PROC FOR SELECT * FROM :TVAR AAA, BBB WHERE AAA.X = BBB.X;
```

**Related Information**  


[ALTER SYSTEM \{ADD | ALTER | REMOVE\} STATEMENT HINT Statement \(System Management\)](alter-system-add-alter-remove-statement-hint-statement-system-management-1ec23ef.md "Adds, alters, or removes statement hints from the system to a specified query or statement hash.")

