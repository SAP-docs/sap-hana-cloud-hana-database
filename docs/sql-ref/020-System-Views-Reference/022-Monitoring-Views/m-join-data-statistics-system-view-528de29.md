<!-- loio528de2912b514a26bd99c89c8921a942 -->

# M\_JOIN\_DATA\_STATISTICS System View

Provides column store join engine join statistics.



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

SCHEMA\_NAME1

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of the first table

</td>
</tr>
<tr>
<td valign="top">

TABLE\_NAME1

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the first table

</td>
</tr>
<tr>
<td valign="top">

COLUMN\_NAME1

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the column name of the first table

</td>
</tr>
<tr>
<td valign="top">

SCHEMA\_NAME2

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of the second table. Join data statistics are not collected

</td>
</tr>
<tr>
<td valign="top">

TABLE\_NAME2

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the second table.

</td>
</tr>
<tr>
<td valign="top">

COLUMN\_NAME2

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the column name of the second table.

</td>
</tr>
<tr>
<td valign="top">

LAST\_REFRESH\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time when the statistics was last refreshed.

</td>
</tr>
<tr>
<td valign="top">

RECORD\_COUNT1

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the estimated total row count of the first table. For temporary tables, this value is always 0.

</td>
</tr>
<tr>
<td valign="top">

COUNT1

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of not Null values of the column of the first table.

</td>
</tr>
<tr>
<td valign="top">

DISTINCT\_COUNT1

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of unique not Null values of the column of the first table.

</td>
</tr>
<tr>
<td valign="top">

VALUE\_COUNTS1

</td>
<td valign="top">

NVARCHAR\(1000\)

</td>
<td valign="top">

Displays a comma-separated sorted list of unique column value counts. An incomplete output of the list is truncated by an asterisk sign. If a uniform distribution of column values is assumed, then there is exactly one value count because values are uniformly distributed and every value counts the same.

</td>
</tr>
<tr>
<td valign="top">

VALUE\_COUNTS\_FREQUENCIES1

</td>
<td valign="top">

NVARCHAR\(1000\)

</td>
<td valign="top">

Displays a comma-separated list of frequencies of the first table's column values with the same count. Any frequency refers to that value count with a corresponding position in the list of value counts. An incomplete output of the list is truncated by an asterisk sign. If a uniform distribution of column values is assumed, then there is exactly one value frequency because values are uniformly distributed. Generally, this single frequency matches the distinct count.

</td>
</tr>
<tr>
<td valign="top">

MATCHING\_VALUES\_COUNTS1

</td>
<td valign="top">

NVARCHAR\(1000\)

</td>
<td valign="top">

Displays a comma-separated list of counts of the first table's column values which find a join partner. Any matching values count refers to that value count with corresponding position in the list of value counts. An incomplete output of the list is truncated by an asterisk sign. If a uniform distribution of column values is assumed, then the matching values count the one and only value count that is calculated from the unified distribution of the value counts.

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

Displays the memory size, in bytes, used by the join data statistics object.

</td>
</tr>
</table>



<a name="loio528de2912b514a26bd99c89c8921a942__section_rzd_fzz_xbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.



<a name="loio528de2912b514a26bd99c89c8921a942__section_vrv_5cq_cdb"/>

## Additional Information

Join data statistics are not collected for temporary tables, so the SCHEMA\_NAME, TABLE\_NAME, and COLUMN\_NAME values for a temporary table are NULL.

**Related Information**  


[ALTER SYSTEM CLEAR COLUMN JOIN DATA STATISTICS \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-column-join-data-statistics-system-management-9ac0859.md "Removes join data statistics from the SAP HANA database cache.")

[M\_JOINENGINE\_STATISTICS System View](m-joinengine-statistics-system-view-c847a34.md "Provides statistics about join engine runtime objects used for column store join operations.")

[M\_JOIN\_TRANSLATION\_TABLES System View](m-join-translation-tables-system-view-f4a7c5e.md "Provides column store join engine translation tables statistics.")

