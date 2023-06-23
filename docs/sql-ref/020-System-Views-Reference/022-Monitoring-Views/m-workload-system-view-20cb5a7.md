<!-- loio20cb5a7675191014a650f7fa8587cf5f -->

# M\_WORKLOAD System View

Provides information about the database workload collected every minute.



<a name="loio20cb5a7675191014a650f7fa8587cf5f___m__w_o_r_k_l_o_a_d_1struct_M_WORKLOAD"/>

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

Displays the internal port.



</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total count of all executed statements for data manipulation, data definition, and system control.



</td>
</tr>
<tr>
<td valign="top">

COMPILATION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of statement preparation.



</td>
</tr>
<tr>
<td valign="top">

UPDATE\_TRANSACTION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of update transactions.



</td>
</tr>
<tr>
<td valign="top">

COMMIT\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of transaction commits.



</td>
</tr>
<tr>
<td valign="top">

ROLLBACK\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of transaction rollbacks.



</td>
</tr>
<tr>
<td valign="top">

CURRENT\_EXECUTION\_RATE



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the current statement execution count per minute.



</td>
</tr>
<tr>
<td valign="top">

PEAK\_EXECUTION\_RATE



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the peak statement execution count per minute.



</td>
</tr>
<tr>
<td valign="top">

CURRENT\_COMPILATION\_RATE



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the current statement preparation count per minute.



</td>
</tr>
<tr>
<td valign="top">

PEAK\_COMPILATION\_RATE



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the peak statement preparation count per minute.



</td>
</tr>
<tr>
<td valign="top">

CURRENT\_UPDATE\_TRANSACTION\_RATE



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the current update transaction count per minute.



</td>
</tr>
<tr>
<td valign="top">

PEAK\_UPDATE\_TRANSACTION\_RATE



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the peak update transaction count per minute.



</td>
</tr>
<tr>
<td valign="top">

CURRENT\_TRANSACTION\_RATE



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the current transaction count per minute.



</td>
</tr>
<tr>
<td valign="top">

PEAK\_TRANSACTION\_RATE



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the peak transaction count per minute.



</td>
</tr>
<tr>
<td valign="top">

CURRENT\_COMMIT\_RATE



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the total number of commits per minute.



</td>
</tr>
<tr>
<td valign="top">

PEAK\_COMMIT\_RATE



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the peak commit counts per minute.



</td>
</tr>
<tr>
<td valign="top">

CURRENT\_ROLLBACK\_RATE



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the total number of rollbacks per minute.



</td>
</tr>
<tr>
<td valign="top">

PEAK\_ROLLBACK\_RATE



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the peak rollback count per minute.



</td>
</tr>
<tr>
<td valign="top">

CURRENT\_MEMORY\_USAGE\_RATE



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the total size of used memory per minute in bytes.



</td>
</tr>
<tr>
<td valign="top">

PEAK\_MEMORY\_USAGE\_RATE



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the peak size of used memory per minute in bytes.



</td>
</tr>
</table>

**Related Information**  


[M\_WORKLOAD\_CAPTURES System View](m-workload-captures-system-view-ea8874b.md "Provides information about workload captures.")

[M\_WORKLOAD\_REPLAYS System View](m-workload-replays-system-view-881959a.md "Provides information about workload replays.")

[M\_WORKLOAD\_REPLAY\_PREPROCESSES System View](m-workload-replay-preprocesses-system-view-a493d08.md "Provides information about preprocesses for captured workloads.")

[CREATE WORKLOAD CLASS Statement \(Workload Management\)](../../010-SQL-Reference/012-SQL-Statements/create-workload-class-statement-workload-management-dc417c3.md "Defines workload classes.")

[ALTER WORKLOAD CLASS Statement \(Workload Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-workload-class-statement-workload-management-d4b4659.md "Changes workload classes.")

[ALTER WORKLOAD MAPPING Statement \(Workload Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-workload-mapping-statement-workload-management-81fc16b.md "Changes workload mappings.")

[CREATE WORKLOAD MAPPING Statement \(Workload Management\)](../../010-SQL-Reference/012-SQL-Statements/create-workload-mapping-statement-workload-management-996978a.md "Defines workload mappings.")

[DROP WORKLOAD CLASS Statement \(Workload Management\)](../../010-SQL-Reference/012-SQL-Statements/drop-workload-class-statement-workload-management-22f628b.md "Removes workload classes.")

[DROP WORKLOAD MAPPING Statement \(Workload Management\)](../../010-SQL-Reference/012-SQL-Statements/drop-workload-mapping-statement-workload-management-8d90e94.md "Drops a workload mapping.")

[Workload Management](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/30f2e9cb92aa4f358dda4ac58e062d83.html "The load on an SAP HANA system can be managed by selectively applying limitations and priorities to how resources are used. Settings can be applied globally or at the level of individual user sessions by using workload classes.") :arrow_upper_right:

