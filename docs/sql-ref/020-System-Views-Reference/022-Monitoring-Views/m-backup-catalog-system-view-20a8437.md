<!-- loio20a8437d7519101495a3fa7ad9961cf6 -->

# M\_BACKUP\_CATALOG System View

Provides common data for all backup catalog entries.



<a name="loio20a8437d7519101495a3fa7ad9961cf6___m__b_a_c_k_u_p__c_a_t_a_l_o_g_1struct_M_BACKUP_CATALOG"/>

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

Dislays the unique ID of the backup catalog entry.

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

Displays the classification of backup catalog entries. The following types are supported: complete data backup, data snapshot, log backup, log missing, differential, and incremental backups.

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

Displays the unique ID of a data backup or a log backup, respectively. All backup files of a single data backup share the same BACKUP\_ID.

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

Displays the start time given in the server's local time.

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

Displays the start time given in UTC.

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

Displays the stop time given in the server's local time.

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

Displays the stop time given in UTC.

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

Displays the result of the corresponding action: successful, failed, running, cancel pending, or canceled.

</td>
</tr>
<tr>
<td valign="top">

COMMENT

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays any additional information.

</td>
</tr>
<tr>
<td valign="top">

MESSAGE

</td>
<td valign="top">

NVARCHAR\(512\)

</td>
<td valign="top">

Displays any additional information.

</td>
</tr>
<tr>
<td valign="top">

SYSTEM\_ID

</td>
<td valign="top">

NVARCHAR\(3\)

</td>
<td valign="top">

Displays the system identifier \(SID\) of the SAP HANA database.

</td>
</tr>
<tr>
<td valign="top">

ENCRYPTION\_ROOT\_KEY\_HASH

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the key hash used, if any, to locate the encryption root key in the keystore.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_DATABASE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the database that created the backup.

</td>
</tr>
</table>



<a name="loio20a8437d7519101495a3fa7ad9961cf6__section_utc_yk2_qbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_BACKUP\_CATALOG\_FILES System View](m-backup-catalog-files-system-view-20a8100.md "Provides location information for all backup catalog entries.")

[M\_BACKUP\_CONFIGURATION System View](m-backup-configuration-system-view-20a8891.md "Provides backup configuration statistics.")

[M\_BACKUP\_HISTORY\_BROKEN System View](m-backup-history-broken-system-view-2726f4d.md "Provides information about broken backup history entries.")

[M\_BACKUP\_SIZE\_ESTIMATIONS System View](m-backup-size-estimations-system-view-fc77a09.md "Provides the estimated size of the next data backup.")

[M\_BACKUP\_PROGRESS System View](m-backup-progress-system-view-783108b.md "Provides the progress of the most recent backup.")

