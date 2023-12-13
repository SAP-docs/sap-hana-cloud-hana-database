<!-- loio9fb8ca5e417d4277a1987e16c5318b6d -->

# M\_SQLSCRIPT\_VARIABLE\_CACHE System view

Provides runtime information about procedures and functions that have variable caches defined.



<a name="loio9fb8ca5e417d4277a1987e16c5318b6d___q_u_e_r_y__p_l_a_n_s_1struct_QUERY_PLANS"/>

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

Displays the host address of the node on which the cached data is located.

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

Displays the port number of the node on which the cached data is located.

</td>
</tr>
<tr>
<td valign="top">

SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema of the target object.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the target object name.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the target object type: PROCEDURE/FUNCTION.

</td>
</tr>
<tr>
<td valign="top">

VARIABLE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the variable to be cached.

</td>
</tr>
<tr>
<td valign="top">

VARIABLE\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the type of variable.

</td>
</tr>
<tr>
<td valign="top">

SQLSCRIPT\_PLAN\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the ID of the execution plan.

</td>
</tr>
<tr>
<td valign="top">

SQLSCRIPT\_OPERATOR\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the ID of the execution plan operator.

</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the memory size of the cached data in bytes.

</td>
</tr>
<tr>
<td valign="top">

LAST\_CACHE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the date and time when the latest cached data was generated.

</td>
</tr>
</table>

**Related Information**  


[SQLSCRIPT\_VARIABLE\_CACHE System view](../021-System-Views/sqlscript-variable-cache-system-view-a7eeeed.md "Provides information about procedures and functions that have variable caches defined.")

[ALTER SYSTEM CLEAR CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-cache-statement-system-management-141ad67.md "Clears resources (entries) from one or more cache instances.")

