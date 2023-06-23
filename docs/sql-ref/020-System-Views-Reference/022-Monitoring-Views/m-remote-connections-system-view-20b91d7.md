<!-- loio20b91d7375191014940dedfed99e278f -->

# M\_REMOTE\_CONNECTIONS System View

Provides detailed information on remote connections between databases and remote sources. The information includes connection status, adapter name, and adapter properties.



<a name="loio20b91d7375191014940dedfed99e278f___m__r_e_m_o_t_e__c_o_n_n_e_c_t_i_o_n_s_1struct_M_REMOTE_CONNECTIONS"/>

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

ADAPTER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the adapter name.



</td>
</tr>
<tr>
<td valign="top">

REMOTE\_SOURCE\_USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the remote source user name.



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

CONNECTION\_STATUS



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the connection status: CONNECTED/DISCONNECTED.



</td>
</tr>
<tr>
<td valign="top">

DETAILS



</td>
<td valign="top">

NVARCHAR\(512\)



</td>
<td valign="top">

Displays the adapter properties.



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

Displays the number of executed statements.



</td>
</tr>
</table>

**Related Information**  


[M\_CONNECTIONS System View](m-connections-system-view-20abcf1.md "Provides detailed information on connections between a client and a database. Information includes: connection status, client information, connection type, and resource utilization.")

[CONNECT Statement \(Session Management\)](../../010-SQL-Reference/012-SQL-Statements/connect-statement-session-management-20d3b9a.md "Connects to a database instance.")

