<!-- loiofa7c9f31eecf45e3bdaa3879784bcd76 -->

# M\_SERVICE\_NETWORK\_METHOD\_IO System View

Displays the number of calls and amount of data that is sent and received.



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

SENDER\_HOST



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the host name of the sender.



</td>
</tr>
<tr>
<td valign="top">

SENDER\_PORT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the host port number of the sender.



</td>
</tr>
<tr>
<td valign="top">

RECEIVER\_HOST



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the host name of the receiver.



</td>
</tr>
<tr>
<td valign="top">

RECEIVER\_PORT



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the host port number of the receiver.



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

Displays the originating method name.



</td>
</tr>
<tr>
<td valign="top">

OPERATOR



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays additional details.



</td>
</tr>
<tr>
<td valign="top">

REQUEST\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total number of requests for the method.



</td>
</tr>
<tr>
<td valign="top">

SEND\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total number of bytes sent.



</td>
</tr>
<tr>
<td valign="top">

RECEIVE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total number of bytes received.



</td>
</tr>
<tr>
<td valign="top">

LAST\_UPDATE\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the last updated timestamp.



</td>
</tr>
</table>

**Related Information**  


[M\_SERVICE\_NETWORK\_METHOD\_IO\_RESET System View](m-service-network-method-io-reset-system-view-5b63005.md "Provides service network method I/O statistics since the last reset.")

