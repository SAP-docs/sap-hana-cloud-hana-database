<!-- loio80c32e9dc5b742efa254adfe164102dc -->

# M\_EXPENSIVE\_STATEMENT\_EXECUTION\_LOCATION\_STATISTICS System View

Provides location statistics for expensive statements.



<a name="loio80c32e9dc5b742efa254adfe164102dc___m__e_x_p_e_n_s_i_v_e_s_t_a_t_e_m_e_n_t_e_x_e_c_u_t_i_o_n_l_o_c_a_t_i_o_n_s_t_a_t_i_s_t_i_c_s_1struct_M_EXPENSIVE_STATEMENT_EXECUTION_LOCATION_STATISTICS"/>

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

STATEMENT\_EXECUTION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the execution ID of the statement.

</td>
</tr>
<tr>
<td valign="top">

START\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the execution start time of the statement.

</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the host where the statement was executed.

</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the port of the host where the statement was executed.

</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the peak memory usage for the host in bytes. For example, if host A has a peak usage of 2 GB and host B has a peak usage of 3 GB, then there is a row with host A showing 2 GB and a row with host B showing 3 GB.

</td>
</tr>
<tr>
<td valign="top">

CPU\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the tracked CPU time that each location consumed.

</td>
</tr>
</table>

**Related Information**  


[M\_EXPENSIVE\_STATEMENTS System View](m-expensive-statements-system-view-20af736.md "Provides all statements with a duration longer than a specified threshold.")

[Expensive Statements Trace](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/5faf04f17830464eacdb7938b383d2ab.html "Expensive statements are individual SQL statements whose execution time exceeds a configured threshold. The expensive statements trace records information about these statements for further analysis and is inactive by default.") :arrow_upper_right:

