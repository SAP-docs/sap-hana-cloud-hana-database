<!-- loio20ae4069751910148d2b8a083d8337b4 -->

# M\_DATABASE\_HISTORY System View

Provides installation version history.



<a name="loio20ae4069751910148d2b8a083d8337b4___m__d_a_t_a_b_a_s_e__h_i_s_t_o_r_y_1struct_M_DATABASE_HISTORY"/>

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

INSTALL\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the installation or first start time.

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
</table>

**Related Information**  


[M\_DATABASE System View](m-database-system-view-20ae63a.md "Provides database information.")

[M\_DATABASES System View](m-databases-system-view-dbbdc0d.md "Provides information about all databases in the system. The full content of this view is only accessible from the system database.")

[PERSISTENCE\_HISTORY System View](../021-System-Views/persistence-history-system-view-a8cb93e.md "Records the database version history.")

[M\_DATABASE\_REPLICAS System View](m-database-replicas-system-view-b83afe7.md "Provides source and target information for databases involved in replication.")

[M\_DATABASE\_REPLICA\_STATISTICS System View](m-database-replica-statistics-system-view-19a4438.md "Provides statistics on databases involved in replication.")

