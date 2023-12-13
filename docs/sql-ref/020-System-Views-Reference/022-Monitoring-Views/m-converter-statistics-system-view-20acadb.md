<!-- loio20acadb5751910148bbcb1243495f6db -->

# M\_CONVERTER\_STATISTICS System View

Provides converter statistics.



<a name="loio20acadb5751910148bbcb1243495f6db___m__c_o_n_v_e_r_t_e_r__s_t_a_t_i_s_t_i_c_s_1struct_M_CONVERTER_STATISTICS"/>

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

TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the type of converter.

</td>
</tr>
<tr>
<td valign="top">

MAX\_LEVEL

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum level. For example, the root page level.

</td>
</tr>
<tr>
<td valign="top">

MAX\_PAGENUMBER

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum page number in HEXID.

</td>
</tr>
<tr>
<td valign="top">

ALLOCATED\_PAGE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of currently allocated pages.

</td>
</tr>
<tr>
<td valign="top">

ALLOCATED\_PAGE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size, in bytes, of the currently allocated pages.

</td>
</tr>
<tr>
<td valign="top">

MAX\_ALLOCATED\_PAGE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum number of allocated pages.

</td>
</tr>
<tr>
<td valign="top">

MAX\_ALLOCATED\_PAGE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum size, in bytes, of the allocated pages.

</td>
</tr>
<tr>
<td valign="top">

ALLOCATE\_PAGE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of page allocations.

</td>
</tr>
<tr>
<td valign="top">

ALLOCATE\_OR\_GET\_STATIC\_PAGE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of page allocations or retrievals during the static phase.

</td>
</tr>
<tr>
<td valign="top">

DEALLOCATE\_PAGE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of page deallocations.

</td>
</tr>
<tr>
<td valign="top">

ASSIGN\_PHYSICAL\_PAGE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of physical page assignments.

</td>
</tr>
<tr>
<td valign="top">

UNASSIGN\_PHYSICAL\_PAGE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of physical page unassignments.

</td>
</tr>
<tr>
<td valign="top">

UNASSIGN\_PHYSICAL\_PAGE\_COUNT\_DURING\_DROP\_SNAPSHOT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of physical page unassignments during a drop snapshot.

</td>
</tr>
<tr>
<td valign="top">

CREATE\_SNAPSHOT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of created snapshots.

</td>
</tr>
<tr>
<td valign="top">

DROP\_SNAPSHOT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of dropped snapshots.

</td>
</tr>
<tr>
<td valign="top">

WRITE\_CONVERTERPAGE\_LEVEL0\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of level 0 converter pages written to the disk.

</td>
</tr>
<tr>
<td valign="top">

WRITE\_CONVERTERPAGE\_LEVEL1\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of level 1 converter pages written to the disk.

</td>
</tr>
<tr>
<td valign="top">

WRITE\_CONVERTERPAGE\_LEVEL2\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of level 2 converter pages written to the disk.

</td>
</tr>
<tr>
<td valign="top">

WRITE\_CONVERTERPAGE\_LEVEL3\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of level 3 converter pages written to the disk.

</td>
</tr>
<tr>
<td valign="top">

WRITE\_CONVERTERPAGE\_LEVEL4\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of level 4 converter pages written to the disk.

</td>
</tr>
</table>



<a name="loio20acadb5751910148bbcb1243495f6db___m__c_o_n_v_e_r_t_e_r__s_t_a_t_i_s_t_i_c_s_1fulldesc_M_CONVERTER_STATISTICS"/>

## Additional Information

This view contains information about the converter, which administers logical page numbers and maps them to physical pages within the DataVolumes.

This view has a resettable counterpart; you can see the values since the last reset in the M\_CONVERTER\_STATISTICS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_CONVERTER_STATISTICS_RESET;`.

**Related Information**  


[M\_CONVERTER\_STATISTICS\_RESET System View](m-converter-statistics-reset-system-view-20acd16.md "Provides converter statistics since the last reset.")

[M\_PAGEACCESS\_STATISTICS System View](m-pageaccess-statistics-system-view-20b6979.md "Provides PageAccess statistics.")

[M\_DATA\_VOLUME\_PAGE\_STATISTICS System View](m-data-volume-page-statistics-system-view-20adabc.md "Provides page usage statistics on data volumes.")

[CREATE STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-statistics-statement-data-definition-20d5252.md "Creates data statistic objects that allow the query optimizer to make better decisions for query plans.")

[ALTER STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-statistics-statement-data-definition-c656476.md "Alters the properties of a data statistics object.")

[REFRESH STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/refresh-statistics-statement-data-definition-20fae6d.md "Specifies a column that is part of the data sources.")

[DROP STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-statistics-statement-data-definition-20d7c59.md "Drops user-defined data statistic objects that the query optimizer uses to make decisions for query plans.")

[Managing Statistics](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2023_4_QRC/en-US/0a9ae9e9ccc743f4a2808399da354657.html "Statistics assist the query optimizer in making better decisions and work for both virtual tables and linked database.") :arrow_upper_right:

