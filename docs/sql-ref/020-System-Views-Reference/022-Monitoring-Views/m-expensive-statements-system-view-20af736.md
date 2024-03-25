<!-- loio20af736e751910148162e2ab1982f035 -->

# M\_EXPENSIVE\_STATEMENTS System View

Provides all statements with a duration longer than a specified threshold.



<a name="loio20af736e751910148162e2ab1982f035___m__e_x_p_e_n_s_i_v_e__s_t_a_t_e_m_e_n_t_s_1struct_M_EXPENSIVE_STATEMENTS"/>

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

CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the connection ID.

</td>
</tr>
<tr>
<td valign="top">

TRANSACTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the transaction object ID.

</td>
</tr>
<tr>
<td valign="top">

UPDATE\_TRANSACTION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the write transaction ID.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_ID

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the statement ID.

</td>
</tr>
<tr>
<td valign="top">

PARENT\_STATEMENT\_ID

</td>
<td valign="top">

NVARCHAR\(20\)

</td>
<td valign="top">

Displays the parent statement ID.

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

Displays the unique identifier for an SQL string.

</td>
</tr>
<tr>
<td valign="top">

DB\_USER

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the user name.

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

Displays the name of the schema in whose context the statement is executed.

</td>
</tr>
<tr>
<td valign="top">

APP\_USER

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the application user name.

</td>
</tr>
<tr>
<td valign="top">

START\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the statement start time.

</td>
</tr>
<tr>
<td valign="top">

DURATION\_MICROSEC

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the statement duration in microseconds.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the related objects.

</td>
</tr>
<tr>
<td valign="top">

OPERATION

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the type of operation \(prepare, execute, fetch, or close\).

</td>
</tr>
<tr>
<td valign="top">

RECORDS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of records.

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

PARAMETERS

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the statement parameters.

</td>
</tr>
<tr>
<td valign="top">

ERROR\_CODE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the error code.

</td>
</tr>
<tr>
<td valign="top">

ERROR\_TEXT

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the error message.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_WAIT\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the accumulated lock wait count.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_WAIT\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated lock wait duration in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the peak memory usage in bytes during the execution of the statement.

This value is kept for cache reasons or released after the statement execution.

</td>
</tr>
<tr>
<td valign="top">

REUSED\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the memory that is reused from cached data structures in bytes. The value is 0 if the cache is empty.

</td>
</tr>
<tr>
<td valign="top">

CPU\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the CPU time, in microseconds, consumed to compute the statement.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_ROOT\_CONTEXT\_ID

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) GUID that identifies the source of the request.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_TRANSACTION\_ID

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) GUID that identifies the business transaction.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_CONNECTION\_ID

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) GUID that identifies the connection.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_CONNECTION\_COUNTER

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the extended passport \(EPP\) connection counter.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_COMPONENT\_TYPE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the extended passport \(EPP\) component type.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_ACTION

</td>
<td valign="top">

NVARCHAR\(40\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) component action.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_ACTION\_TYPE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the extended passport \(EPP\) component action type.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_PREVIOUS\_COMPONENT\_NAME

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) passport component name of the previous context.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_SERVICE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the extended passport \(EPP\) service.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_USER\_ID

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) user ID.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_CLIENT

</td>
<td valign="top">

NVARCHAR\(3\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) client.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_TRACE\_FLAGS

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the extended passport \(EPP\) trace flags.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_START\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time when the first operation of a statement execution starts. All operations of a statement execution \(prepare, execute, fetch, or close\) share the same statement start time.

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

Displays the application from which source file SAP HANA is called. Usage is determined by the application. The value is also displayed in M\_PREPARED\_STATEMENTS.APPLICATION\_SOURCE.

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

Displays the name of the application.

</td>
</tr>
<tr>
<td valign="top">

NETWORK\_MESSAGE\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the client message ID on the physical server connection, also found in M\_SQL\_CLIENT\_NETWORK\_IO and MESSAGE\_ID.

</td>
</tr>
<tr>
<td valign="top">

WORKLOAD\_CLASS\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the effective workload class.

</td>
</tr>
<tr>
<td valign="top">

PRIORITY

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the effective statement priority.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_THREAD\_LIMIT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the effective statement thread limit.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_MEMORY\_LIMIT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the effective statement memory limit.

</td>
</tr>
<tr>
<td valign="top">

SESSION\_VARIABLES

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the statement's session variables.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_TYPES

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the type of tables referenced by the expensive statement, represented by a combination of values: ROW, COLUMN, VIRTUAL.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_STATEMENT\_MEMORY\_LIMIT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the effective total statement memory limit.

</td>
</tr>
</table>



<a name="loio20af736e751910148162e2ab1982f035___m__e_x_p_e_n_s_i_v_e__s_t_a_t_e_m_e_n_t_s_1fulldesc_M_EXPENSIVE_STATEMENTS"/>

## Additional Information

Allows you to monitor all statements that have an execution time longer than a predefined threshold \(configurable in the \[expensive\_statement\] section of the `global.ini` file\), which may sometimes cause barriers.

The M\_EXPENSIVE\_STATEMENTS view provides convenient access to the most expensive statements that are executed on the system. A statement is considered expensive if its runtime exceeds a particular threshold.

The following types of operations are tracked:

-   COMPILE: compiles the statement.

-   FETCH: fetches the result set.

-   CURSOR\_CLOSE: the closing cursor.

-   AGGREGATED\_EXECUTION: calculates the overall execution time for SELECT queries, including compilation time in the case of non-prepared statements.

    For prepared statements, compilation time is not included in the AGGREGATED\_EXECUTION of every prepared statement execution, since compilation usually occurs only once \(except for recompilation at runtime\). Adding compilation time to AGGREGATED\_EXECUTION may exaggerate the overall execution time.

    For non-prepared statements, compilation time is included in the AGGREGATED\_EXECUTION of every ad hoc statement execution since it is newly compiled or is attempting to look up a SQL plan cache every time within a single session request.


The following types of operations execute a DML statement:

-   CALL

-   DELETE

-   DEQUEUE

-   EXPLAIN\_PLAN

-   INSERT

-   SELECT

-   SELECT\_FOR\_UPDATE

-   UPDATE

-   EXECUTE\_DML: represents the less common DML statements that are not listed above.


The following operations execute a DDL statement:

-   CREATE\_TABLE

-   CREATE\_VIEW

-   EXECUTE\_DDL: represents the less common DDL statements that are not listed above.


The following operations execute statements except DML and DDL:

-   EXECUTE: represents the less common SQL statements.


Consider a query with 4 session requests from a client:

1.  Prepare: 10 msec
2.  Execute: 20 msec
3.  Fetch: 15 msec
4.  Close: 5 msec

Assuming that all operations are longer than the threshold, they are shown as: OPERATION DURATION COMPILE 10 SELECT 20 FETCH 15 CURSOR\_CLOSE 5 AGGREGATED\_EXECUTION 40 \(20+15+5\).



<a name="loio20af736e751910148162e2ab1982f035__section_yjl_flg_rkb"/>

## Additional Information

Setting the value of the APPLICATION\_SOURCE is only available via internal APIs of the SAP HANA database client interfaces \(for more information see SAP Note 2873396\).

**Related Information**  


[SAP Note 2873396](https://me.sap.com/notes/2873396)

[M\_EXPENSIVE\_STATEMENT\_EXECUTION\_LOCATION\_STATISTICS System View](m-expensive-statement-execution-location-statistics-system-view-80c32e9.md "Provides location statistics for expensive statements.")

[Expensive Statements Trace](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/5faf04f17830464eacdb7938b383d2ab.html "Expensive statements are individual SQL statements whose execution time exceeds a configured threshold. The expensive statements trace records information about these statements for further analysis and is inactive by default.") :arrow_upper_right:

