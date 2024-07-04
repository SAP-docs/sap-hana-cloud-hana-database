<!-- loio20a8100e75191014870ecf908b5d2abf -->

# M\_BACKUP\_CATALOG\_FILES System View

Provides location information for all backup catalog entries.



<a name="loio20a8100e75191014870ecf908b5d2abf___m__b_a_c_k_u_p__c_a_t_a_l_o_g__f_i_l_e_s_1struct_M_BACKUP_CATALOG_FILES"/>

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

ENTRY\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the unique ID of a backup catalog entry.

</td>
</tr>
<tr>
<td valign="top">

BACKUP\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the unique ID of a data backup and log backup respectively. All backup files of a single data backup share the same backup ID.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the persistence volume ID.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_TYPE\_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the type of persistence to be backed up: volume or topology.

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

SERVICE\_TYPE\_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the type of database service: indexserver, nameserver, or statisticsserver.

</td>
</tr>
<tr>
<td valign="top">

REDO\_LOG\_POSITION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

In the case of a data backup, this value displays the log position that must be processed next when a log recovery is requested after restoring the data backup.

</td>
</tr>
<tr>
<td valign="top">

FIRST\_REDO\_LOG\_POSITION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

In the case of a log backup, this value displays the log position of the oldest log entry contained in the backup.

</td>
</tr>
<tr>
<td valign="top">

LAST\_REDO\_LOG\_POSITION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

In the case of a log backup, this value displays the log position of the newest log entry contained in the backup.

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

Displays the size of the backup in bytes.

</td>
</tr>
<tr>
<td valign="top">

DESTINATION\_PATH

</td>
<td valign="top">

NVARCHAR\(512\)

</td>
<td valign="top">

Displays that the data or log backup was written to this location.

</td>
</tr>
<tr>
<td valign="top">

DESTINATION\_TYPE\_NAME

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the type of location: file or backint.

</td>
</tr>
<tr>
<td valign="top">

EXTERNAL\_BACKUP\_ID

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the identifier of the backup received from a backup tool.

</td>
</tr>
<tr>
<td valign="top">

LOG\_SEGMENT\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

In the case of a log backup, this value displays the number of log segments contained in the backup. In the case of non-log backups, this column always contains the SQL NULL value.

</td>
</tr>
</table>



<a name="loio20a8100e75191014870ecf908b5d2abf__section_egs_hl2_qbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_BACKUP\_CATALOG System View](m-backup-catalog-system-view-20a8437.md "Provides common data for all backup catalog entries.")

[M\_BACKUP\_CONFIGURATION System View](m-backup-configuration-system-view-20a8891.md "Provides backup configuration statistics.")

[M\_BACKUP\_HISTORY\_BROKEN System View](m-backup-history-broken-system-view-2726f4d.md "Provides information about broken backup history entries.")

[M\_BACKUP\_SIZE\_ESTIMATIONS System View](m-backup-size-estimations-system-view-fc77a09.md "Provides the estimated size of the next data backup.")

[M\_BACKUP\_PROGRESS System View](m-backup-progress-system-view-783108b.md "Provides the progress of the most recent backup.")

