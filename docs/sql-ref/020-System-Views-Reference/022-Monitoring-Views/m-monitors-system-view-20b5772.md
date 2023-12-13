<!-- loio20b5772775191014aea79a7f51ae1ee8 -->

# M\_MONITORS System View

Provides available monitoring view information.



<a name="loio20b5772775191014aea79a7f51ae1ee8___m__m_o_n_i_t_o_r_s_1struct_M_MONITORS"/>

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

SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name.

</td>
</tr>
<tr>
<td valign="top">

VIEW\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the monitoring view.

</td>
</tr>
<tr>
<td valign="top">

DESCRIPTION

</td>
<td valign="top">

NVARCHAR\(2000\)

</td>
<td valign="top">

Displays the short description of the monitoring view.

</td>
</tr>
<tr>
<td valign="top">

RESETTABLE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates whether or not the values of this view can be reset: TRUE/FALSE.

</td>
</tr>
</table>



<a name="loio20b5772775191014aea79a7f51ae1ee8___m__m_o_n_i_t_o_r_s_1fulldesc_M_MONITORS"/>

## Additional Information

This view can be used in conjunction with the M\_MONITOR\_COLUMNS system view to get information about existing monitoring views.

**Related Information**  


[M\_MONITOR\_COLUMNS System View](m-monitor-columns-system-view-20b54f6.md "All the columns in the monitoring views.")

[ALTER SYSTEM RESET MONITORING VIEW Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-reset-monitoring-view-statement-system-management-20d27aa.md "Resets statistics data for the specified monitoring view.")

[System Views for Monitoring Partitions](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/9d829883639d445884cc0d9210f14394.html "A number of system views allow you to monitor your partitions.") :arrow_upper_right:

[Monitoring View Extensions for Column Store Paged Data Size](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/b06e99431b2740fdb4a47c7ee130f89d.html "A number of monitoring views provide information about the in-memory and on-disk size of the page-loadable data in relation to the in-memory and on-disk size of non-paged (column-loadable) data, helping you understand the effectiveness of page-loadable storage.") :arrow_upper_right:

