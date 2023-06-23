<!-- loiof411689a6f5b1014ae8ddf599d7a61d1 -->

# M\_SQL\_PLAN\_CACHE\_PARAMETERS System View

Provides bind parameters for statements cached in SQL Plan Cache. It saves a parameter set of the most expensive execution for each plan.



<a name="loiof411689a6f5b1014ae8ddf599d7a61d1___m__s_q_l__p_l_a_n__c_a_c_h_e__p_a_r_a_m_e_t_e_r_s_1struct_M_SQL_PLAN_CACHE_PARAMETERS"/>

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

PLAN\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the logical plan ID which is a non-negative value, same with the one in M\_SQL\_PLAN\_CACHE.



</td>
</tr>
<tr>
<td valign="top">

DATA\_TYPE\_NAME



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the data type of the parameter.



</td>
</tr>
<tr>
<td valign="top">

POSITION



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the position of the parameter in SQL statement.



</td>
</tr>
<tr>
<td valign="top">

PARAMETER\_VALUE



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays the value of the captured parameter.



</td>
</tr>
<tr>
<td valign="top">

BATCH\_EXECUTION\_ORDER



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the execution order in a batch processing.



</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_TIMESTAMP



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the timestamp when the parameter value is captured.



</td>
</tr>
</table>

**Related Information**  


[M\_SQL\_PLAN\_CACHE System View](m-sql-plan-cache-system-view-20c57b8.md "Provides statistics for an individual execution plan.")

[M\_SQL\_PLAN\_CACHE\_EXECUTION\_LOCATION\_STATISTICS System View](m-sql-plan-cache-execution-location-statistics-system-view-ef212ac.md "Provides statistics for hosts where plans were executed.")

[ALTER SYSTEM REMOVE SQL PLAN CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-remove-sql-plan-cache-statement-system-management-dafece7.md "Removes the specified entries from the SQL plan cache.")

[ALTER SYSTEM CLEAR SQL PLAN CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-sql-plan-cache-statement-system-management-20d107c.md "Removes all of the SQL plans that are not currently being executed from the SAP HANA database plan cache.")

[ALTER SYSTEM RECOMPILE SQL PLAN CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-recompile-sql-plan-cache-entry-statement-system-management-d226426.md "Invalidates the designated plan cache entry so that it is recompiled during the next execution time.")

[ALTER SYSTEM \{PIN | UNPIN\} SQL PLAN CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-pin-unpin-sql-plan-cache-entry-statement-system-management-68e2f7a.md "Provides a runtime mechanism to bind the target query and hints to the Hint Table to force the compilation of the target query with the hint.")

