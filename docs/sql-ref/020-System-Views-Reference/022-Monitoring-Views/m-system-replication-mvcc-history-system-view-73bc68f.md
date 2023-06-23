<!-- loio73bc68f943ee466c9cb4dad1bed61c79 -->

# M\_SYSTEM\_REPLICATION\_MVCC\_HISTORY System View

Displays the global multi-version concurrency control \(MVCC\) timestamp history in the secondary site for system replication. The global MVCC timestamp of the secondary site is updated after a chunk of logs from the primary site is replayed on the secondary site.



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

GLOBAL\_MVCC\_TIMESTAMP



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the global MVCC timestamp



</td>
</tr>
<tr>
<td valign="top">

SECONDARY\_SITE\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the global MVCC timestamp updated time of the secondary site



</td>
</tr>
<tr>
<td valign="top">

PRIMARY\_SITE\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the global MVCC updated time of the primary site



</td>
</tr>
<tr>
<td valign="top">

SECONDARY\_SITE\_UPDATE\_DURATION



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the global MVCC update duration of the secondary site in milliseconds



</td>
</tr>
</table>

**Related Information**  


[M\_SYSTEM\_REPLICATION System View](m-system-replication-system-view-4b263e6.md "Monitors system replication information.")

[M\_MVCC\_OVERVIEW System View](m-mvcc-overview-system-view-f405b73.md "Provides an overview of the row-store Multiversion Concurrency Control (MVCC) manager.")

[M\_MVCC\_SNAPSHOTS System View](m-mvcc-snapshots-system-view-b41f6b2.md "Provides detailed snapshot information of the Multiversion Concurrency Control (MVCC) manager.")

[M\_MVCC\_TABLES System View](m-mvcc-tables-system-view-20b5e31.md "Provides statistics for the row-store Multiversion Concurrency Control (MVCC) manager.")

