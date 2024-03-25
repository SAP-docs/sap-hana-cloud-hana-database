<!-- loioc978342a4ac8441fb2ce8e30dcdbf506 -->

# TEMPORAL\_TABLES System View

Provides information about system-versioned tables, history tables, and application-time period tables.



<a name="loioc978342a4ac8441fb2ce8e30dcdbf506___t_a_b_l_e_s_1struct_TABLES"/>

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

SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the table name.

</td>
</tr>
<tr>
<td valign="top">

PERIOD\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the period name.

</td>
</tr>
<tr>
<td valign="top">

PERIOD\_START\_COLUMN

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the column that contains the start of the period.

</td>
</tr>
<tr>
<td valign="top">

PERIOD\_END\_COLUMN

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the column that contains the end of the period.

</td>
</tr>
<tr>
<td valign="top">

HAS\_TIMELINE\_INDEX

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

HISTORY\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema of the history table associated to the system-versioned table.

</td>
</tr>
<tr>
<td valign="top">

HISTORY\_TABLE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the history table associated to the system-versioned table.

</td>
</tr>
</table>



<a name="loioc978342a4ac8441fb2ce8e30dcdbf506__section_zmg_xyz_2zb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[Temporal Tables](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/cf3523ab01834f5e84a32164c1fd597a.html "Temporal tables is a general term for tables which provide functionality to manage historical data: that is, to maintain a set of current values which are valid for a predefined period and also maintain an auditable continuous history of changes.") :arrow_upper_right:

[System-Versioned Tables](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/91302b26f62c4433bbc58e0a951cdc1d.html "System-versioned tables are part of the SQL standard. They support the tracking of changes on column store tables by capturing the validity period of each record.") :arrow_upper_right:

[Application-Time Period Tables](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/2e37d6a82f7b48ccbfcc5a1a6ce490f5.html "Application-Time Period Tables allow you to manage and manipulate historical business data based on application-specific time periods which are independent of system time-stamps.") :arrow_upper_right:

[TABLES System View](tables-system-view-2101973.md "Provides information about tables in the database.")

