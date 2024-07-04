<!-- loio20b7570475191014a6b8fc7108cb20af -->

# M\_PERSISTENCE\_ENCRYPTION\_STATUS System View

Provides information about persistence encryption.



<a name="loio20b7570475191014a6b8fc7108cb20af___m__p_e_r_s_i_s_t_e_n_c_e__e_n_c_r_y_p_t_i_o_n__s_t_a_t_u_s_1struct_M_PERSISTENCE_ENCRYPTION_STATUS"/>

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

ENCRYPTION\_ACTIVE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the encryption is currently active for writing into persistence: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

ENCRYPTION\_ACTIVE\_AFTER\_NEXT\_SAVEPOINT

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the encryption is active for writing into persistence after the next savepoint: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

KEY\_CHANGE\_WITH\_NEXT\_SAVEPOINT

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the next savepoint activates a new key: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

ROOT\_KEY\_CHANGE\_WITH\_NEXT\_SAVEPOINT

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the next savepoint activates a new root key: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_LATEST\_ROOT\_KEY\_VERSION

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the used root key version is the newest one: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

DATA\_CONVERSION\_ACTIVE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the conversion of data to the latest encryption status or key is active: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

KEY\_PAGE\_ENTRY\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of entries within the key page.

</td>
</tr>
<tr>
<td valign="top">

USED\_ROOT\_KEY\_HASH

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the hash of the root key that this service is using.

</td>
</tr>
</table>

**Related Information**  


[M\_PERSISTENCE\_ENCRYPTION\_KEYS System View](m-persistence-encryption-keys-system-view-20b732b.md "Provides information about encryption page keys.")

[SQLScript Encryption](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/afd729f2c11448a6a0cfb2b75fccc21b.html "") :arrow_upper_right:

