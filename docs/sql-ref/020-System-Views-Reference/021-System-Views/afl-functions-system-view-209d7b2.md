<!-- loio209d7b297519101480ddcb980ff2a5d8 -->

# AFL\_FUNCTIONS System View

Provides information about available AFL functions.



<a name="loio209d7b297519101480ddcb980ff2a5d8___a_f_l__f_u_n_c_t_i_o_n_s_1struct_AFL_FUNCTIONS"/>

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

FUNCTION\_OID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the object ID of the AFL function.



</td>
</tr>
<tr>
<td valign="top">

SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name of the AFL function.



</td>
</tr>
<tr>
<td valign="top">

AREA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the AFL area that the AFL function belongs to.



</td>
</tr>
<tr>
<td valign="top">

PACKAGE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the AFL package that the AFL function belongs to.



</td>
</tr>
<tr>
<td valign="top">

FUNCTION\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the AFL function.



</td>
</tr>
<tr>
<td valign="top">

CREATE\_TIMESTAMP



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the timestamp when the AFL function was created.



</td>
</tr>
<tr>
<td valign="top">

INPUT\_PARAMETER\_COUNT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the number of the input parameters of the AFL function.



</td>
</tr>
<tr>
<td valign="top">

RETURN\_VALUE\_COUNT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the umber of the out parameters of the AFL function.



</td>
</tr>
<tr>
<td valign="top">

FUNCTION\_TYPE



</td>
<td valign="top">

NVARCHAR\(7\)



</td>
<td valign="top">

Displays the type of the AFL function.



</td>
</tr>
<tr>
<td valign="top">

TECHNICAL\_CATEGORY



</td>
<td valign="top">

NVARCHAR\(11\)



</td>
<td valign="top">

Displays the technical category of the AFL function.



</td>
</tr>
</table>

**Related Information**  


[AFL\_AREAS System View](afl-areas-system-view-209d1d1.md "Provides information about available AFL areas.")

[AFL\_FUNCTION\_PARAMETERS System View](afl-function-parameters-system-view-d1fce26.md "Provides information about parameters of AFL functions.")

[AFL\_FUNCTION\_PROPERTIES System View](afl-function-properties-system-view-209d4b7.md "Provides information about available AFL function properties.")

[AFL\_PACKAGES System View](afl-packages-system-view-209dae2.md "Provides information about available AFL packages.")

[AFL\_TEXTS System View](afl-texts-system-view-d1fd8aa.md "Provides information about available AFL texts.")

[M\_AFL\_STATES System View](../022-Monitoring-Views/m-afl-states-system-view-3769f7f.md "Provides information about AFL states.")

