<!-- loio20adf779751910148b69cc65258b2f23 -->

# M\_DATA\_VOLUME\_SUPERBLOCK\_STATISTICS System View

Provides FreeBlockManager Superblock statistics.



<a name="loio20adf779751910148b69cc65258b2f23___m__d_a_t_a__v_o_l_u_m_e__s_u_p_e_r_b_l_o_c_k__s_t_a_t_i_s_t_i_c_s_1struct_M_DATA_VOLUME_SUPERBLOCK_STATISTICS"/>

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

Displays the internal port number.

</td>
</tr>
<tr>
<td valign="top">

VOLUME\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the persistence volume ID.

</td>
</tr>
<tr>
<td valign="top">

PARTITION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the partition ID. Returns the following:

-   For partitioned tables, the part ID is equal to the sequential number of the partition, starting at 1.
-   In the case of replicated tables, the part ID is 1 for the original table and subsequent part IDs are assigned to replica tables.
-   The part ID is 0 for tables that are not partitioned.
-   A part ID value of -1 indicates that a modification of the table schema is in progress.



</td>
</tr>
<tr>
<td valign="top">

DATA\_VOLUME\_NAME

</td>
<td valign="top">

NVARCHAR\(512\)

</td>
<td valign="top">

Displays the data volume name.

</td>
</tr>
<tr>
<td valign="top">

STATE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the data volume state: ACTIVATING, ACTIVE, or DEACTIVATING.

</td>
</tr>
<tr>
<td valign="top">

SUPERBLOCK\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the superblock size in bytes.

</td>
</tr>
<tr>
<td valign="top">

USED\_SUPERBLOCK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of used superblocks.

</td>
</tr>
<tr>
<td valign="top">

SUPERBLOCK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of superblocks.

</td>
</tr>
<tr>
<td valign="top">

FILL\_RATIO

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the fill ratio.

</td>
</tr>
</table>



<a name="loio20adf779751910148b69cc65258b2f23__section_hnx_mdn_vbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.



<a name="loio20adf779751910148b69cc65258b2f23___m__d_a_t_a__v_o_l_u_m_e__s_u_p_e_r_b_l_o_c_k__s_t_a_t_i_s_t_i_c_s_1fulldesc_M_DATA_VOLUME_SUPERBLOCK_STATISTICS"/>

## Additional Information

This view shows information about the number and distribution of superblocks inside data volumes:

-   SUPERBLOCK\_COUNT is the total number of superblocks.
-   USED\_SUPERBLOCK\_COUNT is the number of superblocks currently occupied by at least one used or shadow page.
-   FILL\_RATIO specifies the ratio of the number of used superblocks versus the total number of superblocks. The fill ratio of the superblocks themselves is not part of this formula.

**Related Information**  


[M\_DATA\_VOLUME\_PAGE\_STATISTICS System View](m-data-volume-page-statistics-system-view-20adabc.md "Provides page usage statistics on data volumes.")

[M\_DATA\_STATISTICS System View](m-data-statistics-system-view-4f74378.md "Lists data statistics generated when you query column and row store object.")

[M\_DATA\_VOLUMES System View](m-data-volumes-system-view-20ae1b2.md "Provides data volume statistics.")

[M\_DATA\_VOLUME\_PARTITION\_STATISTICS System View](m-data-volume-partition-statistics-system-view-7ff90b1.md "Provides data volume partition statistics.")

[HOST_DATA_VOLUME_SUPERBLOCK_STATISTICS View (Embedded Statistics Service)](https://help.sap.com/viewer/323c57a017234d47a0e7da3e22345822/2024_3_QRC/en-US/54c8f4e486514185862d01fbc805fecf.html "Data volume superblock information per host.") :arrow_upper_right:

