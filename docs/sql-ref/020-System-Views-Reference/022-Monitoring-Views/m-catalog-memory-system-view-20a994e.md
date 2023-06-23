<!-- loio20a994ea751910148ccbd5e7108f3e2e -->

# M\_CATALOG\_MEMORY System View

Provides memory usage information by catalog manager.



<a name="loio20a994ea751910148ccbd5e7108f3e2e___m__c_a_t_a_l_o_g__m_e_m_o_r_y_1struct_M_CATALOG_MEMORY"/>

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

CATEGORY



</td>
<td valign="top">

NVARCHAR\(128\)



</td>
<td valign="top">

Displays the category of the catalog data.



</td>
</tr>
<tr>
<td valign="top">

ALLOCATION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of allocated entries.



</td>
</tr>
<tr>
<td valign="top">

ALLOCATED\_FIXED\_PART\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the allocated memory size in bytes for the fixed-size part.



</td>
</tr>
<tr>
<td valign="top">

USED\_FIXED\_PART\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the used memory size in bytes for the fixed-size part.



</td>
</tr>
<tr>
<td valign="top">

ALLOCATED\_VARIABLE\_PART\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the allocated memory size in bytes for the variable-size part.



</td>
</tr>
<tr>
<td valign="top">

USED\_VARIABLE\_PART\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the used memory size in bytes for the variable-size part.



</td>
</tr>
</table>

**Related Information**  


[Memory Usage in the SAP HANA Database](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/bde79b28bb5710149d6eee5e75fe7f17.html "Memory is a fundamental resource of the SAP HANA database. Understanding how the SAP HANA database requests, uses, and manages this resource is crucial to the understanding of SAP HANA.") :arrow_upper_right:

[Memory Sizing](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/bdf26308bb571014b7bcd3bcd586aecd.html "Memory sizing is the process of estimating in advance the amount of memory that will be required to run a certain workload on an SAP HANA database. To understand memory sizing, several questions need to be answered.") :arrow_upper_right:

