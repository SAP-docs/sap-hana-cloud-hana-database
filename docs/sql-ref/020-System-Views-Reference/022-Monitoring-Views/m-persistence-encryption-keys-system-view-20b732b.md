<!-- loio20b732b4751910149af9a181e6812334 -->

# M\_PERSISTENCE\_ENCRYPTION\_KEYS System View

Provides information about encryption page keys.



<a name="loio20b732b4751910149af9a181e6812334___m__p_e_r_s_i_s_t_e_n_c_e__e_n_c_r_y_p_t_i_o_n__k_e_y_s_1struct_M_PERSISTENCE_ENCRYPTION_KEYS"/>

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

VALID\_FROM\_SAVEPOINT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the valid from savepoint version.



</td>
</tr>
<tr>
<td valign="top">

VALID\_FROM\_TIMESTAMP



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the valid from timestamp, in microseconds, given in UTC.



</td>
</tr>
<tr>
<td valign="top">

IS\_ENCRYPTED



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Indicates whether or not the persistence encryption is active: TRUE/FALSE.



</td>
</tr>
</table>

**Related Information**  


[M\_PERSISTENCE\_ENCRYPTION\_STATUS System View](m-persistence-encryption-status-system-view-20b7570.md "Provides information about persistence encryption.")

[SQLScript Encryption](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/afd729f2c11448a6a0cfb2b75fccc21b.html "") :arrow_upper_right:

