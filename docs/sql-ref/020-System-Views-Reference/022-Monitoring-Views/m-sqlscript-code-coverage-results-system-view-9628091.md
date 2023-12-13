<!-- loio96280912f1f74de789a1ecfe450dda20 -->

# M\_SQLSCRIPT\_CODE\_COVERAGE\_RESULTS System View

Provides per-session SQLScript code coverage results.



<a name="loio96280912f1f74de789a1ecfe450dda20___q_u_e_r_y__p_l_a_n_s_1struct_QUERY_PLANS"/>

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

OBJECT\_DEFINITION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the ID of the object definition. This value corresponds to a value in M\_SQLSCRIPT\_CODE\_COVERAGE\_OBJECT\_DEFINITIONS.OBJECT\_DEFINITION\_ID.

</td>
</tr>
<tr>
<td valign="top">

DATABASE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the database.

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

Displays the name of the schema.

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

Displays the name of the object.

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

Displays the type of object:

-   FUNCTION
-   PROCEDURE
-   ANONYMOUS BLOCK



</td>
</tr>
<tr>
<td valign="top">

OBJECT\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the ID of the object.

</td>
</tr>
<tr>
<td valign="top">

LINE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the line number of the code snippet in the object definition.

</td>
</tr>
<tr>
<td valign="top">

COLUMN

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the starting column of the code snippet in the object definition.

</td>
</tr>
<tr>
<td valign="top">

START\_POSITION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the index of the code snippet's first character in the object definition.

</td>
</tr>
<tr>
<td valign="top">

END\_POSITION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the index of the code snippet's last character in the object definition.

</td>
</tr>
<tr>
<td valign="top">

HIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the hit count for the code snippet during a single invocation of the object; zero if not covered.

</td>
</tr>
<tr>
<td valign="top">

INVOKER\_OBJECT\_DEFINITION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the ID of the invoker's object definition; this value is NULL if this is the top-most function or procedure.

</td>
</tr>
<tr>
<td valign="top">

INVOKER\_LINE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the line number in the invoker's object definition; this value is NULL if this is the top-most function or procedure.

</td>
</tr>
<tr>
<td valign="top">

INVOKER\_COLUMN

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the column in the invoker's object definition; this value is NULL if this is the top-most function or procedure.

</td>
</tr>
<tr>
<td valign="top">

INVOKER\_START\_POSITION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the index of the first character in the invoker's object definition; this value is NULL if this is the top-most function or procedure.

</td>
</tr>
<tr>
<td valign="top">

INVOKER\_END\_POSITION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the index of the last character in the invoker's object definition; this value is NULL if this is the top-most function or procedure.

</td>
</tr>
</table>

**Related Information**  


[M\_SQLSCRIPT\_CODE\_COVERAGE\_OBJECT\_DEFINITIONS System View](m-sqlscript-code-coverage-object-definitions-system-view-7992c97.md "Provides definitions for the objects referenced in SQLScript code coverage results.")

[SQLScript Code Coverage](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/d00c173403154434affc3ace52efd611.html "") :arrow_upper_right:

[ALTER SYSTEM \{START | STOP\} SQLSCRIPT CODE COVERAGE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-start-stop-sqlscript-code-coverage-statement-system-management-1a40f07.md "Starts and stops a SQLScript code coverage session for functions and procedures.")

