<!-- loiod2264261d2951014ae11f585d3cca109 -->

# ALTER SYSTEM RECOMPILE SQL PLAN CACHE ENTRY Statement \(System Management\)

Invalidates the designated plan cache entry so that it is recompiled during the next execution time.



<a name="loiod2264261d2951014ae11f585d3cca109__sql_alter_system_recompile_sql_plan_cache_entry_1sql_alter_system_recompile_sql_plan_cache_entry_syntax"/>

## Syntax

```
ALTER SYSTEM RECOMPILE SQL PLAN CACHE ENTRY <plan_id>
```



<a name="loiod2264261d2951014ae11f585d3cca109__sql_alter_system_recompile_sql_plan_cache_entry_1sql_alter_system_recompile_sql_plan_cache_entry_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<plan\_id\>*

</b></dt>
<dd>

Specifies the entry you want to recompile.

```
<plan_id> ::= <integer_literal>
```

Obtain the *<plan\_id\>* from the PLAN\_ID column of the M\_SQL\_PLAN\_CACHE monitoring view.



</dd>
</dl>



<a name="loiod2264261d2951014ae11f585d3cca109__sql_alter_system_recompile_sql_plan_cache_entry_1sql_alter_system_recompile_sql_plan_cache_entry_description"/>

## Description

When invalidated, the entry is recompiled during the next execution time. Use this command when significant changes have occurred to the data cardinalities acted upon by the query plan.



<a name="loiod2264261d2951014ae11f585d3cca109__section_i43_1vx_vcb"/>

## Permissions

You must have the OPTIMIZER ADMIN privilege to execute this statement.



<a name="loiod2264261d2951014ae11f585d3cca109__sql_alter_system_recompile_sql_plan_cache_entry_1sql_alter_system_recompile_sql_plan_cache_entry_examples"/>

## Example

Flag the plan cache entry with plan\_id 247 for recompilation.

```
ALTER SYSTEM RECOMPILE SQL PLAN CACHE ENTRY 247;
```

**Related Information**  


[M\_SQL\_PLAN\_CACHE System View](../../020-System-Views-Reference/022-Monitoring-Views/m-sql-plan-cache-system-view-20c57b8.md "Provides statistics for an individual execution plan.")

