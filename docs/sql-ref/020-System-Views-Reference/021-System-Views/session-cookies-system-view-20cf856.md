<!-- loio20cf856975191014899998454833ff7c -->

# SESSION\_COOKIES System View

Shows information about available session cookies.



<a name="loio20cf856975191014899998454833ff7c___s_e_s_s_i_o_n__c_o_o_k_i_e_s_1struct_SESSION_COOKIES"/>

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

USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the user that the session cookie was created for.

</td>
</tr>
<tr>
<td valign="top">

CLIENT\_HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the host name of client machine.

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

CREATE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time that the session cookie was created.

</td>
</tr>
<tr>
<td valign="top">

LAST\_CONNECT\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last time that the session cookie was used for successful reconnection.

</td>
</tr>
<tr>
<td valign="top">

SESSION\_END\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time that the main connection ended.

</td>
</tr>
</table>



<a name="loio20cf856975191014899998454833ff7c__section_ex3_3sz_2zb"/>

## Additional Information

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[Session Management Statements](../../010-SQL-Reference/012-SQL-Statements/session-management-statements-20a27b0.md "The following SQL statements manage database sessions.")

[Session-Specific Information for Connections](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2023_4_QRC/en-US/d80b8d7ddf944f55801a534b3ce036e3.html "Set session-specific client information on SAP HANA remote source connections.") :arrow_upper_right:

[Global Session Variables](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/aaef0b96852a4e1d9ce2570bbb1493c9.html "") :arrow_upper_right:

[M\_SESSION\_CONTEXT System View](../022-Monitoring-Views/m-session-context-system-view-20c50b7.md "Displays the session variables set for each connection.")

