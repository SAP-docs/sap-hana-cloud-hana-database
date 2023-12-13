<!-- loio20c50b73751910148ae9d5b996ff1e84 -->

# M\_SESSION\_CONTEXT System View

Displays the session variables set for each connection.



<a name="loio20c50b73751910148ae9d5b996ff1e84___m__s_e_s_s_i_o_n__c_o_n_t_e_x_t_1struct_M_SESSION_CONTEXT"/>

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

KEY

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the key name of a session context variable.

</td>
</tr>
<tr>
<td valign="top">

VALUE

</td>
<td valign="top">

NVARCHAR\(512\)

</td>
<td valign="top">

Displays the value of a session context variable.

</td>
</tr>
<tr>
<td valign="top">

SECTION

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays the section name to distinguish system and user variables:

-   USER=application defined variable using SET command or client API call.
-   SYSTEM=predefined variable or server property.



</td>
</tr>
</table>



<a name="loio20c50b73751910148ae9d5b996ff1e84___m__s_e_s_s_i_o_n__c_o_n_t_e_x_t_1fulldesc_M_SESSION_CONTEXT"/>

## Additional Information

Execute the following statement to view the assigned session variables for the current connection:

```
SELECT * FROM M_SESSION_CONTEXT WHERE connection_id=current_connection;
```

**Related Information**  


[SET \[SESSION\] Statement \(Session Management\)](../../010-SQL-Reference/012-SQL-Statements/set-session-statement-session-management-20fd82b.md "Sets a session variable for the current session.")

[SESSION\_CONTEXT Function \(Miscellaneous\)](../../010-SQL-Reference/011-SQL-Functions/session-context-function-miscellaneous-20e74dc.md "Returns the value of the specified session variable assigned to the current user.")

[Session Variables](../../010-SQL-Reference/session-variables-a16678c.md " 		 		 		 		 		 		 	")

[Session Management Statements](../../010-SQL-Reference/012-SQL-Statements/session-management-statements-20a27b0.md "The following SQL statements manage database sessions.")

