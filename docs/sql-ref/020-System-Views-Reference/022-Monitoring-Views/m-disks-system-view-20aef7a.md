<!-- loio20aef7a275191014b37acbc35b4f20a4 -->

# M\_DISKS System View

Provides information about disk configuration and utilization of the host machine.



<a name="loio20aef7a275191014b37acbc35b4f20a4___m__d_i_s_k_s_1struct_M_DISKS"/>

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

DISK\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the disk ID.



</td>
</tr>
<tr>
<td valign="top">

DEVICE\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the database internal device ID.



</td>
</tr>
<tr>
<td valign="top">

HOST



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the host name. This is only set if the disk is used by exactly one host.



</td>
</tr>
<tr>
<td valign="top">

PATH



</td>
<td valign="top">

NVARCHAR\(512\)



</td>
<td valign="top">

Displays the path.



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

Displays the subpath.



</td>
</tr>
<tr>
<td valign="top">

FILESYSTEM\_TYPE



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the filesystem type.



</td>
</tr>
<tr>
<td valign="top">

USAGE\_TYPE



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the usage type. Values are: LOG, DATA, TRACE, DATA\_BACKUP, LOG\_BACKUP, CATALOG\_BACKUP, ROOTKEY\_BACKUP, or XSA\_WORKSPACE.



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

Displays the volume of the usable space in bytes.



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

Displays the volume size in bytes.



</td>
</tr>
<tr>
<td valign="top">

TOTAL\_DEVICE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total device size returned by the operating system in bytes.



</td>
</tr>
<tr>
<td valign="top">

MOUNT\_SOURCE



</td>
<td valign="top">

NVARCHAR\(512\)



</td>
<td valign="top">

Displays the source of the mount.



</td>
</tr>
<tr>
<td valign="top">

MOUNT\_PATH



</td>
<td valign="top">

NVARCHAR\(512\)



</td>
<td valign="top">

Displays the mount path.



</td>
</tr>
<tr>
<td valign="top">

MOUNT\_DETAILS



</td>
<td valign="top">

NVARCHAR\(2000\)



</td>
<td valign="top">

Displays the mount details as stated in `/proc/mount`.



</td>
</tr>
</table>

**Related Information**  


[M\_DISK\_USAGE System View](m-disk-usage-system-view-a2aac2e.md "Provides disk usage information on host basis group by resource types.")

