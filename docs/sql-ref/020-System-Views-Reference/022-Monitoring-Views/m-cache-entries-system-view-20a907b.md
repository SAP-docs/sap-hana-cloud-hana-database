<!-- loio20a907b675191014b6e8a18b2968e12f -->

# M\_CACHE\_ENTRIES System View

Provides cache entry information.



<a name="loio20a907b675191014b6e8a18b2968e12f___m__c_a_c_h_e__e_n_t_r_i_e_s_1struct_M_CACHE_ENTRIES"/>

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

CACHE\_ID

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the ID of the cache that created the entry.

</td>
</tr>
<tr>
<td valign="top">

ENTRY\_ID

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the ID of the cached entry.

</td>
</tr>
<tr>
<td valign="top">

ENTRY\_DESCRIPTION

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the description of the cached entry.

</td>
</tr>
<tr>
<td valign="top">

COMPONENT

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the information about the component that created the cached entry.

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

Displays the information about the user that created the cached entry.

</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the used memory to store the cached entry in the cache in bytes.

</td>
</tr>
<tr>
<td valign="top">

CREATE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the point in time when the cache entry was inserted into the cache in bytes.

</td>
</tr>
<tr>
<td valign="top">

READ\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Determines how often the cache entry was read successfully from the cache.

</td>
</tr>
<tr>
<td valign="top">

LAST\_ACCESS\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time of the last access of the cache instance.

</td>
</tr>
</table>

**Related Information**  


[M\_CACHES System View](m-caches-system-view-20a93aa.md "Provides aggregated information on caches.")

[ALTER SYSTEM CLEAR CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-cache-statement-system-management-141ad67.md "Clears resources (entries) from one or more cache instances.")

[ALTER SYSTEM REMOVE RESULT CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-remove-result-cache-entry-statement-system-management-2124566.md "Removes the result cache entry for the specified cache ID.")

[ALTER SYSTEM CLEAR SQL PLAN CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-sql-plan-cache-statement-system-management-20d107c.md "Removes all of the SQL plans that are not currently being executed from the SAP HANA database plan cache.")

[ALTER SYSTEM REFRESH RESULT CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-refresh-result-cache-entry-statement-system-management-1ab0dbb.md "Refreshes the specified result cache entry.")

[ALTER SYSTEM REMOVE SQL PLAN CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-remove-sql-plan-cache-statement-system-management-dafece7.md "Removes the specified entries from the SQL plan cache.")

[ALTER SYSTEM CLEAR TIMEZONE CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-timezone-cache-statement-system-management-a780495.md "Clears cached timezone definitions.")

[ALTER SYSTEM CLEAR RESULT CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-result-cache-statement-system-management-97dca93.md "Removes all result cache entries from the system.")

[ALTER SYSTEM REFRESH RESULT CACHE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-refresh-result-cache-statement-system-management-9d274fa.md "Refreshes all result cache entries related to the specified object with up-to-date results.")

[ALTER SYSTEM RECOMPILE SQL PLAN CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-recompile-sql-plan-cache-entry-statement-system-management-d226426.md "Invalidates the designated plan cache entry so that it is recompiled during the next execution time.")

[ALTER SYSTEM \{PIN | UNPIN\} SQL PLAN CACHE ENTRY Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-pin-unpin-sql-plan-cache-entry-statement-system-management-68e2f7a.md "Provides a runtime mechanism to bind the target query and hints to the Hint Table to force the compilation of the target query with the hint.")

[M\_DYNAMIC\_RESULT\_CACHE System View](m-dynamic-result-cache-system-view-01f8a85.md "Lists statistics for the dynamic result cache.")

[M\_SQL\_PLAN\_CACHE\_PARAMETERS System View](m-sql-plan-cache-parameters-system-view-f411689.md "Provides bind parameters for statements cached in SQL Plan Cache. It saves a parameter set of the most expensive execution for each plan.")

