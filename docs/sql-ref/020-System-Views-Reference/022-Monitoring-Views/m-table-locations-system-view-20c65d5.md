<!-- loio20c65d57751910148de3aaf0455fc678 -->

# M\_TABLE\_LOCATIONS System View

Provides information about tables and their logical location. Physical locations are shown in M\_TABLE\_PERSISTENCE\_LOCATIONS.



<a name="loio20c65d57751910148de3aaf0455fc678___m__t_a_b_l_e__l_o_c_a_t_i_o_n_s_1struct_M_TABLE_LOCATIONS"/>

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

Displays the host where table data is located. This value is empty for views.



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

Displays the port where the table data is located. This value is 0 for views.



</td>
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

PART\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Returns the table partition ID:

-   For partitioned tables, the part ID is equal to the sequential number of the partition, starting at 1.
-   For replicated tables, the part ID is 1 for the original table and subsequent part IDs are assigned to replica tables.
-   The part ID is 0 for tables that are not partitioned.
-   A part ID value of -1 indicates that a modification of the table schema is currently in progress.



</td>
</tr>
<tr>
<td valign="top">

LOCATION



</td>
<td valign="top">

NVARCHAR\(75\)



</td>
<td valign="top">

Displays the host and port where the table data is located.



</td>
</tr>
</table>

**Related Information**  


[CREATE TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-table-statement-data-definition-20d58a5.md "Creates a base or temporary table. See the CREATE VIRTUAL TABLE statement for creating virtual tables.")

[ALTER TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-table-statement-data-definition-20d329a.md "Alters a base or temporary table. See the ALTER VIRTUAL TABLE statement for altering virtual tables.")

[Set an Explicit Table Location](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/d4a2e245a0f74edaa98e47599facf1a4.html "You can set an explicit table location with SQL commands.") :arrow_upper_right:

[M\_TABLE\_PERSISTENCE\_LOCATIONS System View](m-table-persistence-locations-system-view-20c67e7.md "Provides information about column store tables and their physical data locations.")

[TABLE\_PLACEMENT System View](../021-System-Views/table-placement-system-view-522cc8e.md "Provides table placement information.")

[M\_EFFECTIVE\_TABLE\_PLACEMENT System View](m-effective-table-placement-system-view-f3f74ec.md "Provides information about effective placement of tables.")

[TABLE\_PLACEMENT\_LOCATIONS System View](../021-System-Views/table-placement-locations-system-view-9e74012.md "Provides table placement location information.")

[M\_TABLE\_PLACEMENT\_LOCATIONS System View](m-table-placement-locations-system-view-7ecc1cc.md "Provides table placement location monitoring information.")

