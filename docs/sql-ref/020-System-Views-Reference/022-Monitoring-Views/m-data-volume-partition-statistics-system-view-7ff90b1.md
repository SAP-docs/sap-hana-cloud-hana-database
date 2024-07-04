<!-- loio7ff90b14514b4214ba3e6ac91ec80d8e -->

# M\_DATA\_VOLUME\_PARTITION\_STATISTICS System View

Provides data volume partition statistics.



<a name="loio7ff90b14514b4214ba3e6ac91ec80d8e___m__d_a_t_a__v_o_l_u_m_e__p_a_r_t_i_t_i_o_n__s_t_a_t_i_s_t_i_c_s_1struct_M_DATA_VOLUME_PARTITION_STATISTICS"/>

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

FILE\_NAME\_PATTERN

</td>
<td valign="top">

NVARCHAR\(512\)

</td>
<td valign="top">

Displays the file name pattern for the data volume partition file.

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

Displays the data volume state. This can be specified as ACTIVATING or ACTIVE. When a data volume partition is added, it is in the ACTIVATING state and is not usable until the next savepoint, at which time it enters the ACTIVE state.

</td>
</tr>
<tr>
<td valign="top">

MAX\_FILE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum file size for the data volume files in bytes. A value of 0 means that there is no limitation for the file size.

</td>
</tr>
<tr>
<td valign="top">

USED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the used size of the data volume partition in bytes.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size of the data volume partition in bytes.

</td>
</tr>
<tr>
<td valign="top">

FILES\_SIZE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the size of the data volume files on the disk in bytes.

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

Displays the fill ratio of the data volume partition.

</td>
</tr>
</table>



<a name="loio7ff90b14514b4214ba3e6ac91ec80d8e__section_ix5_tcn_vbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_DATA\_VOLUME\_PAGE\_STATISTICS\_RESET System View](m-data-volume-page-statistics-reset-system-view-20add39.md "Provides information about FreeBlockManager SizeClass statistics since the last reset.")

[M\_DATA\_VOLUMES System View](m-data-volumes-system-view-20ae1b2.md "Provides data volume statistics.")

[M\_DATA\_VOLUME\_STATISTICS System View](m-data-volume-statistics-system-view-2f4b10f.md "Provides information on data volume statistics.")

[M\_DATA\_VOLUME\_SUPERBLOCK\_STATISTICS System View](m-data-volume-superblock-statistics-system-view-20adf77.md "Provides FreeBlockManager Superblock statistics.")

[Static and Dynamic Partition Pruning](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/602e0dcb40364401a092329296405b84.html "An important partitioning strategy to improve performance is to match partitions wherever possible with the most frequently queried data so that data pruning is possible.") :arrow_upper_right:

