<!-- loiobb6efb92b5ba449986912af0785a7114 -->

# M\_EXECUTED\_STATEMENTS System View

Provides all statement executions that belong to a specified category.



<a name="loiobb6efb92b5ba449986912af0785a7114__section_bjn_nwg_x2b"/>

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

Displays the internal port number.

</td>
</tr>
<tr>
<td valign="top">

CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the connection ID.

</td>
</tr>
<tr>
<td valign="top">

TRANSACTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the transaction object ID.

</td>
</tr>
<tr>
<td valign="top">

UPDATE\_TRANSACTION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the write transaction ID. This number is ever increasing.

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

Displays the statement ID.

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

Displays the unique identifier for an SQL string.

</td>
</tr>
<tr>
<td valign="top">

DB\_USER

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the user name.

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

Displays the name of the schema in whose context the statement is executed.

</td>
</tr>
<tr>
<td valign="top">

APP\_USER

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the application user name.

</td>
</tr>
<tr>
<td valign="top">

CLIENT\_IP

</td>
<td valign="top">

NVARCHAR\(45\)

</td>
<td valign="top">

Displays the IP address of the client machine.

</td>
</tr>
<tr>
<td valign="top">

CLIENT\_PID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the client process ID.

</td>
</tr>
<tr>
<td valign="top">

START\_TIME

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

DURATION\_MICROSEC

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the statement duration in microseconds.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the name of the related object.

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

Displays the statement string.

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

ERROR\_TEXT

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

PASSPORT\_ROOTCONTEXT\_ID

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) GUID that identifies the source of the request.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_TRANSACTION\_ID

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) GUID that identifies the business transaction.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_CONNECTION\_ID

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) GUID that identifies the connection.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_CONNECTION\_COUNTER

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the extended passport \(EPP\) connection counter.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_COMPONENT\_NAME

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) component name.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_COMPONENT\_TYPE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the extended passport \(EPP\) component type.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_ACTION

</td>
<td valign="top">

NVARCHAR\(40\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) component action.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_ACTION\_TYPE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the extended passport \(EPP\) component action type.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_PREVIOUS\_COMPONENT\_NAME

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) passport component name of the previous context.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_SERVICE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the extended passport \(EPP\) service.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_USER\_ID

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) user ID.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_CLIENT

</td>
<td valign="top">

NVARCHAR\(3\)

</td>
<td valign="top">

Displays the extended passport \(EPP\) client.

</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_TRACE\_FLAGS

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the extended passport \(EPP\) trace flags.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_SOURCE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the application that defines from which source file SAP HANA is called. The usage is up to the application. This value is also displayed in M\_PREPARED\_STATEMENTS.APPLICATION\_SOURCE.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the application.

</td>
</tr>
</table>



<a name="loiobb6efb92b5ba449986912af0785a7114__section_cjn_nwg_x2b"/>

## Additional Information

This view allows you to collect all of the executed statements from whichever category you want to collect from. Only the DDL category is supported. The historization of DDL statement executions investigates the root cause more easily when your SAP HANA instance falls into the invalid metadata status. The collection functionality is turned off by setting the enable\_ddl parameter to OFF in the \[executed\_statements\] section of `global.ini`.

The collected history persists by generating the dedicated trace files \(for example, `indexserver_selqnta3.32503.executed_statements.000.trc`\). You can adjust the consumed disk size for persisted trace files by configuring the maxfiles and maxfilesize parameter, which represents the maximum number of files to be generated \(the default is 10\) and represents the size limit of each trace file in bytes \(the default is 10MB\) respectively, in the \[executed\_statements\] section of `global.ini`.

If the history for an executed statement is immediately persisted to the file whenever it is collected, then it may degrade the performance, as the disk input/output is usually more expensive \(that is, it takes more times to flush\) than memory input/output. Therefore, each statistic is stored at the in-memory buffer instead of instant disk input/output, and the buffer is flushed whenever N records are accumulated in the buffer. Adjust the degree of the flush interval with the trace\_flush\_interval parameter \(the default is 10 records\) in the \[executed\_statements\] section of `global.ini` and turn OFF this feature by setting use\_in\_memory\_tracing to OFF in the same section.

The following SQL statements are collected as DDL \(Data Definition Language\):

-   All SQL statements starting with CREATE, DROP, ALTER, and RENAME. For example, CREATE TABLE, CREATE USER and ALTER TABLE.

-   All SQL statements starting with TRUNCATE, GRANT, REVOKE, LOAD, EXPORT, IMPORT, and COMMENT.
-   The SET SYSTEM LICENSE *<license\_key\>* and UNSET SYSTEM LICENSE ALL statements.



<a name="loiobb6efb92b5ba449986912af0785a7114__section_yjl_flg_rkb"/>

## Additional Information

Setting the value of the APPLICATION\_SOURCE is only available via internal APIs of the SAP HANA database client interfaces \(for more information see SAP Note 2873396\).

**Related Information**  


[SAP Note 2873396](https://me.sap.com/notes/2873396)

[Controlling Parallel Execution of SQL Statements](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/5c012ca1def64bceb5f29028325193bd.html "Job management takes place in the HANA worker framework and is handled by the JobExecutor which is a job queueing and dispatching subsystem.") :arrow_upper_right:

[SQL Statements](../../010-SQL-Reference/012-SQL-Statements/sql-statements-20a6791.md "SAP HANA supports many SQL statements to allow you to perform such tasks as create database objects, administer your system, and manipulate data.")

[EXECUTE IMMEDIATE](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/093c4fd307064f838cb582555c187b9e.html "") :arrow_upper_right:

[Explicit Parallel Execution](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/8db200a4f585490c81c4930689ec1a5c.html "") :arrow_upper_right:

