<!-- loioa2aac2ee72b341699fa8eb3988d8cecb -->

# M\_DISK\_USAGE System View

Provides disk usage information on host basis group by resource types.



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

USAGE\_TYPE



</td>
<td valign="top">

NVARCHAR\(11\)



</td>
<td valign="top">

Displays the resource type: LOG, DATA, TRACE, DATA\_BACKUP, LOG\_BACKUP, CATALOG\_BACKUP, ROOTKEY\_BACKUP, or AUDITING.



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

Displays the size of the used disk space in bytes.



</td>
</tr>
<tr>
<td valign="top">

FILE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the size of all files in bytes.



</td>
</tr>
</table>

**Related Information**  


[M\_DISKS System View](m-disks-system-view-20aef7a.md "Provides information about disk configuration and utilization of the host machine.")

