<!-- loio20cb217375191014baaae23d8bc9e927 -->

# M\_VOLUME\_SIZES System View

Provides information about volume sizes used by SAP HANA servers.



<a name="loio20cb217375191014baaae23d8bc9e927___m__v_o_l_u_m_e__s_i_z_e_s_1struct_M_VOLUME_SIZES"/>

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

VOLUME\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the volume ID. See M\_VOLUMES.



</td>
</tr>
<tr>
<td valign="top">

DISK\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the disk ID. See M\_DISKS.



</td>
</tr>
<tr>
<td valign="top">

DATA\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the data area size in bytes.



</td>
</tr>
<tr>
<td valign="top">

LOG\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the log area size in bytes.



</td>
</tr>
</table>

**Related Information**  


[M\_DISKS System View](m-disks-system-view-20aef7a.md "Provides information about disk configuration and utilization of the host machine.")

[M\_VOLUMES System View](m-volumes-system-view-20cb3e1.md "Provides information about the volumes used by SAP HANA servers.")

