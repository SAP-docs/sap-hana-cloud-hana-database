<!-- loio8824d53ce1b241bf895337989ea2e438 -->

# M\_WORKLOAD\_CLASS\_STATISTICS System View

Displays how many resources have been consumed by statements that belong to a specified workload class.



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

WORKLOAD\_CLASS\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the workload class name.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_STATEMENT\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total peak memory size, in bytes, used by statements.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_STATEMENT\_CPU\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total CPU time, in microseconds, used by statements.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_STATEMENT\_ADMIN\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of admitted statements.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_STATEMENT\_REJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of rejected statements.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_STATEMENT\_ENQUEUE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of enqueued statements.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_STATEMENT\_DEQUEUE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of dequeued statements for deferred execution.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_STATEMENT\_TIMEOUT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of dequeued statements for timed out.

</td>
</tr>
</table>

**Related Information**  


[WORKLOAD\_CLASSES System View](../021-System-Views/workload-classes-system-view-d520e47.md "Provides information about available workload classes.")

[M\_WORKLOAD System View](m-workload-system-view-20cb5a7.md "Provides information about the database workload collected every minute.")

[M\_WORKLOAD\_CAPTURES System View](m-workload-captures-system-view-ea8874b.md "Provides information about workload captures.")

[M\_WORKLOAD\_REPLAYS System View](m-workload-replays-system-view-881959a.md "Provides information about workload replays.")

[M\_WORKLOAD\_REPLAY\_PREPROCESSES System View](m-workload-replay-preprocesses-system-view-a493d08.md "Provides information about preprocesses for captured workloads.")

[WORKLOAD\_MAPPINGS System View](../021-System-Views/workload-mappings-system-view-89a0660.md "Provides information about available workload mappings.")

[Managing Workload with Workload Classes](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/5066181717df4110931271d1efd84cbc.html "You can manage workload in SAP HANA by creating workload classes and workload class mappings. Appropriate workload parameters are then dynamically applied to each client session.") :arrow_upper_right:

[Monitoring Views for Workload Classes](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/89d991fde38c47f9be78aa2a6cb4ee0f.html "You can use system views to monitor details of workload classes.") :arrow_upper_right:

[Workload Classes and Other Workload Management Features](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/dafe347e32dc4884a7b2b37909dabf94.html "Here we give examples to show how the workload management features interact together.") :arrow_upper_right:

