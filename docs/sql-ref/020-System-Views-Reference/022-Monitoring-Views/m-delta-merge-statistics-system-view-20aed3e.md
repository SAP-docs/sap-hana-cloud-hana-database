<!-- loio20aed3e475191014aae191f316692093 -->

# M\_DELTA\_MERGE\_STATISTICS System View

Provides information on table delta merge statistics.



<a name="loio20aed3e475191014aae191f316692093___m__d_e_l_t_a__m_e_r_g_e__s_t_a_t_i_s_t_i_c_s_1struct_M_DELTA_MERGE_STATISTICS"/>

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

TYPE

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays the type of the statistic:


<dl>
<dt><b>

MERGE

</b></dt>
<dd>

The table delta merge.



</dd><dt><b>

HINT

</b></dt>
<dd>

The application merge hint.



</dd><dt><b>

SPARSE

</b></dt>
<dd>

Optimizes compression.



</dd><dt><b>

FACT

</b></dt>
<dd>

The fact table compression.



</dd><dt><b>

RECLAIM

</b></dt>
<dd>

The table delta garbage collection.



</dd>
</dl>



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

Displays the schema name.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the table name.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID of the table.

</td>
</tr>
<tr>
<td valign="top">

PART\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the partition ID. Returns the following:

-   For partitioned tables, the part ID is equal to the sequential number of the partition, starting at 1.
-   In the case of replicated tables, the part ID is 1 for the original table and subsequent part IDs are assigned to replica tables.
-   The part ID is 0 for tables that are not partitioned.
-   A part ID value of -1 indicates that a modification of the table schema is in progress.



</td>
</tr>
<tr>
<td valign="top">

INTERNAL\_PART\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the internal partition ID.

</td>
</tr>
<tr>
<td valign="top">

MEMORY\_MERGE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Deprecated. Use the TYPE column, which displays more detailed information.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the external identifier for the table merge called by an application.

</td>
</tr>
<tr>
<td valign="top">

LOG\_REPLAY\_QUEUE\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the ID of the log replay queue where the job was started. During log replay, only delta merge and optimize compression operations are possible.

During online operation, all TYPEs apply. -1 indicates that online merges and optimized compressions exist.

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

Displays the execution start time.

</td>
</tr>
<tr>
<td valign="top">

RESOURCE\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total wait time in milliseconds for memory and CPU resources when too many merges or optimized compressions have been started in parallel.

</td>
</tr>
<tr>
<td valign="top">

PHASE\_1\_HESITANT\_LOCK\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total wait time in milliseconds to acquire an exclusive lock in the first exclusive merge phase. The time includes configured timeout and subsequent retries.

</td>
</tr>
<tr>
<td valign="top">

PHASE\_1\_BLOCKING\_LOCK\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the wait time in milliseconds to acquire an exclusive lock in the first exclusive merge phase in the event the hesitant acquire was unsuccessful. New readers and writers are already blocked.

</td>
</tr>
<tr>
<td valign="top">

PHASE\_1\_LOCK\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the time in milliseconds spent under exclusive lock in the first exclusive merge phase.

</td>
</tr>
<tr>
<td valign="top">

PHASE\_2\_HESITANT\_LOCK\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total wait time in milliseconds to acquire an exclusive lock for the second exclusive merge phase or the exclusive optimize compression phase, respectively. The time includes configured timeout and subsequent retries."

</td>
</tr>
<tr>
<td valign="top">

PHASE\_2\_BLOCKING\_LOCK\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the time in milliseconds to acquire an exclusive lock for the second exclusive merge phase or the exclusive optimize compression phase, respectively, in the event the hesitant acquire was unsuccessful. New readers and writers are already blocked.

</td>
</tr>
<tr>
<td valign="top">

PHASE\_2\_LOCK\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the time in milliseconds spent under exclusive lock in the second exclusive merge phase or the exclusive optimize compression phase, respectively.

</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the execution duration in milliseconds.

</td>
</tr>
<tr>
<td valign="top">

MOTIVATION

</td>
<td valign="top">

NVARCHAR\(9\)

</td>
<td valign="top">

Displays the motivation of the statistics:


<dl>
<dt><b>

AUTO

</b></dt>
<dd>

Triggered based on an automatic decision function.



</dd><dt><b>

SMART

</b></dt>
<dd>

Triggered by a HINT from the user based on a smart decision function.



</dd><dt><b>

CRITICAL

</b></dt>
<dd>

Triggered based on a critical decision function.



</dd><dt><b>

HARD

</b></dt>
<dd>

Triggered via SQL based on a hard decision function.



</dd><dt><b>

FORCED

</b></dt>
<dd>

A merge triggered via SQL, circumventing resource availability checks, based on a forced decision function.



</dd>
</dl>



</td>
</tr>
<tr>
<td valign="top">

SUCCESS

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays a call success flag, which depends on the field TYPE.


<dl>
<dt><b>

HINT

</b></dt>
<dd>

Displays whether the application merge hint was accepted or rejected.



</dd><dt><b>

MERGE/SPARSE

</b></dt>
<dd>

Displays whether the delta merge/optimize compression was completed with or without success: TRUE/FALSE. For example, a table delta merge call which did not result in a delta merge because the delta was empty, is indicated with FALSE.



</dd>
</dl>



</td>
</tr>
<tr>
<td valign="top">

OLD\_MAIN\_RECORDS

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of rows in old main prior to the delta merge. -1 indicates other operation types.

</td>
</tr>
<tr>
<td valign="top">

MERGED\_MAIN\_RECORDS

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of rows merged from old main to new main. -1 indicates other operation types.

</td>
</tr>
<tr>
<td valign="top">

OLD\_DELTA\_RECORDS

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of rows merged from old main to new main. -1 indicates other operation types.

</td>
</tr>
<tr>
<td valign="top">

MERGED\_DELTA\_RECORDS

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of rows merged from old delta1 to new main for MERGE operation or the number of rows evicted from delta during RECLAIM delta operation. -1 indicates other operation types.

</td>
</tr>
<tr>
<td valign="top">

NEW\_MAIN\_RECORDS

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the total number of rows in new main after the merge. It is the sum of MERGED\_MAIN\_RECORDS and MERGED\_DELTA\_RECORDS. -1 indicates other operation types.

</td>
</tr>
<tr>
<td valign="top">

OLD\_MAIN\_IN\_USE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays TRUE when old main is still in use by old readers once the merge or optimize compression is finished. Old main will only be deleted after the last reader has finished. FALSE indicates other operation types.

</td>
</tr>
<tr>
<td valign="top">

OLD\_DELTA\_IN\_USE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays TRUE when old delta1 is still in use by old readers once the merge is finished. It will only be deleted after the last reader has finished. FALSE indicates other operation types.

</td>
</tr>
<tr>
<td valign="top">

LAST\_ERROR

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the error code of the last error that occurred. This explains why a merge did not succeed. See ERROR\_DESCRIPTION for details.

</td>
</tr>
<tr>
<td valign="top">

CS\_ERROR

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the column store specific error code. See ERROR\_DESCRIPTION for details.

</td>
</tr>
<tr>
<td valign="top">

ERROR\_DESCRIPTION

</td>
<td valign="top">

NVARCHAR\(2000\)

</td>
<td valign="top">

Displays the description of the last error that occurred during the merge. A failing merge does not necessarily indicate a problem.

</td>
</tr>
</table>



<a name="loio20aed3e475191014aae191f316692093___m__d_e_l_t_a__m_e_r_g_e__s_t_a_t_i_s_t_i_c_s_1fulldesc_M_DELTA_MERGE_STATISTICS"/>

## Additional Information

Table delta merges, optimize compression runs, and application merge hints are listed separately.

**Related Information**  


[MERGE DELTA Statement \(Data Manipulation\)](../../010-SQL-Reference/012-SQL-Statements/merge-delta-statement-data-manipulation-20f8d0a.md "Merges the column store table delta storage to the table's main storage.")

[MERGE INTO Statement \(Data Manipulation\)](../../010-SQL-Reference/012-SQL-Statements/merge-into-statement-data-manipulation-3226201.md "Merges data into an existing column store table.")

[HOST_DELTA_MERGE_STATISTICS View (Embedded Statistics Service)](https://help.sap.com/viewer/323c57a017234d47a0e7da3e22345822/2024_1_QRC/en-US/b1a754a52a484a85922a87a269592cfa.html "Specifies the table delta merge statistics per host.") :arrow_upper_right:

