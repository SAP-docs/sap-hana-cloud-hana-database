<!-- loio5e357e96fd4648c887966b2830feecd5 -->

# M\_STATISTICS\_LASTVALUES System View

Provides information on last values for statistics.



## Structure


<table>
<tr>
<th valign="top">

 

</th>
<th valign="top">

 

</th>
<th valign="top">

 

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

Displays the port name.

</td>
</tr>
<tr>
<td valign="top">

NAME

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the statistic name.

</td>
</tr>
<tr>
<td valign="top">

INDEX

</td>
<td valign="top">

NVARCHAR\(1024\)

</td>
<td valign="top">

Displays the index value.

</td>
</tr>
<tr>
<td valign="top">

REACHED\_AT

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays time when the last value was captured.

</td>
</tr>
<tr>
<td valign="top">

VALUE

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the last value for the statistic.

</td>
</tr>
</table>

**Related Information**  


[LAST\_VALUE Function \(Aggregate\)](../../010-SQL-Reference/011-SQL-Functions/last-value-function-aggregate-32e95b7.md "Returns the value of the last element of an expression. This function can also be used as a window function.")

