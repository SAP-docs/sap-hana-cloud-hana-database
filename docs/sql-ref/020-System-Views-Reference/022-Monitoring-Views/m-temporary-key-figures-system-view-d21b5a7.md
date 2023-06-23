<!-- loiod21b5a73d2951014b2fdb98d213a52dc -->

# M\_TEMPORARY\_KEY\_FIGURES System View

Provides information about temporary key figures.



<a name="loiod21b5a73d2951014b2fdb98d213a52dc___m__t_e_m_p_o_r_a_r_y__k_e_y__f_i_g_u_r_e_s_1struct_M_TEMPORARY_KEY_FIGURES"/>

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

Displays the join view name.



</td>
</tr>
<tr>
<td valign="top">

KEY\_FIGURE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the key figure name.



</td>
</tr>
<tr>
<td valign="top">

DEFAULT\_AGGREGATION\_TYPE



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the aggregation type.



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

Displays the description.



</td>
</tr>
<tr>
<td valign="top">

UNIT\_CONVERSION\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the unit conversion.



</td>
</tr>
<tr>
<td valign="top">

TABLE\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name of the column.



</td>
</tr>
<tr>
<td valign="top">

TABLE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the table name of the column.



</td>
</tr>
<tr>
<td valign="top">

COLUMN\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the column name.



</td>
</tr>
<tr>
<td valign="top">

EXPRESSION\_FLAGS



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the expression flags.



</td>
</tr>
<tr>
<td valign="top">

EXPRESSION



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the expression.



</td>
</tr>
</table>

**Related Information**  


[CS\_KEY\_FIGURES System View](../021-System-Views/cs-key-figures-system-view-20a0f88.md "Provides information about the key figures defined for column store join views.")

