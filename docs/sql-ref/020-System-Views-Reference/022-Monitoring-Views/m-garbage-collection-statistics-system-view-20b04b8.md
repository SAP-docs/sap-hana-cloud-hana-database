<!-- loio20b04b8f7519101499c39b3f35659a7f -->

# M\_GARBAGE\_COLLECTION\_STATISTICS System View

Provides garbage collection and history manager statistics.



<a name="loio20b04b8f7519101499c39b3f35659a7f___m__g_a_r_b_a_g_e__c_o_l_l_e_c_t_i_o_n__s_t_a_t_i_s_t_i_c_s_1struct_M_GARBAGE_COLLECTION_STATISTICS"/>

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

STORE\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the type of storage handled: COLUMN STORE.

</td>
</tr>
<tr>
<td valign="top">

HISTORY\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the current count of history files in the garbage collection.

</td>
</tr>
<tr>
<td valign="top">

WAITER\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the current count of garbage collection waiters.

</td>
</tr>
<tr>
<td valign="top">

MIN\_READ\_TID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last known minimum transaction ID \(TID\) of a reading transaction at end of transaction \(EOT\).

</td>
</tr>
<tr>
<td valign="top">

LAST\_STARTED\_TID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the TID of the last started cleanup job.

</td>
</tr>
<tr>
<td valign="top">

LAST\_STARTED\_TID\_POSTCOMMIT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the TID of the last started postcommit job.

</td>
</tr>
<tr>
<td valign="top">

FIRST\_WAITING\_TID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the TID of the first waiting cleanup job.

</td>
</tr>
<tr>
<td valign="top">

FIRST\_WAITING\_TID\_POSTCOMMIT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the TID of the first waiting postcommit job.

</td>
</tr>
<tr>
<td valign="top">

ENTERS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of history files that entered the queue for cleanup.

</td>
</tr>
<tr>
<td valign="top">

ENTERS\_POSTCOMMIT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of history files that entered the queue for postcommit.

</td>
</tr>
<tr>
<td valign="top">

STARTED\_JOBS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of started garbage collection cleanup jobs.

</td>
</tr>
<tr>
<td valign="top">

STARTED\_JOBS\_POSTCOMMIT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of started postcommit jobs.

</td>
</tr>
<tr>
<td valign="top">

PROCESSED\_JOBS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of undo files processed for cleanup.

</td>
</tr>
<tr>
<td valign="top">

PROCESSED\_JOBS\_POSTCOMMIT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of undo files processed for postcommit.

</td>
</tr>
<tr>
<td valign="top">

QUEUE\_LOADS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of all garbage collection queue loads.

</td>
</tr>
<tr>
<td valign="top">

QUEUE\_LOADS\_NONEMPTY

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of garbage collection queue loads which found elements.

</td>
</tr>
<tr>
<td valign="top">

QUEUE\_EMPTY\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of queue empty states after garbage collection finished.

</td>
</tr>
<tr>
<td valign="top">

SAVEPOINTS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of savepoints.

</td>
</tr>
<tr>
<td valign="top">

LAST\_HISTORY\_SIZE\_AT\_SVP

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the lastest number of history files present at the savepoint.

</td>
</tr>
<tr>
<td valign="top">

MAX\_HISTORY\_SIZE\_AT\_SVP

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum number of history files present at the savepoint.

</td>
</tr>
<tr>
<td valign="top">

MIN\_HISTORY\_SIZE\_AT\_SVP

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum number of history files present at the savepoint.

</td>
</tr>
<tr>
<td valign="top">

SUM\_HISTORY\_SIZE\_AT\_SVP

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of history files present at the savepoint.

</td>
</tr>
<tr>
<td valign="top">

AVG\_HISTORY\_SIZE\_AT\_SVP

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the average number of history files present at the savepoint.

</td>
</tr>
<tr>
<td valign="top">

EMPTY\_HISTORY\_AT\_SVP\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of savepoints with an empty queue.

</td>
</tr>
</table>



<a name="loio20b04b8f7519101499c39b3f35659a7f___m__g_a_r_b_a_g_e__c_o_l_l_e_c_t_i_o_n__s_t_a_t_i_s_t_i_c_s_1fulldesc_M_GARBAGE_COLLECTION_STATISTICS"/>

## Additional Information

This view shows various statistics about garbage collection jobs.

Garbage collection is used to remove old versions of data objects from the system. Afterward, transactions cannot reference these old versions. References to these objects are kept in history \(cleanup\) files, which are processed by the garbage collector.

Normally, the system runs in statement consistency isolation level \(that is, a consistent view is acquired when an SQL operation starts\). Alternatively, the system can be run in transaction consistency isolation level, where the consistent view is acquired when the transaction starts and is held until the transaction terminates \(snapshot isolation, similar to SERIALIZABLE isolation level\). Each consistent view contains a reference to a minReadTID Transaction ID \(TID\), which is the minimum TID, from which the changes are "seen" by the transaction. Global minReadTID \(minimum of minReadTIDs of all consistent views\) is used by the garbage collector to determine which history files can be cleaned.

In cases where the history files accumulate and MIN\_READ\_TID does not advance, some transactions probably hold their consistent view for very long time \(for example, a long-running transaction of a forgotten read transaction in a GUI\). Query the M\_TRANSACTIONS system view to see information about each running transaction.

This view has a resettable counterpart; you can see the values since the last reset in the M\_GARBAGE\_COLLECTION\_STATISTICS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_GARBAGE_COLLECTION_STATISTICS_RESET;`.

**Related Information**  


[M\_TRANSACTIONS System View](m-transactions-system-view-20c9610.md "Provides information about all transactions created by users or the database.")

[ALTER SYSTEM RESET MONITORING VIEW Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-reset-monitoring-view-statement-system-management-20d27aa.md "Resets statistics data for the specified monitoring view.")

[Deterministic Procedures](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/dae6fae315c546ba9dc8665c0ca51cb9.html "") :arrow_upper_right:

