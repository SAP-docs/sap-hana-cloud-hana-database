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

**Related Information**  


[M\_BACKUP\_HISTORY\_BROKEN System View](../022-Monitoring-Views/m-backup-history-broken-system-view-2726f4d.md "Provides information about broken backup history entries.")

[M\_JOB\_HISTORY\_INFO System View](../022-Monitoring-Views/m-job-history-info-system-view-6c9f04a.md "Provides a history of long running system operations.")

