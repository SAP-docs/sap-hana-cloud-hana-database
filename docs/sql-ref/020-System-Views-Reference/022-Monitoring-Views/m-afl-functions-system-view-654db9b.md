<!-- loio654db9b1c0874a2ba417add5a58fb848 -->

# M\_AFL\_FUNCTIONS System View

Provides application function execution information.



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

AREA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the area of the function.



</td>
</tr>
<tr>
<td valign="top">

FUNCTION\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the function.



</td>
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

EXECUTION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of executions.



</td>
</tr>
<tr>
<td valign="top">

LAST\_EXECUTION\_TIMESTAMP



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the timestamp of the last execution.



</td>
</tr>
</table>

**Related Information**  


[AFL\_FUNCTIONS System View](../021-System-Views/afl-functions-system-view-209d7b2.md "Provides information about available AFL functions.")

[AFL\_FUNCTION\_PARAMETERS System View](../021-System-Views/afl-function-parameters-system-view-d1fce26.md "Provides information about parameters of AFL functions.")

[AFL\_FUNCTION\_PROPERTIES System View](../021-System-Views/afl-function-properties-system-view-209d4b7.md "Provides information about available AFL function properties.")

[AFL\_TEXTS System View](../021-System-Views/afl-texts-system-view-d1fd8aa.md "Provides information about available AFL texts.")

[AFL\_PACKAGES System View](../021-System-Views/afl-packages-system-view-209dae2.md "Provides information about available AFL packages.")

[M\_AFL\_STATES System View](m-afl-states-system-view-3769f7f.md "Provides information about AFL states.")

