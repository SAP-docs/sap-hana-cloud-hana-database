<!-- loio68e2f7a8e06f41cb871276858202c605 -->

# ALTER SYSTEM \{PIN | UNPIN\} SQL PLAN CACHE ENTRY Statement \(System Management\)

Provides a runtime mechanism to bind the target query and hints to the Hint Table to force the compilation of the target query with the hint.



## Syntax

```
ALTER SYSTEM PIN SQL PLAN CACHE ENTRY <plan_id> [ WITH HINT ( <hint_items> ) ]
 | ALTER SYSTEM PIN SQL PLAN CACHE ENTRY LIKE <plan_id> WITH HINT ( <hint_items> )
 | ALTER SYSTEM UNPIN SQL PLAN CACHE ENTRY [ LIKE ] <plan_id>
```



## Syntax Elements


<dl>
<dt><b>

*<plan\_id\>*

</b></dt>
<dd>

Specifies the identifier of the plan to be pinned.

```
<plan_id> ::= <integer_literal>
```

Refer to the M\_SQL\_PLAN\_CACHE view to find the *<plan\_id\>* for the desired plan cache entry.



</dd><dt><b>

WITH HINT *<hint\_items\>*

</b></dt>
<dd>

Specifies one or more hints \(comma-separated list\) to apply to the query. Refer to the HINTS system view for list of available hint items.

```
<hint_items> ::= <string_literal>
```

Pinning a plan with a WITH HINT clause binds the target query to the HINT table.



</dd><dt><b>

PIN

</b></dt>
<dd>

PIN specifies to preserve a plan.

ALTER SYSTEM PIN...WITH HINT clause binds the target query to the HINT table.

ALTER SYSTEM PIN without a WITH HINT clause pins a plan to the SQL plan cache so that the pinned plan will not be evicted from the SQL plan cache, even after an ALTER SYSTEM CLEAR SQL PLAN CACHE is executed. SESSION LOCAL plans are pinned for the duration of the connection, and are evicted when the user connection is closed, regardless of its pin status

Pinned plans are returned to being normal plans after a restart. Only hints remain after a restart.



</dd><dt><b>

UNPIN

</b></dt>
<dd>

UNPIN reverts a pinned plan to a state where it may be evicted following the normal Last Recently Used \(LRU\) eviction scheme, as follows:

-   If the plan was compiled with a WITH HINT clause and pinned to the plan cache \(ALTER SYSTEM PIN...WITH HINT\), then UNPIN removes the hint, unpins the plan, and the plan will be evicted as per the LRU scheme.

-   If the plan was compiled without a WITH HINT clause and pinned \(ALTER SYSTEM PIN\), then the plan is unpinned and will be evicted as per the LRU scheme.




</dd>
</dl>



## Description

Refer to the PINNED\_SQL\_PLANS view to verify the list of currently pinned queries.

If you want to unpin a plan from the SQL plan cache but keep the hint info, you can run an ALTER SYSTEM ADD STATEMENT HINT statement after unpinning.

Check whether the hints in *<hint\_items\>* affect the query plan by using the EXPLAIN PLAN command with the *<plan\_id\>* parameter.

Typical pinning scenario:

1.  Identify the problematic query from the system.

2.  Try to append applicable hints to the query to find the target hint.

3.  Look for the corresponding cache entry from the M\_SQL\_PLAN\_CACHE view and identify the *<plan\_id\>*.

4.  Bind the query and the hint using the ALTER SYSTEM PIN statement. Subsequent execution of the query should use the newly compiled/cached plan.


If WITH HINT is specified, then during indexserver start-up, pinned queries are restored using information from the PINNED\_SQL\_PLANS view. For each pair of SQL Plan Cache key and hints in the PINNED\_SQL\_PLANS view, a plan with the respective hint is compiled and inserted into the SQL Plan cache. If WITH HINT is not specified, then pinned plans are no longer pinned after an indexserver restart.



<a name="loio68e2f7a8e06f41cb871276858202c605__section_iqd_2dg_qbb"/>

## Permissions

You must have the OPTIMIZER ADMIN system privilege to execute the statements listed in the syntax section and access the PINNED\_SQL\_PLANS view.



## Examples

The following statement pins a fictitious plan ***20170203150455***:

```
ALTER SYSTEM PIN SQL PLAN CACHE ENTRY 20170203150455;
```

The following statement unpins the fictitious plan ***20170203150455***:

```
ALTER SYSTEM UNPIN SQL PLAN CACHE ENTRY 20170203150455;
```

The following statement pins the fictitious plan ***1000003***, and specifies the USE\_OLAP\_PLAN hint:

```
ALTER SYSTEM PIN SQL PLAN CACHE ENTRY 1000003 WITH HINT (USE_OLAP_PLAN);
```

**Related Information**  


[EXPLAIN PLAN Statement \(Data Manipulation\)](explain-plan-statement-data-manipulation-20d9ec5.md "Evaluates the execution plan that the database follows when executing an SQL statement.")

[PINNED\_SQL\_PLANS System View](../../020-System-Views-Reference/021-System-Views/pinned-sql-plans-system-view-3a827da.md "Provides information on currently pinned SQL plans and corresponding hints.")

[HINTS System View](../../020-System-Views-Reference/021-System-Views/hints-system-view-f55ce8e.md "Provides all available hints to be used in WITH HINT clauses.")

[M\_SQL\_PLAN\_CACHE System View](../../020-System-Views-Reference/022-Monitoring-Views/m-sql-plan-cache-system-view-20c57b8.md "Provides statistics for an individual execution plan.")

