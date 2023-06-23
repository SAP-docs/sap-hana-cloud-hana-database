<!-- loio3d028423c65b44bb8c34971bf4af1e1d -->

# PROCEDURE\_PARAMETER\_COLUMNS System View

Lists available columns of table parameters of stored procedures.



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

Displays the schema name of the stored procedure.



</td>
</tr>
<tr>
<td valign="top">

PROCEDURE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the same of the stored procedure.



</td>
</tr>
<tr>
<td valign="top">

PROCEDURE\_OID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the object ID of the stored procedure.



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

Displays the number of characters for character types, the number of max digits for numeric types, the number of charactesr for datetime types, or the number of bytes for LOB types,



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

For numeric types, displays the maximum number of digits to the right of the decimal point. For time and timestamp types, displays the decimal digits defined as the number of digits to the right of the decimal point in the second's component of the data.



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

Displays whether the column is allowed to accept NULL values: TRUE/FALSE.



</td>
</tr>
</table>

**Related Information**  


[PROCEDURES System View](procedures-system-view-20cc87c.md "Provides information about available stored procedures.")

[PROCEDURE\_OBJECTS System View](procedure-objects-system-view-20cc4d6.md "Contains the results of the system procedure GET_PROCEDURE_OBJECTS.")

[PROCEDURE\_PARAMETERS System View](procedure-parameters-system-view-20cc6b9.md "Provides information about the stored procedure parameters.")

[PROCEDURE\_ROUTES System View](procedure-routes-system-view-61d897c.md "Provides information about the procedure being routed. This view is for internal use only.")

[Column View Parameter Binding](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/f1c17eb3a5b04f8b82d5908218e3fa68.html "") :arrow_upper_right:

[Procedure Parameters](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/3809c45287c44908a3d45a4db1514a55.html "") :arrow_upper_right:

[Array Parameters for Procedures and Functions](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/dcffe459010546bd981d3b74b3798962.html "You can create procedures and functions with array parameters so that array variables or constant arrays can be passed to them.") :arrow_upper_right:

