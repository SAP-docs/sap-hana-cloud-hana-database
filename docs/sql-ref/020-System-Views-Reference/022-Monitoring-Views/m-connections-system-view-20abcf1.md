<!-- loio20abcf1f75191014a254a82b3d0f66bf -->

# M\_CONNECTIONS System View

Provides detailed information on connections between a client and a database. Information includes: connection status, client information, connection type, and resource utilization.



<a name="loio20abcf1f75191014a254a82b3d0f66bf___m__c_o_n_n_e_c_t_i_o_n_s_1struct_M_CONNECTIONS"/>

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

START\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the connected time.

</td>
</tr>
<tr>
<td valign="top">

IDLE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the time that the connection is unused and idle in milliseconds.

</td>
</tr>
<tr>
<td valign="top">

CONNECTION\_STATUS

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the connection status:


<dl>
<dt><b>

RUNNING

</b></dt>
<dd>

A statement is executing.



</dd><dt><b>

IDLE

</b></dt>
<dd>

No statements are currently executing on this connection.



</dd><dt><b>

QUEUEING

</b></dt>
<dd>

The connection is currently queued. The status changes to RUNNING when it is dequeued \(this depends on the system's resource consumption\).



</dd><dt><b>

EMPTY

</b></dt>
<dd>

A historic connection that is removed after 1 hour. The removal time can be configured in `indexserver.ini [session] connection_history_lifetime = 60 # minutes`.



</dd>
</dl>



</td>
</tr>
<tr>
<td valign="top">

CLIENT\_HOST

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the host name of client machine.

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

Displays the IP of client machine.

</td>
</tr>
<tr>
<td valign="top">

CLIENT\_PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the client's communication port number.

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

USER\_NAME

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

CONNECTION\_TYPE

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the connection type. Connection types include: Remote, Local, History \(remote\), and History \(local\).

</td>
</tr>
<tr>
<td valign="top">

OWN

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays the user's own connection. Returns TRUE if it is your own connection and FALSE if it is not.

</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE\_PER\_CONNECTION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the allocated memory size per connection in bytes.

</td>
</tr>
<tr>
<td valign="top">

AUTO\_COMMIT

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays the commit mode of the current transaction. Returns TRUE if the current connection is in auto-commit mode and FALSE if it is not.

</td>
</tr>
<tr>
<td valign="top">

LAST\_ACTION

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the last action completed by the current connection. Actions include: ExecuteGroup, CommitTrans, AbortTrans, PrepareStatement, CloseStatement, ExecutePrepared, ExecuteStatement, FetchCursor, CloseCursor, LobGetPiece, LogPutPiece, LobFind, Authenticate, Connect, Disconnect, ExecQidItab, CursorFetchItab, InsertIncompleteItab, AbapStream, TxStartXA, and TxJoinXA.

</td>
</tr>
<tr>
<td valign="top">

CURRENT\_STATEMENT\_ID

</td>
<td valign="top">

NVARCHAR\(20\)

</td>
<td valign="top">

Displays the current statement ID.

</td>
</tr>
<tr>
<td valign="top">

CURRENT\_OPERATOR\_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the current operator name.

</td>
</tr>
<tr>
<td valign="top">

FETCHED\_RECORD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the sum of the record count fetched by select statements.

</td>
</tr>
<tr>
<td valign="top">

AFFECTED\_RECORD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the sum of the record count affected by DML/DDL statements, for example:

```
INSERT/UPDATE/DELETE/REPLACE/CREATE TABLE ... LIKE ... WITH DATA/CREATE TABLE ... AS (SELECT ..)/IMPORT/EXPORT
```



</td>
</tr>
<tr>
<td valign="top">

SENT\_MESSAGE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size of messages sent by the current connection in bytes.

</td>
</tr>
<tr>
<td valign="top">

SENT\_MESSAGE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total message count sent by the current connection.

</td>
</tr>
<tr>
<td valign="top">

RECEIVED\_MESSAGE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size of messages received by the current connection in bytes.

</td>
</tr>
<tr>
<td valign="top">

RECEIVED\_MESSAGE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total message count received by the current connection.

</td>
</tr>
<tr>
<td valign="top">

CREATOR\_THREAD\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the thread ID that created the current connection.

</td>
</tr>
<tr>
<td valign="top">

CREATED\_BY

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the engine component that created the connections. These include: Session, Planning, Repository, CalcEngine, Authentication, Table Exporter, Loader, LLVM, JSVM, IMS Search API, OLAP Engine, Mergedog, Ping Status, Name Server, Queue Server, SQL Stored Procedure, Authorization, TrexViaDbsl from ABAP, HybridTable Reorganizer, and Session external.

</td>
</tr>
<tr>
<td valign="top">

IS\_ENCRYPTED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the connection is encrypted with secure communication enabled \(SSL enabled\): TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

SSL\_VERSION

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the SSL/TLS protocol version.

The result is empty if the connection does not use SSL \(IS\_ENCRYTED\) or if the SSL\_VERSION contains the used SSL protocol version.

</td>
</tr>
<tr>
<td valign="top">

SSL\_CIPHER

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the SSL cipher used for the connection.

The result is empty if SSL\_CIPHER contains the used ciphersuite.

</td>
</tr>
<tr>
<td valign="top">

HAS\_SSL\_CLIENT\_CERTIFICATE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether mutual authentication is enabled: TRUE/FALSE. TRUE indicates that the secure communication is enabled \(SSL enabled\) and the certificate of the client is validated. If not, FALSE is returned.

</td>
</tr>
<tr>
<td valign="top">

AUTHENTICATION\_METHOD

</td>
<td valign="top">

NVARCHAR\(48\)

</td>
<td valign="top">

Displays the name of the authentication method used to authenticate the connection.

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
<tr>
<td valign="top">

PARENT\_CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the parent connection ID.

</td>
</tr>
<tr>
<td valign="top">

CLIENT\_DISTRIBUTION\_MODE

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the client distribution mode of the current connection \(for example, \[distribution\] client\_distribution\_mode\).

</td>
</tr>
<tr>
<td valign="top">

LOGICAL\_CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the logical connection ID in statement routing.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_SITE\_LOGICAL\_CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the logical connection ID of the origin site.

</td>
</tr>
<tr>
<td valign="top">

CURRENT\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the current schema name.

</td>
</tr>
<tr>
<td valign="top">

CURRENT\_THREAD\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current executing thread ID.

</td>
</tr>
<tr>
<td valign="top">

PRIORITY

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Displays the user-specified priority.

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

CURRENT\_COLLATION\_NAME

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the name of the current collation.

</td>
</tr>
<tr>
<td valign="top">

CLOSE\_REASON

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the reason for the connection close.

</td>
</tr>
<tr>
<td valign="top">

PROXY\_IP

</td>
<td valign="top">

NVARCHAR\(45\)

</td>
<td valign="top">

Displays the IP of the reverse proxy.

</td>
</tr>
<tr>
<td valign="top">

PROXY\_PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the communication port number of the reverse proxy.

</td>
</tr>
<tr>
<td valign="top">

CLIENT\_TYPE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the client interface name.

</td>
</tr>
<tr>
<td valign="top">

CLIENT\_VERSION

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the client version number.

</td>
</tr>
<tr>
<td valign="top">

CLIENT\_APPLICATION

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the client program name.

</td>
</tr>
</table>



<a name="loio20abcf1f75191014a254a82b3d0f66bf__section_ary_y55_tbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_CONNECTION\_STATISTICS System View](m-connection-statistics-system-view-20ab928.md "Provides detailed statistics on each connection between an application and database.")

[CONNECT Statement \(Session Management\)](../../010-SQL-Reference/012-SQL-Statements/connect-statement-session-management-20d3b9a.md "Connects to a database instance.")

[HOST_CONNECTIONS View (Embedded Statistics Service)](https://help.sap.com/viewer/323c57a017234d47a0e7da3e22345822/2024_3_QRC/en-US/96a0a52b735c4fb9a450c6464eb544ae.html "Displays detailed information about connections between the client and the database.") :arrow_upper_right:

[Session-Specific Information for Connections](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_3_QRC/en-US/d80b8d7ddf944f55801a534b3ce036e3.html "Set session-specific client information on SAP HANA remote source connections.") :arrow_upper_right:

