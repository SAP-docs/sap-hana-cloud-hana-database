<!-- loiofc82c6c5212e413fb754c91123ae2cab -->

# M\_TIMEZONE\_ALERTS System View

Provides information about alerts relating to the status of SAP HANA internal timezone conversion.



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

STATUS

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the status to report: TABLES NOT FOUND, TABLES EMPTY, NO SYSTEM TIMEZONE, SYSTEM TIMEZONE DISABLED, or CONVERSION MISMATCH.

</td>
</tr>
<tr>
<td valign="top">

TIMEZONE\_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the name of the timezone to which status message applies or NULL if the status does not apply to a specific timezone.

</td>
</tr>
<tr>
<td valign="top">

MISMATCH\_BEGIN

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the UTC time at which the first mismatch of the mismatch period occurred or NULL if no mismatch applies.

</td>
</tr>
<tr>
<td valign="top">

MISMATCH\_END

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the UTC time at which the last mismatch of the mismatch period occurred or NULL if no mismatch applies.

</td>
</tr>
<tr>
<td valign="top">

DETAILS

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the detailed information.

</td>
</tr>
</table>

**Related Information**  


[TIMEZONES System View](../021-System-Views/timezones-system-view-adeba8e.md "Provides information about the available time zones, together with their originating data set.")

[ALTER SYSTEM CLEAR TRACES Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-traces-statement-system-management-20d1281.md "Clears trace files opened by SAP HANA.")

[ALTER SYSTEM CLEAR TIMEZONE CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-timezone-cache-statement-system-management-a780495.md "Clears cached timezone definitions.")

[UTCTOLOCAL Function \(Datetime\)](../../010-SQL-Reference/011-SQL-Functions/utctolocal-function-datetime-20f52f4.md "Converts the specified timestamp between UTC and local time.")

[LOCALTOUTC Function \(Datetime\)](../../010-SQL-Reference/011-SQL-Functions/localtoutc-function-datetime-20e39ac.md "A timestamp parameter holding the time to be converted between UTC and local time.")

