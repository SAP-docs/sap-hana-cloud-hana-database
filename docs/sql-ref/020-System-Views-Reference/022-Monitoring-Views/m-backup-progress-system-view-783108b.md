<!-- loio783108ba8b8b4c709959220b4535a010 -->

# M\_BACKUP\_PROGRESS System View

Provides the progress of the most recent backup.



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

BACKUP\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the unique ID of a data backup. All backup files of a single data backup share the same BACKUP\_ID.



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

Displays the name of the service.



</td>
</tr>
<tr>
<td valign="top">

ENTRY\_TYPE\_NAME



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the classification of the type of backup.



</td>
</tr>
<tr>
<td valign="top">

SYS\_START\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the local server time that the backup started.



</td>
</tr>
<tr>
<td valign="top">

UTC\_START\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the time that the backup started.



</td>
</tr>
<tr>
<td valign="top">

SYS\_END\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the local server time that the backup was terminated.



</td>
</tr>
<tr>
<td valign="top">

UTC\_END\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the time that the backup was terminated.



</td>
</tr>
<tr>
<td valign="top">

STATE\_NAME



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the current state of the backup.



</td>
</tr>
<tr>
<td valign="top">

BACKUP\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total amount of data in bytes.



</td>
</tr>
<tr>
<td valign="top">

TRANSFERRED\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the amount of data transferred in bytes.



</td>
</tr>
</table>

**Related Information**  


[M\_BACKUP\_CATALOG System View](m-backup-catalog-system-view-20a8437.md "Provides common data for all backup catalog entries.")

[M\_BACKUP\_CATALOG\_FILES System View](m-backup-catalog-files-system-view-20a8100.md "Provides location information for all backup catalog entries.")

[M\_BACKUP\_CONFIGURATION System View](m-backup-configuration-system-view-20a8891.md "Provides backup configuration statistics.")

[M\_BACKUP\_HISTORY\_BROKEN System View](m-backup-history-broken-system-view-2726f4d.md "Provides information about broken backup history entries.")

[M\_BACKUP\_SIZE\_ESTIMATIONS System View](m-backup-size-estimations-system-view-fc77a09.md "Provides the estimated size of the next data backup.")

