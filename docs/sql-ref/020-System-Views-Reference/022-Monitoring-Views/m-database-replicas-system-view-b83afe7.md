<!-- loiob83afe7e4bb144d68f41dd99aad5cf22 -->

# M\_DATABASE\_REPLICAS System View

Provides source and target information for databases involved in replication.



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

SOURCE\_DATABASE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the source database.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_SYSTEMDB\_HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the host of the source system database.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_SYSTEMDB\_PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the source system database port.

</td>
</tr>
<tr>
<td valign="top">

TARGET\_DATABASE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the target database.

</td>
</tr>
<tr>
<td valign="top">

TARGET\_SYSTEMDB\_HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the target system database host.

</td>
</tr>
<tr>
<td valign="top">

TARGET\_SYSTEMDB\_PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the target system database port.

</td>
</tr>
<tr>
<td valign="top">

REPLICATION\_STATUS

</td>
<td valign="top">

NVARCHAR\(12\)

</td>
<td valign="top">

Displays the aggregated replication status of the database services.

</td>
</tr>
</table>

**Related Information**  


[M\_DATABASE\_REPLICA\_STATISTICS System View](m-database-replica-statistics-system-view-19a4438.md "Provides statistics on databases involved in replication.")

[M\_DATABASE System View](m-database-system-view-20ae63a.md "Provides database information.")

[M\_DATABASES System View](m-databases-system-view-dbbdc0d.md "Provides information about all databases in the system. The full content of this view is only accessible from the system database.")

