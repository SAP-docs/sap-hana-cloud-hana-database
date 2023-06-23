<!-- loio20bdd30475191014be9c89841ce18d8b -->

# M\_SAVEPOINTS System View

Displays current and historical savepoint statistics.



<a name="loio20bdd30475191014be9c89841ce18d8b___m__s_a_v_e_p_o_i_n_t_s_1struct_M_SAVEPOINTS"/>

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

START\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the savepoint start time.



</td>
</tr>
<tr>
<td valign="top">

INITIATION



</td>
<td valign="top">

NVARCHAR\(24\)



</td>
<td valign="top">

Displays the reason why the savepoint was executed.



</td>
</tr>
<tr>
<td valign="top">

PURPOSE



</td>
<td valign="top">

NVARCHAR\(24\)



</td>
<td valign="top">

Displays the purpose of the savepoint.



</td>
</tr>
<tr>
<td valign="top">

STATE



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the savepoint state. A savepoint is triggered periodically, but it can be also triggered on demand using the ALTER SYSTEM SAVEPOINT statement or by a data backup. The savepoint then runs through the following various states:

-   ***INITIAL*** - Displays the empty statistics record \(just allocated\); immediately goes to the ***PREPARE*** state.

-    ***PREPARE*** - Displays that the savepoint is preparing to run.

-    ***PAGEFLUSH*** - flushes dirty pages asynchronously. ***PAGES*** and ***SIZE*** counters are updated to reflect the savepoint progress.

-    ***PRECRITICAL*** - runs any pre-critical-phase callbacks and waits for I/O of the rest of the flushed pages.

-    ***ENTERCRITICAL*** - entering critical phase: stops updaters and waits for the critical phase lock.

-    ***CRITICAL*** - critical phase: copies and triggers the write of any pages that are still dirty, records various information in the restart record \(log position, transaction manager state, and so on\), and increments the savepoint version. ***PAGES\_IN\_CRITICAL\_PHASE*** and ***SIZE\_IN\_CRITICAL\_PHASE*** counters are updated appropriately.

-    ***EXITCRITICAL*** - exit critical phase: releases critical phase locks and restarts updaters.

-    ***POSTCRITICAL*** - calls any post-critical phase callbacks, finalizes the savepoint record, and cleans up unneeded RTT entries.

-    ***FINISHING*** - waits for the flush of pages written in the critical phase and writes out the restart record and anchor page.

-    ***DONE*** - Displays that the savepoint has been completed successfully.

-    ***ABORTED*** - Displays that the savepoint has been aborted \(for example, due to a timeout during the synchronization of the global savepoint\).




</td>
</tr>
<tr>
<td valign="top">

VERSION



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the savepoint version.



</td>
</tr>
<tr>
<td valign="top">

REQUESTED\_FREQUENCY



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the frequency of the savepoint.



</td>
</tr>
<tr>
<td valign="top">

TIME\_SINCE\_PREVIOUS



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the time in seconds between the current and previous current savepoints.



</td>
</tr>
<tr>
<td valign="top">

DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total time in microseconds to create the savepoint.



</td>
</tr>
<tr>
<td valign="top">

PREPARE\_FLUSH\_RETRY\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of times the pages were flushed in the non-critical phase before entering the critical phase.



</td>
</tr>
<tr>
<td valign="top">

BLOCKING\_PHASE\_START\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the start time of the last blocking phase.



</td>
</tr>
<tr>
<td valign="top">

BLOCKING\_PHASE\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the phase duration in microseconds.



</td>
</tr>
<tr>
<td valign="top">

CRITICAL\_PHASE\_START\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the start time of the last critical phase.



</td>
</tr>
<tr>
<td valign="top">

CRITICAL\_PHASE\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the time in microseconds spent in the critical phase, during which updates are blocked.



</td>
</tr>
<tr>
<td valign="top">

CRITICAL\_PHASE\_WAIT\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the wait time in microseconds for the critical phase.



</td>
</tr>
<tr>
<td valign="top">

TOTAL\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of bytes that have been prompted to be written to the disk.



</td>
</tr>
<tr>
<td valign="top">

FLUSHED\_PAGES



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of asynchronously flushed pages.



</td>
</tr>
<tr>
<td valign="top">

FLUSHED\_PAGES\_IN\_CRITICAL\_PHASE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of pages flushed in the critical phase.



</td>
</tr>
<tr>
<td valign="top">

FLUSHED\_ROWSTORE\_PAGES



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of asynchronously flushed row store pages.



</td>
</tr>
<tr>
<td valign="top">

FLUSHED\_ROWSTORE\_PAGES\_IN\_CRITICAL\_PHASE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of row store pages flushed in the critical phase.



</td>
</tr>
<tr>
<td valign="top">

FLUSHED\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size of asynchronously flushed pages in bytes.



</td>
</tr>
<tr>
<td valign="top">

FLUSHED\_SIZE\_IN\_CRITICAL\_PHASE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size in bytes of pages flushed in the critical phase.



</td>
</tr>
<tr>
<td valign="top">

FLUSHED\_ROWSTORE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size in bytes of the asynchronously flushed row store pages.



</td>
</tr>
<tr>
<td valign="top">

FLUSHED\_ROWSTORE\_SIZE\_IN\_CRITICAL\_PHASE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size of the row store pages flushed in the critical phase .



</td>
</tr>
<tr>
<td valign="top">

RTT\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total size in bytes of the rollback transaction table at the savepoint.



</td>
</tr>
</table>



<a name="loio20bdd30475191014be9c89841ce18d8b___m__s_a_v_e_p_o_i_n_t_s_1fulldesc_M_SAVEPOINTS"/>

## Additional Information

This monitor view contains information about the current and some past savepoints. Information is kept on the last 128 savepoints per persistence manager.

> ### Note:  
> Only savepoint information since the startup is kept. The information in this monitor view does not persist. The statistics server collects some information about savepoints that persists.

This view is associated with the ALTER SYSTEM SAVEPOINT statement.

The following information can be extracted from the numbers in this view:

-    ***CRITICAL\_PHASE\_DURATION*** shows the period of time during which the updaters were blocked in a savepoint. Normally, this should be in the millisecond range, except for global savepoints for data backup, which may take longer due to global synchronization across all nodes. If the critical phase duration is too long, there may be a problem \(for example, the I/O load is too high\).

-    ***DURATION*** shows the total time taken by a savepoint. This should be significantly less than the configured savepoint frequency ***REQUESTED\_FREQUENCY*** \(in the range 0-10%, depending on the load\). Higher ratios indicate an I/O overload.

-    ***TIME\_SINCE\_PREVIOUS*** should be close to ***REQUESTED\_FREQUENCY***. If it is significantly higher, this indicates that the savepoint is encountering a block, such as a very long column merge operation.

-   A ratio of ***FLUSHED\_PAGES\**** vs. ***FLUSHED\_ROWSTORE\_PAGES\**** or a ratio of ***FLUSHED\_SIZE\**** vs. ***FLUSHED\_ROWSTORE\_SIZE\**** shows the respective load of column store vs. row store. The row store is only flushed during the savepoint, and the column store also flushes the data between savepoints to balance the load.

-   A high ratio of ***FLUSHED\_\*PAGES\_IN\_CRITICAL\_PHASE*** vs. ***FLUSHED\_\*PAGES*** or a ratio of ***FLUSHED\_\*SIZE\_IN\_CRITICAL\_PHASE*** vs. ***FLUSHED\_\*SIZE*** indicates a potential I/O overload. Normally, zero or only a few pages should be written in the critical phase, except for special situations like a global savepoint for data backups \(but in this case, the number of pages written in the critical phase should be in the order of the magnitude, 1% or less, of asynchronously flushed pages\). High amounts of data written in the critical phase indicates an overload of the I/O subsystem and can lead to increased blocking times of update transactions due to an increased ***CRITICAL\_PHASE\_DURATION***.

-   A big ***RTT\_SIZE*** \(more than a few entries\) indicates a problem in distributed transaction handling. RTT \(rollback transaction table\) holds rollback entries for distributed transactions that are currently in rollback. Normally, these entries are eliminated quickly after the respective rollback is finished. In cases where a secondary node fails, entries for the secondary node are held persistently until the secondary node restarts. This number goes to zero or close to zero shortly after the restart of a failed secondary node \(or after the restart of the whole system\).


Aggregated values for individual counters can be queried from the M\_SAVEPOINT\_STATISTICS system view.

**Related Information**  


[M\_SAVEPOINT\_STATISTICS System View](m-savepoint-statistics-system-view-20bc9a8.md "Provides information about executed savepoints.")

[M\_SAVEPOINT\_STATISTICS\_RESET System View](m-savepoint-statistics-reset-system-view-20bcc12.md "Provides the savepoint statistics since the last reset.")

[ALTER SYSTEM SAVEPOINT Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-savepoint-statement-system-management-20d2b6e.md "Executes a database checkpoint on the persistence manager.")

[ROLLBACK TO SAVEPOINT Statement \(Transaction Management\)](../../010-SQL-Reference/012-SQL-Statements/rollback-to-savepoint-statement-transaction-management-104ae26.md "Rolls back a transaction to the named savepoint without terminating the transaction.")

[RELEASE SAVEPOINT Statement \(Transaction Management\)](../../010-SQL-Reference/012-SQL-Statements/release-savepoint-statement-transaction-management-445eb4d.md "Releases a specified savepoint name.")

[SAVEPOINT](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/e933397e9ec84f439f25962f4e193063.html "") :arrow_upper_right:

