<!-- loio20c61f0675191014a1d5f96d9668855b -->

# M\_SYSTEM\_OVERVIEW System View

Provides an overview of system status including important resource usage information and alerts.



<a name="loio20c61f0675191014a1d5f96d9668855b___m__s_y_s_t_e_m__o_v_e_r_v_i_e_w_1struct_M_SYSTEM_OVERVIEW"/>

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

SECTION

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the section name.

</td>
</tr>
<tr>
<td valign="top">

NAME

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the key name in section.

</td>
</tr>
<tr>
<td valign="top">

STATUS

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays the status value: OK, ERROR, or WARNING. This row is empty for info items.

</td>
</tr>
<tr>
<td valign="top">

VALUE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the key value in section.

</td>
</tr>
</table>

**Related Information**  


[System Privileges](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2023_4_QRC/en-US/cadbcfc38b084808b80b3551b1cd756e.html "System privileges control general system activities.") :arrow_upper_right:

[System Limitations](../../010-SQL-Reference/system-limitations-20a7605.md "Limitations to take into consideration when administering an SAP HANA Cloud database.")

