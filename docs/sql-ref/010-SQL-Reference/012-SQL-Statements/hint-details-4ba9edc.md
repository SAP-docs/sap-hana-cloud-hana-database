<!-- loio4ba9edce1f2347a0b9fcda99879c17a1 -->

# HINT Details

The SQL Optimizer usually determines the access path \(for example, index search versus table scan\) on the basis of the costs \(Cost-Based Optimizer\). You can override the SQL Optimizer choice by explicitly specifying hints in the query that enforces a certain access path.



## Hint Syntax in SQL Statements

```
{ SELECT | INSERT | UPDATE | DELETE } ... <hint_clause>
```

```
<hint_clause> ::= WITH HINT( <hint> [, <hint> ...])

<hint>::= { <hint_element> | <routing_hint> | <value_input> }

<hint_element> ::= <hint_name> from public hint list [(<hint_argument_list>)]<hint_argument_list>

<hint_argument_list> ::= <hint_argument> [, <hint_argument> ...]

<hint_argument> ::= hint argument type according to each hint specification (for example, one of STR_CONST, INT_CONST,  ID, or <table_ref>)

<routing_hint> ::=
   ROUTE_TO( <volumd_id> [, <volumd_id> [,...] ] )
   | ROUTE_TO( <service_type> [, <service_type> [,...] ] )
   | NO_ROUTE_TO( <volumd_id> [, <volumd_id> [,...] ] )
   | NO_ROUTE_TO( <service_type> [, <service_type> [,...] ] )
   | ROUTE_BY( { <table_name> | <projection_view_name> } [ ,{ <table_name> | <projection_view_name> } [,...] ] )
   | ROUTE_BY_CARDINALITY( { <table_name> | <projection_view_name> } [, { <table_name> | <projection_view_name> } [,...] ] )

<value_input> ::= MAX_CONCURRENCY (1) | DATA_TRANSFER_COST ({0 | 1})

```

Hint arguments with a framework are also applied.

In the following example, the USE\_OLAP\_PLAN hint is applied:

```
SELECT T2.*FROM (SELECT MAX(COL) FROM T1 GROUP BY COL) T2 WITH HINT( USE_OLAP_PLAN );
```



## Hints by Category

Refer to each category for a more detailed description.



<a name="loio4ba9edce1f2347a0b9fcda99879c17a1__section_ktp_cmf_2z"/>

## Hints for Controlling Request Processing


<dl>
<dt><b>

THROW\_ERROR

</b></dt>
<dd>

Blocks the execution of a given query.



</dd>
</dl>

Examples:

```
SELECT * FROM T1 WITH HINT( THROW_ERROR );
```

```
ALTER SYSTEM ADD STATEMENT HINT ( THROW_ERROR ) FOR SELECT * FROM T1;
```



## Hints for Controlling Cache Behaviors

SAP HANA supports different cache types.

SQL Plan Cache saves compiled plans so that the same query does not need to be compiled every time. This setting saves CPU and compilation time and enables the gathering of statistics \(user name, execution count, avg execution time, and so on\) for each plan.


<dl>
<dt><b>

IGNORE\_PLAN\_CACHE

</b></dt>
<dd>

Ignores the existing plan cache entry \(if any\) and forces the query to compile and execute.

-   If a plan cache entry already exists then it is ignored but still remains in the plan cache.
-   If a plan cache entry does not exist, then no plan cache entry is added.



</dd><dt><b>

USE\_REMOTE\_CACHE

</b></dt>
<dd>

Optimizes SAP HANA Hadoop and forces virtual table queries to have to a materialized result set. Subsequent queries are served from the materialized view.



</dd>
</dl>

Examples:

```
SELECT * FROM T1 WITH HINT( IGNORE_PLAN_CACHE );
```

```
SELECT * FROM T1 WITH HINT( USE_REMOTE_CACHE );
```



## Hints for Scale-out Environment

For a scale-out environment, the SQL optimizer decides on the execution location for each operator based on the operator cost and the data transfer cost. Query routing is determined in a round-robin manner to one of the nodes that contains related objects, such as tables and views.

You may want to specify preferred nodes or objects for routing for performance or any other possible issues. Volume ID or table name can be supplied to hints to enable such routing.

> ### Note:  
> Wrong volume IDs generate an SQL warning.

> ### Note:  
> If more than one hint is listed or nested, then the order of parsing determines which hint to apply. The hint that was given last takes effect.


<dl>
<dt><b>

ROUTE\_TO

</b></dt>
<dd>

Routes the query to the specified volume ID or service type.



</dd><dt><b>

NO\_ROUTE\_TO

</b></dt>
<dd>

Avoids query routing to a specified volume ID or service type.



</dd><dt><b>

ROUTE\_BY

</b></dt>
<dd>

Routes the query to the hosts related to the base table\(s\) of the specified projection view\(s\).



</dd><dt><b>

ROUTE\_BY\_CARDINALITY

</b></dt>
<dd>

Routes the query to the hosts related to the base table\(s\) of the specified projection view\(s\) with the highest cardinality from the input list.



</dd><dt><b>

DATA\_TRANSFER\_COST \(*<value\>*\)

</b></dt>
<dd>

Guides the optimizer to use the weighting factor for the data transfer cost. The value 0 ignores the data transfer cost.



</dd><dt><b>

ROUTE\_OPTIMIZATION\_LEVEL \(MINIMAL | ALL\)

</b></dt>
<dd>

Guides the optimizer to compile with ROUTE\_OPTIMIZATION\_LEVEL \(MINIMAL\) or to default to ROUTE\_OPTIMIZATION\_LEVEL. If the MINIMAL compiled plan is cached, then it compiles once more using the default optimization level during the first execution. This hint is primarily used to shorten statement routing decisions during the initial compilation.



</dd>
</dl>

Example:

```
SELECT * FROM T1 WITH HINT(DATA_TRANSFER_COST(0));
```

The following example routes to the node where the volume ID = 1:

```
CALL P1() WITH HINT( ROUTE_TO(1));
```

The following example routes to one of the nodes with a volume ID other than 2 or 3:

```
CALL P1() WITH HINT( NO_ROUTE_TO(2,3));
```

The following example routes to the node containing table T2:

```
CALL P1() WITH HINT( ROUTE_BY(T2));
```

The following example routes to the node that has the highest cardinality among tables T1, T2, or T3:

```
CALL P1() WITH HINT( ROUTE_BY_CARDINALITY(T1,T2,T3));
```

The following example routes to a volume ID = 1 \(where the last 1 is used\):

```
CALL P1() WITH HINT( NO_ROUTE_TO(1), ROUTE_TO(1));
```



## Hints for OLAP Engine

The Column Search execution engine is chosen automatically by the optimizer based on the cost model.


<dl>
<dt><b>

USE\_OLAP\_PLAN

</b></dt>
<dd>

Guides the optimizer to prefer the OLAP engine over other engines.



</dd><dt><b>

NO\_USE\_OLAP\_PLAN

</b></dt>
<dd>

Guides the optimizer to avoid the use of the OLAP engine.



</dd>
</dl>

Examples:

```
SELECT * FROM T1 WITH HINT( USE_OLAP_PLAN ); 
```

```
SELECT * FROM T1 WITH HINT( NO_USE_OLAP_PLAN ); 
```



<a name="loio4ba9edce1f2347a0b9fcda99879c17a1__section_wnc_d3g_zbb"/>

## Hints for ESX Engine Selection

Use the ESX engine to execute a query.


<dl>
<dt><b>

USE\_ESX\_PLAN

</b></dt>
<dd>

Guides the optimizer to choose the ESX engine over other engines.



</dd><dt><b>

NO\_USE\_ESX\_PLAN

</b></dt>
<dd>

Guides the optimizer to avoid the use of the ESX engine.



</dd>
</dl>

Examples:

```
SELECT * FROM T1 WITH HINT( USE_ESX_PLAN );
```

```
SELECT * FROM T1 WITH HINT( NO_USE_ESX_PLAN );
```



<a name="loio4ba9edce1f2347a0b9fcda99879c17a1__section_itp_1jg_zbb"/>

## Hints for HEX Engine Selection

Use the HEX engine to execute a query.


<dl>
<dt><b>

USE\_HEX\_PLAN

</b></dt>
<dd>

Guides the optimizer to choose the HEX engine over other engines.



</dd><dt><b>

NO\_USE\_HEX\_PLAN

</b></dt>
<dd>

Guides the optimizer to avoid the use of the HEX engine.



</dd>
</dl>

Examples:

```
SELECT * FROM T1 WITH HINT( USE_HEX_PLAN );
```

```
SELECT * FROM T1 WITH HINT( NO_USE_HEX_PLAN );
```



<a name="loio4ba9edce1f2347a0b9fcda99879c17a1__section_vpw_5dd_fcb"/>

## Hints for HEX Enumeration Decisions

The following hints determine special hex enumeration decisions that have performance impacts if the query goes through HEX enumeration.


<dl>
<dt><b>

HEX\_HASH\_JOIN

</b></dt>
<dd>

Guides the optimizer to prefer HEX hash joins over other joins.



</dd><dt><b>

NO\_HEX\_HASH\_JOIN

</b></dt>
<dd>

Guides the optimizer to avoid HEX hash joins.



</dd><dt><b>

HEX\_INDEX\_JOIN

</b></dt>
<dd>

Guides the optimizer to prefer HEX index joins over other joins.



</dd><dt><b>

NO\_HEX\_INDEX\_JOIN

</b></dt>
<dd>

Guides the optimizer to avoid HEX index joins.



</dd><dt><b>

HEX\_NESTED\_LOOP\_JOIN

</b></dt>
<dd>

Guides the optimizer to prefer HEX nested loop joins over other joins.



</dd><dt><b>

NO\_HEX\_NESTED\_LOOP\_JOIN

</b></dt>
<dd>

Guides the optimizer to avoid HEX nested loop joins.



</dd><dt><b>

CONCAT\_FILTER

</b></dt>
<dd>

Guides the optimizer to prefer HEX concat replacements.



</dd><dt><b>

NO\_CONCAT\_FILTER

</b></dt>
<dd>

Guides the optimizer to avoid HEX concat replacements.



</dd>
</dl>



## Hints for Join Engine Optimization

The following hints force a certain join operation behavior:


<dl>
<dt><b>

MAX\_CONCURRENCY \(1\)

</b></dt>
<dd>

Controls concurrency. This setting only accepts the value 1 \(single thread plan execution\) and the Join Engine determines suitable parallelism by default.



</dd>
</dl>

Examples:

```
SELECT * FROM T1 WITH HINT( MAX_CONCURRENCY(1) );
```


<dl>
<dt><b>

CS\_JOIN\_RESULT\_MATERIALIZATION\( ' \[ *<schema\_name\>* :\] *<table\_name\>* ' \)

</b></dt>
<dd>

Specifies the table at which join materialization begins.



</dd><dt><b>

CS\_JOIN\_REDUCTION\( ' \[ *<schema\_name\>* :\] *<table\_name\>* ' \)

</b></dt>
<dd>

Specifies the table at which the reduction phase begins.



</dd><dt><b>

CS\_JOIN\_CYCLE\_BREAK\( ' \[ *<schema\_name\>* :\] *<table\_name\_left\>* ' , ' \[ *<schema\_name\>* :\] *<table\_name\_right\>* ' \)

</b></dt>
<dd>

Specifies the join edge at which a cyclic join is broken up.



</dd><dt><b>

CS\_JOIN\_MATERIALIZATION\_BIGGEST\_TABLE\_FIRST

</b></dt>
<dd>

Specifies that the materialization starts at the biggest table.



</dd><dt><b>

CS\_JOIN\_MATERIALIZATION\_SMALLEST\_TABLE\_FIRST

</b></dt>
<dd>

Specifies that the materialization starts at the smallest table.



</dd><dt><b>

CS\_JOIN\_MATERIALIZATION\_CONCURRENCY\(*<number\>*\)

</b></dt>
<dd>

Defines the concurrency of the join materialization.



</dd><dt><b>

CS\_JOIN\_SHRINK\_SIZE\_THRESHOLD\(*<number\>*\)

</b></dt>
<dd>

Specifies that the intermediate result exceeds this threshold, then tries to shrink it.



</dd><dt><b>

CS\_JOIN\_POST\_CHECK\_SIZE\_THRESHOLD\(*<number\>*\)

</b></dt>
<dd>

Specifies the intermediate result exceeds this threshold, then runs post-conditions and distinct checks on it.



</dd><dt><b>

CS\_JOIN\_REDUCTION\_MULTICOLUMN\_FIRST\('*<table\_name\>*.*<column\_name\>*'\)

</b></dt>
<dd>

Specifies the column to be evaluated first in the JoinEngine semi-join reduction, in the case of a multicolumn join with skewed data distribution.



</dd><dt><b>

CS\_JOIN\_FILTER\_AFTER\_REDUCTION\( ' \[ *<schema\_name\>* :\] *<table\_name\>* ' \)

</b></dt>
<dd>

Applies filters on a table after a join reduction in the join engine.



</dd><dt><b>

CS\_JOIN\_FILTER\_BEFORE\_REDUCTION\( ' \[ *<schema\_name\>* :\] *<table\_name\>* ' \)

</b></dt>
<dd>

Applies filters on a table before a join reduction in the join engine.



</dd>
</dl>



## Hints for Controlling Access Path

The following hints override the cost-based decision of the optimizer in order to utilize or avoid indexes for table access.


<dl>
<dt><b>

INDEX\_SEARCH

</b></dt>
<dd>

Guides the optimizer to access the table by using the available index.



</dd><dt><b>

NO\_INDEX\_SEARCH

</b></dt>
<dd>

Guides the optimizer to avoid table access by using the available index.



</dd>
</dl>

Examples:

```
SELECT * FROM T1 WITH HINT( INDEX_SEARCH );
```

```
SELECT * FROM T1 WITH HINT( NO_INDEX_SEARCH );
```



## Hints for Controlling Join Operations

There are different join algorithms for performing join operations.


<dl>
<dt><b>

INDEX\_JOIN

</b></dt>
<dd>

Guides the optimizer to join input relations through index searches.



</dd><dt><b>

NO\_INDEX\_JOIN

</b></dt>
<dd>

Guides the optimizer to avoid joining the input relations through index searches.



</dd><dt><b>

HASH\_JOIN

</b></dt>
<dd>

Guides the optimizer to join the input relations through probing the hash table.



</dd><dt><b>

NO\_HASH\_JOIN

</b></dt>
<dd>

Guides the optimizer to avoid joining the input relations through probing the hash table.



</dd>
</dl>

Examples:

```
SELECT * FROM T1, T2 WITH HINT( INDEX_JOIN );
```

```
SELECT * FROM T1, T2 WITH HINT( NO_INDEX_JOIN );
```

```
SELECT * FROM T1, T2 WITH HINT( HASH_JOIN );
```

```
SELECT * FROM T1, T2 WITH HINT( NO_HASH_JOIN );
```



## Hints for Controlling Row/Column Store Operations

Most of the operations can be supported in both the row engine and the column engine. The optimizer selects the best operations based on the cost-model. The hints in this section can be used to control whether to prefer or avoid the use of specific engine operators in the query plan.

The following hints guide the optimizer to prefer the column engine operator:

-   CS\_SORT
-   CS\_LIMIT
-   CS\_FILTER
-   CS\_DISTINCT
-   CS\_AGGR
-   CS\_JOIN
-   CS\_UNION\_ALL

> ### Note:  
> A full list of hints to control other row engine or column engine operators can be found in the HINTS view. Using hints that are not described in this section is not recommended.

The following hints guide the optimizer to prefer the row engine operator:

-   NO\_CS\_SORT
-   NO\_CS\_LIMIT
-   NO\_CS\_FILTER
-   NO\_CS\_DISTINCT
-   NO\_CS\_AGGR
-   NO\_CS\_JOIN
-   NO\_CS\_UNION\_ALL



## Hints for Smart Data Access

Smart Data Access uses two kinds of operators to read data from the remote source: Remote Column Scan reads data from the remote server and stores it in ITAB and Remote Row Scan reads data from the remote server and stores it in a buffer.


<dl>
<dt><b>

REMOTE\_COLUMN\_SCAN

</b></dt>
<dd>

Guides the optimizer to prefer Remote Column Scan, which returns ITAB from the remote server.



</dd><dt><b>

NO\_REMOTE\_COLUMN\_SCAN

</b></dt>
<dd>

Guides the optimizer to prefer Remote Row Scan.



</dd><dt><b>

REMOTE\_JOIN\_RELOCATION

</b></dt>
<dd>

Guides the optimizer to process the join at the remote server if possible \(default behavior\).



</dd><dt><b>

NO\_REMOTE\_JOIN\_RELOCATION

</b></dt>
<dd>

Guides the optimizer to process the join at the HANA server if possible.



</dd><dt><b>

REMOTE\_EXPR\_MATERIALIZATION

</b></dt>
<dd>

Guides the optimizer to prefer the expression evaluation at the remote server if possible \(default behavior\).



</dd><dt><b>

NO\_REMOTE\_EXPR\_MATERIALIZATION

</b></dt>
<dd>

Guides the optimizer to prefer the expression evaluation at the HANA server if possible.



</dd><dt><b>

REMOTE\_PREAGGR

</b></dt>
<dd>

Guides the optimizer to generate pre-aggregation at the remote server \(default behavior\).



</dd><dt><b>

NO\_REMOTE\_PREAGGR

</b></dt>
<dd>

Guides the optimizer not to generate pre-aggregation at the remote server.



</dd><dt><b>

REMOTE\_AGGR

</b></dt>
<dd>

Guides the optimizer to process aggregation at remote data source if possible \(default behavior\).



</dd><dt><b>

NO\_REMOTE\_AGGR

</b></dt>
<dd>

Guides the optimizer to process aggregation at HANA server if possible.



</dd><dt><b>

REMOTE\_JOIN

</b></dt>
<dd>

Guides the optimizer to process the join at the remote server if possible. When used with NO\_REMOTE\_JOIN\_RELOCATION, it prefers processing of the join involving tables from the same remote source at the remote server \(default behavior\).



</dd><dt><b>

NO\_REMOTE\_JOIN

</b></dt>
<dd>

Guides the optimizer to process the join between tables at HANA server, even if the tables are from the same remote source.



</dd><dt><b>

REMOTE\_DISTINCT

</b></dt>
<dd>

Guides the optimizer to process the distinct operation at the remote server if possible \(default behavior\).



</dd><dt><b>

NO\_REMOTE\_DISTINCT

</b></dt>
<dd>

Guides the optimizer to process the distinct operation at the HANA server if possible.



</dd><dt><b>

REMOTE\_UNION

</b></dt>
<dd>

Guides the optimizer to process union operation at the remote server if possible \(default behavior\).



</dd><dt><b>

NO\_REMOTE\_UNION

</b></dt>
<dd>

Guides the optimizer to process the union operation at the HANA server if possible.



</dd>
</dl>

Examples:

```
SELECT * FROM T1 WITH HINT( REMOTE_COLUMN_SCAN );
```

```
SELECT * FROM T1 WITH HINT( REMOTE_JOIN_RELOCATION );
```

```
SELECT * FROM T1 WITH HINT( REMOTE_EXPR_MATERIALIZATION );
```

```
SELECT * FROM T1 WITH HINT( REMOTE_PREAGGR );
```

```
SELECT SUM(HT.C1) FROM RT  JOIN HT ON  RT.C1 = HT.C1 GROUP BY  RT.C1 WITH HINT(REMOTE_AGGR)
```

```
SELECT * FROM RT  JOIN HT ON  RT.C1= HT.C1 WITH HINT(REMOTE_JOIN)
```

```
SELECT DISTINCT(HT.C1) FROM RT  JOIN HT ON  RT.C1 = HT.C1 WITH HINT(REMOTE_DISTINCT)
```

```
SELECT * FROM RT UNION SELECT * FROM HT WITH HINT(REMOTE_UNION)
```



## Hints for Result Cache

Use the result cache for applications that accept stale data access. Table functions and SQL/Calculation views can be cached. Since the result cache shows stale data, it can only be used when suitable hints are turned on.


<dl>
<dt><b>

RESULT\_CACHE

</b></dt>
<dd>

Guides the optimizer to utilize the result cache regardless of indexserver configuration, if the result cache is available.



</dd><dt><b>

RESULT\_CACHE\_MAX\_LAG\(*<seconds\>*\)

</b></dt>
<dd>

Guides the optimizer to set the retention period of the result cache to a minimum of this value or the value set in the ADD CACHE configuration.



</dd><dt><b>

RESULT\_CACHE\_NON\_TRANSACTIONAL

</b></dt>
<dd>

Allows join or union operations using the result cache entries and disregards possible transaction inconsistencies.



</dd><dt><b>

RESULT\_CACHE\_NO\_REFRESH

</b></dt>
<dd>

Accesses cached data if cached data is prepared before, without refreshing it, even when its retention period is over.



</dd><dt><b>

RESULT\_LAG\('*<name\>*'\[, *<seconds\>*\]\)

</b></dt>
<dd>

Guides the optimizer to use specified engines if its result lag is less than the maximum seconds.



</dd><dt><b>

RESULT\_CACHE\_AFTER\_ANALYTIC\_PRIVILEGE

</b></dt>
<dd>

Enforces the result cache to use separate data cached after filtering with analytic privileges. This hint does not enforce using the result cache and it is only effective when the query can use the result cache.



</dd><dt><b>

RESULT\_CACHE\_BEFORE\_ANALYTIC\_PRIVILEGE

</b></dt>
<dd>

Enables the result cache to use shared data cached before filtering with analytic privileges. This hint does not enforce using the result cache and it is only effective when the query can use the result cache.



</dd>
</dl>

Examples:

```
SELECT * FROM T1 WITH HINT( NO_RESULT_CACHE );
```

```
SELECT * FROM T1 WITH HINT( RESULT_CACHE );
```

```
SELECT * FROM T1 WITH HINT( RESULT_CACHE_MAX_LAG(60) );
```

```
SELECT * FROM T1 WITH HINT( RESULT_CACHE_NON_TRANSACTIONAL );
```

```
SELECT * FROM T1 WITH HINT( RESULT_LAG ('hana_long') );
```

```
SELECT * FROM T1 WITH HINT( RESULT_LAG ( 'hana_long', 30) );
```

```
SELECT * FROM T1 WITH HINT( RESULT_CACHE_AFTER_ANALYTIC_PRIVILEGE );
```

```
SELECT * FROM T1 WITH HINT( RESULT_CACHE_BEFORE_ANALYTIC_PRIVILEGE );
```



<a name="loio4ba9edce1f2347a0b9fcda99879c17a1__section_ghm_kgs_dz"/>

## Hints for Dynamic Result Cache

Returns an up-to-date query result. This means that the result of the query run on the dynamic result cache is always the same as the result of a query that is not using the cache.


<dl>
<dt><b>

NO\_DYNAMIC\_RESULT\_CACHE

</b></dt>
<dd>

Guides the optimizer not to utilize the dynamic result cache regardless of indexserver configuration, even if it is available.



</dd><dt><b>

DYNAMIC\_RESULT\_CACHE

</b></dt>
<dd>

Guides the optimizer to utilize the dynamic result cache if the dynamic result cache is available \(default\).



</dd><dt><b>

NO\_DYNAMIC\_RESULT\_CACHE\_IMPLICIT\_MATCH

</b></dt>
<dd>

Guides the optimizer not to try automatic view matching \(default\).



</dd><dt><b>

DYNAMIC\_RESULT\_CACHE\_IMPLICIT\_MATCH

</b></dt>
<dd>

Guides the optimizer to try automatic view matching regardless of indexserver configuration.



</dd><dt><b>

DYNAMIC\_RESULT\_CACHE\_IMPLICIT\_MATCH

</b></dt>
<dd>

Guides the optimizer to try automatic view matching only with given views.

```
DYNAMIC_RESULT_CACHE_IMPLICIT_MATCH(<schema_name>.<view_name>[,<schema_name>.<view_name>…]);
```



</dd>
</dl>

Examples:

```
SELECT * FROM V1 WITH HINT( NO_DYNAMIC_RESULT_CACHE );
```

```
SELECT * FROM V1 WITH HINT( DYNAMIC_RESULT_CACHE);
```

```
SELECT * FROM T1 WITH HINT( NO_DYNAMIC_RESULT_CACHE_IMPLICIT_MATCH );
```

```
SELECT * FROM T1 WITH HINT( DYNAMIC_RESULT_CACHE_IMPLICIT_MATCH );
```

```
SELECT * FROM T1 WITH HINT( DYNAMIC_RESULT_CACHE_IMPLICIT_MATCH ("TEST"."V1") );
```



## Hints for Asynchronous Table Replication

Used for applications that accept stale data access. Since the asynchronous table shows stale data, it can only be used with suitable hints or to access the replica table by using the explicit replica table name.


<dl>
<dt><b>

RESULT\_LAG

</b></dt>
<dd>

Guides the optimizer to access source or replica tables by evaluating stale data with the *<seconds\>* parameter. For example:

```
RESULT_LAG('<name>' [ ,<seconds>])
```



</dd>
</dl>

Examples:

```
SELECT * FROM T1 WITH HINT( RESULT_LAG ('hana_short') );
```

```
SELECT * FROM T1 WITH HINT( RESULT_LAG ('hana_atr') );
```



## Hints for Column View Cardinality Estimation

Column Views \(Join views, OLAP views, and Calculation views\) are relations, which can be used in SQL plans. Cardinality estimation of such view objects is necessary for the SQL Optimizer to find an optimal plan.

The optimizer has three different estimation methods, each of which has its own trade-offs in terms of the quality and efficiency. The optimizer utilizes an appropriate method among them, considering the complexity of a given plan.

These hints maneuver the optimizer to use a designated method for cardinality estimation of all of the related Column views.


<dl>
<dt><b>

NO\_COLUMN\_VIEW\_ESTIMATION

</b></dt>
<dd>

Gets a record count estimation of the largest base table \(legacy\).



</dd><dt><b>

COLUMN\_VIEW\_ESTIMATION\(RECORD COUNT\)

</b></dt>
<dd>

Guides the optimizer to use the output record count estimation, which is done in each engine layer.



</dd><dt><b>

COLUMN\_VIEW\_ESTIMATION\(SIMPLE\)

</b></dt>
<dd>

Guides the optimizer to use a comprehensive estimation method to retrieve SIMPLE histograms \(record count, distinct value count, and so on\) for all of the requested attributes.



</dd><dt><b>

COLUMN\_VIEW\_ESTIMATION

</b></dt>
<dd>

Guides the optimizer to utilize the latest estimation method.



</dd>
</dl>

Examples:

```
SELECT * FROM T1 WITH HINT( NO_COLUMN_VIEW_ESTIMATION );
```

```
SELECT * FROM T1 WITH HINT( COLUMN_VIEW_ESTIMATION (RECORD COUNT) );
```

```
SELECT * FROM T1 WITH HINT( COLUMN_VIEW_ESTIMATION (SIMPLE) );
```

```
SELECT * FROM T1 WITH HINT( COLUMN_VIEW_ESTIMATION ); 
```



## Hints for Access Path Optimization on Column Store Tables


<dl>
<dt><b>

CS\_PRIMARY\_KEY

</b></dt>
<dd>

Forces the use of the primary key, even though the optimizer estimates otherwise. This hint is only applicable if the key is not fully defined in the query.



</dd><dt><b>

NO\_CS\_PRIMARY\_KEY

</b></dt>
<dd>

Forbids the use of the primary key, although the optimizer estimates otherwise. This hint is only applicable if the key is not fully defined in the query.



</dd><dt><b>

CS\_ESTIMATION\(SIMPLE | ALL\)

</b></dt>
<dd>

Controls the estimation phase of the column-store table query. ALL \(default\) estimates all of the predicates and SIMPLE skips predicates that are too expensive to estimate.



</dd><dt><b>

NO\_CS\_ESTIMATION

</b></dt>
<dd>

Skips the estimation phase of the column-store table query completely.



</dd><dt><b>

CS\_FILTER\_FIRST\(*<column\>*\)

</b></dt>
<dd>

Specifies the preferred starting column in a conjunction.



</dd>
</dl>



<a name="loio4ba9edce1f2347a0b9fcda99879c17a1__section_nbh_c5r_dz"/>

## Hints for Workload Management

Provides a method to set another workload class for a query, regardless of any workload mappings.


<dl>
<dt><b>

WORKLOAD\_CLASS\(*<workload\_class\_name\>*\)

</b></dt>
<dd>

Designates a certain workload class for the statement execution:

-   The workload class must be created before using this hint.
-   If the specified workload class does not exist, the hint is ignored and the corresponding SQL warning is returned for the statement execution.
-   Only workload classes which have more restricted properties compared to the ones set for session-wise admission control are applied. Otherwise, the hint is ignored and the corresponding SQL warning is returned. This hint clause only allows priority, thread limit, and memory limit down-wise.



</dd>
</dl>

Examples:

```
CREATE WORKLOAD CLASS "MY_WORKLOAD_CLASS_1" SET 'PRIORITY'='9';
```

```
SELECT * FROM T1 WITH HINT( WORKLOAD_CLASS("MY_WORKLOAD_CLASS_1") );
```

The following examples suppose that two workload classes are matched to the current execution request:


<dl>
<dt><b>

Case 1

</b></dt>
<dd>

-   Workload class 'MY\_WORKLOAD\_CLASS1' fit by mapping: PRIORITY 5, THREAD 5, MEMORY 50GB
-   Workload class 'MY\_WORKLOAD\_CLASS2' fit by HINT: PRIORITY 4, THREAD 4, MEMORY 30GB

The hint clause is applied and the effective values are: `PRIORITY 4`, `THREAD 4`, and `MEMORY 30 GB`.



</dd><dt><b>

Case 2

</b></dt>
<dd>

-   Workload class 'MY\_WORKLOAD\_CLASS1' fit by mapping: PRIORITY 5, THREAD 5, MEMORY 50GB
-   Workload class 'MY\_WORKLOAD\_CLASS2' fit by HINT: PRIORITY 4, THREAD undefined, MEMORY 30GB

The hint clause is ignored because the thread limit is not defined.



</dd><dt><b>

Case 3

</b></dt>
<dd>

-   Workload class 'MY\_WORKLOAD\_CLASS1' fit by mapping: PRIORITY 5, THREAD undefined, MEMORY 50GB
-   Workload class 'MY\_WORKLOAD\_CLASS2' fit by HINT: PRIORITY 4, THREAD undefined, MEMORY 30GB

The hint clause is applied because both thread limits are not defined.



</dd><dt><b>

Case 4

</b></dt>
<dd>

-   Workload class 'MY\_WORKLOAD\_CLASS1' fit by mapping: PRIORITY 5, THREAD undefined, MEMORY 50GB
-   Workload class 'MY\_WORKLOAD\_CLASS2' fit by HINT: PRIORITY 4, THREAD undefined, MEMORY 70GB

The hint clause is ignored because the memory limit exceeded the 50 GB that is defined by the mapping.



</dd>
</dl>



## Hints for Size Estimation

Size Estimations are related to the SQL Optimizer and are necessary to find an optimal plan.


<dl>
<dt><b>

ESTIMATION\_SAMPLES\(*<number\>*\)

</b></dt>
<dd>

-   Controls the number of samples that are randomly picked from each of the base tables. The samples estimate local filter selectivity, as well as join condition selectivity. You can increase the number of samples to increase the accuracy of the estimation in exchange for a longer compilation time.
-   By default, the *<number\>* value is 1000 when there is no hint.
-   If the *<number\>* is 0, then no sampling is done and all sampling related estimation is skipped.
-   A *<number\>* value, which is below 0 is not allowed and throws an exception.



</dd><dt><b>

JOIN\_SAMPLING, NO\_JOIN\_SAMPLING

</b></dt>
<dd>

-   Turns join selectivity sampling on or off.
-   By default join sampling is enabled.
-   The feature also turns off when ESTIMATION\_SAMPLES\(0\) is specified because there are no samples to use.



</dd><dt><b>

JOIN\_SKEW\_ESTIMATION, NO\_JOIN\_SKEW\_ESTIMATION

</b></dt>
<dd>

-   Turns join skew estimation using the top k value from base tables on or off.
-   By default join skew estimation is enabled, but depending on the INI configuration, it can be turned off. The hint has higher priority over the INI configuration settings.
-   Join skew estimation is internally implemented independently from join sampling. Join sampling uses randomly selected samples, whereas skew factor computations use the top 10 most frequent values provided by the column store. Their related issues have different characteristics: Join sampling related issues are usually performance related issues whereas Skew factor computation issues are usually crash problems.



</dd><dt><b>

TABLE\_FILTER\_ESTIMATION\(MINIMAL | SAMPLING | ALL\)

</b></dt>
<dd>

-   Controls the level of techniques used to estimate the table filter selectivity. Lower-level use is a subset of techniques that are used in the upper level.
-   MINIMAL: uses heuristic-based selectivity estimation using only base statistics \(table row count and distinct count of each column\).
-   SAMPLING: uses basic sampling for filter estimation together with heuristic-based estimation.
-   ALL \(default\): uses table filter estimation. Newly added estimation techniques are only included for this level.



</dd><dt><b>

DISTRIBUTED\_ESTIMATION, NO\_DISTRIBUTED\_ESTIMATION

</b></dt>
<dd>

-   Turns remote size statistics \(row count/distinct count/filter selectivity of remote tables\) retrieval on or off.
-   By default remote statistics retrieval is enabled, but depending on the initial configuration, it can be turned off. The hint has higher priority over the initial configuration setting.



</dd><dt><b>

EXHAUSTIVE\_JOIN\_ESTIMATION, NO\_EXHAUSTIVE\_JOIN\_ESTIMATION

</b></dt>
<dd>

Controls if the size estimation should be updated using join alternatives. While this increases the accuracy of the size estimation of join, it can also increase the compilation time and memory. The default value is off.



</dd>
</dl>

Examples:

```
SELECT * FROM T1 WITH HINT( ESTIMATION_SAMPLES(0) );
```

```
SELECT * FROM T1 WITH HINT( JOIN_SAMPLING );
```

```
SELECT * FROM T1 WITH HINT( NO_JOIN_SKEW_ESTIMATION );
```

```
SELECT * FROM T1 WITH HINT( TABLE_FILTER_ESTIMATION(SAMPLING) );
```

```
SELECT * FROM T1 WITH HINT( NO_DISTRIBUTED_ESTIMATION );
```



## Hints for SQL Optimizer Plan Generation

There can be a plan where the same sequence of execution repeats multiple times, each with a different requester. For such plans, the optimizer can perform the sequence of executions only once and pass the results to all the requesters depending on the cost model \(called subplan sharing\).

> ### Note:  
> Subplan sharing can be beneficial if the repeated sequence uses heavy CPU, consumes a large amount of memory, or takes a long time to execute.


<dl>
<dt><b>

SUBPLAN\_SHARING

</b></dt>
<dd>

Guides the optimizer to prefer choosing the shared subplan.

-   Accepts view names as optional parameters to provide more granular control of subplan sharing.
-   Accepts aliases and nested views \(optional\).



</dd><dt><b>

NO\_SUBPLAN\_SHARING

</b></dt>
<dd>

Guides the optimizer to unfold the shared subplan:

-   Accepts view names as optional parameters to provide more granular control of unfolding the shared subplan.
-   Accepts aliases and nested views \(optional\).



</dd>
</dl>

Examples:

```
SELECT * FROM T1 WITH HINT( SUBPLAN_SHARING );
```

```
SELECT * FROM VIEW1 WITH HINT( SUBPLAN_SHARING (VIEW1) );
```

```
SELECT * FROM T1 WITH HINT( NO_SUBPLAN_SHARING );
```

```
SELECT * FROM VIEW1,VIEW2 WITH HINT( NO_SUBPLAN_SHARING (VIEW1, VIEW2) );
```

The following example forces subplan sharing on view1 and forces no subplan sharing on view2 \(the rest of the shared views are generated following default logic\):

```
SELECT * FROM VIEW1,VIEW2 WITH HINT( SUBPLAN_SHARING (VIEW1), NO_SUBPLAN_SHARING (VIEW2) );
```

The following example forces subplan sharing on view1 and forces no subplan sharing on any other possible shared views:

```
SELECT * FROM VIEWS WITH HINT( SUBPLAN_SHARING (VIEW1), NO_SUBPLAN_SHARING );
```

Calculation views are unfolded during plan generation to enable optimization using the SQL Optimizer whenever possible. Normally an unfolding calculation view is beneficial, but there can be cases where it leads to a degradation in performance.


<dl>
<dt><b>

CALC\_VIEW\_UNFOLDING

</b></dt>
<dd>

Guides the optimizer to unfold calculation views.

-   Accepts view names as optional parameters to provide more granular control of calculation view unfolding.
-   Accepts nested views but does not accept aliases \(optional\).



</dd><dt><b>

NO\_CALC\_VIEW\_UNFOLDING

</b></dt>
<dd>

Guides the optimizer to preserve the calculation view \(does not unfold the calculation view\):

-   Accepts view names as optional parameters to provide more granular control of calculation view unfolding.
-   Accepts nested views but does not accept aliases \(optional\).



</dd>
</dl>

Examples:

```
SELECT * FROM T1 WITH HINT( CALC_VIEW_UNFOLDING ); 
```

```
SELECT * FROM VIEW1 WITH HINT( CALC_VIEW_UNFOLDING ("SYS_BIC"."CALC_VIEW") ); 
```

```
SELECT * FROM T1 WITH HINT( NO_CALC_VIEW_UNFOLDING ); 
```

```
SELECT * FROM VIEW1,VIEW2 WITH HINT( NO_CALC_VIEW_UNFOLDING ("SYS_BIC"."CALC_VIEW1", "SYS_BIC"."CALC_VIEW2") );
```

The following example forces calculation view unfolding on view1 and forces no calculation view unfolding on view2 \(the rest of the calculation views are generated following default logic\):

```
SELECT * FROM VIEW1,VIEW2 WITH HINT( CALC_VIEW_UNFOLDING ("SYS_BIC"."CALC_VIEW1"), NO_CALC_VIEW_UNFOLDING ("SYS_BIC"."CALC_VIEW2") );
```

The following example forces calculation view unfolding on view1 and forces no calculation view unfolding on any other calculation views:

```
SELECT * FROM VIEWS WITH HINT( CALC_VIEW_UNFOLDING (("SYS_BIC"."CALC_VIEW1"), NO_CALC_VIEW_UNFOLDING );
```

There are optimization levels created during plan generation to enable optimization using the SQL Optimizer. Normally, a high optimization level is beneficial but selecting another level can be useful in some cases when optimization leads to a degradation in performance:

-   Accepts ID-type arguments \(MINIMAL | RULE\_BASED | MINIMAL\_COST\_BASED | COST\_BASED\).
-   COST\_BASED is the default optimization level, which enables all optimization steps.
-   Other hints that control rewriting rules can be used together with the OPTIMIZATION\_LEVEL to selectively override decisions made by the hint.

**OPTIMIZATION\_LEVEL**


<table>
<tr>
<th valign="top">

Hint Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

OPTIMIZATION\_LEVEL \(MINIMAL\)

</td>
<td valign="top">

Disables all optimization rules except the mandatory rules that execute the query as it is.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZATION\_LEVEL \(RULE\_BASED\)

</td>
<td valign="top">

Displays all rewriting rules, including the MINIMAL optimization level.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZATION\_LEVEL \(MINIMAL\_COST\_BASED\)

</td>
<td valign="top">

Displays the RULE\_BASED optimization level plus the heuristic join reordering.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZATION\_LEVEL \(COST\_BASED\)

</td>
<td valign="top">

Displays the MINIMAL\_COST\_BASED optimization level plus available cost-based optimizations, including logical enumeration. This is the default option.

</td>
</tr>
</table>

Examples:

```
SELECT * FROM TABLES WITH HINT (OPTIMIZATION_LEVEL(MINIMAL))
```

```
SELECT * FROM TABLES WITH HINT (OPTIMIZATION_LEVEL(MINIMAL), JOIN_REMOVAL)
```

```
SELECT * FROM TABLES WITH HINT (OPTIMIZATION_LEVEL(RULE_BASED))
```

```
SELECT * FROM TABLES WITH HINT (OPTIMIZATION_LEVEL(MINIMAL_COST_BASED))
```

```
SELECT * FROM TABLES WITH HINT (OPTIMIZATION_LEVEL(COST_BASED), NO_JOIN_REMOVAL)
```

Inter-operator parallelism for multiple column search operator is decided during plan generation to enable optimization using the SQL Optimizer. Normally parallelism is beneficial in performance, but minimizing parallelism is useful in some cases.


<dl>
<dt><b>

PARALLEL\_COLUMN\_SEARCH

</b></dt>
<dd>

Guides the optimizer to force column search operator parallelism.



</dd><dt><b>

NO\_PARALLEL\_COLUMN\_SEARCH

</b></dt>
<dd>

Guides the optimizer to minimize column search operator parallelism.



</dd>
</dl>

Example:

```
SELECT * FROM (SELECT t1.a, t1.b, SUM(t1.c) AS s1 , ROW_NUMBER() OVER (PARTITION by t1.b) AS rr1 FROM t1,t2 WHERE t1.a+0=t2.a+0 GROUP BY t1.a, t1.b) UNION ALL (SELECT t2.a, t2.b, SUM(t2.c) AS s2, ROW_NUMBER() OVER (PARTITION BY t2.b) AS rr2 FROM t2 GROUP BY t2.a, t2.b) WITH HINT (NO_CS_EXPR_JOIN, PARALLEL_COLUMN_SEARCH)
```

Generated plan:

![](images/SAP_HANA_Size_Estimation_Diagram_59b3fb3.png)

Without the hint, TS1 is not parallelized, which means an OLTP search may be used. However, you can parallelize TS1 by using the hint PARALLEL\_COLUMN\_SEARCH.

The predicate is simplified during plan generation to enable optimization using the SQL Optimizer whenever possible. Normally, simplifying the predicate is beneficial but there can be cases where it leads to a degradation in performance.


<dl>
<dt><b>

NO\_PREDICATE\_SIMPLIFICATION

</b></dt>
<dd>

Guides the optimizer to disable predicate simplification. This setting applies to all internal predicates.



</dd>
</dl>

Example:

```
Given predicate: a != 0 and a = 0 Without hint: const false With hint: a != 0 and a = 0
```

Constant values are pre-evaluated during plan generation to enable optimization using the SQL Optimizer whenever possible. Normally pre-evaluating constant values are beneficial but there can be cases where it leads to a degradation in performance.


<dl>
<dt><b>

NO\_CONST\_PREEVALUATION

</b></dt>
<dd>

Guides the optimizer to disable constant pre-evaluation. This is applied to all internal constant values.



</dd>
</dl>

Example:

```
Given constant value: a = 0 + 1 Without hint: a = 1 With hint: a = 0 + 1
```


<dl>
<dt><b>

JOIN\_FILTER\_REORDERING

</b></dt>
<dd>

Guides the optimizer to reorder join predicates inside of conjunctive and disjunctive conditions:

-   Reordering is done by using the estimated selectivity of each predicate inside of conjunctive and disjunctive terms.
-   Can only be applied to row store join operations.



</dd><dt><b>

OLAP\_FACT\_TABLE\("*<table\_name\>*"\)

</b></dt>
<dd>

Chooses a fact table whose name is as given:

-   If the *<table\_name\>* does not exist, then the hint is ignored.
-   If candidate table exists more than two times in one column search \(for example, in a self-join\), then one of the tables is chosen by the current fact table decision heuristic logic.



</dd><dt><b>

\(NO\_\)RECOMPILE\_WITH\_SQL\_PARAMETERS

</b></dt>
<dd>

Guides the optimizer to enable/disable recompilation if a query has parameters:

-   The default behavior for compilation is to compile without parameters.
-   The default behavior for execution is to recompile with parameters if parameters exist and the plan is not based on heuristics.
-   When used with the RECOMPILE\_WITH\_SQL\_PARAMETERS hint, this is compiled without parameters.
-   When used with the RECOMPILE\_WITH\_SQL\_PARAMETERS hint, execution is performed by recompiling with parameters if parameters exist.
-   When used with the NO\_RECOMPILE\_WITH\_SQL\_PARAMETERS hint, this is compiled without parameters.



</dd><dt><b>

NO\_JOIN\_CARDINALITY\(*<option\>*\)

</b></dt>
<dd>

Discards the join cardinality information in the plan so that it does not affect the optimization.


<table>
<tr>
<th valign="top">

Hint name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

NO\_JOIN\_CARDINALITY\(ALL\)

</td>
<td valign="top">

Discards all join cardinality information in the plan.

</td>
</tr>
<tr>
<td valign="top">

NO\_JOIN\_CARDINALITY\(EXPLICIT\)

</td>
<td valign="top">

Discards all join cardinality information specified in the model.

</td>
</tr>
<tr>
<td valign="top">

NO\_JOIN\_CARDINALITY\(IMPLICIT\)

</td>
<td valign="top">

Discards all join cardinality that is computed or derived by the SQL Optimizer using the metadata or the join cardinality specified in the model.

</td>
</tr>
</table>



</dd><dt><b>

CHECK\_JOIN\_CARDINALITY

</b></dt>
<dd>

Forces the SQL Optimizer to create a plan that runs in join cardinality check mode. It checks every join operator with join cardinality information and returns an error when it finds any row that violates this information. The error message displays the identifier of the join operator with the violation. It can only find one join operator at a time so to correct all of the incorrect join cardinalities in a query it is necessary to fix one issue at a time and repeat the check until all of the errors are resolved.

> ### Note:  
> Due to the additional checking, the query performance can be very slow compared to the plan without the hint so it is not recommended to turn the checking on by default.



</dd><dt><b>

PRESERVE\_GROUPBY

</b></dt>
<dd>

Forces the SQL Optimizer to not remove or retrieve any redundant group bys in the plan and executes as many user-given group bys as possible. This aids in avoiding using up too much memory caused by large intermediate results made of joins.

This hint blocks the following transformations:

-   Join through aggregation
-   Merge aggregation
-   Group by simplification



</dd><dt><b>

OPTIMIZATION\_TRANSFORMATION\_LIMIT\(*<integer\>*\)

</b></dt>
<dd>

Sets the maximum number of transformation rules to apply during plan enumeration.

The default value is 2,000. Specifying a large value can lead to increased compilation time.



</dd><dt><b>

NO\_LARGE\_EXPR\_MATERIALIZATION

</b></dt>
<dd>

Disables the early materialization of a large expression created by the SQL Optimizer.

The unfolding view copies the expression when the parent of the view references the view column. When the expression is very large, copying it can have a huge impact, slowing down other optimization steps because of the increase in size.



</dd>
</dl>



<a name="loio4ba9edce1f2347a0b9fcda99879c17a1__section_d1m_2hk_y1c"/>

## Hints for Plan Variant

Refer to the below table for a list of hints and their descriptions:


<dl>
<dt><b>

PLAN\_VARIANT

</b></dt>
<dd>

When a column argument is provided with this hint, filters with the given column argument\(T1.C1\) are preferred as variant filter.



</dd><dt><b>

PLAN\_VARIANT\_FILTER\_COUNT

</b></dt>
<dd>

Change the maximum number of variant filters. The default is 3.



</dd><dt><b>

PLAN\_VARIANT\_PLAN\_COUNT

</b></dt>
<dd>

Change the maximum number of stored plans in the plan variant cache. The default is 10.



</dd>
</dl>

Examples:

```
SELECT * FROM T1 WHERE C1 = ? WITH HINT (PLAN_VARIANT(T1.C1));
SELECT * FROM DUMMY WITH HINT (PLAN_VARIANT, PLAN_VARIANT_FILTER_COUNT(10));
SELECT * FROM DUMMY WITH HINT (PLAN_VARIANT, PLAN_VARIANT_PLAN_COUNT(20));
```



## Hints for Query Rewriting and Logical Transformations

The SQL Optimizer relies heavily on query rewriting and logical transformation rules to enumerate all possible plans to find the best plan in the potential search space. Using the hints below can help you manipulate the SQL Optimizer and provide a quick workaround to fix various issues. For example:

```
SELECT * FROM T1 WITH HINT( JOIN_REMOVAL ); 
SELECT * FROM T1 WITH HINT(  NO_JOIN_REMOVAL );
```

Refer to the below table for a list of hints and their descriptions:


<table>
<tr>
<th valign="top">

Category

</th>
<th valign="top">

Hint Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

AGGR\_TARGET

</td>
<td valign="top">

Prefers aggregation toward a target.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

DISJ\_FILTER\_TRANSFORMATION

</td>
<td valign="top">

Prefers a split disjunctive filter into union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

NO\_DISJ\_FILTER\_TRANSFORMATION

</td>
<td valign="top">

Avoids a split disjunctive filter into union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

JOIN\_SIMPLIFICATION

</td>
<td valign="top">

Prefers join simplification.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

NO\_JOIN\_SIMPLIFICATION

</td>
<td valign="top">

Avoids join simplification.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

GROUPING\_REMOVAL

</td>
<td valign="top">

Prefers unnecessary grouping removal.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

NO\_GROUPING\_REMOVAL

</td>
<td valign="top">

Avoids unnecessary grouping removal.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

AGGR\_SIMPLIFICATION

</td>
<td valign="top">

Prefers aggregation simplification.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

NO\_AGGR\_SIMPLIFICATION

</td>
<td valign="top">

Avoids aggregation simplification.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

MATERIALIZED\_COLUMN\_REMOVAL

</td>
<td valign="top">

Prefers an unnecessary column removal.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

NO\_MATERIALIZED\_COLUMN\_REMOVAL

</td>
<td valign="top">

Avoids an unnecessary column removal.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

JOIN\_REMOVAL

</td>
<td valign="top">

Prefers an unnecessary join removal.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

NO\_JOIN\_REMOVAL

</td>
<td valign="top">

Avoids an unnecessary join removal.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

GROUPING\_SIMPLIFICATION

</td>
<td valign="top">

Prefers a group by simplification.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

NO\_GROUPING\_SIMPLIFICATION

</td>
<td valign="top">

Avoids a group by simplification.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

CONST\_VIEW\_UNFOLDING

</td>
<td valign="top">

Prefers constant view unfolding.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

NO\_CONST\_VIEW\_UNFOLDING

</td>
<td valign="top">

Avoids constant view unfolding.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

HOST\_PORT\_JOIN\_COLOCATION

</td>
<td valign="top">

Prefers a host/port join thru union.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

NO\_HOST\_PORT\_JOIN\_COLOCATION

</td>
<td valign="top">

Avoids a host/port join thru union.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

CALC\_VIEW\_UNFOLDING

</td>
<td valign="top">

Prefers the unfold calculation view.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

NO\_CALC\_VIEW\_UNFOLDING

</td>
<td valign="top">

Avoids the unfold calculation view.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

TYPE\_CAST\_REMOVAL

</td>
<td valign="top">

Prefers the removal of a redundant type cast.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

NO\_TYPE\_CAST\_REMOVAL

</td>
<td valign="top">

Avoids the removal of a redundant type cast.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

WINDOW\_REMOVAL

</td>
<td valign="top">

Prefers the removal of window function aggregation.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

NO\_WINDOW\_REMOVAL

</td>
<td valign="top">

Avoids the removal of window function aggregation.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

JOIN\_REMOVAL\_USING\_CARDINALITY

</td>
<td valign="top">

Prefers join removal based on cardinality.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

NO\_JOIN\_REMOVAL\_USING\_CARDINALITY

</td>
<td valign="top">

Avoids join removal based on cardinality.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

PARTITION\_PRUNING

</td>
<td valign="top">

Prefers compile-time partition pruning.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

NO\_PARTITION\_PRUNING

</td>
<td valign="top">

Avoids compile-time partition pruning.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

FILTER\_RULE

</td>
<td valign="top">

Prefers applying the filter rule.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

NO\_FILTER\_RULE

</td>
<td valign="top">

Avoids applying the filter rule.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

JOIN\_RULE

</td>
<td valign="top">

Prefers applying the join rule.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

NO\_JOIN\_RULE

</td>
<td valign="top">

Avoids applying the join rule.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

UNFOLD\_SCALAR\_UDF

</td>
<td valign="top">

Prefers scalar UDF unfolding.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_REWRITE

</td>
<td valign="top">

NO\_UNFOLD\_SCALAR\_UDF

</td>
<td valign="top">

Avoids scalar UDF unfolding.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

AGGR\_THRU\_FILTER

</td>
<td valign="top">

Prefers push down aggregation through a filter.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_AGGR\_THRU\_FILTER

</td>
<td valign="top">

Avoids push down aggregation through a filter.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

AGGR\_THRU\_JOIN

</td>
<td valign="top">

Prefers push down aggregation through join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_AGGR\_THRU\_JOIN

</td>
<td valign="top">

Avoids push down aggregation through join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

DISTINCT\_THRU\_UNION

</td>
<td valign="top">

Prefers push down distinct through union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_DISTINCT\_THRU\_UNION

</td>
<td valign="top">

Avoids push down distinct through union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

AGGR\_INTO\_AGGR

</td>
<td valign="top">

Prefers merging two aggregations into one.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_AGGR\_INTO\_AGGR

</td>
<td valign="top">

Avoids merging two aggregations into one.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

AGGR\_INTO\_TABLE

</td>
<td valign="top">

Prefers merging aggregation with table scans.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_AGGR\_INTO\_TABLE

</td>
<td valign="top">

Avoids merging aggregation with table scans.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

DISTINCT\_INTO\_DISTINCT

</td>
<td valign="top">

Prefers merging two distincts into one.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_DISTINCT\_INTO\_DISTINCT

</td>
<td valign="top">

Avoids merging two distincts into one.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

DISTINCT\_INTO\_SEMI\_JOIN

</td>
<td valign="top">

Prefers merging a distinct with a join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_DISTINCT\_INTO\_SEMI\_JOIN

</td>
<td valign="top">

Avoids merging a distinct with a join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

UNION\_INTO\_UNION

</td>
<td valign="top">

Prefers merge\_union\_all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_UNION\_INTO\_UNION

</td>
<td valign="top">

Avoids merge\_union\_all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

UNION \_INTO\_UNION \_THRU\_AGGR

</td>
<td valign="top">

Prefers merge union all through aggregation.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_UNION \_INTO\_UNION \_THRU\_AGGR

</td>
<td valign="top">

Avoids merge union all through aggregation.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

PREAGGR\_BEFORE\_JOIN

</td>
<td valign="top">

Prefers pre-aggregation before join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_PREAGGR\_BEFORE\_JOIN

</td>
<td valign="top">

Avoids pre-aggregation before join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

DOUBLE\_PREAGGR\_BEFORE\_JOIN

</td>
<td valign="top">

Prefers pre-aggregation before join for both of the children.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_DOUBLE\_PREAGGR\_BEFORE\_JOIN

</td>
<td valign="top">

Avoids pre-aggregation before join for both of the children.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

PREAGGR\_BEFORE\_UNION

</td>
<td valign="top">

Prefers pre-aggregation before union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_PREAGGR\_BEFORE\_UNION

</td>
<td valign="top">

Avoids pre-aggregation before union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

DISJ\_JOIN\_INTO\_UNION

</td>
<td valign="top">

Prefers to split disjunctive join predicates into filters and making union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_DISJ\_JOIN\_INTO\_UNION

</td>
<td valign="top">

Avoids splitting disjunctive join predicates into filters and making union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

PREDISTINCT\_BEFORE\_SEMI\_JOIN

</td>
<td valign="top">

Prefers putting DISTINCT on the right child of SEMI or ANTI SEMI joins.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_PREDISTINCT\_BEFORE\_SEMI\_JOIN

</td>
<td valign="top">

Avoids putting DISTINCT on the right child of SEMI or ANTI SEMI joins.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

JOIN\_THRU\_AGGR

</td>
<td valign="top">

Prefers pushing down joins through aggregation.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_JOIN\_THRU\_AGGR

</td>
<td valign="top">

Avoids pushing down joins through aggregation.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

JOIN\_THRU\_FILTER

</td>
<td valign="top">

Prefers pushing down joins through the filter.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_JOIN\_THRU\_FILTER

</td>
<td valign="top">

Avoids pushing down joins through the filter.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

JOIN\_THRU\_JOIN

</td>
<td valign="top">

Prefers pushing down joins through join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_JOIN\_THRU\_JOIN

</td>
<td valign="top">

Avoids pushing down joins through join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

JOIN\_THRU\_UNION

</td>
<td valign="top">

Prefers pushing down joins through union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_JOIN\_THRU\_UNION

</td>
<td valign="top">

Avoids pushing down joins through union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

SEMI\_JOIN\_BEFORE\_UNION

</td>
<td valign="top">

Prefers pushing down semi-joins through union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_SEMI\_JOIN\_BEFORE\_UNION

</td>
<td valign="top">

Avoids pushing down semi-joins through union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

FILTER\_THRU\_JOIN

</td>
<td valign="top">

Prefers pushing down filters through union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_FILTER\_THRU\_JOIN

</td>
<td valign="top">

Avoids pushing down filters through union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

FILTER\_THRU\_AGGR

</td>
<td valign="top">

Prefers pushing down filters through aggregation.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_FILTER\_THRU\_AGGR

</td>
<td valign="top">

Avoids pushing down filters through aggregation.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

FILTER\_THRU\_UNION

</td>
<td valign="top">

Prefers pushing down filters through union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_FILTER\_THRU\_UNION

</td>
<td valign="top">

Avoids pushing down filters through union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

PRELIMIT\_BEFORE\_UNION

</td>
<td valign="top">

Prefers pushing down limits before union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_PRELIMIT\_BEFORE\_UNION

</td>
<td valign="top">

Avoids pushing down limits before union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

LIMIT\_THRU\_JOIN

</td>
<td valign="top">

Prefers pushing down limits through joins.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_LIMIT\_THRU\_JOIN

</td>
<td valign="top">

Avoids pushing down limits through joins.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

PRELIMIT\_BEFORE\_JOIN

</td>
<td valign="top">

Prefers LIMIT/SORT on the left child of the LEFT OUTER JOIN.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_PRELIMIT\_BEFORE\_JOIN

</td>
<td valign="top">

Avoids LIMIT/SORT on the left child of the LEFT OUTER JOIN.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

PREAGGR\_BEFORE\_CASE\_AGGR

</td>
<td valign="top">

Prefers pre-aggregation before case expression aggregation.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_PREAGGR\_BEFORE\_CASE\_AGGR

</td>
<td valign="top">

Avoids pre-aggregation before case expression aggregation.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

DOUBLE\_JOIN\_THRU\_UNION\_ALL

</td>
<td valign="top">

Prefers a pushdown join through double union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_LOGICAL\_ENUMERATION

</td>
<td valign="top">

NO\_DOUBLE\_JOIN\_THRU\_UNION\_ALL

</td>
<td valign="top">

Avoids a pushdown join through double union all

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

INDEX\_SEARCH

</td>
<td valign="top">

Prefers the row engine index search.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_INDEX\_SEARCH

</td>
<td valign="top">

Avoids the row engine index search.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

INDEX\_JOIN

</td>
<td valign="top">

Prefers the row engine index join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_INDEX\_JOIN

</td>
<td valign="top">

Avoids the row engine index join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

HASH\_JOIN

</td>
<td valign="top">

Prefers the row engine hash join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_HASH\_JOIN

</td>
<td valign="top">

Avoids the row engine hash join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

RANGE\_JOIN

</td>
<td valign="top">

Prefers the row engine range join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_RANGE\_JOIN

</td>
<td valign="top">

Avoids the row engine range join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

HASHED\_RANGE\_JOIN

</td>
<td valign="top">

Prefers the row engine hashed range join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_HASHED\_RANGE\_JOIN

</td>
<td valign="top">

Avoids the row engine hashed range join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

JOIN\_FILTER\_REORDERING

</td>
<td valign="top">

Prefers join predicate reordering.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_JOIN\_FILTER\_REORDERING

</td>
<td valign="top">

Avoids join predicate reordering.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

CS\_SORT

</td>
<td valign="top">

Prefers the column engine order by.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_CS\_SORT

</td>
<td valign="top">

Avoids the column engine order by.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

CS\_LIMIT

</td>
<td valign="top">

Prefers the column engine limit.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_CS\_LIMIT

</td>
<td valign="top">

Avoids the column engine limit.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

CS\_FILTER

</td>
<td valign="top">

Prefers the column engine filter.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_CS\_FILTER

</td>
<td valign="top">

Avoids the column engine filter.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

CS\_DISTINCT

</td>
<td valign="top">

Prefers the column engine distinct.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_CS\_DISTINCT

</td>
<td valign="top">

Avoids the column engine distinct.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

CS\_AGGR

</td>
<td valign="top">

Prefers column engine aggregation.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_CS\_AGGR

</td>
<td valign="top">

Avoids column engine aggregation.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

CS\_JOIN

</td>
<td valign="top">

Prefers column engine join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_CS\_JOIN

</td>
<td valign="top">

Avoids the column engine join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

CS\_SCALAR\_SUBQUERY

</td>
<td valign="top">

Prefers the column engine scalar subquery.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_CS\_SCALAR\_SUBQUERY

</td>
<td valign="top">

Avoids the column engine scalar subquery.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

CS\_ITAB\_IN\_SUBQUERY

</td>
<td valign="top">

Prefers the column engine ITAB in the subquery.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_CS\_ITAB\_IN\_SUBQUERY

</td>
<td valign="top">

Avoids the column engine ITAB in the subquery.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

CS\_ITAB\_IN\_PREDICATE

</td>
<td valign="top">

Prefers the column engine ITAB for multi-columns in predicates.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_CS\_ITAB\_IN\_PREDICATE

</td>
<td valign="top">

Avoids the column engine ITAB for multi-columns in predicates.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

CS\_UNION\_ALL

</td>
<td valign="top">

Prefers the column engine union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

CS\_UNION\_ALL\(CALC\)

</td>
<td valign="top">

Prefers the calc engine union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_CS\_UNION\_ALL

</td>
<td valign="top">

Avoids the column engine union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

CS\_WINDOW

</td>
<td valign="top">

Prefers the column engine window for row numbers only.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_CS\_WINDOW

</td>
<td valign="top">

Avoids the column engine window for row numbers only.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

CYCLIC\_JOIN

</td>
<td valign="top">

Prefers cyclic joins in a single column search.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_CYCLIC\_JOIN

</td>
<td valign="top">

Avoids cyclic joins in a single column search.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

OLAP\_GUIDED\_NAVIGATION

</td>
<td valign="top">

Prefers OLAP engine guided navigation.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_OLAP\_GUIDED\_NAVIGATION

</td>
<td valign="top">

Avoids OLAP engine guided navigation.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

OLAP\_FEMS

</td>
<td valign="top">

Prefers the OLAP engine fems.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_OLAP\_FEMS

</td>
<td valign="top">

Avoids the OLAP engine fems.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

CS\_EXPR\_JOIN

</td>
<td valign="top">

Prefers the column engine expression join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_CS\_EXPR\_JOIN

</td>
<td valign="top">

Avoids the column engine expression join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

CS\_SEMI\_JOIN

</td>
<td valign="top">

Prefers the column engine semi-join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_CS\_SEMI\_JOIN

</td>
<td valign="top">

Avoids the column engine semi-join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

CS\_OUTER\_JOIN\_WITH\_FILTER

</td>
<td valign="top">

Prefers the outer join with the filter pushed down to the column engine.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_CS\_OUTER\_JOIN\_WITH\_FILTER

</td>
<td valign="top">

Avoids the outer join with the filter pushed down to the column engine.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

REMOTE\_COLUMN\_SCAN

</td>
<td valign="top">

Prefers the ITAB-producing remote scan operator.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_REMOTE\_COLUMN\_SCAN

</td>
<td valign="top">

Avoids the ITAB-producing remote scan operator.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

REMOTE\_JOIN\_RELOCATION

</td>
<td valign="top">

Prefers join relocation. Performs a JOIN between SAP HANA and the remote table at the remote database.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_REMOTE\_JOIN\_RELOCATION

</td>
<td valign="top">

Avoids join relocation. Performs a JOIN between SAP HANA and the remote table at the remote database.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

REMOTE\_EXPR\_MATERIALIZATION

</td>
<td valign="top">

Prefers expression materialization at the remote database.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_REMOTE\_EXPR\_MATERIALIZATION

</td>
<td valign="top">

Avoids expression materialization at the remote database.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

DISJUNCTIVE\_HASH\_JOIN

</td>
<td valign="top">

Prefers disjunctive hash join implementation.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_DISJUNCTIVE\_HASH\_JOIN

</td>
<td valign="top">

Avoids disjunctive hash join implementation.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

OLAP\_FACT\_TABLE

</td>
<td valign="top">

Prefers choosing a fact table whose name is the same as is given.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

ESX\_TOPK\_SORT

</td>
<td valign="top">

Prefers choosing a fact table whose name is the same as the one given.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_ESX\_TOPK\_SORT

</td>
<td valign="top">

Avoids choosing a fact table whose name is the same as the one given.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

ESX\_FILTER

</td>
<td valign="top">

Prefers using the ESX engine filter.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_ESX\_FILTER

</td>
<td valign="top">

Avoids using the ESX engine filter.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

ESX\_SORT

</td>
<td valign="top">

Prefers using the ESX engine sort.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_ESX\_SORT

</td>
<td valign="top">

Avoids using the ESX engine sort.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

ESX\_LIMIT

</td>
<td valign="top">

Prefers using the ESX engine limit.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_ESX\_LIMIT

</td>
<td valign="top">

Avoids using the ESX engine limit.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

ESX\_DISTINCT

</td>
<td valign="top">

Prefers using the ESX engine distinct.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_ESX\_DISTINCT

</td>
<td valign="top">

Avoids using the ESX engine distinct.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

ESX\_AGGR

</td>
<td valign="top">

Prefers using ESX engine aggregation.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_ESX\_AGGR

</td>
<td valign="top">

Avoids using ESX engine aggregation.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

ESX\_JOIN

</td>
<td valign="top">

Prefers using the ESX join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_ESX\_JOIN

</td>
<td valign="top">

Avoids using the ESX join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

ESX\_UNION\_ALL

</td>
<td valign="top">

Prefers using the ESX engine union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_ESX\_UNION\_ALL

</td>
<td valign="top">

Avoids using the ESX engine union all.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

ESX\_WINDOW

</td>
<td valign="top">

Prefers using the ESX engine window.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_ESX\_WINDOW

</td>
<td valign="top">

Avoids using the ESX engine window.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

ESX\_DISK\_HASH\_JOIN

</td>
<td valign="top">

Prefers ESX engine disk-based hash join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

NO\_ESX\_DISK\_HASH\_JOIN

</td>
<td valign="top">

Avoids ESX engine disk-based hash join.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER\_PHYSICAL\_ENUMERATION

</td>
<td valign="top">

ESX\_PARTITION\_HASH\_JOIN\_BUCKETS\(*<bucket\_size\>*\)

</td>
<td valign="top">

Sets the size of the bucket for an ESX disk-based hash join. The hint configures the number of buckets to split the data.

</td>
</tr>
</table>

**Related Information**  


[HINTS System View](../../020-System-Views-Reference/021-System-Views/hints-system-view-f55ce8e.md "Provides all available hints to be used in WITH HINT clauses.")

[SELECT Statement \(Data Manipulation\)](select-statement-data-manipulation-20fcf24.md "Queries data from the database.")

[STATEMENT\_HINTS System View](../../020-System-Views-Reference/021-System-Views/statement-hints-system-view-161a91a.md "Provides information about statement hints, including when they were last enabled and/or disabled and by whom.")

[Using Hints with Select Statements](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/556a518b49f84d8db770cbd068b94b65.html "In some cases hints can be appended to select statements to determine how the statement is run. This may be used, for example, to improve performance or to route a query to a specific data source.") :arrow_upper_right:

