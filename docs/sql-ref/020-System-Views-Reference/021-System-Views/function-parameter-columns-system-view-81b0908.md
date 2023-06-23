<!-- loio81b0908978894baba15a7f1cfea27bb0 -->

# FUNCTION\_PARAMETER\_COLUMNS System View

Provides information about columns that are available for function table parameters.



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

SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name of the function.



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

FUNCTION\_OID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the object ID of the function.



</td>
</tr>
<tr>
<td valign="top">

PARAMETER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the parameter name.



</td>
</tr>
<tr>
<td valign="top">

PARAMETER\_POSITION



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the ordinal position of the parameter.



</td>
</tr>
<tr>
<td valign="top">

COLUMN\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the column in the table parameter.



</td>
</tr>
<tr>
<td valign="top">

POSITION



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the ordinal position of the column in the table parameter.



</td>
</tr>
<tr>
<td valign="top">

DATA\_TYPE\_NAME



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the SQL data type name of the column.



</td>
</tr>
<tr>
<td valign="top">

LENGTH



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Depending on the data type:

-   Displays the number of characters for characters types
-   Displays the maximum number of digits for numeric types
-   Displays the number of characters for datetime types
-   Displays the number of bytes for LOB types



</td>
</tr>
<tr>
<td valign="top">

SCALE



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

For numeric data types, displays the maximum number of digits to the right of the decimal point. For time and timestamp data types, Displays the decimal digits, which are defined as the number of digits to the right of the decimal point in the second's component of the data.



</td>
</tr>
<tr>
<td valign="top">

IS\_NULLABLE



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the column can accept NULL values: TRUE/FALSE.



</td>
</tr>
</table>

**Related Information**  


[FUNCTION\_PARAMETERS System View](function-parameters-system-view-20a4c5c.md "Provides information about parameters for functions.")

[FUNCTIONS System View](functions-system-view-20a5023.md "Provides information about available functions.")

[Function Parameters](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/58106d8f4fb44120b76fc6fb1f4a0bcc.html "") :arrow_upper_right:

[Array Parameters for Procedures and Functions](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/dcffe459010546bd981d3b74b3798962.html "You can create procedures and functions with array parameters so that array variables or constant arrays can be passed to them.") :arrow_upper_right:

