<!-- loio20c57b8e75191014b22fcc8222b15970 -->

# M\_SQL\_PLAN\_CACHE System View

Provides statistics for an individual execution plan.



<a name="loio20c57b8e75191014b22fcc8222b15970___m__s_q_l__p_l_a_n__c_a_c_h_e_1struct_M_SQL_PLAN_CACHE"/>

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

VARCHAR\(64\)



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

VARCHAR\(32\)



</td>
<td valign="top">

Displays the MD5 hash value for the STATEMENT\_STRING column.



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

Displays the session user name who prepared the plan. This is the same value appears for USER\_NAME in the M\_CONNECTIONS.USER monitoring view.



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

Displays the schema name that the SQL plan belongs to. SQL plans are generated in each schema even though the statement string is the same, since the query optimizer statistics might be different.



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

Displays the composed variables from the session context.



</td>
</tr>
<tr>
<td valign="top">

IS\_VALID



</td>
<td valign="top">

VARCHAR\(5\)



</td>
<td valign="top">

Displays whether a plan is currently validated \(TRUE/FALSE\). A plan is invalidated when its corresponding schema objects, such as table and view, are changed. Invalidated plans are recompiled if the same statement is executed; otherwise, they are evicted by another plan when newly compiled.



</td>
</tr>
<tr>
<td valign="top">

LAST\_INVALIDATION\_REASON



</td>
<td valign="top">

VARCHAR\(64\)



</td>
<td valign="top">

Displays the reason for the last invalidation.



</td>
</tr>
<tr>
<td valign="top">

IS\_INTERNAL



</td>
<td valign="top">

VARCHAR\(5\)



</td>
<td valign="top">

Displays TRUE if the query plan was initiated from a database internal connection, not from the user nor other servers. For example, when an internal SAP HANA component executes a SQL statement related to the Statistics Service \(\_SYS\_STATISTICS\), or runs SQL statements in a background thread that exploit SQL Plan Cache, and so on.

Displays FALSE if the query plan was initiated by a client application.



</td>
</tr>
<tr>
<td valign="top">

IS\_DISTRIBUTED\_EXECUTION



</td>
<td valign="top">

VARCHAR\(5\)



</td>
<td valign="top">

Displays whether tables are located in multiple nodes or multiple services are involved in plan execution \(TRUE/FALSE\).



</td>
</tr>
<tr>
<td valign="top">

COMPILATION\_OPTIONS



</td>
<td valign="top">

VARCHAR\(128\)



</td>
<td valign="top">

Displays the compilation options that are used by the SQL Query Optimizer when it generates cached execution plans:

-   Returns an empty string if the SQL Query Optimizer compiled without any special settings
-   Returns a STATEMENT HINT option when the SQL Query Optimizer compiles and optimizes with a statement hint
-   Returns an ABSTRACT SQL PLAN option when the SQL Query Optimizer compiles with an abstract sql plan

Multiple options can used together to create a list of options, for example: STATEMENT HINT, ABSTRACT SQL PLAN.



</td>
</tr>
<tr>
<td valign="top">

IS\_PINNED\_PLAN



</td>
<td valign="top">

VARCHAR\(5\)



</td>
<td valign="top">

Displays whether the plan is explicitly stored by the PlanViz utility \(TRUE/FALSE\).



</td>
</tr>
<tr>
<td valign="top">

PINNED\_PLAN\_ID



</td>
<td valign="top">

VARCHAR\(5\)



</td>
<td valign="top">

This is deprecated.



</td>
</tr>
<tr>
<td valign="top">

ABAP\_VARCHAR\_MODE



</td>
<td valign="top">

VARCHAR\(5\)



</td>
<td valign="top">

Displays whether the ABAP VARCHAR mode is enabled \(TRUE/FALSE\). Only ABAP application developers are concerned with this mode, which indicates if it is a NULL terminated string or not.



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

VARCHAR\(5000\)



</td>
<td valign="top">

Displays the relevant base table ID list accessed in the plan. The format is \( \) for a list entry, with entries separated by commas.



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

Displays the relevant base table name list accessed in the plan. The format is \( \) for a list entry, with entries separated by commas.



</td>
</tr>
<tr>
<td valign="top">

ACCESSED\_OBJECTS



</td>
<td valign="top">

VARCHAR\(5000\)



</td>
<td valign="top">

Displays the relevant schema object ID list accessed in the plan. The format is \( \) for a list entry, with entries separated by commas.



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

Displays the relevant schema object name list accessed in the plan. The format is \( \) for a list entry, with entries separated by commas.



</td>
</tr>
<tr>
<td valign="top">

TABLE\_LOCATIONS



</td>
<td valign="top">

VARCHAR\(2000\)



</td>
<td valign="top">

Displays all relevant table locations for both original and replicated tables.

The table location contains the host, port, database ID, and volume ID, for example `lddbqm0:30240, 0, 3`.



</td>
</tr>
<tr>
<td valign="top">

TABLE\_TYPES



</td>
<td valign="top">

VARCHAR\(128\)



</td>
<td valign="top">

Displays whether the plan refers to the column store only, row store only, or mixed. Possible values are: ROW, COLUMN, or ROW, COLUMN.



</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_ENGINE



</td>
<td valign="top">

VARCHAR\(32\)



</td>
<td valign="top">

Displays the list of all involved execution frameworks.



</td>
</tr>
<tr>
<td valign="top">

PLAN\_SHARING\_TYPE



</td>
<td valign="top">

VARCHAR\(128\)



</td>
<td valign="top">

Displays the plan sharing type: GLOBAL, SESSION LOCAL, or LOGICAL SESSION GLOBAL.

See below for definitions.



</td>
</tr>
<tr>
<td valign="top">

OWNER\_CONNECTION\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the connection owning the plan.



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

Displays the logical plan ID, which is a non-negative value.



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

REFERENCE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of statements using the plan. When the number reaches zero, it can be evicted by the victim selection policy of the plan cache.



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

Displays the number of parameters assigned to the execution.



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

Displays the object ID of the updated table for the plan.



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

Displays the volume ID of the logical connection. This value is 0 if there is no session context defining it as a global plan.



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

Displays the accumulated count of the plan execution.



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

Displays the accumulated count of the plan execution by a client-routed connection in the statement routing. This column shows how many times the statement is executed in the routed connection. The routed connection is a physical connection in a part of the logical session.



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

Displays the sum of time of the plan execution in microseconds, including the communication time with clients.



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

Displays the average time of the plan execution in microseconds, including the communication time with clients.



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

Displays the minimum time of the plan execution in microseconds, including the communication time with clients.



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

Displays the maximum time of the plan execution in microseconds, including the communication time with clients.



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

Displays the sum of time of the plan executions in microseconds.



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

Displays the average time of the plan execution in microseconds.



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

Displays the minimum time of the plan execution in microseconds.



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

Displays the maximum time of the plan execution in microseconds.



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

Displays the sum of time in microseconds establishing result sets.



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

Displays the average time that the cursor is open in microseconds.



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

Displays the minimum time for cursor open in microseconds.



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

Displays the maximum time for cursor open in microseconds.



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

Displays the sum of time for transferring rows in microseconds.



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

Displays the average time for cursor fetch in microseconds.



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

Displays the minimum time for cursor fetch in microseconds.



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

Displays the maximum time for cursor fetch in microseconds.



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

Displays the sum of time for result set cleanup in microseconds.



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

Displays the average time for cursor close in microseconds.



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

Displays the minimum time for cursor close in microseconds.



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

Displays the maximum time for cursor close in microseconds.



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

Displays the sum of the table loading time during plan preparation in microseconds.



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

Displays the average table loading time during plan preparation in microseconds.



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

Displays the minimum table loading time during plan preparation in microseconds.



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

Displays the maximum table loading time during plan preparation in microseconds.



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

Displays the number of plan preparations.



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

Displays the sum of time of the plan preparation in microseconds.



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

Displays the average time of the plan preparation in microseconds.



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

Displays the minimum time of the plan preparation in microseconds.



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

Displays the maximum time of the plan preparation in microseconds.



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

Displays the accumulated number of records during plan execution.



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

Displays the accumulated lock wait count for the plan.



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

Displays the accumulated lock wait duration for the plan in microseconds.



</td>
</tr>
<tr>
<td valign="top">

LAST\_CONNECTION\_ID



</td>
<td valign="top">

INTEGER



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

Displays the last execution timestamp.



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

Displays the last preparation timestamp.



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

Displays the sum of memory peaks of all plan executions, in bytes.

In cases where a query was executed in a scale-out system \(that is, the query was running distributed across multiple hosts\), then TOTAL\_EXECUTION\_MEMORY\_SIZE is the highest peak memory usage across all involved hosts\). So, if host A had a peak usage of 2 GB and host B has a peak usage of 3 GB, then MEMORY\_SIZE displays 3 GB.



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

Displays the average memory peak of all plan executions, in bytes.



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

Displays the minimum memory peak of all plan executions, in bytes.



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

Displays the maximum memory peak of all plan executions, in bytes.



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

AVG\_SERVICE\_NETWORK\_REQUEST\_COUNT



</td>
<td valign="top">

REAL



</td>
<td valign="top">

Displays the average count of service network requests during plan execution.



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

Displays the maximum count of service network requests during plan execution.



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

Displays the total count of service network requests during plan execution.



</td>
</tr>
<tr>
<td valign="top">

AVG\_CALLED\_THREAD\_COUNT



</td>
<td valign="top">

REAL



</td>
<td valign="top">

Displays the average count of called threads used during plan execution.



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

Displays the maximum count of called threads used during plan execution.



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

Displays the total count of called threads used during plan execution.



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

Displays a total batch count per one execution for cached DML plans.



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

Displays an average batch count per one execution for cached DML plans.



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

Displays a minimum batch count per one execution for cached DML plans.



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

Displays a maximum batch count per one execution for cached DML plans.



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

Displays the average time in microseconds of service network requests during plan execution.



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

Displays the maximum time in microseconds of service network requests during plan execution.



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

Displays the total time in microseconds of service network requests during plan execution.



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

Displays the average data amount in bytes of service network requests during plan execution.



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

Displays the maximum amount in bytes of service network requests during plan execution.



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

Displays the total amount in bytes of service network requests during plan execution.



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

Displays the total number of times the NSE page was found in buffer cache memory.



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

Displays the average number of times page the NSE page was found in buffer cache memory.



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

Displays the minimum number of times the NSE page was found in buffer cache memory.



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

Displays the maximum number of times the NSE page was found in buffer cache memory.



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

Displays the total number of times the NSE page had to be read from disk.



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

Displays the average number of times the NSE page had to be read from disk.



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

Displays the minimum number of times the NSE page had to be read from disk.



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

Displays the maximum number of times the NSE page had to be read from disk.



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

Displays the total size of pinned the NSE page memory out of buffer cache.



</td>
</tr>
<tr>
<td valign="top">

AVG\_BUFFER\_CACHE\_PINNED\_MEMORY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average size of pinned the NSE page memory out of buffer cache.



</td>
</tr>
<tr>
<td valign="top">

MIN\_BUFFER\_CACHE\_PINNED\_MEMORY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the minimum size of pinned the NSE page memory out of buffer cache.



</td>
</tr>
<tr>
<td valign="top">

MAX\_BUFFER\_CACHE\_PINNED\_MEMORY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the maximum size of pinned the NSE page memory out of buffer cache.



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



<a name="loio20c57b8e75191014b22fcc8222b15970___m__s_q_l__p_l_a_n__c_a_c_h_e_1fulldesc_M_SQL_PLAN_CACHE"/>

## Additional Information

-   GLOBAL: A plan always can be shared with any other connections concurrently. There are no restrictions for this plan sharing type.

-   SESSION LOCAL: A plan is never shared. This sharing type is more restricted than LOGICAL SESSION GLOBAL. If a connection generates a plan, the plan belongs to the connection.

-   LOGICAL SESSION GLOBAL: This plan sharing type is for a plan with global temporary tables. This plan can be shared between sessions with same GTT location.


The M\_SQL\_PLAN\_CACHE view shows statistics for an individual plan but not all plans. It shows whether a specified plan runs longer than expected or which part of execution is dominant. For each cached plan, this view delivers statistics from execution on distributed configuration as well as technical details such as related object IDs, updated objects and so on.

This view has a resettable counterpart; you can see the values since the last reset in the M\_SQL\_PLAN\_CACHE\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_SQL_PLAN_CACHE_RESET;`.

**Related Information**  


[M\_SQL\_PLAN\_CACHE\_RESET System View](m-sql-plan-cache-reset-system-view-20c5b36.md "Provides statistics of an individual execution plan since the last reset.")

[M\_CONNECTIONS System View](m-connections-system-view-20abcf1.md "Provides detailed information on connections between a client and a database. Information includes: connection status, client information, connection type, and resource utilization.")

[ALTER SYSTEM RESET MONITORING VIEW Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-reset-monitoring-view-statement-system-management-20d27aa.md "Resets statistics data for the specified monitoring view.")

[ALTER SYSTEM REMOVE SQL PLAN CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-remove-sql-plan-cache-statement-system-management-dafece7.md "Removes the specified entries from the SQL plan cache.")

[ALTER SYSTEM CLEAR SQL PLAN CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-sql-plan-cache-statement-system-management-20d107c.md "Removes all of the SQL plans that are not currently being executed from the SAP HANA database plan cache.")

[ALTER SYSTEM RECOMPILE SQL PLAN CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-recompile-sql-plan-cache-entry-statement-system-management-d226426.md "Invalidates the designated plan cache entry so that it is recompiled during the next execution time.")

[ALTER SYSTEM \{PIN | UNPIN\} SQL PLAN CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-pin-unpin-sql-plan-cache-entry-statement-system-management-68e2f7a.md "Provides a runtime mechanism to bind the target query and hints to the Hint Table to force the compilation of the target query with the hint.")

