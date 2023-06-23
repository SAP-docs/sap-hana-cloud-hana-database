<!-- loio20b54f6275191014824cedc723f8ad13 -->

# M\_MONITOR\_COLUMNS System View

All the columns in the monitoring views.



<a name="loio20b54f6275191014824cedc723f8ad13___m__m_o_n_i_t_o_r__c_o_l_u_m_n_s_1struct_M_MONITOR_COLUMNS"/>

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

VIEW\_COLUMN\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the monitoring view column.



</td>
</tr>
<tr>
<td valign="top">

DATA\_TYPE\_ID



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

Displays the column data type ID.



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

Displays the column data type name.



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

Displays the ordinal position of the column in a record.



</td>
</tr>
<tr>
<td valign="top">

DEFAULT\_VALUE



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

Displays the default value.



</td>
</tr>
<tr>
<td valign="top">

UNIT



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the unit for the value.



</td>
</tr>
<tr>
<td valign="top">

LENGTH



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the length.



</td>
</tr>
<tr>
<td valign="top">

SCALE



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the scale.



</td>
</tr>
<tr>
<td valign="top">

IS\_NULLABLE



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Indicates whether or not a NULL value is allowed: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

DESCRIPTION



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

Displays the short description of the monitoring view column.



</td>
</tr>
</table>



<a name="loio20b54f6275191014824cedc723f8ad13___m__m_o_n_i_t_o_r__c_o_l_u_m_n_s_1fulldesc_M_MONITOR_COLUMNS"/>

## Additional Information

This view can be used in conjunction with the M\_MONITORS system view to get information about existing monitoring views.

**Related Information**  


[M\_MONITORS System View](m-monitors-system-view-20b5772.md "Provides available monitoring view information.")

[Monitoring View Extensions for Column Store Paged Data Size](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/b06e99431b2740fdb4a47c7ee130f89d.html "A number of monitoring views provide information about the in-memory and on-disk size of the page-loadable data in relation to the in-memory and on-disk size of non-paged (column-loadable) data, helping you understand the effectiveness of page-loadable storage.") :arrow_upper_right:

