<!-- loio20cb3e1975191014a6979aa8976f409b -->

# M\_VOLUMES System View

Provides information about the volumes used by SAP HANA servers.



<a name="loio20cb3e1975191014a6979aa8976f409b___m__v_o_l_u_m_e_s_1struct_M_VOLUMES"/>

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

SERVICE\_NAME



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the service name.



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

Displays the volume ID.



</td>
</tr>
<tr>
<td valign="top">

SUBPATH



</td>
<td valign="top">

NVARCHAR\(512\)



</td>
<td valign="top">

Displays the subpath appended to M\_DISKS.PATH.



</td>
</tr>
<tr>
<td valign="top">

REMOVE\_STATUS



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the remove progress.



</td>
</tr>
</table>

**Related Information**  


[M\_VOLUME\_SIZES System View](m-volume-sizes-system-view-20cb217.md "Provides information about volume sizes used by SAP HANA servers.")

[M\_VOLUME\_FILES System View](m-volume-files-system-view-20c9c84.md "Provides information about volume files.")

[M\_DATA\_VOLUME\_STATISTICS System View](m-data-volume-statistics-system-view-2f4b10f.md "Provides information on data volume statistics.")

[M\_PERSISTENT\_MEMORY\_VOLUME\_STATISTICS System View](m-persistent-memory-volume-statistics-system-view-33f228a.md "Reports the statistics of physical lifecycle events of blocks managed by SAP HANA services on the persistent memory volumes.")

[M\_PERSISTENT\_MEMORY\_VOLUMES System View](m-persistent-memory-volumes-system-view-8aba468.md "Reports the capacity, usage and metadata of persistent memory volumes.")

