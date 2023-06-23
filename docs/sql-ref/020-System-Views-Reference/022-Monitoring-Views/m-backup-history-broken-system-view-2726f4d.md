<!-- loio2726f4d07068416c8761b4da9cabfcf3 -->

# M\_BACKUP\_HISTORY\_BROKEN System View

Provides information about broken backup history entries.



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

Displays the unique ID of the broken backup history entry.



</td>
</tr>
<tr>
<td valign="top">

SYS\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the time at which the broken backup history was detected. The time is provided in the system's local time.



</td>
</tr>
<tr>
<td valign="top">

UTC\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the time at which the broken backup history was detected. The time is given in UTC time.



</td>
</tr>
<tr>
<td valign="top">

SOURCE\_ID



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

Displays the type of database service.



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

Displays the redo log position of the broken backup history entry.



</td>
</tr>
<tr>
<td valign="top">

REASON



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the reason for the broken backup history:

-   Unknown reason
-   Redo log writing disabled on persistence session
-   Redo log flush partially turned OFF
-   Redo log flush turned ON
-   Migration to "level 2 delta"
-   General reason for persistence factory



</td>
</tr>
<tr>
<td valign="top">

MESSAGE



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays any additional information.



</td>
</tr>
</table>

**Related Information**  


[M\_BACKUP\_CATALOG System View](m-backup-catalog-system-view-20a8437.md "Provides common data for all backup catalog entries.")

[M\_BACKUP\_CATALOG\_FILES System View](m-backup-catalog-files-system-view-20a8100.md "Provides location information for all backup catalog entries.")

[M\_BACKUP\_CONFIGURATION System View](m-backup-configuration-system-view-20a8891.md "Provides backup configuration statistics.")

[M\_BACKUP\_SIZE\_ESTIMATIONS System View](m-backup-size-estimations-system-view-fc77a09.md "Provides the estimated size of the next data backup.")

[M\_BACKUP\_PROGRESS System View](m-backup-progress-system-view-783108b.md "Provides the progress of the most recent backup.")

