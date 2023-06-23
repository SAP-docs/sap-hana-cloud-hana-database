<!-- loio20c4d1dc751910148e5d947af2f72eae -->

# M\_SERVICE\_TYPES System View

Provides information about service types.



<a name="loio20c4d1dc751910148e5d947af2f72eae___m__s_e_r_v_i_c_e__t_y_p_e_s_1struct_M_SERVICE_TYPES"/>

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

SERVICE\_NAME



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the service name.



</td>
</tr>
<tr>
<td valign="top">

INIFILE



</td>
<td valign="top">

NVARCHAR\(36\)



</td>
<td valign="top">

Displays the configuration file name of service.



</td>
</tr>
<tr>
<td valign="top">

HAS\_DETAIL



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the service shows details in M\_SERVICE\_STATISTICS: TRUE/FALSE.



</td>
</tr>
</table>

**Related Information**  


[M\_SERVICE\_STATISTICS System View](m-service-statistics-system-view-20c460b.md "Provides statistics on active services.")

[ALTER SYSTEM RECONFIGURE SERVICE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-reconfigure-service-statement-system-management-20d23ea.md "Reconfigures a specified service by applying the current configuration parameters.")

