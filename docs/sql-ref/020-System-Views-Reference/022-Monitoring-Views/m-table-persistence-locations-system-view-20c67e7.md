<!-- loio20c67e7875191014a84fa76c9f7b6ae3 -->

# M\_TABLE\_PERSISTENCE\_LOCATIONS System View

Provides information about column store tables and their physical data locations.



<a name="loio20c67e7875191014a84fa76c9f7b6ae3___m__t_a_b_l_e__p_e_r_s_i_s_t_e_n_c_e__l_o_c_a_t_i_o_n_s_1struct_M_TABLE_PERSISTENCE_LOCATIONS"/>

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

PART\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the table partition ID:

-   For partitioned tables, the part ID is equal to the sequential number of the partition, starting at 1.
-   In the case of replicated tables, the part ID is 1 for the original table and subsequent part IDs are assigned to replica tables.
-   The part ID is 0 for tables that are not partitioned.
-   A part ID value of -1 indicates that the table schema is currently in being modified.



</td>
</tr>
<tr>
<td valign="top">

PERSISTENCE\_HOST



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the host where table data is located.



</td>
</tr>
<tr>
<td valign="top">

PERSISTENCE\_PORT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the port where table data is located.



</td>
</tr>
</table>



<a name="loio20c67e7875191014a84fa76c9f7b6ae3___m__t_a_b_l_e__p_e_r_s_i_s_t_e_n_c_e__l_o_c_a_t_i_o_n_s_1fulldesc_M_TABLE_PERSISTENCE_LOCATIONS"/>

## Additional Information

This view shows information on which node contains the persistence parts of a table. This includes the assigned node as visible from the M\_TABLE\_LOCATIONS view, but also includes other nodes that still contain some persistence of the table. This could occur if a table is moved and not yet merged. In this case the old node still contains some persistence content for the table beside the currently assigned node.

**Related Information**  


[M\_TABLE\_LOCATIONS System View](m-table-locations-system-view-20c65d5.md "Provides information about tables and their logical location. Physical locations are shown in M_TABLE_PERSISTENCE_LOCATIONS.")

[Set an Explicit Table Location](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/d4a2e245a0f74edaa98e47599facf1a4.html "You can set an explicit table location with SQL commands.") :arrow_upper_right:

[M\_TABLE\_PERSISTENCE\_LOCATION\_STATISTICS System View](m-table-persistence-location-statistics-system-view-2d7c695.md "Provides persistence storage statistics for tables partitions and services.")

