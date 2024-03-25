<!-- loio20ab928875191014acedd7d1c3eaecaa -->

# M\_CONNECTION\_STATISTICS System View

Provides detailed statistics on each connection between an application and database.



<a name="loio20ab928875191014acedd7d1c3eaecaa___m__c_o_n_n_e_c_t_i_o_n__s_t_a_t_i_s_t_i_c_s_1struct_M_CONNECTION_STATISTICS"/>

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

SELECT\_EXECUTION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of select statement executions.

</td>
</tr>
<tr>
<td valign="top">

SELECT\_TOTAL\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total execution time of select statement executions.

</td>
</tr>
<tr>
<td valign="top">

SELECT\_AVG\_EXECUTION\_TIME

</td>
<td valign="top">

REAL

</td>
<td valign="top">

Displays the average execution time of select statement executions.

</td>
</tr>
<tr>
<td valign="top">

SELECT\_MAX\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum execution time of select statement executions.

</td>
</tr>
<tr>
<td valign="top">

SELECT\_FOR\_UPDATE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of select for update executions.

</td>
</tr>
<tr>
<td valign="top">

SELECT\_FOR\_UPDATE\_TOTAL\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total execution time of select for update executions.

</td>
</tr>
<tr>
<td valign="top">

SELECT\_FOR\_UPDATE\_AVG\_EXECUTION\_TIME

</td>
<td valign="top">

REAL

</td>
<td valign="top">

Displays the average execution time of select for update executions.

</td>
</tr>
<tr>
<td valign="top">

SELECT\_FOR\_UPDATE\_MAX\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum execution time of select for update execution.

</td>
</tr>
<tr>
<td valign="top">

SELECT\_FOR\_UPDATE\_LOCK\_WAIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of lock waits during select for update.

</td>
</tr>
<tr>
<td valign="top">

SELECT\_FOR\_UPDATE\_TOTAL\_LOCK\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total lock wait time during select for update.

</td>
</tr>
<tr>
<td valign="top">

SELECT\_FOR\_UPDATE\_AVG\_LOCK\_WAIT\_TIME

</td>
<td valign="top">

REAL

</td>
<td valign="top">

Displays the average lock wait time during select for update.

</td>
</tr>
<tr>
<td valign="top">

SELECT\_FOR\_UPDATE\_MAX\_LOCK\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum lock wait time during select for update.

</td>
</tr>
<tr>
<td valign="top">

UPDATE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of update statement and insert statement executions.

</td>
</tr>
<tr>
<td valign="top">

UPDATE\_TOTAL\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total execution time of update statement executions in microseconds.

</td>
</tr>
<tr>
<td valign="top">

UPDATE\_AVG\_EXECUTION\_TIME

</td>
<td valign="top">

REAL

</td>
<td valign="top">

Displays the average execution time of update statement executions in microseconds.

</td>
</tr>
<tr>
<td valign="top">

UPDATE\_MAX\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum execution time of update statement executions in microseconds.

</td>
</tr>
<tr>
<td valign="top">

UPDATE\_LOCK\_WAIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of lock waits during update statement executions.

</td>
</tr>
<tr>
<td valign="top">

UPDATE\_TOTAL\_LOCK\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total lock wait execution time during update statement executions in microseconds.

</td>
</tr>
<tr>
<td valign="top">

UPDATE\_AVG\_LOCK\_WAIT\_TIME

</td>
<td valign="top">

REAL

</td>
<td valign="top">

Displays the average lock wait time during update statement executions in microseconds.

</td>
</tr>
<tr>
<td valign="top">

UPDATE\_MAX\_LOCK\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum lock wait time during update statement executions in microseconds.

</td>
</tr>
<tr>
<td valign="top">

READ\_ONLY\_TRANSACTION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of read only transactions.

</td>
</tr>
<tr>
<td valign="top">

READ\_ONLY\_TRANSACTION\_TOTAL\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total execution time of read only transactions in microseconds.

</td>
</tr>
<tr>
<td valign="top">

READ\_ONLY\_TRANSACTION\_AVG\_EXECUTION\_TIME

</td>
<td valign="top">

REAL

</td>
<td valign="top">

Displays the average execution time of read only transactions in microseconds.

</td>
</tr>
<tr>
<td valign="top">

READ\_ONLY\_TRANSACTION\_MAX\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum execution time of read only transactions.

</td>
</tr>
<tr>
<td valign="top">

UPDATE\_TRANSACTION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of update transactions.

</td>
</tr>
<tr>
<td valign="top">

UPDATE\_TRANSACTION\_TOTAL\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total execution time of update transactions.

</td>
</tr>
<tr>
<td valign="top">

UPDATE\_TRANSACTION\_AVG\_EXECUTION\_TIME

</td>
<td valign="top">

REAL

</td>
<td valign="top">

Displays the average execution time of update transactions.

</td>
</tr>
<tr>
<td valign="top">

UPDATE\_TRANSACTION\_MAX\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum execution time of update transactions.

</td>
</tr>
<tr>
<td valign="top">

ROLLBACK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of rolled backed transactions.

</td>
</tr>
<tr>
<td valign="top">

ROLLBACK\_TOTAL\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total execution time of rollbacks.

</td>
</tr>
<tr>
<td valign="top">

ROLLBACK\_AVG\_EXECUTION\_TIME

</td>
<td valign="top">

REAL

</td>
<td valign="top">

Displays the average execution time of rollbacks.

</td>
</tr>
<tr>
<td valign="top">

ROLLBACK\_MAX\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum execution time of rollbacks.

</td>
</tr>
<tr>
<td valign="top">

OTHERS\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of other statement executions including data definition statements and data control statements.

</td>
</tr>
<tr>
<td valign="top">

OTHERS\_TOTAL\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total execution time of other statements.

</td>
</tr>
<tr>
<td valign="top">

OTHERS\_AVG\_EXECUTION\_TIME

</td>
<td valign="top">

REAL

</td>
<td valign="top">

Displays the average execution time of other statements.

</td>
</tr>
<tr>
<td valign="top">

OTHERS\_MAX\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum execution time of other statements.

</td>
</tr>
<tr>
<td valign="top">

OTHERS\_LOCK\_WAIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total lock wait count of other statements.

</td>
</tr>
<tr>
<td valign="top">

OTHERS\_TOTAL\_LOCK\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total lock wait time of other statements.

</td>
</tr>
<tr>
<td valign="top">

OTHERS\_AVG\_LOCK\_WAIT\_TIME

</td>
<td valign="top">

REAL

</td>
<td valign="top">

Displays the average lock wait time of other statements.

</td>
</tr>
<tr>
<td valign="top">

OTHERS\_MAX\_LOCK\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum lock wait time of other statements.

</td>
</tr>
<tr>
<td valign="top">

LAST\_EXECUTED\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last execution timestamp with this connection.

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

Displays the average memory size used during each execution in bytes.

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

Displays the maximum memory size used during each execution in bytes.

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

Displays the minimum memory size used during each execution in bytes.

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

Displays the sum of the memory size used during each execution in bytes.

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

Displays the average time of the statement preparation.

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

Displays the maximum time of the statement preparation.

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

Displays the minimum time of the statement preparation.

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

Displays the total time of the statement preparation.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_PREPARATION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total count of statement preparation.

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

Displays the execution count by the client routed connection in statement routing.

</td>
</tr>
<tr>
<td valign="top">

COMMIT\_MAX\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum time of the commit execution.

</td>
</tr>
<tr>
<td valign="top">

COMMIT\_AVG\_EXECUTION\_TIME

</td>
<td valign="top">

REAL

</td>
<td valign="top">

Displays the average time of the commit execution.

</td>
</tr>
<tr>
<td valign="top">

COMMIT\_TOTAL\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total time of the commit duration.

</td>
</tr>
<tr>
<td valign="top">

COMMIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the completed commit count.

</td>
</tr>
<tr>
<td valign="top">

END\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time when the connection is closed for history connections.

</td>
</tr>
</table>

**Related Information**  


[M\_CONNECTIONS System View](m-connections-system-view-20abcf1.md "Provides detailed information on connections between a client and a database. Information includes: connection status, client information, connection type, and resource utilization.")

[CONNECT Statement \(Session Management\)](../../010-SQL-Reference/012-SQL-Statements/connect-statement-session-management-20d3b9a.md "Connects to a database instance.")

[HOST_CONNECTIONS View (Embedded Statistics Service)](https://help.sap.com/viewer/323c57a017234d47a0e7da3e22345822/2024_1_QRC/en-US/96a0a52b735c4fb9a450c6464eb544ae.html "Displays detailed information about connections between the client and the database.") :arrow_upper_right:

[Session-Specific Information for Connections](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/d80b8d7ddf944f55801a534b3ce036e3.html "Set session-specific client information on SAP HANA remote source connections.") :arrow_upper_right:

