<!-- loio20bc9a8475191014a5fbda538716ea05 -->

# M\_SAVEPOINT\_STATISTICS System View

Provides information about executed savepoints.



<a name="loio20bc9a8475191014a5fbda538716ea05___m__s_a_v_e_p_o_i_n_t__s_t_a_t_i_s_t_i_c_s_1struct_M_SAVEPOINT_STATISTICS"/>

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

Displays the persistence Volume ID.

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

Displays the number of executed savepoints.

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

Displays the start time of the last savepoint.

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

Displays the reason why the last savepoint was executed.

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

Displays the reason why the last savepoint was executed.

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

Displays the last savepoint state.

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

Displays the last savepoint version.

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

Displays the currently active configured savepoint frequency in seconds.

</td>
</tr>
<tr>
<td valign="top">

LAST\_FREQUENCY

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the actual frequency in seconds between the last two savepoints.

</td>
</tr>
<tr>
<td valign="top">

AVG\_FREQUENCY

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the actual average frequency in seconds between last two savepoints.

</td>
</tr>
<tr>
<td valign="top">

LAST\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total time spent in microseconds creating the last savepoint.

</td>
</tr>
<tr>
<td valign="top">

AVG\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time spent in microseconds creating the last two savepoints.

</td>
</tr>
<tr>
<td valign="top">

LAST\_BLOCKING\_PHASE\_START\_TIME

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

LAST\_BLOCKING\_PHASE\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the duration in seconds of the last blocking phase.

</td>
</tr>
<tr>
<td valign="top">

LAST\_CRITICAL\_PHASE\_START\_TIME

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

LAST\_CRITICAL\_PHASE\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the time spent in microseconds in the last critical phase, during which updates are blocked.

</td>
</tr>
<tr>
<td valign="top">

AVG\_CRITICAL\_PHASE\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time spent in microseconds for the last two critical phases, during which updates are blocked.

</td>
</tr>
<tr>
<td valign="top">

LAST\_TOTAL\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of bytes written for the last savepoint.

</td>
</tr>
<tr>
<td valign="top">

AVG\_TOTAL\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average number of bytes written for a savepoint.

</td>
</tr>
<tr>
<td valign="top">

LAST\_FLUSHED\_PAGES

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last number of asynchronously flushed pages.

</td>
</tr>
<tr>
<td valign="top">

AVG\_FLUSHED\_PAGES

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the average number of asynchronously flushed pages.

</td>
</tr>
<tr>
<td valign="top">

LAST\_FLUSHED\_PAGES\_IN\_CRITICAL\_PHASE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last number of pages flushed in the critical phase.

</td>
</tr>
<tr>
<td valign="top">

AVG\_FLUSHED\_PAGES\_IN\_CRITICAL\_PHASE

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the average number of pages flushed in the critical phase.

</td>
</tr>
<tr>
<td valign="top">

LAST\_FLUSHED\_ROWSTORE\_PAGES

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last number of asynchronously flushed row store pages.

</td>
</tr>
<tr>
<td valign="top">

AVG\_FLUSHED\_ROWSTORE\_PAGES

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the average number of asynchronously flushed row store pages.

</td>
</tr>
<tr>
<td valign="top">

LAST\_FLUSHED\_ROWSTORE\_PAGES\_IN\_CRITICAL\_PHASE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last number of row store pages flushed in the critical phase.

</td>
</tr>
<tr>
<td valign="top">

AVG\_FLUSHED\_ROWSTORE\_PAGES\_IN\_CRITICAL\_PHASE

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the average number of row store pages flushed in the critical phase.

</td>
</tr>
<tr>
<td valign="top">

LAST\_FLUSHED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size in bytes of the last asynchronously flushed pages.

</td>
</tr>
<tr>
<td valign="top">

AVG\_FLUSHED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average size in bytes of asynchronously flushed pages.

</td>
</tr>
<tr>
<td valign="top">

LAST\_FLUSHED\_SIZE\_IN\_CRITICAL\_PHASE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size in bytes of the last pages flushed in the critical phase.

</td>
</tr>
<tr>
<td valign="top">

AVG\_FLUSHED\_SIZE\_IN\_CRITICAL\_PHASE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average size of pages flushed in the critical phase.

</td>
</tr>
<tr>
<td valign="top">

LAST\_FLUSHED\_ROWSTORE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size in bytes of the last asynchronously flushed row store pages.

</td>
</tr>
<tr>
<td valign="top">

AVG\_FLUSHED\_ROWSTORE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average size in bytes of the asynchronously flushed row store pages.

</td>
</tr>
<tr>
<td valign="top">

LAST\_FLUSHED\_ROWSTORE\_SIZE\_IN\_CRITICAL\_PHASE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size in bytes of the last row store pages flushed in the critical phase.

</td>
</tr>
<tr>
<td valign="top">

AVG\_FLUSHED\_ROWSTORE\_SIZE\_IN\_CRITICAL\_PHASE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average size in bytes of the row store pages flushed in the critical phase.

</td>
</tr>
<tr>
<td valign="top">

LAST\_RTT\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size in bytes of the rollback transaction table at last savepoint. This may be less than the sum of components if there are duplicate TIDs.

</td>
</tr>
</table>



<a name="loio20bc9a8475191014a5fbda538716ea05___m__s_a_v_e_p_o_i_n_t__s_t_a_t_i_s_t_i_c_s_1fulldesc_M_SAVEPOINT_STATISTICS"/>

## Additional Information

This view shows information about executed savepoints, and is associated with the ALTER SYSTEM SAVEPOINT statement.

The ***START\_TIME***, ***STATE***, ***VERSION***, and ***LAST\_\**** columns relate to the last executed or currently executing savepoint. Other columns contain aggregated values. Refer to the M\_SAVEPOINTS system view for further information about various counters.

This view has a resettable counterpart; you can see the values since the last reset in the M\_SAVEPOINT\_STATISTICS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_SAVEPOINT_STATISTICS_RESET;`.

**Related Information**  


[M\_SAVEPOINT\_STATISTICS\_RESET System View](m-savepoint-statistics-reset-system-view-20bcc12.md "Provides the savepoint statistics since the last reset.")

[M\_SAVEPOINTS System View](m-savepoints-system-view-20bdd30.md "Displays current and historical savepoint statistics.")

[ALTER SYSTEM SAVEPOINT Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-savepoint-statement-system-management-20d2b6e.md "Executes a database checkpoint on the persistence manager.")

[ROLLBACK TO SAVEPOINT Statement \(Transaction Management\)](../../010-SQL-Reference/012-SQL-Statements/rollback-to-savepoint-statement-transaction-management-104ae26.md "Rolls back a transaction to the named savepoint without terminating the transaction.")

[RELEASE SAVEPOINT Statement \(Transaction Management\)](../../010-SQL-Reference/012-SQL-Statements/release-savepoint-statement-transaction-management-445eb4d.md "Releases a specified savepoint name.")

[SAVEPOINT](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/e933397e9ec84f439f25962f4e193063.html "") :arrow_upper_right:

