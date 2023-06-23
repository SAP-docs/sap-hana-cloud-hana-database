<!-- loio20a50237751910149785ae5ef858c5da -->

# FUNCTIONS System View

Provides information about available functions.



<a name="loio20a50237751910149785ae5ef858c5da___f_u_n_c_t_i_o_n_s_1struct_FUNCTIONS"/>

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

SQL\_SECURITY



</td>
<td valign="top">

NVARCHAR\(7\)



</td>
<td valign="top">

Displays the SQL security setting of the function: DEFINER/INVOKER.



</td>
</tr>
<tr>
<td valign="top">

DEFAULT\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name of the unqualified objects in the function.



</td>
</tr>
<tr>
<td valign="top">

INPUT\_PARAMETER\_COUNT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the input type parameter count.



</td>
</tr>
<tr>
<td valign="top">

RETURN\_VALUE\_COUNT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the return value type parameter count.



</td>
</tr>
<tr>
<td valign="top">

IS\_ENCRYPTED



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the function is encrypted: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

DEFINITION



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays the query string of the function.



</td>
</tr>
<tr>
<td valign="top">

FUNCTION\_TYPE



</td>
<td valign="top">

NVARCHAR\(10\)



</td>
<td valign="top">

Displays the type of function.



</td>
</tr>
<tr>
<td valign="top">

FUNCTION\_USAGE\_TYPE



</td>
<td valign="top">

NVARCHAR\(9\)



</td>
<td valign="top">

Displays the usage type of the function: SCALAR, TABLE, AGGREGATE, or WINDOW.



</td>
</tr>
<tr>
<td valign="top">

IS\_VALID



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the function is valid or not. This value becomes FALSE when its base objects are changed or dropped: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

IS\_HEADER\_ONLY.



</td>
<td valign="top">

NVARCHAR\(5\).



</td>
<td valign="top">

Displays whether the function is a header-only function: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

IS\_DETERMINISTIC



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the function is deterministic: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

OWNER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the owner of the function.



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

Displays the creation time of the function.



</td>
</tr>
</table>

**Related Information**  


[FUNCTION\_PARAMETERS System View](function-parameters-system-view-20a4c5c.md "Provides information about parameters for functions.")

[FUNCTION\_PARAMETER\_COLUMNS System View](function-parameter-columns-system-view-81b0908.md "Provides information about columns that are available for function table parameters.")

[CREATE FUNCTION Statement \(Procedural\)](../../010-SQL-Reference/012-SQL-Statements/create-function-statement-procedural-20d42e7.md "Creates a user-defined function.")

[ALTER FUNCTION Statement \(Procedural\)](../../010-SQL-Reference/012-SQL-Statements/alter-function-statement-procedural-1102d57.md "Modifies a user-defined function.")

[DROP FUNCTION Statement \(Procedural\)](../../010-SQL-Reference/012-SQL-Statements/drop-function-statement-procedural-20d6852.md "Deletes a function from the database.")

[Aggregate Functions](../../010-SQL-Reference/011-SQL-Functions/aggregate-functions-6fff7f0.md "Aggregate functions are analytic functions that calculate an aggregate value based on a group of rows.")

[Array Functions](../../010-SQL-Reference/011-SQL-Functions/array-functions-e32b3b4.md "Array functions take arrays as input.")

[Data Type Conversion Functions](../../010-SQL-Reference/011-SQL-Functions/data-type-conversion-functions-209ddef.md "Data type conversion functions convert data from one data type to another data type.")

[Datetime Functions](../../010-SQL-Reference/011-SQL-Functions/datetime-functions-209f228.md "Date and time functions perform operations on date and time data types or return date or time information.")

[Hierarchy Functions](../../010-SQL-Reference/011-SQL-Functions/hierarchy-functions-2969da8.md "Hierarchy functions allow you to work with hierarchical data such as tables with rows arranged in a tree or directed graph.")

[JSON Functions](../../010-SQL-Reference/011-SQL-Functions/json-functions-5848028.md "JSON functions are functions that return or operate on JSON data.")

[Miscellaneous Functions](../../010-SQL-Reference/011-SQL-Functions/miscellaneous-functions-20a465c.md "SAP HANA supports many functions that return system values and perform various operations on values, expressions, and return values of other functions.")

[Numeric Functions](../../010-SQL-Reference/011-SQL-Functions/numeric-functions-20a190b.md "Numeric functions perform mathematical operations on numerical data types or return numeric information.")

[Security Functions](../../010-SQL-Reference/011-SQL-Functions/security-functions-287e6e0.md "Security functions provide special functionality for security purposes.")

[Series Data Functions](../../010-SQL-Reference/011-SQL-Functions/series-data-functions-2dea02f.md "Series data functions provide special functionality for series data and series tables.")

[String Functions](../../010-SQL-Reference/011-SQL-Functions/string-functions-20a24d4.md "String functions perform extraction and manipulation on strings, or return information about strings.")

[Window Functions and the Window Specification](../../010-SQL-Reference/011-SQL-Functions/window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

[CREATE FUNCTION](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/2fc6d7beebd14c579457092e91519082.html "This SQL statement creates read-only user-defined functions that are free of side effects. This means that neither DDL, nor DML statements (INSERT, UPDATE, and DELETE) are allowed in the function body. All functions or procedures selected or called from the body of the function must be read-only.") :arrow_upper_right:

[ALTER FUNCTION](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/906c179f2d62418b957c801aa2c99e62.html "") :arrow_upper_right:

[DROP FUNCTION](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/1eccca0a59854c7192f0f855f8d5dc7c.html "") :arrow_upper_right:

[Function Metadata](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/98599d94ae4e440eaea23dfd740de41b.html "") :arrow_upper_right:

[Function Parameters](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/58106d8f4fb44120b76fc6fb1f4a0bcc.html "") :arrow_upper_right:

