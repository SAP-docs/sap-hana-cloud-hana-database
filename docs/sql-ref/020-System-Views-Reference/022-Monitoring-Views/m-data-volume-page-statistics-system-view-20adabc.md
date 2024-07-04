<!-- loio20adabcc751910148d3df511a05d5390 -->

# M\_DATA\_VOLUME\_PAGE\_STATISTICS System View

Provides page usage statistics on data volumes.



<a name="loio20adabcc751910148d3df511a05d5390___m__d_a_t_a__v_o_l_u_m_e__p_a_g_e__s_t_a_t_i_s_t_i_c_s_1struct_M_DATA_VOLUME_PAGE_STATISTICS"/>

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

PAGE\_SIZECLASS

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the page size class.

</td>
</tr>
<tr>
<td valign="top">

PAGE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the page size in bytes.

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

INITIAL\_BLOCK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of init pages.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_ALLOCATE\_BLOCK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of single and group allocated blocks.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_SET\_BLOCK\_FREE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of single and group freed blocks.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_SET\_BLOCK\_FREE\_AFTER\_SAVEPOINT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of single and group freed-after-savepoint blocks.

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

Displays the number of used superblocks.

</td>
</tr>
<tr>
<td valign="top">

USED\_BLOCK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of used blocks.

</td>
</tr>
<tr>
<td valign="top">

SHADOW\_BLOCK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of shadow blocks.

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



<a name="loio20adabcc751910148d3df511a05d5390__section_rfz_2cn_vbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.



<a name="loio20adabcc751910148d3df511a05d5390___m__d_a_t_a__v_o_l_u_m_e__p_a_g_e__s_t_a_t_i_s_t_i_c_s_1fulldesc_M_DATA_VOLUME_PAGE_STATISTICS"/>

## Additional Information

This view contains information about the number and distribution of free, used, and shadow pages inside data volumes:

-   INITIAL\_BLOCK\_COUNT is the number of pages the database was started with.
-   TOTAL\_\*\_COUNT specifies the numbers of blocks allocated, freed or set to status FreeAfterSavepoint since the start of the database.
-   SUPERBLOCK\_COUNT, USED\_BLOCK\_COUNT, and SHADOW\_BLOCK\_COUNT columns contain the number of blocks or superblocks currently in use by the database.
-   FILL\_RATIO specifies the ratio of the minimum number of needed superblocks versus the actual number of used superblocks. Unused superblocks are not part of this formula.

This view has a resettable counterpart; you can see the values since the last reset in the M\_DATA\_VOLUME\_PAGE\_STATISTICS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_DATA_VOLUME_PAGE_STATISTICS_RESET;`.

**Related Information**  


[M\_DATA\_VOLUME\_PAGE\_STATISTICS\_RESET System View](m-data-volume-page-statistics-reset-system-view-20add39.md "Provides information about FreeBlockManager SizeClass statistics since the last reset.")

[M\_DATA\_VOLUMES System View](m-data-volumes-system-view-20ae1b2.md "Provides data volume statistics.")

[M\_DATA\_VOLUME\_PARTITION\_STATISTICS System View](m-data-volume-partition-statistics-system-view-7ff90b1.md "Provides data volume partition statistics.")

[M\_DATA\_VOLUME\_STATISTICS System View](m-data-volume-statistics-system-view-2f4b10f.md "Provides information on data volume statistics.")

[M\_DATA\_VOLUME\_SUPERBLOCK\_STATISTICS System View](m-data-volume-superblock-statistics-system-view-20adf77.md "Provides FreeBlockManager Superblock statistics.")

[HOST_DATA_VOLUME_PAGE_STATISTICS View (Embedded Statistics Service)](https://help.sap.com/viewer/323c57a017234d47a0e7da3e22345822/2024_3_QRC/en-US/c8009f66ea304c5d9893b8a89de9de8c.html "Specifies the data volume page information per host.") :arrow_upper_right:

[Statistics for Page-Loadable Storage](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/d791786e1f324187bd3a6ce2a8c1c601.html "A number of monitoring views report information at the partition, column, and column sub-object level, along with the existing non-paged memory size statistics.") :arrow_upper_right:

