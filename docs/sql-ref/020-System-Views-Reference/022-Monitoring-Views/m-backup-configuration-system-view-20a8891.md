<!-- loio20a8891d7519101492c2bcf835d1c119 -->

# M\_BACKUP\_CONFIGURATION System View

Provides backup configuration statistics.



<a name="loio20a8891d7519101492c2bcf835d1c119___m__b_a_c_k_u_p__c_o_n_f_i_g_u_r_a_t_i_o_n_1struct_M_BACKUP_CONFIGURATION"/>

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

MAX\_RECOVERY\_FILE\_AGE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum recovery file age in seconds.

</td>
</tr>
<tr>
<td valign="top">

MAX\_RECOVERY\_BACKINT\_CHANNELS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum number of parallel backint channels per request during recovery.

</td>
</tr>
<tr>
<td valign="top">

BACKINT\_EXECUTABLE\_LINK

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the backint executable link name.

</td>
</tr>
<tr>
<td valign="top">

BACKINT\_EXECUTABLE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the backint executable file name.

</td>
</tr>
<tr>
<td valign="top">

BACKINT\_DATA\_BACKUP\_PATH

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the data backup directory for the backint.

</td>
</tr>
<tr>
<td valign="top">

BACKINT\_LOG\_BACKUP\_PATH

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the log backup directory for the backint.

</td>
</tr>
<tr>
<td valign="top">

BACKINT\_CATALOG\_BACKUP\_PATH

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the directory for backint-based catalog backups.

</td>
</tr>
<tr>
<td valign="top">

FILE\_DATA\_BACKUP\_PATH

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the default directory for file-based data backups.

</td>
</tr>
<tr>
<td valign="top">

FILE\_LOG\_BACKUP\_PATH

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the current directory for file-based log backups.

</td>
</tr>
<tr>
<td valign="top">

FILE\_CATALOG\_BACKUP\_PATH

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the directory for file-based catalog backups.

</td>
</tr>
<tr>
<td valign="top">

FILE\_ROOTKEY\_BACKUP\_PATH

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the directory for file-based rootkey backups.

</td>
</tr>
<tr>
<td valign="top">

LOG\_BACKUP\_TIMEOUT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the log backup timeout in seconds.

</td>
</tr>
<tr>
<td valign="top">

LOG\_BACKUP\_INTERVAL\_MODE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the log backup interval mode.

</td>
</tr>
<tr>
<td valign="top">

IS\_ROOT\_KEY\_BACKUP\_PASSWORD\_SET

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays if the root key backup password is set for the specified database: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

ROOT\_KEY\_ENCRYPTION\_CONTROL

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays where encryption is configured.

</td>
</tr>
<tr>
<td valign="top">

ROOT\_KEY\_BACKUP\_PASSWORD\_LAST\_CHANGE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays when the root key backup password was last changed.

</td>
</tr>
</table>

**Related Information**  


[M\_BACKUP\_CATALOG System View](m-backup-catalog-system-view-20a8437.md "Provides common data for all backup catalog entries.")

[M\_BACKUP\_CATALOG\_FILES System View](m-backup-catalog-files-system-view-20a8100.md "Provides location information for all backup catalog entries.")

[M\_BACKUP\_HISTORY\_BROKEN System View](m-backup-history-broken-system-view-2726f4d.md "Provides information about broken backup history entries.")

[M\_BACKUP\_SIZE\_ESTIMATIONS System View](m-backup-size-estimations-system-view-fc77a09.md "Provides the estimated size of the next data backup.")

[M\_BACKUP\_PROGRESS System View](m-backup-progress-system-view-783108b.md "Provides the progress of the most recent backup.")

