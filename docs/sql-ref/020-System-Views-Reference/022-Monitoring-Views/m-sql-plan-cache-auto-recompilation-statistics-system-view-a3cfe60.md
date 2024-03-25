<!-- loioa3cfe6088df542c692a541a216c6112a -->

# M\_SQL\_PLAN\_CACHE\_AUTO\_RECOMPILATION\_STATISTICS System View

Provides information about triggered auto recompilations.




<table>
<tr>
<th valign="top">

COLUMN\_NAME

</th>
<th valign="top">

DATA\_TYPE\_NAME

</th>
<th valign="top">

COMMENTS

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

VOLUME\_ID

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

PLAN\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the logical plan ID, which is a non-negative value.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_STRING

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the statement string.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_HASH

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the MD5 hash value for STATEMENT\_STRING.

</td>
</tr>
<tr>
<td valign="top">

PREPARATION\_COUNT\_BY\_AUTO\_RECOMPILATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of plan preparations by automatic recompilation based on execution statistics.

</td>
</tr>
<tr>
<td valign="top">

PREPARATION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of plan preparations.

</td>
</tr>
<tr>
<td valign="top">

LAST\_AUTO\_RECOMPILATION\_REASON

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the last recompilation reason.

</td>
</tr>
<tr>
<td valign="top">

LAST\_AUTO\_RECOMPILATION\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last recompilation timestamp.

</td>
</tr>
</table>



<a name="loioa3cfe6088df542c692a541a216c6112a__section_v3n_gjp_j1c"/>

## Additional Information

Auto recompilation must be enabled for data to appear in this monitoring system view.

**Related Information**  


[Plan Cache](https://help.sap.com/docs/HANA_CLOUD_DATABASE/f9c5015e72e04fffa14d7d4f7267d897/f0aaab730a1540758a8f36c9aee2118a.html)

