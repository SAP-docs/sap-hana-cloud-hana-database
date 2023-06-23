<!-- loio72c83485ea814b9abca5a02f5096e474 -->

# M\_REPLICATION\_LOG System View

Provides replication log monitoring information.



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

Displays the host.



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

VOLUME\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the volume ID.



</td>
</tr>
<tr>
<td valign="top">

IS\_ENABLED



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays TRUE when the replication logs are being collected and FALSE when collecting replication logs is disabled.



</td>
</tr>
<tr>
<td valign="top">

LAST\_DISABLE\_REASON



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the latest disable reason: REPLICATION\_LOG\_SPACE FULL/USER\_COMMAND.



</td>
</tr>
<tr>
<td valign="top">

USED\_REPLICATION\_LOG\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the used replication log size in the volume in bytes.



</td>
</tr>
<tr>
<td valign="top">

MAX\_REPLICATION\_LOG\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the limitation of the replication log size in the volume in bytes.



</td>
</tr>
</table>

**Related Information**  


[LOG Function \(Numeric\)](../../010-SQL-Reference/011-SQL-Functions/log-function-numeric-20e3d2f.md "Returns the natural logarithm of a specified number and base.")

