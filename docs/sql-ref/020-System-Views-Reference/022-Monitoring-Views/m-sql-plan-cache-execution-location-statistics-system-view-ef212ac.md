<!-- loioef212acf0c28411190a5c303c0f09a32 -->

# M\_SQL\_PLAN\_CACHE\_EXECUTION\_LOCATION\_STATISTICS System View

Provides statistics for hosts where plans were executed.





<a name="loioef212acf0c28411190a5c303c0f09a32___m__s_q_l__p_l_a_n__c_a_c_h_e_1struct_M_SQL_PLAN_CACHE_EXECUTION_LOCATION_STATISTICS"/>

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

PLAN\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the logical plan ID as a non-negative value.



</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_HOST



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the host where the plan was executed.



</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_PORT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the port where the plan was executed.



</td>
</tr>
<tr>
<td valign="top">

TOTAL\_MEMORY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total size of the tracked memory consumption in bytes.



</td>
</tr>
<tr>
<td valign="top">

AVG\_MEMORY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the average size of the tracked memory consumption in bytes.



</td>
</tr>
<tr>
<td valign="top">

MIN\_MEMORY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the minimum size of the tracked memory consumption in bytes.



</td>
</tr>
<tr>
<td valign="top">

MAX\_MEMORY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the maximum size of the tracked memory consumption in bytes.



</td>
</tr>
</table>



<a name="loioef212acf0c28411190a5c303c0f09a32__section_npg_xd4_x2b"/>

## Additional Information

This view has a resettable counterpart; you can see the values since the last reset in the M\_SQL\_PLAN\_CACHE\_EXECUTION\_LOCATION\_STATISTICS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_SQL_PLAN_CACHE_EXECUTION_LOCATION_STATISTICS_RESET;`.

**Related Information**  


[M\_SQL\_PLAN\_CACHE\_EXECUTION\_LOCATION\_STATISTICS\_RESET System View](m-sql-plan-cache-execution-location-statistics-reset-system-view-56f5d8c.md "Provides statistics for hosts where plans were executed.")

[M\_SQL\_PLAN\_CACHE System View](m-sql-plan-cache-system-view-20c57b8.md "Provides statistics for an individual execution plan.")

[ALTER SYSTEM RESET MONITORING VIEW Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-reset-monitoring-view-statement-system-management-20d27aa.md "Resets statistics data for the specified monitoring view.")

[ALTER SYSTEM REMOVE SQL PLAN CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-remove-sql-plan-cache-statement-system-management-dafece7.md "Removes the specified entries from the SQL plan cache.")

[ALTER SYSTEM CLEAR SQL PLAN CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-sql-plan-cache-statement-system-management-20d107c.md "Removes all of the SQL plans that are not currently being executed from the SAP HANA database plan cache.")

[ALTER SYSTEM RECOMPILE SQL PLAN CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-recompile-sql-plan-cache-entry-statement-system-management-d226426.md "Invalidates the designated plan cache entry so that it is recompiled during the next execution time.")

[ALTER SYSTEM \{PIN | UNPIN\} SQL PLAN CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-pin-unpin-sql-plan-cache-entry-statement-system-management-68e2f7a.md "Provides a runtime mechanism to bind the target query and hints to the Hint Table to force the compilation of the target query with the hint.")

