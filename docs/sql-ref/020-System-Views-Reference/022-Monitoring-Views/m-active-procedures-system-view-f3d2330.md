<!-- loiof3d23305d0dd495590e0061c3546de9a -->

# M\_ACTIVE\_PROCEDURES System View

Provides statistics of procedure execution.



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

PROCEDURE\_HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the procedure host.

</td>
</tr>
<tr>
<td valign="top">

PROCEDURE\_PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the procedure internal port.

</td>
</tr>
<tr>
<td valign="top">

PROCEDURE\_SCHEMA\_NAME

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

PROCEDURE\_CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the procedure connection ID.

</td>
</tr>
<tr>
<td valign="top">

PROCEDURE\_TRANSACTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the procedure transaction ID.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_ID

</td>
<td valign="top">

NVARCHAR\(20\)

</td>
<td valign="top">

Displays the ID of the statement.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_HASH

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the hash value of the statement.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_STRING

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the SQL statement string.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_PARAMETERS

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the statement parameters.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_STATUS

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the status of the statement:

-   EXECUTING: the statement is still running
-   COMPLETED: the statement is completed
-   COMPILING: the statement is compiling
-   ABORTED: the statement was aborted



</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_EXECUTION\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the count of statement execution.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_DEPTH

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the statement depth.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_COMPILE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the elapsed time spent compiling the statement.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the elapsed time spent executing the statement.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_START\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the statement start time.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_END\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the statement end time.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the connection ID of the statement.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_TRANSACTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the transaction ID of the statement.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_MATERIALIZATION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the internal table materialization time.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_MATERIALIZATION\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the memory size, in bytes, of the internal table materialization.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_EXECUTION\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the peak amount of memory, in bytes, used for executing each statement inside a procedure. If you are using a distributed execution, shows the sum of local peak memory for multiple servers.

</td>
</tr>
</table>

**Related Information**  


[ALTER PROCEDURE Statement \(Procedural\)](../../010-SQL-Reference/012-SQL-Statements/alter-procedure-statement-procedural-20d0328.md "Alters a procedure or manually triggers a recompilation of a procedure by generating an updated execution plan.")

[CREATE PROCEDURE Statement \(Procedural\)](../../010-SQL-Reference/012-SQL-Statements/create-procedure-statement-procedural-20d4674.md "Creates a procedure that uses the specified programming language.")

[DROP PROCEDURE Statement \(Procedural\)](../../010-SQL-Reference/012-SQL-Statements/drop-procedure-statement-procedural-20d7165.md "Deletes a procedure from the database.")

[M\_ACTIVE\_STATEMENTS System View](m-active-statements-system-view-d20500a.md "Provides a prepared statements list.")

[Procedural Statements](../../010-SQL-Reference/012-SQL-Statements/procedural-statements-20a64c8.md "Procedural statements manage system and user-defined procedures for the SAP HANA database.")

[PROCEDURES System View](../021-System-Views/procedures-system-view-20cc87c.md "Provides information about available stored procedures.")

[SAP HANA Cloud, SAP HANA SQLScript Reference](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/28f2d64d4fab4e789ee0070be418419d.html "This reference describes how to use the SQL extension SAP HANA SQLScript to embed data-intensive application logic into SAP HANA.") :arrow_upper_right:

[CREATE PROCEDURE](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/7a2da744ce544db1814a5fff250e99f6.html "You use this SQL statement to create a procedure.") :arrow_upper_right:

[DROP PROCEDURE](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/5f244d38d5984899ae8263539badf306.html "") :arrow_upper_right:

[ALTER PROCEDURE](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/042ab4636cf34a9cb88dd61c808861a8.html "") :arrow_upper_right:

[Procedures](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/d43d91578c3b42b3bacfd89aacf0d62f.html "") :arrow_upper_right:

