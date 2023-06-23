<!-- loio729e472b1fed465883b9b603886c4927 -->

# M\_DSO\_OPERATIONS System View

Provides information about data store object \(DSO\) operations.



<a name="loio729e472b1fed465883b9b603886c4927__section_et3_qwq_wy"/>

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

OPERATION



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the operation: ACTIVATION or ROLLBACK.



</td>
</tr>
<tr>
<td valign="top">

USAGE\_MODE



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the usage mode. This clarifies which variant of DSO is used:

-   ADSO for advanced DSOs
-   ODSO for classic DSOs with persistent change log tables
-   IMO for older in-memory optimized DSOs \(not recommended\)



</td>
</tr>
<tr>
<td valign="top">

ACTIVATION\_IDS



</td>
<td valign="top">

NVARCHAR\(1024\)



</td>
<td valign="top">

Displays the activation IDs.



</td>
</tr>
<tr>
<td valign="top">

TARGET\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name of the target table.



</td>
</tr>
<tr>
<td valign="top">

TARGET\_TABLE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the target table.



</td>
</tr>
<tr>
<td valign="top">

START\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the start time of the operation.



</td>
</tr>
<tr>
<td valign="top">

END\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the end time of the operation.



</td>
</tr>
<tr>
<td valign="top">

ERROR\_CODE



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the last error code in the case of a failure. Otherwise this value is 0.



</td>
</tr>
<tr>
<td valign="top">

ERROR\_MESSAGE



</td>
<td valign="top">

NVARCHAR\(2000\)



</td>
<td valign="top">

Displays the last error message in the case of a failure. Otherwise this value displays "no error".



</td>
</tr>
<tr>
<td valign="top">

SOURCE\_RECORD\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of source table rows activated.



</td>
</tr>
<tr>
<td valign="top">

INSERT\_RECORD\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of rows inserted into the target table.



</td>
</tr>
<tr>
<td valign="top">

DELETE\_RECORD\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of rows deleted from the target table.



</td>
</tr>
<tr>
<td valign="top">

UPDATE\_RECORD\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of target table rows that were updated.



</td>
</tr>
<tr>
<td valign="top">

CHANGE\_LOG\_RECORD\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of rows inserted into the change log.



</td>
</tr>
<tr>
<td valign="top">

PACKAGE\_PROCESSING\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the sum of the processing times for all packages in microseconds.



</td>
</tr>
<tr>
<td valign="top">

PACKAGE\_INBOUND\_QUEUE\_READ\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the sum of the inbound queue read times in all packages in microseconds.



</td>
</tr>
<tr>
<td valign="top">

PACKAGE\_ACTIVE\_DATA\_READ\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the sum of the active data read times in all packages in microseconds.



</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_DATA\_READ\_RECORD\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total number of active rows read.



</td>
</tr>
<tr>
<td valign="top">

PACKAGE\_CALCULATION\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the sum of the calculation times for the change log and the new active data in microseconds.



</td>
</tr>
<tr>
<td valign="top">

AVG\_CALCULATION\_JOB\_COUNT



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Displays the active number of jobs per package used for the calculation of the change log and the new active data.



</td>
</tr>
<tr>
<td valign="top">

CHANGE\_LOG\_INSERT\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the sum of the time spent inserting the change log records in microseconds.



</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_DATA\_INSERT\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the sum of the time spent inserting new active data records in microseconds.



</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_DATA\_UPDATE\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the sum of the time spent updating active data records in microseconds.



</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_DATA\_DELETE\_TIME



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the time spent deleting active data records in microseconds.



</td>
</tr>
<tr>
<td valign="top">

PACKAGE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total number of packages.



</td>
</tr>
<tr>
<td valign="top">

PARAMETERS



</td>
<td valign="top">

NCLOB\(2147483647\)



</td>
<td valign="top">

Displays the call parameters.



</td>
</tr>
<tr>
<td valign="top">

CONFIGURATION



</td>
<td valign="top">

NCLOB\(2147483647\)



</td>
<td valign="top">

Displays the non-default, DSO-specific `ini` file settings used by the operation.



</td>
</tr>
<tr>
<td valign="top">

USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the user name.



</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the application user name.



</td>
</tr>
</table>

**Related Information**  


[M\_JOB\_PROGRESS System View](m-job-progress-system-view-20b1b23.md "Provides information about current long running system operations.")

