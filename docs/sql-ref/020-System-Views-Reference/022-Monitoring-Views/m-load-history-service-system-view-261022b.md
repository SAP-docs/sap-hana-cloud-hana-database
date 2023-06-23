<!-- loio261022b7e22b4de9b04f931b78c4c6b4 -->

# M\_LOAD\_HISTORY\_SERVICE System View

Lists service-specific load history KPIs.



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

TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the KPI collection timestamp.



</td>
</tr>
<tr>
<td valign="top">

CPU



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the percent of CPU used by the service.



</td>
</tr>
<tr>
<td valign="top">

SYSTEM\_CPU



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the percent of OS Kernel/System CPU used by the service.



</td>
</tr>
<tr>
<td valign="top">

MEMORY\_USED



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the memory used by the service in bytes.



</td>
</tr>
<tr>
<td valign="top">

MEMORY\_ALLOCATION\_LIMIT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the memory allocation limit for the service in bytes.



</td>
</tr>
<tr>
<td valign="top">

HANDLE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of open handles.



</td>
</tr>
<tr>
<td valign="top">

PING\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the duration, in microseconds, of the service ping request \(THREAD\_METHOD=\_\_nsWatchdog\). This request includes the time it takes to measure the values shown in this view.



</td>
</tr>
<tr>
<td valign="top">

SWAP\_IN



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the bytes read from the swap by the service \(column 12\(majflt\) in /proc/*<pid\>*/stat \* sysconf\(\_SC\_PAGESIZE\)\).



</td>
</tr>
<tr>
<td valign="top">

CONNECTION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of open SQL connections.



</td>
</tr>
<tr>
<td valign="top">

INTERNAL\_CONNECTION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of open SQL internal connections.



</td>
</tr>
<tr>
<td valign="top">

EXTERNAL\_CONNECTION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of open SQL external connections.



</td>
</tr>
<tr>
<td valign="top">

IDLE\_CONNECTION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of open SQL idle connections.



</td>
</tr>
<tr>
<td valign="top">

TRANSACTION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of open SQL transactions.



</td>
</tr>
<tr>
<td valign="top">

INTERNAL\_TRANSACTION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of internal transactions.



</td>
</tr>
<tr>
<td valign="top">

EXTERNAL\_TRANSACTION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of external transactions.



</td>
</tr>
<tr>
<td valign="top">

USER\_TRANSACTION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of user transactions.



</td>
</tr>
<tr>
<td valign="top">

BLOCKED\_TRANSACTION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of blocked SQL transactions.



</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of finished SQL statements.



</td>
</tr>
<tr>
<td valign="top">

COMMIT\_ID\_RANGE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the range between the newest and oldest active commit IDs.



</td>
</tr>
<tr>
<td valign="top">

MVCC\_VERSION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of active MVCC versions.



</td>
</tr>
<tr>
<td valign="top">

PENDING\_SESSION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of pending requests.



</td>
</tr>
<tr>
<td valign="top">

RECORD\_LOCK\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of acquired record locks.



</td>
</tr>
<tr>
<td valign="top">

CS\_READ\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of read requests \(SELECT\).



</td>
</tr>
<tr>
<td valign="top">

CS\_WRITE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of write requests \(INSERT, UPDATE, DELETE\).



</td>
</tr>
<tr>
<td valign="top">

CS\_MERGE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of merge requests.



</td>
</tr>
<tr>
<td valign="top">

CS\_UNLOAD\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of column unloads.



</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_THREAD\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of active threads.



</td>
</tr>
<tr>
<td valign="top">

WAITING\_THREAD\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of waiting threads.



</td>
</tr>
<tr>
<td valign="top">

TOTAL\_THREAD\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total number of threads.



</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_SQL\_EXECUTOR\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of active SQLExecutors.



</td>
</tr>
<tr>
<td valign="top">

WAITING\_SQL\_EXECUTOR\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of waiting SQLExecutors.



</td>
</tr>
<tr>
<td valign="top">

TOTAL\_SQL\_EXECUTOR\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total number of SQLExecutors.



</td>
</tr>
<tr>
<td valign="top">

DATA\_WRITE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the bytes written to the data area.



</td>
</tr>
<tr>
<td valign="top">

DATA\_WRITE\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the time used for writing to the data area in microseconds.



</td>
</tr>
<tr>
<td valign="top">

LOG\_WRITE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the bytes written to the log area.



</td>
</tr>
<tr>
<td valign="top">

LOG\_WRITE\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the time used for writing to the log area in microseconds.



</td>
</tr>
<tr>
<td valign="top">

DATA\_READ\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the bytes read from the data area.



</td>
</tr>
<tr>
<td valign="top">

DATA\_READ\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the time used for reading from the data area in microseconds.



</td>
</tr>
<tr>
<td valign="top">

LOG\_READ\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the bytes read from the log area.



</td>
</tr>
<tr>
<td valign="top">

LOG\_READ\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the time used for reading from the log area in microseconds.



</td>
</tr>
<tr>
<td valign="top">

DATA\_BACKUP\_WRITE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the bytes written to the data backup.



</td>
</tr>
<tr>
<td valign="top">

DATA\_BACKUP\_WRITE\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the time used for writing to the data backup in microseconds.



</td>
</tr>
<tr>
<td valign="top">

LOG\_BACKUP\_WRITE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the bytes written to the log backup.



</td>
</tr>
<tr>
<td valign="top">

LOG\_BACKUP\_WRITE\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

The time used for writing to the log backup.



</td>
</tr>
<tr>
<td valign="top">

MUTEX\_COLLISION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of collisions on mutexes.



</td>
</tr>
<tr>
<td valign="top">

READ\_WRITE\_LOCK\_COLLISION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of collisions on read/write locks.



</td>
</tr>
<tr>
<td valign="top">

ADMISSION\_CONTROL\_ADMIT\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of admission requests admitted by admission control.



</td>
</tr>
<tr>
<td valign="top">

ADMISSION\_CONTROL\_REJECT\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of session requests rejected by admission control.



</td>
</tr>
<tr>
<td valign="top">

ADMISSION\_CONTROL\_QUEUE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of session requests waiting in the admission control queue.



</td>
</tr>
<tr>
<td valign="top">

ADMISSION\_CONTROL\_WAIT\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total wait time of the session requests queued in the admission control queue in microseconds.



</td>
</tr>
<tr>
<td valign="top">

ADMISSION\_CONTROL\_ENQUEUE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of session requests queued by admission control.



</td>
</tr>
<tr>
<td valign="top">

ADMISSION\_CONTROL\_DEQUEUE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of session requests dequeued for deferred execution by admission control.



</td>
</tr>
<tr>
<td valign="top">

ADMISSION\_CONTROL\_TIMEOUT\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of session requests dequeued for timed out by admission control.



</td>
</tr>
</table>

**Related Information**  


[M\_LOAD\_HISTORY\_HOST System View](m-load-history-host-system-view-3fa52ab.md "Host specific load history KPIs.")

[M\_LOAD\_HISTORY\_INFO System View](m-load-history-info-system-view-2148ede.md "Load history KPI description.")

[LOAD Statement \(Data Manipulation\)](../../010-SQL-Reference/012-SQL-Statements/load-statement-data-manipulation-20f83c8.md "Explicitly loads column store table data into memory instead of upon first access.")

[PERSISTENCE\_HISTORY System View](../021-System-Views/persistence-history-system-view-a8cb93e.md "Records the database version history.")

