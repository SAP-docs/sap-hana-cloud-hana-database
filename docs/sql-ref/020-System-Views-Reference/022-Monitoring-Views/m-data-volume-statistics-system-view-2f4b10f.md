<!-- loio2f4b10f44dc749ad80720a4afc6a7dcf -->

# M\_DATA\_VOLUME\_STATISTICS System View

Provides information on data volume statistics.



<a name="loio2f4b10f44dc749ad80720a4afc6a7dcf___m__d_a_t_a__v_o_l_u_m_e__s_t_a_t_i_s_t_i_c_s_1struct_M_DATA_VOLUME_STATISTICS"/>

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

PARTITION\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of partitions.

</td>
</tr>
<tr>
<td valign="top">

PATH\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of partition paths.

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

Displays the used size of the data volume in bytes.

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

Displays the total size of the data volume in bytes.

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

Displays the fill ratio of the data volume.

</td>
</tr>
</table>

**Related Information**  


[M\_DATA\_STATISTICS System View](m-data-statistics-system-view-4f74378.md "Lists data statistics generated when you query column and row store object.")

[M\_DATA\_VOLUMES System View](m-data-volumes-system-view-20ae1b2.md "Provides data volume statistics.")

[M\_DATA\_VOLUME\_PAGE\_STATISTICS System View](m-data-volume-page-statistics-system-view-20adabc.md "Provides page usage statistics on data volumes.")

[M\_DATA\_VOLUME\_PARTITION\_STATISTICS System View](m-data-volume-partition-statistics-system-view-7ff90b1.md "Provides data volume partition statistics.")

[M\_DATA\_VOLUME\_SUPERBLOCK\_STATISTICS System View](m-data-volume-superblock-statistics-system-view-20adf77.md "Provides FreeBlockManager Superblock statistics.")

[M\_VOLUME\_SIZES System View](m-volume-sizes-system-view-20cb217.md "Provides information about volume sizes used by SAP HANA servers.")

