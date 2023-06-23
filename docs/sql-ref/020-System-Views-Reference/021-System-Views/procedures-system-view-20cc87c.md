<!-- loio20cc87c275191014bfc3a174bfc15c51 -->

# PROCEDURES System View

Provides information about available stored procedures.



<a name="loio20cc87c275191014bfc3a174bfc15c51___p_r_o_c_e_d_u_r_e_s_1struct_PROCEDURES"/>

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

Displays the name of the stored procedure.



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

SQL\_SECURITY



</td>
<td valign="top">

NVARCHAR\(7\)



</td>
<td valign="top">

Displays the SQL security setting of the stored procedure: DEFINER/INVOKER



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

Displays the schema name of the unqualified objects in the procedure.



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

OUTPUT\_PARAMETER\_COUNT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the output type parameter count.



</td>
</tr>
<tr>
<td valign="top">

INOUT\_PARAMETER\_COUNT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the in/out type parameter count.



</td>
</tr>
<tr>
<td valign="top">

RESULT\_SET\_COUNT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the result set count.



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

Displays whether the stored procedure is encrypted: TRUE/FALSE.



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

Displays the query string of the stored procedure.



</td>
</tr>
<tr>
<td valign="top">

PROCEDURE\_TYPE



</td>
<td valign="top">

NVARCHAR\(10\)



</td>
<td valign="top">

Displays the type of the stored procedure.



</td>
</tr>
<tr>
<td valign="top">

READ\_ONLY



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the procedure is read-only: TRUE/FALSE



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

Displays whether the procedure is valid: TRUE/FALSE. A procedure become invalid when its base objects are changed or dropped.



</td>
</tr>
<tr>
<td valign="top">

IS\_HEADER\_ONLY



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the procedure is a header only procedure: TRUE/FALSE.



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

Displays whether the stored procedure is deterministic: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

HAS\_TRANSACTION\_CONTROL\_STATEMENTS



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the procedure has transaction control statements: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

AUTO\_COMMIT\_DDL



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the stored procedure runs with autocommit DDL enabled: TRUE/FALSE.



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

Displays the name of the owner of the stored procedure.



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

Displays the creation time of the procedure.



</td>
</tr>
</table>

**Related Information**  


[CREATE PROCEDURE Statement \(Procedural\)](../../010-SQL-Reference/012-SQL-Statements/create-procedure-statement-procedural-20d4674.md "Creates a procedure that uses the specified programming language.")

[ALTER PROCEDURE Statement \(Procedural\)](../../010-SQL-Reference/012-SQL-Statements/alter-procedure-statement-procedural-20d0328.md "Alters a procedure or manually triggers a recompilation of a procedure by generating an updated execution plan.")

[DROP PROCEDURE Statement \(Procedural\)](../../010-SQL-Reference/012-SQL-Statements/drop-procedure-statement-procedural-20d7165.md "Deletes a procedure from the database.")

[Procedural Statements](../../010-SQL-Reference/012-SQL-Statements/procedural-statements-20a64c8.md "Procedural statements manage system and user-defined procedures for the SAP HANA database.")

[PROCEDURE\_OBJECTS System View](procedure-objects-system-view-20cc4d6.md "Contains the results of the system procedure GET_PROCEDURE_OBJECTS.")

[PROCEDURE\_PARAMETERS System View](procedure-parameters-system-view-20cc6b9.md "Provides information about the stored procedure parameters.")

[PROCEDURE\_PARAMETER\_COLUMNS System View](procedure-parameter-columns-system-view-3d02842.md "Lists available columns of table parameters of stored procedures.")

[PROCEDURE\_ROUTES System View](procedure-routes-system-view-61d897c.md "Provides information about the procedure being routed. This view is for internal use only.")

[Procedures](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/d43d91578c3b42b3bacfd89aacf0d62f.html "") :arrow_upper_right:

[CREATE PROCEDURE](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/7a2da744ce544db1814a5fff250e99f6.html "You use this SQL statement to create a procedure.") :arrow_upper_right:

[ALTER PROCEDURE](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/042ab4636cf34a9cb88dd61c808861a8.html "") :arrow_upper_right:

[DROP PROCEDURE](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/5f244d38d5984899ae8263539badf306.html "") :arrow_upper_right:

[Deterministic Procedures](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/dae6fae315c546ba9dc8665c0ca51cb9.html "") :arrow_upper_right:

[Procedure Metadata](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/8c59aace1caf472ebe71e6592a06b27a.html "") :arrow_upper_right:

[Procedure Calls](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/461da7cfaaff4d89b518b8ae48121263.html "") :arrow_upper_right:

[Procedure Result Cache](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/23bd07d4f4a1444ab64ca580373e8efc.html "Procedure Result Cache (PRC) is a server-wide in-memory cache that caches the output arguments of procedure calls using the input arguments as keys.") :arrow_upper_right:

[SYS.PROCEDURES](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/a7b1261516ae4166883e6bc373733de5.html "Available stored procedures") :arrow_upper_right:

