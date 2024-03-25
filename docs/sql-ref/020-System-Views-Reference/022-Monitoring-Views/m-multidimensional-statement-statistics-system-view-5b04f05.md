<!-- loio5b04f05f501f4f91aea202f1394cfddc -->

# M\_MULTIDIMENSIONAL\_STATEMENT\_STATISTICS System View

Displays all multidimensional statement statistics gathered since the server started. This information does not persist when you restart the server.



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

Displays the internal port.

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

Displays the multidimensional services \(MDS\) statement hash.

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

Displays the name of the user.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the application user.

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

STATEMENT\_TYPE

</td>
<td valign="top">

NVARCHAR\(3\)

</td>
<td valign="top">

Displays the statement type.

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

Displays the last connection ID that executed the statement.

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

Displays the time of the last execution.

</td>
</tr>
<tr>
<td valign="top">

LAST\_METADATA\_READ\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last metadata read duration, in milliseconds \(ms\).

</td>
</tr>
<tr>
<td valign="top">

Feature removal - MDX - LQNLAST\_QUERY\_PREPARATION\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last query preparation duration, in milliseconds \(ms\).

</td>
</tr>
<tr>
<td valign="top">

LAST\_PLAN\_EXECUTION\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last plan execution duration, in milliseconds \(ms\).

</td>
</tr>
<tr>
<td valign="top">

LAST\_POST\_PROCESSING\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last post processing duration, in milliseconds \(ms\).

</td>
</tr>
<tr>
<td valign="top">

LAST\_CUBE\_PROCESSING\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last cube processing duration, in milliseconds \(ms\).

</td>
</tr>
<tr>
<td valign="top">

LAST\_PLAN\_EXECUTION\_RESULTSET\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last size of the intermediate result returned by the plan execution, in bytes.

</td>
</tr>
<tr>
<td valign="top">

LAST\_RESULTSET\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of the last result set, in bytes.

</td>
</tr>
<tr>
<td valign="top">

LAST\_RESULTSET\_CELL\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of cells in the last result set.

</td>
</tr>
<tr>
<td valign="top">

LAST\_HIERARCHY\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the latest number of hierarchies.

</td>
</tr>
<tr>
<td valign="top">

LAST\_CACHED\_HIERARCHY\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the last number of hierarchy cache hits.

</td>
</tr>
<tr>
<td valign="top">

LAST\_CALCULATION\_ENTITY\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the last number of calculation entities.

</td>
</tr>
<tr>
<td valign="top">

LAST\_CALCULATION\_ENTITY\_GROUP\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the last number of calculation entity groups.

</td>
</tr>
<tr>
<td valign="top">

LAST\_DRILL\_DIMENSION\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the last number of dimensions in the drill.

</td>
</tr>
<tr>
<td valign="top">

LAST\_AGGREGATION\_DIMENSION\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the last number of aggregation dimensions.

</td>
</tr>
<tr>
<td valign="top">

LAST\_SERIALIZED\_CUBE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last size of the serialized cube, in bytes.

</td>
</tr>
<tr>
<td valign="top">

LAST\_REQUEST\_QUEUE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of jobs waiting in the request queue.

</td>
</tr>
<tr>
<td valign="top">

LAST\_EXECUTION\_STATUS

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the last execution status of the statement.

</td>
</tr>
<tr>
<td valign="top">

LAST\_PERFORMANCE\_DATA

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the last performance data.

</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the execution count.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_METADATA\_CACHE\_HIT\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of data cache hits.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_DATA\_CACHE\_HIT\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of data cached hits.

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

Displays the total time of the execution, in milliseconds \(ms\).

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

Displays the average time of the execution, in milliseconds \(ms\).

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

Displays the minimum time of the execution, in milliseconds \(ms\).

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

Displays the maximum time of the execution, in milliseconds \(ms\).

</td>
</tr>
<tr>
<td valign="top">

MAX\_CALLED\_THREAD\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the maximum thread count.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_EXECUTION\_MEMORY\_SIZE<sup>\*\*</sup>

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total memory size, in bytes.

</td>
</tr>
<tr>
<td valign="top">

AVG\_EXECUTION\_MEMORY\_SIZE<sup>\*\*</sup>

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average memory size, in bytes.

</td>
</tr>
<tr>
<td valign="top">

MIN\_EXECUTION\_MEMORY\_SIZE<sup>\*\*</sup>

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum memory size, in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAX\_EXECUTION\_MEMORY\_SIZE<sup>\*\*</sup>

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum memory size, in bytes.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_EXECUTION\_CPU\_TIME<sup>\*\*</sup>

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Specifies the total used CPU time, in milliseconds \(ms\).

</td>
</tr>
<tr>
<td valign="top">

AVG\_EXECUTION\_CPU\_TIME<sup>\*\*</sup>

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Specifies the average used CPU time, in milliseconds \(ms\).

</td>
</tr>
<tr>
<td valign="top">

MIN\_EXECUTION\_CPU\_TIME<sup>\*\*</sup>

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Specifies the minimum used CPU time, in milliseconds \(ms\).

</td>
</tr>
<tr>
<td valign="top">

MAX\_EXECUTION\_CPU\_TIME<sup>\*\*</sup>

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Specifies the maximum used CPU time, in milliseconds \(ms\).

</td>
</tr>
</table>



<a name="loio5b04f05f501f4f91aea202f1394cfddc__section_n2h_4fs_dyb"/>

## Additional Information

<sup>\*\*</sup>Only memory usage and CPU time on the main system is tracked. If any other system is involved, for example, an external view is used, then memory usage and CPU time on this system is not tracked. For batch queries, there is always one entry for the complete query and one for each sub query. To avoid a double counting of memory and CPU time, the following rules apply:


<dl>
<dt><b>

Normal Batch Request:

</b></dt>
<dd>

The memory usage is tracked for the complete query, while CPU-Time is tracked for each sub query.

-   Batch query:
    -   For all forms, EXECUTION\_MEMORY\_SIZE is the memory-usage of all subqueries together.
    -   For all forms, EXECUTION\_CPU\_TIME is NULL.

-   Sub queries:
    -   For all forms, EXECUTION\_MEMORY\_SIZE is NULL.
    -   For all forms, EXECUTION\_CPU\_TIME is the CPU time used by the subquery.




</dd><dt><b>

Asynchronous Batch Request:

</b></dt>
<dd>

For asynchronous batch requests, both CPU time and memory usage are tracked per subquery.

-   Batch query:
    -   All forms of EXECUTION\_MEMORY\_SIZE and EXECUTION\_CPU\_TIME are null.

-   Sub queries:
    -   For all forms of EXECUTION\_MEMORY\_SIZE is the memory used by the subquery.
    -   For all forms of EXECUTION\_CPU\_TIME is the CPU time used by the subquery.




</dd>
</dl>

The M\_MULTIDIMENSIONAL\_STATEMENTS\_STATISTICS view is not enabled by default. Refer to the *mds* section in the *SAP HANA Cloud, SAP HANA Database Configuration Parameter Reference* for details on enabling.

