<!-- loio9b9fc14858414427ba1cab6570864806 -->

# M\_MEMORY\_PROFILER System View

Provides memory profiler information.



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

FILE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the file name.

</td>
</tr>
<tr>
<td valign="top">

PROFILE\_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the profile name.

</td>
</tr>
<tr>
<td valign="top">

SERVICE\_NAME

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the service name.

</td>
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

SAMPLING\_INTERVAL

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the sampling interval in milliseconds.

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

Displays the start time.

</td>
</tr>
<tr>
<td valign="top">

STOPE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the stop time.

</td>
</tr>
<tr>
<td valign="top">

REMAINING\_SECONDS

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the remaining seconds until an automatic stop.

</td>
</tr>
<tr>
<td valign="top">

STATUS

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the status: STARTED/STOPPED.

</td>
</tr>
<tr>
<td valign="top">

HAS\_CALLSTACKS

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates whether or not the profiler has callstacks recorded: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

FILE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of the file in bytes.

</td>
</tr>
</table>

**Related Information**  


[ALTER SYSTEM \{START | STOP | SAVE | CLEAR\} KERNEL PROFILER Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-start-stop-save-clear-kernel-profiler-statement-system-manageme-864e9b9.md "Manages the operation of the Kernel Profiler.")

[Kernel Profiler](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/bdd27500bb571014b7f7e61e7c4cda04.html "The kernel profiler is a sampling profiler built into the SAP HANA database. It can be used to analyze performance issues and it collects, for example, information about frequent and/or expensive execution paths during query processing.") :arrow_upper_right:

