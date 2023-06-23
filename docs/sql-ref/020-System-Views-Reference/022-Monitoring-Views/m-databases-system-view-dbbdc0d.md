<!-- loiodbbdc0d96675470e80801c5ddfb8d348 -->

# M\_DATABASES System View

Provides information about all databases in the system. The full content of this view is only accessible from the system database.



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

DATABASE\_NAME



</td>
<td valign="top">

NVARCHAR \(256\)



</td>
<td valign="top">

Displays the database name.



</td>
</tr>
<tr>
<td valign="top">

DESCRIPTION



</td>
<td valign="top">

NVARCHAR \(2000\)



</td>
<td valign="top">

Displays the database description.



</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_STATUS



</td>
<td valign="top">

NVARCHAR \(16\)



</td>
<td valign="top">

Displays the database status.



</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_STATUS\_DETAILS



</td>
<td valign="top">

NVARCHAR \(128\)



</td>
<td valign="top">

Displays the database status details. Possible values include: stopped by user, stopped due to broken recovery, or stopped by takeover.



</td>
</tr>
<tr>
<td valign="top">

OS\_USER



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the database isolation operation system user.



</td>
</tr>
<tr>
<td valign="top">

OS\_GROUP



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the database isolation operation system group.



</td>
</tr>
<tr>
<td valign="top">

RESTART\_MODE



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the restart behavior after a system restart. Possible values are NO \(do not restart the database after a system restart\) or DEFAULT \(restore the database to the state it had before the system restart\).



</td>
</tr>
<tr>
<td valign="top">

FALLBACK\_SNAPSHOT\_CREATE\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the timestamp for when the fallback snapshot was created, or NULL if there is no fallback snapshot for the database.



</td>
</tr>
</table>

**Related Information**  


[M\_DATABASE System View](m-database-system-view-20ae63a.md "Provides database information.")

[M\_SNAPSHOTS System View](m-snapshots-system-view-20c5439.md "Provides information about existing snapshots.")

[M\_DATABASE\_HISTORY System View](m-database-history-system-view-20ae406.md "Provides installation version history.")

[M\_DATABASE\_REPLICAS System View](m-database-replicas-system-view-b83afe7.md "Provides source and target information for databases involved in replication.")

[M\_DATABASE\_REPLICA\_STATISTICS System View](m-database-replica-statistics-system-view-19a4438.md "Provides statistics on databases involved in replication.")

[Database Roles](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/e7f358b6e85b4610a2b62c5a25755fc0.html "A database role is a collection of privileges that can be granted to either a database user or another role in runtime.") :arrow_upper_right:

[Log On to a Database](https://help.sap.com/viewer/f1b440ded6144a54ada97ff95dac7adf/LATEST/en-US/c2a6d9cbbb5710148afea455ba5746c0.html)

