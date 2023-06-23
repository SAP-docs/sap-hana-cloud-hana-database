<!-- loio20c89f08751910148102dcbca6a1ed14 -->

# M\_TRACE\_CONFIGURATION System View

Provides information about trace configuration statistics.



<a name="loio20c89f08751910148102dcbca6a1ed14___m__t_r_a_c_e__c_o_n_f_i_g_u_r_a_t_i_o_n_1struct_M_TRACE_CONFIGURATION"/>

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

Displays the internal port number.



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

Displays the Persistence Volume ID.



</td>
</tr>
<tr>
<td valign="top">

STATISTICS\_NAME



</td>
<td valign="top">

NVARCHAR\(128\)



</td>
<td valign="top">

Displays the statistics object name.



</td>
</tr>
<tr>
<td valign="top">

TRACE\_DIRECTORY



</td>
<td valign="top">

NVARCHAR\(512\)



</td>
<td valign="top">

Displays the default trace level.



</td>
</tr>
<tr>
<td valign="top">

FORMATTER



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the trace formatter name.



</td>
</tr>
<tr>
<td valign="top">

FILE\_NAME\_PREFIX



</td>
<td valign="top">

NVARCHAR\(512\)



</td>
<td valign="top">

Displays the trace file name prefix.



</td>
</tr>
<tr>
<td valign="top">

ALERT\_FORMATTER



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the alert trace formatter name.



</td>
</tr>
<tr>
<td valign="top">

ALERT\_FILE\_NAME\_PREFIX



</td>
<td valign="top">

NVARCHAR\(512\)



</td>
<td valign="top">

Displays the alert trace file name prefix.



</td>
</tr>
<tr>
<td valign="top">

TRACE\_FLUSH\_INTERVAL



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the trace flush interval in seconds.



</td>
</tr>
<tr>
<td valign="top">

ALERT\_TRACE\_LEVEL



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

The trace level for alert traces.



</td>
</tr>
<tr>
<td valign="top">

DEFAULT\_TRACE\_LEVEL



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the default trace level.



</td>
</tr>
<tr>
<td valign="top">

TRACE\_BUFFER\_SIZE



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the trace buffer size in bytes.



</td>
</tr>
<tr>
<td valign="top">

MAX\_TRACE\_FILE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the max trace file size in bytes.



</td>
</tr>
<tr>
<td valign="top">

MAX\_TRACE\_FILE\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the max trace file ID.



</td>
</tr>
<tr>
<td valign="top">

MAX\_TRACE\_FILES



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the max trace files to keep.



</td>
</tr>
<tr>
<td valign="top">

ALERT\_TRACE\_BUFFER\_SIZE



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the alert trace buffer size in bytes.



</td>
</tr>
<tr>
<td valign="top">

MAX\_ALERT\_TRACE\_FILE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the max alert trace file size in bytes.



</td>
</tr>
<tr>
<td valign="top">

TRACE\_COMPRESSION\_INTERVAL



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the interval, in seconds, to check for trace files that need to be compressed.



</td>
</tr>
</table>



<a name="loio20c89f08751910148102dcbca6a1ed14__section_jzc_jn4_x2b"/>

## Additional Information

This view has a resettable counterpart; you can see the values since the last reset in the M\_TRACE\_CONFIGURATION\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_TRACE_CONFIGURATION_RESET;`.

**Related Information**  


[M\_TRACE\_CONFIGURATION\_RESET System View](m-trace-configuration-reset-system-view-20c8bbc.md "Provides information about trace configuration statistics since the last reset.")

[ALTER SYSTEM CLEAR TRACES Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-traces-statement-system-management-20d1281.md "Clears (removes) trace files opened by SAP HANA.")

[ALTER SYSTEM REMOVE TRACES Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-remove-traces-statement-system-management-20d25bf.md "Deletes the trace files on a specified host to reduce the disk space used by large trace files.")

[M\_SERVICE\_TRACES System View](m-service-traces-system-view-20c4b5c.md "Provides configured trace components for each service type.")

