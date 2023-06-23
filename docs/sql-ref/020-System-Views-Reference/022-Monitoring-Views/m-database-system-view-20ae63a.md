<!-- loio20ae63aa7519101496f6b832ec86afbd -->

# M\_DATABASE System View

Provides database information.



<a name="loio20ae63aa7519101496f6b832ec86afbd___m__d_a_t_a_b_a_s_e_1struct_M_DATABASE"/>

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

SYSTEM\_ID



</td>
<td valign="top">

NVARCHAR\(3\)



</td>
<td valign="top">

Displays the system SID.



</td>
</tr>
<tr>
<td valign="top">

DATABASE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the database name.



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

Displays the default coordinator host.



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

VERSION



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the version: major.minor.patch.build.



</td>
</tr>
<tr>
<td valign="top">

USAGE



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Database usage type. Recommended values: production, test, development, or custom. Any value is allowed, but recommended values may be used by clients to alter behavior.



</td>
</tr>
</table>

**Related Information**  


[M\_DATABASES System View](m-databases-system-view-dbbdc0d.md "Provides information about all databases in the system. The full content of this view is only accessible from the system database.")

[M\_DATABASE\_HISTORY System View](m-database-history-system-view-20ae406.md "Provides installation version history.")

[M\_DATABASE\_REPLICAS System View](m-database-replicas-system-view-b83afe7.md "Provides source and target information for databases involved in replication.")

[M\_DATABASE\_REPLICA\_STATISTICS System View](m-database-replica-statistics-system-view-19a4438.md "Provides statistics on databases involved in replication.")

[Database Roles](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/e7f358b6e85b4610a2b62c5a25755fc0.html "A database role is a collection of privileges that can be granted to either a database user or another role in runtime.") :arrow_upper_right:

[Log On to a Database](https://help.sap.com/viewer/f1b440ded6144a54ada97ff95dac7adf/LATEST/en-US/c2a6d9cbbb5710148afea455ba5746c0.html)

