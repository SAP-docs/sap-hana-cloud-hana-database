<!-- loio2102244575191014a7bde2c7e6b52081 -->

# USER\_PARAMETERS System View

Lists all parameters and their values, which have been assigned to users in the system \(using CREATE USER ... SET PARAMETER or ALTER USER ... SET PARAMETER\).



<a name="loio2102244575191014a7bde2c7e6b52081___u_s_e_r__p_a_r_a_m_e_t_e_r_s_1struct_USER_PARAMETERS"/>

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

USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the user.



</td>
</tr>
<tr>
<td valign="top">

PARAMETER



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the client parameter name.



</td>
</tr>
<tr>
<td valign="top">

VALUE



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

Displays the parameter value.



</td>
</tr>
</table>

**Related Information**  


[USERS System View](users-system-view-2102609.md "Lists all users.")

[Restrict Use of the CLIENT User Parameter](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/91af0e7d50a14936a388618974ef8dc1.html "Allow only authorized technical users to overwrite the value of the CLIENT parameter for a database connection or the value of the $$client$$ parameter in an SQL query.") :arrow_upper_right:

