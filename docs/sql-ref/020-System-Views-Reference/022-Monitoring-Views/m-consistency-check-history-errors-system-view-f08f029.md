<!-- loiof08f02989dd34fa3b310b204dfb5c1a7 -->

# M\_CONSISTENCY\_CHECK\_HISTORY\_ERRORS System View

Lists the errors that were found within a specified check run.



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

CHECK\_EXECUTION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the execution ID of the consistency check run that produced the error.

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

Displays the schema name.

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

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the type of the object.

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

Displays the column name.

</td>
</tr>
<tr>
<td valign="top">

PART\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the partition ID. Contains 0 for an unpartitioned table.

</td>
</tr>
<tr>
<td valign="top">

ERROR\_CODE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the error code.

</td>
</tr>
<tr>
<td valign="top">

ERROR\_MESSAGE

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the error message.

</td>
</tr>
<tr>
<td valign="top">

SEVERITY

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays the error severity: LOW, INFO, HIGH, or ERROR.

</td>
</tr>
<tr>
<td valign="top">

CHECK\_ACTION

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the check action that produced the error. Contains NULL for errors not related to a specific check action.

</td>
</tr>
<tr>
<td valign="top">

AFFECTED\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of rows affected by the error \(optional\).

This column does not always contain a value, even in the case of an error. For some errors, this column may contain a NULL value.

</td>
</tr>
<tr>
<td valign="top">

DETAILS

</td>
<td valign="top">

NCLOB \(JSON\)

</td>
<td valign="top">

Displays the detailed information related to the error \(optional\).

This column does not always contain a value, even in the case of an error. For some errors, this column may contain a NULL value.

</td>
</tr>
</table>

**Related Information**  


[M\_CONSISTENCY\_CHECK\_HISTORY System View](m-consistency-check-history-system-view-1f696b9.md "Provides table check run information.")

[SQL Error Codes](../../010-SQL-Reference/sql-error-codes-20a78d3.md "Each SAP HANA error has a numeric error code. The M_ERROR_CODES system view contains information about the error codes.")

[Table Consistency Check](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/9357bf52c7324bee9567dca417ad9f8b.html "The table consistency check is a procedure available in the SAP HANA database that performs a range of consistency check actions on database tables. It can be run from the command line or scheduled within the statistics service.") :arrow_upper_right:

[Table and Catalog Consistency Checks](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/2584ec2e324d44529edc8221956359ea.html "Using stored procedures and commands available in the SAP HANA database, you can perform a range of consistency checks on the database catalog and on database tables.") :arrow_upper_right:

[Partitioning Consistency Checks](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/7b1e7a1577cc4e05bb4c05b4189c5b2f.html "A number of table consistency checks are available to check the validity of partitioned tables.") :arrow_upper_right:

[Catalog Consistency Check](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/9aed20fccc28455ea515c8c4eeceb7b3.html "The catalog consistency check can be run from the command line or be scheduled at the operating system level to perform a range of consistency check actions on the database catalog. The frequency with which you do this depends on your scenario.") :arrow_upper_right:

[Configuration Parameters for the Table Consistency Check](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/49ff94736bb84e948321cb1e8cd1ca22.html "A set of configuration parameters in the indexserver.ini file is available to control the manual table consistency check.") :arrow_upper_right:

[Break on Error](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/d3378a9550204fee8c327f7545d55f9a.html "") :arrow_upper_right:

[Supported Error Codes](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/83686b04386e4c009f57418bccb7d9ee.html "The following is a list of the error codes supported by the exit handler.") :arrow_upper_right:

