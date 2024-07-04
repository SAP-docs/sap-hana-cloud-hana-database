<!-- loio20b37788751910148d69997ce4bc365b -->

# M\_LIVECACHE\_SCHEMA\_STATISTICS System View

Provides accumulated liveCache schema statistics.



<a name="loio20b37788751910148d69997ce4bc365b___m__l_i_v_e_c_a_c_h_e__s_c_h_e_m_a__s_t_a_t_i_s_t_i_c_s_1struct_M_LIVECACHE_SCHEMA_STATISTICS"/>

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

OMS\_SCHEMA\_HANDLE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the Object Management System \(OMS\) schema ID.

</td>
</tr>
<tr>
<td valign="top">

OMS\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(96\)

</td>
<td valign="top">

Displays the Object Management System \(OMS\) schema name.

</td>
</tr>
<tr>
<td valign="top">

CREATE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the created timestamp.

</td>
</tr>
</table>



<a name="loio20b37788751910148d69997ce4bc365b__section_unb_yd1_ybc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.



<a name="loio20b37788751910148d69997ce4bc365b__section_flz_qch_x2b"/>

## Additional Information

This view has a resettable counterpart; you can see the values since the last reset in the M\_LIVECACHE\_SCHEMA\_STATISTICS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_LIVECACHE_SCHEMA_STATISTICS_RESET;`.

**Related Information**  


[M\_LIVECACHE\_SCHEMA\_STATISTICS\_RESET System View](m-livecache-schema-statistics-reset-system-view-20b39b9.md "Provides accumulated LiveCache schema statistics since the last reset.")

[SCHEMAS System View](../021-System-Views/schemas-system-view-20cde59.md "Shows available schemas.")

[CREATE SCHEMA Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-schema-statement-data-definition-20d4eca.md "Creates a schema in the current database.")

[RENAME SCHEMA Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/rename-schema-statement-data-definition-a521980.md "Rename a schema without creating a new schema.")

[SET SCHEMA Statement \(Session Management\)](../../010-SQL-Reference/012-SQL-Statements/set-schema-statement-session-management-20fd550.md "Changes the default schema for the session to the specified schema.")

[DROP SCHEMA Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-schema-statement-data-definition-20d7891.md "Removes a schema.")

