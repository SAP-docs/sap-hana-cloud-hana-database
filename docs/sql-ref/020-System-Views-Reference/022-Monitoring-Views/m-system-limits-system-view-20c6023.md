<!-- loio20c6023775191014be17d92c9bd287eb -->

# M\_SYSTEM\_LIMITS System View

Provides system limit information.



<a name="loio20c6023775191014be17d92c9bd287eb___m__s_y_s_t_e_m__l_i_m_i_t_s_1struct_M_SYSTEM_LIMITS"/>

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

CATEGORY

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays whether the category of the system limit is adaptable.

</td>
</tr>
<tr>
<td valign="top">

NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the system limit.

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

Displays the value of the system limit.

</td>
</tr>
<tr>
<td valign="top">

TYPE

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the type of value.

</td>
</tr>
<tr>
<td valign="top">

UNIT

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the unit of value.

</td>
</tr>
<tr>
<td valign="top">

COMMENT

</td>
<td valign="top">

NVARCHAR\(2000\)

</td>
<td valign="top">

Displays any additional comments for system limits.

</td>
</tr>
</table>

**Related Information**  


[System Limitations](../../010-SQL-Reference/system-limitations-20a7605.md "Limitations to take into consideration when administering an SAP HANA Cloud database.")

[Analyzing System Performance](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/2f1b50583b214f8c8d64d5a8f65bd74b.html "You can use monitoring views to analyze how effectively your system is handling the current workload.") :arrow_upper_right:

