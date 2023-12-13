<!-- loioa8cb93e80f494c15b19fc41109e7343c -->

# PERSISTENCE\_HISTORY System View

Records the database version history.



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

CHANGE\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the order of database installations.

</td>
</tr>
<tr>
<td valign="top">

CHANGE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the timestamp when the database was upgraded or recovered to the current version.

</td>
</tr>
<tr>
<td valign="top">

VERSION

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the version.

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

Displays the system ID of the SAP HANA instance.

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

Displays the host name of the catalog coordinator. Only users with INIFILE ADMIN or CATALOG READ privileges are able to view this column.

</td>
</tr>
</table>



<a name="loioa8cb93e80f494c15b19fc41109e7343c__section_r1s_qr4_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_BACKUP\_HISTORY\_BROKEN System View](../022-Monitoring-Views/m-backup-history-broken-system-view-2726f4d.md "Provides information about broken backup history entries.")

[M\_JOB\_HISTORY\_INFO System View](../022-Monitoring-Views/m-job-history-info-system-view-6c9f04a.md "Provides a history of long running system operations.")

