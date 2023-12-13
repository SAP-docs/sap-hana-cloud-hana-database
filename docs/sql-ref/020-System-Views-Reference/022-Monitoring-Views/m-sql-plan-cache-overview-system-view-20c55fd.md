<!-- loio20c55fd5751910148c79cdff7c2273e3 -->

# M\_SQL\_PLAN\_CACHE\_OVERVIEW System View

Provides overall statistics of evicted and cached plans.



<a name="loio20c55fd5751910148c79cdff7c2273e3___m__s_q_l__p_l_a_n__c_a_c_h_e__o_v_e_r_v_i_e_w_1struct_M_SQL_PLAN_CACHE_OVERVIEW"/>

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

PLAN\_CACHE\_ENABLED

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays whether the SQL Plan Cash is enabled \(TRUE/FALSE\).

ALTER SYSTEM ALTER CONFIGURATION \('indexserver.ini','system'\) SET\('sql', 'plan\_cache\_enabled'\) = <'True' or 'False'\> WITH RECONFIGURE.

</td>
</tr>
<tr>
<td valign="top">

STATISTICS\_COLLECTION\_ENABLED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the runtime statistics are being collected \(TRUE/FALSE\).

ALTER SYSTEM ALTER CONFIGURATION \('indexserver.ini','system'\) SET\('sql', 'plan\_cache\_statistics\_enabled'\) = <'True' or 'False'\> WITH RECONFIGURE.

</td>
</tr>
<tr>
<td valign="top">

PLAN\_CACHE\_CAPACITY

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum SQL Plan Cache size in bytes.

ALTER SYSTEM ALTER CONFIGURATION \('indexserver.ini','system'\) SET\('sql', 'plan\_cache\_size'\) = '268435456' WITH RECONFIGURE.

</td>
</tr>
<tr>
<td valign="top">

CACHED\_PLAN\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size of SQL Plan Cache in bytes.

</td>
</tr>
<tr>
<td valign="top">

PLAN\_CACHE\_HIT\_RATIO

</td>
<td valign="top">

REAL

</td>
<td valign="top">

Displays the SQL Plan Cache hit ratio.

</td>
</tr>
<tr>
<td valign="top">

PLAN\_CACHE\_LOOKUP\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of plan lookup counts from SQL Plan Cache.

</td>
</tr>
<tr>
<td valign="top">

PLAN\_CACHE\_HIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of hit counts from SQL Plan Cache.

</td>
</tr>
<tr>
<td valign="top">

EVICTED\_PLAN\_AVG\_CACHE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average duration in microseconds between plan cache insertion and eviction.

</td>
</tr>
<tr>
<td valign="top">

EVICTED\_PLAN\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of evicted plans from SQL Plan Cache.

</td>
</tr>
<tr>
<td valign="top">

EVICTED\_PLAN\_PREPARATION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total plan preparation count for evicted plans.

</td>
</tr>
<tr>
<td valign="top">

EVICTED\_PLAN\_EXECUTION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total plan execution count for evicted plans.

</td>
</tr>
<tr>
<td valign="top">

EVICTED\_PLAN\_PREPARATION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total duration in microseconds for plan preparation for all evicted plans. It is the sum of the evicted plan's TOTAL\_PREPARATION\_TIME.

</td>
</tr>
<tr>
<td valign="top">

EVICTED\_PLAN\_CURSOR\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total cursor duration in microseconds for evicted plans. It is the sum of the evicted plan's TOTAL\_CURSOR\_DURATION.

</td>
</tr>
<tr>
<td valign="top">

EVICTED\_PLAN\_TOTAL\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total execution time in microseconds for evicted plans. It is the sum of th evicted plan's TOTAL\_EXECUTION\_TIME.

</td>
</tr>
<tr>
<td valign="top">

EVICTED\_PLAN\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated total size of evicted plans in bytes.

</td>
</tr>
<tr>
<td valign="top">

CACHED\_PLAN\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total cached plan count in SQL Plan Cache.

</td>
</tr>
<tr>
<td valign="top">

CACHED\_PLAN\_PREPARATION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the yotal plan preparation count for cached plans.

</td>
</tr>
<tr>
<td valign="top">

CACHED\_PLAN\_EXECUTION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total execution count for cached plans.

</td>
</tr>
<tr>
<td valign="top">

CACHED\_PLAN\_PREPARATION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total plan preparation duration for cached plans in microseconds.

</td>
</tr>
<tr>
<td valign="top">

CACHED\_PLAN\_CURSOR\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total cursor duration for cached plans in microseconds.

</td>
</tr>
<tr>
<td valign="top">

CACHED\_PLAN\_TOTAL\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total execution time for cached plans in microseconds.

</td>
</tr>
<tr>
<td valign="top">

CLEAR\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the timestamp when SQL Plan Cache was cleared for the last time using ALTER SYSTEM CLEAR SQL PLAN CACHE.

</td>
</tr>
</table>



<a name="loio20c55fd5751910148c79cdff7c2273e3___m__s_q_l__p_l_a_n__c_a_c_h_e__o_v_e_r_v_i_e_w_1fulldesc_M_SQL_PLAN_CACHE_OVERVIEW"/>

## Additional Information

M\_SQL\_PLAN\_CACHE\_OVERVIEW shows the overall statistics of evicted and cached plans. It shows information such as how many times plan eviction occurred and how long it takes to execute currently cached plans. You can check the eviction rate with the EVICTED\_PLAN\_COUNT column. If EVICTED\_PLAN\_COUNT is too high, it means SQL plan cache capacity is not enough and too many compilations occurs.

In addition to statistics, the current status and flags of the SQL plan cache are shown in this view.

**Related Information**  


[M\_SQL\_PLAN\_CACHE System View](m-sql-plan-cache-system-view-20c57b8.md "Provides statistics for an individual execution plan.")

[M\_SQL\_PLAN\_CACHE\_EXECUTION\_LOCATION\_STATISTICS System View](m-sql-plan-cache-execution-location-statistics-system-view-ef212ac.md "Provides statistics for hosts where plans were executed.")

[M\_SQL\_PLAN\_CACHE\_PARAMETERS System View](m-sql-plan-cache-parameters-system-view-f411689.md "Provides bind parameters for statements cached in SQL Plan Cache. It saves a parameter set of the most expensive execution for each plan.")

[ALTER SYSTEM REMOVE SQL PLAN CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-remove-sql-plan-cache-statement-system-management-dafece7.md "Removes the specified entries from the SQL plan cache.")

[ALTER SYSTEM CLEAR SQL PLAN CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-sql-plan-cache-statement-system-management-20d107c.md "Removes all of the SQL plans that are not currently being executed from the SAP HANA database plan cache.")

[ALTER SYSTEM RECOMPILE SQL PLAN CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-recompile-sql-plan-cache-entry-statement-system-management-d226426.md "Invalidates the designated plan cache entry so that it is recompiled during the next execution time.")

[ALTER SYSTEM RESET MONITORING VIEW Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-reset-monitoring-view-statement-system-management-20d27aa.md "Resets statistics data for the specified monitoring view.")

[ALTER SYSTEM \{PIN | UNPIN\} SQL PLAN CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-pin-unpin-sql-plan-cache-entry-statement-system-management-68e2f7a.md "Provides a runtime mechanism to bind the target query and hints to the Hint Table to force the compilation of the target query with the hint.")

[M\_SQL\_PLAN\_CACHE\_RESET System View](m-sql-plan-cache-reset-system-view-20c5b36.md "Provides statistics of an individual execution plan since the last reset.")

[M\_CONNECTIONS System View](m-connections-system-view-20abcf1.md "Provides detailed information on connections between a client and a database. Information includes: connection status, client information, connection type, and resource utilization.")

