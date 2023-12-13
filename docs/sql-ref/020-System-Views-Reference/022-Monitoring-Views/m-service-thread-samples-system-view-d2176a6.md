<!-- loiod2176a65d2951014b80cbf93343900d5 -->

# M\_SERVICE\_THREAD\_SAMPLES System View

Displays detailed information about locks held by threads.



<a name="loiod2176a65d2951014b80cbf93343900d5___m__s_e_r_v_i_c_e__t_h_r_e_a_d__s_a_m_p_l_e_s_1struct_M_SERVICE_THREAD_SAMPLES"/>

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

SERVICE\_NAME

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the service name. See the M\_SERVICE\_TYPES system view for all known service names.

</td>
</tr>
<tr>
<td valign="top">

HIERARCHY

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the thread grouping information. This column contains the connection ID, the update transaction ID, and the transaction ID. The column is empty if the threads are inactive.

</td>
</tr>
<tr>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the timestamp of the record.

</td>
</tr>
<tr>
<td valign="top">

THREAD\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the thread ID.

</td>
</tr>
<tr>
<td valign="top">

THREAD\_TYPE

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the thread type.

</td>
</tr>
<tr>
<td valign="top">

THREAD\_METHOD

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the thread method.

</td>
</tr>
<tr>
<td valign="top">

THREAD\_DETAIL

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the thread detail \(truncated\).

</td>
</tr>
<tr>
<td valign="top">

THREAD\_STATE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the thread state.

</td>
</tr>
<tr>
<td valign="top">

IS\_ACTIVE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the thread is active.

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

Displays the duration of the operation in milliseconds.

</td>
</tr>
<tr>
<td valign="top">

CALLER

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the service, which called this thread.

</td>
</tr>
<tr>
<td valign="top">

CALLING

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the service, which the thread calls.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_ID

</td>
<td valign="top">

NVARCHAR\(20\)

</td>
<td valign="top">

Displays the statement ID.

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

ROOT\_STATEMENT\_ID

</td>
<td valign="top">

NVARCHAR\(20\)

</td>
<td valign="top">

Displays the ID of the root statement being executed.

</td>
</tr>
<tr>
<td valign="top">

ROOT\_STATEMENT\_HASH

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the MD5 hash value for the root statement string.

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

Displays the transaction ID.

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

Displays the write transaction ID \(this number increment\).

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

Displays the SQL user name.

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

APPLICATION\_USER\_NAME

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

APPLICATION\_SOURCE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays that the application can define which source file SAP HANA is called from. The usage is up to the application. This value is also displayed in M\_PREPARED\_STATEMENTS.APPLICATION\_SOURCE.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_COMPONENT\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Can be populated by the application to provide context for the statement execution: Displays which component type SAP HANA is called from.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_COMPONENT\_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Can be populated by the application to provide context for the statement execution: Displays which component name SAP HANA is called from.

</td>
</tr>
<tr>
<td valign="top">

CPU\_TIME\_SELF

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the active CPU time of the thread in microseconds.

</td>
</tr>
<tr>
<td valign="top">

CPU\_TIME\_CUMULATIVE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the active CPU time of the thread and any associated children in microseconds.

</td>
</tr>
<tr>
<td valign="top">

CLIENT\_IP

</td>
<td valign="top">

NVARCHAR\(45\)

</td>
<td valign="top">

Displays the IP of the client machine.

</td>
</tr>
<tr>
<td valign="top">

CLIENT\_PID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the client process ID.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_EXECUTION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the statement execution ID.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_WAIT\_COMPONENT

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the waiting time for the lock component.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_WAIT\_NAME

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the waiting time for the lock ID \(can be joined with STATISTICS\_NAME from, for example, M\_MUTEXES\).

</td>
</tr>
<tr>
<td valign="top">

LOCK\_OWNER\_THREAD\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the waiting time for the thread ID.

</td>
</tr>
<tr>
<td valign="top">

LOCKS\_OWNED

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the locks currently owned by the thread, including the lock type \(shared/exclusive\). Not all locks are monitored and show up here.

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

PASSPORT\_ROOTCONTEXT\_ID

</td>
<td valign="top">

VARBINARY\(16\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) root context ID.

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

Displays the extended passport \(EPP\) transaction ID.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_CONNECTION\_ID

</td>
<td valign="top">

VARBINARY\(16\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) connection ID.

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

PASSPORT\_COMPONENT\_NAME

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) component name.

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

Displays the extended passport \(EPP\) action.

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

NUMA\_NODE\_INDEX

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the last known NUMA node that the thread was executed on.

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

Displays the name of the workload class.

</td>
</tr>
</table>

**Related Information**  


[M\_PREPARED\_STATEMENTS System View](m-prepared-statements-system-view-20b7ea5.md "Provides information about prepared statements.")

[M\_SERVICE\_THREADS System View](m-service-threads-system-view-20c499a.md "Displays detailed information about threads created by services.")

[M\_SERVICE\_THREAD\_CALLSTACKS System View](m-service-thread-callstacks-system-view-20c47d7.md "Provides stack frame information for service threads.")

[M\_SERVICE\_TYPES System View](m-service-types-system-view-20c4d1d.md "Provides information about service types.")

