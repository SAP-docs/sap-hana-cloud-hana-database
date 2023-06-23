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

REMOTE\_CONNECTION\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the ID of the remote connection.



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

Displays the statement end time.



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

REMOTE\_STATEMENT\_STATUS



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the statement status: EXECUTING/CLOSED.



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

Displays the statement string, to a maximum of 64K of text.



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

Displays the statement details.



</td>
</tr>
</table>

**Related Information**  


[CREATE REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-remote-source-statement-access-control-20d4834.md "Defines an external data source that can connect to the SAP HANA database.")

[ALTER REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-remote-source-statement-access-control-f423eb4.md "Modifies the configuration of an external data source that is connected to an SAP HANA database.")

[DROP REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-remote-source-statement-access-control-20d7332.md "Removes an existing remote source.")

