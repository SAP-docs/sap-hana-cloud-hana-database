<!-- loio20b2491475191014af92c7fda202e9ac -->

# M\_LIVECACHE\_CONTAINER\_STATISTICS System View

Provides accumulated liveCache container statistics.



<a name="loio20b2491475191014af92c7fda202e9ac___m__l_i_v_e_c_a_c_h_e__c_o_n_t_a_i_n_e_r__s_t_a_t_i_s_t_i_c_s_1struct_M_LIVECACHE_CONTAINER_STATISTICS"/>

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

CONTAINER\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the container ID.

</td>
</tr>
<tr>
<td valign="top">

OMS\_CLASS\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the Object Management System class ID.

</td>
</tr>
<tr>
<td valign="top">

OMS\_CLASS\_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the Object Management System class name.

</td>
</tr>
<tr>
<td valign="top">

OMS\_SCHEMA\_HANDLE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the Object Management System schema handle.

</td>
</tr>
<tr>
<td valign="top">

OMS\_CONTAINER\_NO

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the Object Management System container number.

</td>
</tr>
<tr>
<td valign="top">

CLASS\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object class size in bytes.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_TYPE

</td>
<td valign="top">

NVARCHAR\(3\)

</td>
<td valign="top">

Displays the object type: STD, KEY, or VAR.

</td>
</tr>
<tr>
<td valign="top">

KEY\_SIZE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the object key size in bytes.

</td>
</tr>
<tr>
<td valign="top">

KEY\_PARTITION\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the key partition count.

</td>
</tr>
<tr>
<td valign="top">

KEY\_PARTITION\_PREFIX\_SIZE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the key partition prefix length in bytes.

</td>
</tr>
<tr>
<td valign="top">

CACHED\_KEYS

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the cached keys are active: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

COPY\_ON\_UPDATE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether copy on update is active: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

PREFETCH

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates whether the prefetch is active: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_LOADED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates whether the statistics are loaded into the memory: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object count.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_SIZE\_SUM

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object size sum in bytes.

</td>
</tr>
<tr>
<td valign="top">

GC\_PENDING\_OBJECT\_DELETE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the count of objects that are deleted and not yet freed by the garbage collection.

</td>
</tr>
<tr>
<td valign="top">

GC\_PENDING\_OBJECT\_DELETE\_SIZE\_SUM

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the transient size sum of the objects that are deleted and not yet freed by the garbage collection in bytes.

</td>
</tr>
<tr>
<td valign="top">

HISTORY\_OBJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of transient history object versions that are not yet freed by the garbage collection.

</td>
</tr>
<tr>
<td valign="top">

HISTORY\_SIZE\_SUM

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size sum, in bytes, of the transient history object versions that are not yet freed by the garbage collection.

</td>
</tr>
<tr>
<td valign="top">

PAGE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the page count.

</td>
</tr>
<tr>
<td valign="top">

PAGE\_SIZE\_SUM

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the page size sum in bytes.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_CREATE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of objects created since the last restart.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_UPDATE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of objects updated since the last restart.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_DELETE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of objects delete since the last restart.

</td>
</tr>
<tr>
<td valign="top">

HEAP\_USAGE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the memory currently used by the container, in bytes.

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

Displays the created timestamp.

</td>
</tr>
</table>



<a name="loio20b2491475191014af92c7fda202e9ac__section_xb5_rbh_x2b"/>

## Additional Information

This view has a resettable counterpart; you can see the values since the last reset in the M\_LIVECACHE\_CONTAINER\_STATISTICS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_LIVECACHE_CONTAINER_STATISTICS_RESET;`.

**Related Information**  


[M\_LIVECACHE\_CONTAINER\_STATISTICS\_RESET System View](m-livecache-container-statistics-reset-system-view-20b26d9.md "Provides accumulated LiveCache container statistics since last reset.")

[HOST_LIVECACHE_CONTAINER_STATISTICS View (Embedded Statistics Service)](https://help.sap.com/viewer/323c57a017234d47a0e7da3e22345822/2023_4_QRC/en-US/ef6f2f4a443d427880f712674afbc7bc.html "Returns LiveCache container statistics per host status information.") :arrow_upper_right:

[HOST_LIVECACHE_OMS_VERSIONS View (Embedded Statistics Service)](https://help.sap.com/viewer/323c57a017234d47a0e7da3e22345822/2023_4_QRC/en-US/29ffcc773260413481653377de803596.html "Returns LiveCache OMS versions per host status information.") :arrow_upper_right:

[HOST_LIVECACHE_SCHEMA_STATISTICS View (Embedded Statistics Service)](https://help.sap.com/viewer/323c57a017234d47a0e7da3e22345822/2023_4_QRC/en-US/e908695d7b2b4220a6d7df7923da68fd.html "LiveCache schema statistics per host. This view contains information only for the last 21 days. The collection interval is 30 minutes.") :arrow_upper_right:

[HOST_LIVECACHE_PROCEDURE_STATISTICS View (Embedded Statistics Service)](https://help.sap.com/viewer/323c57a017234d47a0e7da3e22345822/2023_4_QRC/en-US/9bd3356b46c44487ab86167aaa8056c3.html "LiveCache procedure statistics per host. This view contains information only for the last 21 days. The collection interval is 30 minutes.") :arrow_upper_right:

[ALTER SYSTEM RESET MONITORING VIEW Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-reset-monitoring-view-statement-system-management-20d27aa.md "Resets statistics data for the specified monitoring view.")

