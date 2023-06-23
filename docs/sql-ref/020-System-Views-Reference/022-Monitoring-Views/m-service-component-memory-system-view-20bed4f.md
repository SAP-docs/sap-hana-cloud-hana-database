<!-- loio20bed4f675191014a4cf8e62c28d16ae -->

# M\_SERVICE\_COMPONENT\_MEMORY System View

Provides service-specific memory usage by logical component.



<a name="loio20bed4f675191014a4cf8e62c28d16ae___m__s_e_r_v_i_c_e__c_o_m_p_o_n_e_n_t__m_e_m_o_r_y_1struct_M_SERVICE_COMPONENT_MEMORY"/>

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

Displays the host where the service is running.



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

Displays the port where the service is running.



</td>
</tr>
<tr>
<td valign="top">

COMPONENT



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the logical component for which memory usage is reported.



</td>
</tr>
<tr>
<td valign="top">

USED\_MEMORY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the amount of memory, in bytes, being used for the logical component.



</td>
</tr>
</table>

**Related Information**  


[M\_SERVICES System View](m-services-system-view-20c4ef8.md "Provides the status of all services.")

[M\_SERVICE\_MEMORY System View](m-service-memory-system-view-20bf33c.md "Displays detailed memory utilization information by services.")

[Memory Allocator Statistics](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/546bac9a6f924210aabd34dc90c00e05.html "Detailed information about memory consumption can be found by looking into allocator statistics.") :arrow_upper_right:

