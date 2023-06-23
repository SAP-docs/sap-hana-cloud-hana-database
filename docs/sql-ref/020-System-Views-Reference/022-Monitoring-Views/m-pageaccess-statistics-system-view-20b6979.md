<!-- loio20b69793751910148374d05a00d03c78 -->

# M\_PAGEACCESS\_STATISTICS System View

Provides PageAccess statistics.



<a name="loio20b69793751910148374d05a00d03c78___m__p_a_g_e_a_c_c_e_s_s__s_t_a_t_i_s_t_i_c_s_1struct_M_PAGEACCESS_STATISTICS"/>

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

Displays the type of pageaccess.



</td>
</tr>
<tr>
<td valign="top">

CHUNK\_SIZE



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the chunk size in bytes.



</td>
</tr>
<tr>
<td valign="top">

ALLOCATE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of allocations.



</td>
</tr>
<tr>
<td valign="top">

GET\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of gets.



</td>
</tr>
<tr>
<td valign="top">

LOAD\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of synchronous loads.



</td>
</tr>
<tr>
<td valign="top">

TRIGGER\_LOAD\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of asynchronous loads.



</td>
</tr>
<tr>
<td valign="top">

DEALLOCATE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of deallocations.



</td>
</tr>
</table>



<a name="loio20b69793751910148374d05a00d03c78___m__p_a_g_e_a_c_c_e_s_s__s_t_a_t_i_s_t_i_c_s_1fulldesc_M_PAGEACCESS_STATISTICS"/>

## Additional Information

This view contains information about pages accessed:

-   TYPE specifies the pageaccess.
-   The \*\_COUNT values are the number of the respective operations on the page access.
-   CHUNK\_SIZE is the number of pages accessed by one operation \(CHUNK\_SIZE is 1 except for RowStorePageAccess, where blocks of pages are accessed. For example, LOAD\_COUNT=4 and CHUNK\_SIZE=1024 means that 2\*1024=4096 pages had been loaded\). the corresponding Converter is accessed on allocation and deallocation.

This view has a resettable counterpart; you can see the values since the last reset in the M\_PAGEACCESS\_STATISTICS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_PAGEACCESS_STATISTICS_RESET;`.

**Related Information**  


[M\_PAGEACCESS\_STATISTICS\_RESET System View](m-pageaccess-statistics-reset-system-view-20b6c34.md "Provides the PageAccess statistics since the last reset.")

[ALTER SYSTEM RESET MONITORING VIEW Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-reset-monitoring-view-statement-system-management-20d27aa.md "Resets statistics data for the specified monitoring view.")

[M\_CONVERTER\_STATISTICS System View](m-converter-statistics-system-view-20acadb.md "Provides converter statistics.")

[Reduce the Memory Footprint Using Page-Loadable Columns in SAP HANA NSE](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/786c621dd35e4534a2f955bf2f04a2e2.html "SAP HANA native storage extension (NSE) uses techniques to load only the pages into memory that include data that is relevant to your search. Pages containing data that is not accessed by your query are not loaded from disk.") :arrow_upper_right:

[Data Access in the SAP HANA Cloud, SAP HANA Database](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/7791e61775f949d9989eafc443158cdb.html "The SAP HANA database in SAP HANA Cloud supports the integration of data from many data sources to enrich your applications and deliver in-depth analysis. These include federated queries, data replication, and processes to improve data quality.") :arrow_upper_right:

