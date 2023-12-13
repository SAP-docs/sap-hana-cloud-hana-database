<!-- loio20c9c84a751910149141f19b303f75e6 -->

# M\_VOLUME\_FILES System View

Provides information about volume files.



<a name="loio20c9c84a751910149141f19b303f75e6___m__v_o_l_u_m_e__f_i_l_e_s_1struct_M_VOLUME_FILES"/>

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

FILE\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the type of file: DATA, LOG, and so on.

</td>
</tr>
<tr>
<td valign="top">

FILE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the file name.

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

Displays the size of used data within the file in bytes.

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

Displays the total file size in bytes.

</td>
</tr>
</table>



<a name="loio20c9c84a751910149141f19b303f75e6___m__v_o_l_u_m_e__f_i_l_e_s_1fulldesc_M_VOLUME_FILES"/>

## Additional Information

Displays information about files in the volume directories. All files in these directories are shown, but only registered files \(files currently used by the database\) have a file type. ***TOTAL\_SIZE*** is the size as reported by the file system.

The meaning of ***USED\_SIZE*** depends on the file type:

-   **DATA:** Displays the size of used and shadow pages in the data volume file.

-   **LOG:** Displays that the used size equals the ***TOTAL\_SIZE***.


**Related Information**  


[M\_DATA\_VOLUME\_PARTITION\_STATISTICS System View](m-data-volume-partition-statistics-system-view-7ff90b1.md "Provides data volume partition statistics.")

[M\_DATA\_VOLUME\_STATISTICS System View](m-data-volume-statistics-system-view-2f4b10f.md "Provides information on data volume statistics.")

