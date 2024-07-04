<!-- loio20ae1b2875191014815ce801d2843a02 -->

# M\_DATA\_VOLUMES System View

Provides data volume statistics.



<a name="loio20ae1b2875191014815ce801d2843a02___m__d_a_t_a__v_o_l_u_m_e_s_1struct_M_DATA_VOLUMES"/>

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

FILE\_NAME

</td>
<td valign="top">

NVARCHAR\(512\)

</td>
<td valign="top">

Displays the filename of the data volume.

</td>
</tr>
<tr>
<td valign="top">

FILE\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the file ID of data volume.

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

SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of the data volume in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAX\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum size of the data volume in bytes.

</td>
</tr>
</table>



<a name="loio20ae1b2875191014815ce801d2843a02__section_wqg_sbn_vbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_DATA\_VOLUME\_PAGE\_STATISTICS System View](m-data-volume-page-statistics-system-view-20adabc.md "Provides page usage statistics on data volumes.")

[M\_DATA\_VOLUME\_PAGE\_STATISTICS\_RESET System View](m-data-volume-page-statistics-reset-system-view-20add39.md "Provides information about FreeBlockManager SizeClass statistics since the last reset.")

[M\_DATA\_VOLUME\_PARTITION\_STATISTICS System View](m-data-volume-partition-statistics-system-view-7ff90b1.md "Provides data volume partition statistics.")

[M\_DATA\_VOLUME\_STATISTICS System View](m-data-volume-statistics-system-view-2f4b10f.md "Provides information on data volume statistics.")

[M\_DATA\_VOLUME\_SUPERBLOCK\_STATISTICS System View](m-data-volume-superblock-statistics-system-view-20adf77.md "Provides FreeBlockManager Superblock statistics.")

[M\_VOLUME\_SIZES System View](m-volume-sizes-system-view-20cb217.md "Provides information about volume sizes used by SAP HANA servers.")

