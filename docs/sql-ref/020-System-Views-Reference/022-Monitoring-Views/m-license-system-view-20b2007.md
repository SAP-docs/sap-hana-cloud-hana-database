<!-- loio20b20073751910149fcad0b73c80193f -->

# M\_LICENSE System View

Provides information on the currently valid license for the SAP HANA database that is installed on this system.



<a name="loio20b20073751910149fcad0b73c80193f___m__l_i_c_e_n_s_e_1struct_M_LICENSE"/>

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

HARDWARE\_KEY



</td>
<td valign="top">

NVARCHAR\(11\)



</td>
<td valign="top">

Displays the hardware key of the SAP HANA installation.



</td>
</tr>
<tr>
<td valign="top">

SYSTEM\_ID



</td>
<td valign="top">

NVARCHAR\(3\)



</td>
<td valign="top">

Displays the System Identifier \(SID\).



</td>
</tr>
<tr>
<td valign="top">

INSTALL\_NO



</td>
<td valign="top">

NVARCHAR\(10\)



</td>
<td valign="top">

Displays the installation number.



</td>
</tr>
<tr>
<td valign="top">

SYSTEM\_NO



</td>
<td valign="top">

NVARCHAR\(18\)



</td>
<td valign="top">

Displays the system number.



</td>
</tr>
<tr>
<td valign="top">

PRODUCT\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the licensed software product, for example, SAP HANA.



</td>
</tr>
<tr>
<td valign="top">

START\_DATE



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the start date of the validity period of the license.



</td>
</tr>
<tr>
<td valign="top">

EXPIRATION\_DATE



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the expiration date of the validity period of the license.



</td>
</tr>
<tr>
<td valign="top">

LAST\_SUCCESSFUL\_CHECK



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the latest date on which the license was successfully checked and found valid.



</td>
</tr>
<tr>
<td valign="top">

PERMANENT



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays TRUE if the license is permanent and FALSE if the license is temporary.



</td>
</tr>
<tr>
<td valign="top">

VALID



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Indicates whether the license is valid or not: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

LOCKED\_DOWN



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Indicates whether the system is locked down due to license status: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

IS\_DATABASE\_LOCAL



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Indicates whether the license is a local database local license: TRUE/FALSE.



</td>
</tr>
</table>

**Related Information**  


[M\_LICENSES System View](m-licenses-system-view-1d7e7f5.md "Provides information on all of the licenses (if any) that are installed on this system.")

