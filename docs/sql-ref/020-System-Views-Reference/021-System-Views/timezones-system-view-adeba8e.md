<!-- loioadeba8e5b0c04b1880800f3e06b455b4 -->

# TIMEZONES System View

Provides information about the available time zones, together with their originating data set.



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

TIMEZONE\_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the name of the respective time zone that can be used as parameter to give the source a respective destination timezone for UTCTOLOCAL and LOCALTOUTC.

</td>
</tr>
<tr>
<td valign="top">

TIMEZONE\_DATASET

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays the data set where the time zone's definition is located. Possible values include: SAP, PLATFORM. The value of this column can thus be directly used as an input for the respective UTCTOLOCAL/LOCALTOUTC parameter.

</td>
</tr>
</table>



<a name="loioadeba8e5b0c04b1880800f3e06b455b4__section_cmn_zyz_2zb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[ALTER SYSTEM CLEAR TIMEZONE CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-timezone-cache-statement-system-management-a780495.md "Clears cached timezone definitions.")

[LOCALTOUTC Function \(Datetime\)](../../010-SQL-Reference/011-SQL-Functions/localtoutc-function-datetime-20e39ac.md "A timestamp parameter holding the time to be converted between UTC and local time.")

[UTCTOLOCAL Function \(Datetime\)](../../010-SQL-Reference/011-SQL-Functions/utctolocal-function-datetime-20f52f4.md "Converts the specified timestamp between UTC and local time.")

[M\_TIMEZONE\_ALERTS System View](../022-Monitoring-Views/m-timezone-alerts-system-view-fc82c6c.md "Provides information about alerts relating to the status of SAP HANA internal timezone conversion.")

