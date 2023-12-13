<!-- loio84d12a5a4b9449cf8bc3c5ccb16c30c6 -->

# M\_SQL\_PLAN\_STATISTICS System View

Provides statistics of a live or evicted individual execution plan.



## Structure


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the host name.

</td>
</tr>
<tr>
<td valign="top">

PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the internal port number.

</td>
</tr>
<tr>
<td valign="top">

VOLUME\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the persistence volume ID.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_STRING

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the statement string.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_HASH

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the MD5 hash value for STATEMENT\_STRING.

</td>
</tr>
<tr>
<td valign="top">

USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the user name who prepared the plan.

</td>
</tr>
<tr>
<td valign="top">

SESSION\_USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the SESSION\_USER name who prepared the plan. The same value as M\_CONNECTIONS.USER\_NAME.

</td>
</tr>
<tr>
<td valign="top">

SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name that the SQL plan belongs to.

</td>
</tr>
<tr>
<td valign="top">

SESSION\_PROPERTIES

</td>
<td valign="top">

NVARCHAR\(500\)

</td>
<td valign="top">

Displays the composed variables that can be changed by session context.

</td>
</tr>
<tr>
<td valign="top">

IS\_VALID

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the plan is currently valid: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_EVICTED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the plan has already been evicted: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

LAST\_INVALIDATION\_REASON

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the last plan invalidation reason.

</td>
</tr>
<tr>
<td valign="top">

IS\_INTERNAL

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the plan is executed from a database internal connection \(TRUE\) or from a remote connection \(FALSE\).

</td>
</tr>
<tr>
<td valign="top">

IS\_DISTRIBUTED\_EXECUTION

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the tables are located in multiple nodes: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

COMPILATION\_OPTIONS

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the compilation options that are used by the SQL Query Optimizer when it generates cached execution plans:

-   Returns an empty string if the SQL Query Optimizer compiled without any special settings
-   Returns a STATEMENT HINT option when the SQL Query Optimizer compiles and optimizes with a statement hint
-   Returns an ABSTRACT SQL PLAN option when the SQL Query Optimizer compiles with an abstract sql plan

Multiple options can be used together to create a list of options, for example: STATEMENT HINT, ABSTRACT SQL PLAN.

</td>
</tr>
<tr>
<td valign="top">

IS\_PINNED\_PLAN

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the plan is explicitly stored by PlanViz utility: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

PINNED\_PLAN\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

If this plan is pinned, dispalys the same value as PINNED\_SQL\_PLANS.ID.

</td>
</tr>
<tr>
<td valign="top">

ABAP\_VARCHAR\_MODE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether ABAP NVARCHAR mode is enabled: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the application name information.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_SOURCE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the application source information.

</td>
</tr>
<tr>
<td valign="top">

ACCESSED\_TABLES

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the relevant base table ID list accessed in the plan.

</td>
</tr>
<tr>
<td valign="top">

ACCESSED\_TABLE\_NAMES

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the relevant base table name list accessed in the plan.

</td>
</tr>
<tr>
<td valign="top">

ACCESSED\_OBJECTS

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the relevant table object ID list accessed in the plan.

</td>
</tr>
<tr>
<td valign="top">

ACCESSED\_OBJECT\_NAMES

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the relevant schema object name list accessed in the plan.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_LOCATIONS

</td>
<td valign="top">

NVARCHAR\(2000\)

</td>
<td valign="top">

Displays the relevant table locations for the plan.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_TYPES

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays whether the plan refers Column store only, Row store only or mixed.

</td>
</tr>
<tr>
<td valign="top">

PLAN\_SHARING\_TYPE

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the plan sharing type.

</td>
</tr>
<tr>
<td valign="top">

OWNER\_CONNECTION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the connection owning the plan. The possible values are:

-   GLOBAL: -1 \(always\)

-   SESSION EXCLUSIVE GLOBAL: -1, owner connection ID, which is a positive value

-   SESSION LOCAL: owner connection ID, which is a positive value \(never changed\)




</td>
</tr>
<tr>
<td valign="top">

PLAN\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the logical plan ID, which is a non-negative value. If the plan is evicted, -1 is shown.

</td>
</tr>
<tr>
<td valign="top">

PLAN\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the memory size used by the plan in bytes.

</td>
</tr>
<tr>
<td valign="top">

EVICTION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of evictions that have occurred for the plan.

</td>
</tr>
<tr>
<td valign="top">

LAST\_EVICTION\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the timestamp when the plan was evicted for the last time. Returns zero if the plan has never been evicted.

</td>
</tr>
<tr>
<td valign="top">

REFERENCE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of statements using the plan.

</td>
</tr>
<tr>
<td valign="top">

PARAMETER\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of parameters to be assigned for the execution.

</td>
</tr>
<tr>
<td valign="top">

UPDATED\_TABLE\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID of the table changed by the plan.

</td>
</tr>
<tr>
<td valign="top">

LOGICAL\_CONNECTION\_VOLUME\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the volume ID of the logical connection. This value is 0 if there is no session context.

</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated count of plan execution for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_COUNT\_BY\_ROUTING

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated count of plan execution by client-routed connection in statement routing for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_CURSOR\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the sum of time, in microseconds, that cursors were opened. This includes plan execution and communication time with clients for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

AVG\_CURSOR\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time, in microseconds, of the plan execution, including communication time with clients for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

MIN\_CURSOR\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum time, in microseconds, of the plan execution, including communication time with clients for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

MAX\_CURSOR\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum time, in microseconds, of the plan execution, including communication time with clients for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the sum of time, in microseconds, of the plan execution for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

AVG\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time of the plan execution.

</td>
</tr>
<tr>
<td valign="top">

MIN\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum time of the plan execution.

</td>
</tr>
<tr>
<td valign="top">

MAX\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum time of the plan execution.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_EXECUTION\_OPEN\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the sum of time in microseconds for cursor open for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

AVG\_EXECUTION\_OPEN\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time in microseconds for cursor open for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

MIN\_EXECUTION\_OPEN\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum time in microseconds for cursor open for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

MAX\_EXECUTION\_OPEN\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum time in microseconds for cursor open for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_EXECUTION\_FETCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the sum of time in microseconds for cursor fetch for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

AVG\_EXECUTION\_FETCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time in microseconds for cursor fetch for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

MIN\_EXECUTION\_FETCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum time in microseconds for cursor fetch for valid and evicted plans

</td>
</tr>
<tr>
<td valign="top">

MAX\_EXECUTION\_FETCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum time in microseconds for cursor fetch for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_EXECUTION\_CLOSE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the sum of time in microseconds for cursor close for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

AVG\_EXECUTION\_CLOSE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time in microseconds for cursor close for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

MIN\_EXECUTION\_CLOSE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum time in microseconds for cursor close for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

MAX\_EXECUTION\_CLOSE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum time in microseconds for cursor close for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_METADATA\_CACHE\_MISS\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Deprecated.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_TABLE\_LOAD\_TIME\_DURING\_PREPARATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the sum of table loading time during plan preparation for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

AVG\_TABLE\_LOAD\_TIME\_DURING\_PREPARATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average table loading time in microseconds during plan preparation for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

MIN\_TABLE\_LOAD\_TIME\_DURING\_PREPARATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum table loading time during plan preparation for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

MAX\_TABLE\_LOAD\_TIME\_DURING\_PREPARATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum table loading time in microseconds during plan preparation for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

PREPARATION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the count of plan preparations for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_PREPARATION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the sum of time in microseconds of plan preparation for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

AVG\_PREPARATION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time in microseconds of plan preparation for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

MIN\_PREPARATION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum time in microseconds of plan preparation for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

MAX\_PREPARATION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum time in microseconds of plan preparation for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_RESULT\_RECORD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated number of records during plan execution for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_LOCK\_WAIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated lock wait count for the plan for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_LOCK\_WAIT\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated lock wait duration in microseconds for the plan for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

LAST\_CONNECTION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last connection ID that executed the plan.

</td>
</tr>
<tr>
<td valign="top">

LAST\_EXECUTION\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the timestamp when the plan was executed for the last time.

</td>
</tr>
<tr>
<td valign="top">

LAST\_PREPARATION\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the timestamp when the plan was compiled for the last time.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_EXECUTION\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

With memory tracking, displays the average size in bytes of tracked actual memory consumption for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

AVG\_EXECUTION\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

With memory tracking, displays the maximum size in bytes of tracked actual memory consumption for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

MIN\_EXECUTION\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

With memory tracking, displays the minimum size in bytes of tracked actual memory consumption for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

MAX\_EXECUTION\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

With memory tracking, displays the total size in bytes of tracked actual memory consumption for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_SERVICE\_NETWORK\_REQUEST\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total count of service network requests during plan execution for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

AVG\_SERVICE\_NETWORK\_REQUEST\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average count of service network requests during plan execution for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

MAX\_SERVICE\_NETWORK\_REQUEST\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum count of service network requests during plan execution for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_CALLED\_THREAD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total count of called threads used during plan execution for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

AVG\_CALLED\_THREAD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average count of called threads used during plan execution for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

MAX\_CALLED\_THREAD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average count of called threads used during plan execution for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_BATCH\_EXECUTION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays a total batch count per one execution for cached DML plans for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

AVG\_BATCH\_EXECUTION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays an average batch count per one execution for cached DML plans for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

MIN\_BATCH\_EXECUTION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays a minimum batch count per one execution for cached DML plans for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

MAX\_BATCH\_EXECUTION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays a maximum batch count per one execution for cached DML plans for valid and evicted plans.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_SERVICE\_NETWORK\_REQUEST\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total time of the service network requests during plan execution.

</td>
</tr>
<tr>
<td valign="top">

AVG\_SERVICE\_NETWORK\_REQUEST\_DURATION

</td>
<td valign="top">

REAL

</td>
<td valign="top">

Displays the average time of the service network requests during plan execution.

</td>
</tr>
<tr>
<td valign="top">

MAX\_SERVICE\_NETWORK\_REQUEST\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum time of the service network requests during plan execution.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_SERVICE\_NETWORK\_REQUEST\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total amount of service network requests during plan execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

AVG\_SERVICE\_NETWORK\_REQUEST\_SIZE

</td>
<td valign="top">

REAL

</td>
<td valign="top">

Displays the average data amount of service network requests during plan execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAX\_SERVICE\_NETWORK\_REQUEST\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum amount of service network requests during plan execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_EXECUTION\_CPU\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total amount of tracked CPU time.

</td>
</tr>
<tr>
<td valign="top">

AVG\_EXECUTION\_CPU\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average amount of tracked CPU time.

</td>
</tr>
<tr>
<td valign="top">

MIN\_EXECUTION\_CPU\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum amount of tracked CPU time.

</td>
</tr>
<tr>
<td valign="top">

MAX\_EXECUTION\_CPU\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum amount of tracked CPU time.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_BUFFER\_CACHE\_PAGE\_HIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of times an NSE page was found in buffer cache memory.

</td>
</tr>
<tr>
<td valign="top">

AVG\_BUFFER\_CACHE\_PAGE\_HIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average number of times an NSE page was found in buffer cache memory.

</td>
</tr>
<tr>
<td valign="top">

MIN\_BUFFER\_CACHE\_PAGE\_HIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum number of times an NSE page was found in buffer cache memory.

</td>
</tr>
<tr>
<td valign="top">

MAX\_BUFFER\_CACHE\_PAGE\_HIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum number of times an NSE page was found in buffer cache memory.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_BUFFER\_CACHE\_PAGE\_MISS\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of times an NSE page was read from disk into the buffer cache.

</td>
</tr>
<tr>
<td valign="top">

AVG\_BUFFER\_CACHE\_PAGE\_MISS\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average number of times an NSE page was read from disk into the buffer cache.

</td>
</tr>
<tr>
<td valign="top">

MIN\_BUFFER\_CACHE\_PAGE\_MISS\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum number of times an NSE page was read from disk into the buffer cache.

</td>
</tr>
<tr>
<td valign="top">

MAX\_BUFFER\_CACHE\_PAGE\_MISS\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum number of times an NSE page was read from disk into the buffer cache.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_BUFFER\_CACHE\_PINNED\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size of pinned NSE page memory in the buffer cache in bytes.

</td>
</tr>
<tr>
<td valign="top">

AVG\_ BUFFER\_CACHE\_PINNED\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average size of pinned NSE page memory in the buffer cache in bytes.

</td>
</tr>
<tr>
<td valign="top">

MIN\_ BUFFER\_CACHE\_PINNED\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum size of pinned NSE page memory in the buffer cache in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAX\_ BUFFER\_CACHE\_PINNED\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum size of pinned NSE page memory in the buffer cache in bytes.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_BUFFER\_CACHE\_IO\_READ\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size of NSE pages read from disk into the buffer cache.

</td>
</tr>
<tr>
<td valign="top">

AVG\_BUFFER\_CACHE\_IO\_READ\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average size of NSE pages read from disk into the buffer cache.

</td>
</tr>
<tr>
<td valign="top">

MIN\_BUFFER\_CACHE\_IO\_READ\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum size of NSE pages read from disk into the buffer cache.

</td>
</tr>
<tr>
<td valign="top">

MAX\_BUFFER\_CACHE\_IO\_READ\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum size of NSE pages read from disk into the buffer cache.

</td>
</tr>
</table>



## Additional Information

The M\_SQL\_PLAN\_STATISTICS view shows statistics for an individual plan, whether it is live or evicted. A plan is evicted from the plan cache, and is not stored in the M\_SQL\_PLAN\_CACHE System View, if it is the least recently used cache entry. It shows whether a specified plan runs longer than expected or which part of execution is dominant. For each cached plan, this view delivers statistics from execution on distributed configuration, as well as technical details such as related object IDs, updated objects, and so on.

Information about live and evicted plans is useful in the following scenarios:

-   If a previously evicted plan entry is recreated in the plan cache with a high execution statistics number, then you might assume that the plan should not have been evicted and should increase your plan cache size.

-   If you want to have an overview of plan statistics, even though some plans have already been evicted.

-   If you want to determine which kinds of queries are repeatedly evicted.

-   If you want to determine the cause of performance regression, then you can check the statistics of evicted plans for information on how frequently the plan was executed, for how long, and so on.


**Related Information**  


[M\_SQL\_PLAN\_STATISTICS\_RESET System View](m-sql-plan-statistics-reset-system-view-228302e.md "Provides statistics of a live or evicted individual execution plan since the last reset.")

[M\_SQL\_PLAN\_CACHE System View](m-sql-plan-cache-system-view-20c57b8.md "Provides statistics for an individual execution plan.")

[M\_CONNECTIONS System View](m-connections-system-view-20abcf1.md "Provides detailed information on connections between a client and a database. Information includes: connection status, client information, connection type, and resource utilization.")

[CREATE STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-statistics-statement-data-definition-20d5252.md "Creates data statistic objects that allow the query optimizer to make better decisions for query plans.")

[REFRESH STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/refresh-statistics-statement-data-definition-20fae6d.md "Specifies a column that is part of the data sources.")

[ALTER STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-statistics-statement-data-definition-c656476.md "Alters the properties of a data statistics object.")

[DROP STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-statistics-statement-data-definition-20d7c59.md "Drops user-defined data statistic objects that the query optimizer uses to make decisions for query plans.")

