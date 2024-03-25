<!-- loio14785819e59e4be8b78b5b927839c3f0 -->

# M\_PROCEDURE\_ASYNC\_EXECUTIONS System View

Provides status information related to the procedure called with ASYNC keyword.



<a name="loio14785819e59e4be8b78b5b927839c3f0___m__p_r_e_p_a_r_e_d__s_t_a_t_e_m_e_n_t_s_1struct_M_PREPARED_STATEMENTS"/>

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

STATEMENT\_STRING

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the called statement.

</td>
</tr>
<tr>
<td valign="top">

CALL\_CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the identifier of the connection for the call statement.

</td>
</tr>
<tr>
<td valign="top">

CALL\_TRANSACTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the transaction identifier used for the call statement.

</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the identifier of the connection for executing the procedure.

</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_TRANSACTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the transaction identifier used for the procedure execution.

</td>
</tr>
<tr>
<td valign="top">

ASYNC\_CALL\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the unique identifier of the procedure execution.

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

Displays the start time of the procedure.

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

Displays the end time of the procedure. While the procedure is running, this value is NULL.

</td>
</tr>
<tr>
<td valign="top">

ERROR\_CODE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the error code.

</td>
</tr>
<tr>
<td valign="top">

ERROR\_TEXT

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the procedure error message.

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

Displays the username.

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

Displays the application username.

</td>
</tr>
</table>

