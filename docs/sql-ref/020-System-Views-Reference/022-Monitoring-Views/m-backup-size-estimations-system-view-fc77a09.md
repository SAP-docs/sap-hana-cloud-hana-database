<!-- loiofc77a09ad59f481bb86d5ec534235b8b -->

# M\_BACKUP\_SIZE\_ESTIMATIONS System View

Provides the estimated size of the next data backup.



<a name="loiofc77a09ad59f481bb86d5ec534235b8b__section_azn_c2b_x2b"/>

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

Displays the classification of the type of backup. The following types are supported: complete data backup, differential, and incremental backups.



</td>
</tr>
<tr>
<td valign="top">

ESTIMATED\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the estimated size of the backup in bytes.



</td>
</tr>
</table>



<a name="loiofc77a09ad59f481bb86d5ec534235b8b__section_bzn_c2b_x2b"/>

## Additional Information

> ### Note:  
> The actual backup size may differ from the estimation shown in this view.

The ENTRY\_TYPE\_NAME column is equivalent to the column in the M\_BACKUP\_CATALOG view. The table contains records for each service with a volume for all the supported backup types. You cannot create a differential or incremental backup or view estimation of a differential or incremental backup if a complete backup does not exist. However, once a complete backup exists, you can view estimations for differential or incremental backups, even if these backups have not been created.

**Related Information**  


[M\_BACKUP\_CATALOG System View](m-backup-catalog-system-view-20a8437.md "Provides common data for all backup catalog entries.")

[M\_BACKUP\_CATALOG\_FILES System View](m-backup-catalog-files-system-view-20a8100.md "Provides location information for all backup catalog entries.")

[M\_BACKUP\_CONFIGURATION System View](m-backup-configuration-system-view-20a8891.md "Provides backup configuration statistics.")

[M\_BACKUP\_HISTORY\_BROKEN System View](m-backup-history-broken-system-view-2726f4d.md "Provides information about broken backup history entries.")

[M\_BACKUP\_PROGRESS System View](m-backup-progress-system-view-783108b.md "Provides the progress of the most recent backup.")

