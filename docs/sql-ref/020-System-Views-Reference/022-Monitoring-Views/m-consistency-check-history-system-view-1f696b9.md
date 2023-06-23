<!-- loio1f696b9f9df34f268c0c996e73421363 -->

# M\_CONSISTENCY\_CHECK\_HISTORY System View

Provides table check run information.



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

Displays the unique identifier for a run.



</td>
</tr>
<tr>
<td valign="top">

CONNECTION\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the connection ID of the last check execution.



</td>
</tr>
<tr>
<td valign="top">

USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the ID of the user performing the consistency check.



</td>
</tr>
<tr>
<td valign="top">

CHECK\_PROCEDURE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the check procedure, for example CHECK\_TABLE\_CONSISTENCY.



</td>
</tr>
<tr>
<td valign="top">

CHECK\_ACTION



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the single check action or a comma-separated list of check actions.



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

Displays the schema name. NULL is used if all schemas were checked.



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

CHECK\_EXECUTION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of executions related to the aggregated entry.



</td>
</tr>
<tr>
<td valign="top">

FIRST\_START\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the first start time of an aggregated entry. For an aggregated entry without any errors, this value defines the interval in which all checks were error-free.



</td>
</tr>
<tr>
<td valign="top">

LAST\_START\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the last invocation start time of an aggregated entry. For an aggregated entry without any errors, this value defines the interval in which all checks were error-free.



</td>
</tr>
<tr>
<td valign="top">

LAST\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total duration of the last check in milliseconds.



</td>
</tr>
<tr>
<td valign="top">

MIN\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the minimum duration of the check runs in milliseconds.



</td>
</tr>
<tr>
<td valign="top">

MAX\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the maximum duration of the check runs in milliseconds.



</td>
</tr>
<tr>
<td valign="top">

AVG\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average duration of the check runs milliseconds.



</td>
</tr>
<tr>
<td valign="top">

LAST\_SCHEDULED\_TABLE\_COUNT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the number of tables scheduled for checking.



</td>
</tr>
<tr>
<td valign="top">

MIN\_SCHEDULED\_TABLE\_COUNT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the minimum number of scheduled table counts for the checks runs.



</td>
</tr>
<tr>
<td valign="top">

MAX\_SCHEDULED\_TABLE\_COUNT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the maximum number of scheduled table counts for the checks runs.



</td>
</tr>
<tr>
<td valign="top">

AVG\_SCHEDULED\_TABLE\_COUNT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the average number of scheduled table counts for the checks runs.



</td>
</tr>
<tr>
<td valign="top">

EXECUTED\_TABLE\_COUNT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the number of tables that have been checked.



</td>
</tr>
<tr>
<td valign="top">

ERROR\_TABLE\_COUNT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the number of tables with errors.



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

Displays the error code returned by the check.



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

Displays the error message returned by the check.



</td>
</tr>
</table>



<a name="loio1f696b9f9df34f268c0c996e73421363__section_hxj_pqh_cfb"/>

## Additional Information

Further information about errors found during check runs can be found in the M\_CONSISTENCY\_CHECK\_HISTORY\_ERRORS system view.

Entries are aggregated, meaning that an existing entry is updated if the same checks were executed by the same user producing the same result.

**Related Information**  


[M\_CONSISTENCY\_CHECK\_HISTORY\_ERRORS System View](m-consistency-check-history-errors-system-view-f08f029.md "Lists the errors that were found within a specified check run.")

[Table Consistency Check](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/9357bf52c7324bee9567dca417ad9f8b.html "The table consistency check is a procedure available in the SAP HANA database that performs a range of consistency check actions on database tables. It can be run from the command line or scheduled within the statistics service.") :arrow_upper_right:

[Table and Catalog Consistency Checks](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/2584ec2e324d44529edc8221956359ea.html "Using stored procedures and commands available in the SAP HANA database, you can perform a range of consistency checks on the database catalog and on database tables.") :arrow_upper_right:

[Partitioning Consistency Checks](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/7b1e7a1577cc4e05bb4c05b4189c5b2f.html "A number of table consistency checks are available to check the validity of partitioned tables.") :arrow_upper_right:

[Catalog Consistency Check](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/9aed20fccc28455ea515c8c4eeceb7b3.html "The catalog consistency check can be run from the command line or be scheduled at the operating system level to perform a range of consistency check actions on the database catalog. The frequency with which you do this depends on your scenario.") :arrow_upper_right:

[Configuration Parameters for the Table Consistency Check](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/49ff94736bb84e948321cb1e8cd1ca22.html "A set of configuration parameters in the indexserver.ini file is available to control the manual table consistency check.") :arrow_upper_right:

