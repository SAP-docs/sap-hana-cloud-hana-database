<!-- loiod2188bf0d295101480fffb8a1bfb6161 -->

# M\_SQL\_CLIENT\_NETWORK\_IO System View

Provides the client and server elapsed time as well as message sizes for client network messages.



<a name="loiod2188bf0d295101480fffb8a1bfb6161___m__s_q_l__c_l_i_e_n_t__n_e_t_w_o_r_k__i_o_1struct_M_SQL_CLIENT_NETWORK_IO"/>

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

CLIENT\_HOST



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the host of the client machine, also found in M\_CONNECTIONS.CLIENT\_HOST.



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

Displays the connection ID of the physical server connection.



</td>
</tr>
<tr>
<td valign="top">

MESSAGE\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the client message ID on the physical server connection.



</td>
</tr>
<tr>
<td valign="top">

CLIENT\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the elapsed time on the client side including send, server execution, and receive.



</td>
</tr>
<tr>
<td valign="top">

SERVER\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the execution time on the server side. Transport time is the delta between CLIENT\_DURATION and SERVER\_DURATION.



</td>
</tr>
<tr>
<td valign="top">

SERVER\_RECEIVED\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the time when the message was received on the server side and begin of execution.



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

Displays the size of messages received on the server side in bytes.



</td>
</tr>
<tr>
<td valign="top">

SEND\_MESSAGE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size of the messages sent to the client side in bytes.



</td>
</tr>
</table>



<a name="loiod2188bf0d295101480fffb8a1bfb6161__section_ir1_4rb_k1b"/>

## Additional Information

By default, collection of statistics related to client network I/O is controlled by the sql\_client\_network\_io parameter in the `indexserver.ini` configuration file.

**Related Information**  


[M\_CONNECTIONS System View](m-connections-system-view-20abcf1.md "Provides detailed information on connections between a client and a database. Information includes: connection status, client information, connection type, and resource utilization.")

