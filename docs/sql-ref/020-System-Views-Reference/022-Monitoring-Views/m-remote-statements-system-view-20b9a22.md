<!-- loio20b9a2217519101483f6949244f55513 -->

# M\_REMOTE\_STATEMENTS System View

Displays detailed information about executed remote queries. This information includes the query status and the number of fetched rows.



<a name="loio20b9a2217519101483f6949244f55513___m__r_e_m_o_t_e__s_t_a_t_e_m_e_n_t_s_1struct_M_REMOTE_STATEMENTS"/>

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

Displays the statement ID.

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

Displays the MD5 hash value for STATEMENT\_STRING.

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

Displays the root statement ID.

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

Displays the MD5 hash value for ROOT\_STATEMENT\_STRING.

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

Displays the execution ID of statement.

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_CONNECTION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the remote connection ID.

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_SOURCE\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the remote source schema name.

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_SOURCE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the remote source name.

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

END\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time when the statement was closed.

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

Displays the number of fetched records.

</td>
</tr>
<tr>
<td valign="top">

FETCHED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the byte size of fetched records.

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the duration, in milliseconds, of the total remote request \(open/fetch/close\).

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_FETCH\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total remote request fetch duration.

</td>
</tr>
<tr>
<td valign="top">

NETWORK\_SENT\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the network sent bytes.

</td>
</tr>
<tr>
<td valign="top">

NETWORK\_RECEIVED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the network received bytes.

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_SERVER\_PROCESSING\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the remote server processing time in milliseconds.

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_SERVER\_CPU\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the remote server CPU time.

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_SERVER\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the remote server peak memory size in bytes.

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_STATEMENT\_STATUS

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the status of the statement. Valid entries are: EXECUTING and CLOSED.

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_STATEMENT\_STRING

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

REMOTE\_STATEMENT\_DETAILS

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays statement details.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_ROOTCONTEXT\_ID

</td>
<td valign="top">

VARBINARY

</td>
<td valign="top">

Displays the root context ID of outbound passport.

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

Displays the transaction ID of outbound passport.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_CONNECTION\_ID

</td>
<td valign="top">

VARBINARY

</td>
<td valign="top">

Displays the connection ID of outbound passport.

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

Displays the connection counter of outbound passport.

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

Displays the component name of outbound passport.

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

Displays the component type of outbound passport.

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

Displays the action of outbound passport.

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

Displays the action type of outbound passport.

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

Displays the previous component name of outbound passport.

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

Displays the service of outbound passport.

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

Displays the user ID of outbound passport.

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

Displays the client of outbound passport.

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

Displays the trace flags of outbound passport.

</td>
</tr>
</table>

**Related Information**  


[CREATE REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-remote-source-statement-access-control-20d4834.md "Defines an external data source that can connect to the SAP HANA database.")

[ALTER REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-remote-source-statement-access-control-f423eb4.md "Modifies the configuration of an external data source that is connected to an SAP HANA database.")

[DROP REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-remote-source-statement-access-control-20d7332.md "Removes an existing remote source.")

