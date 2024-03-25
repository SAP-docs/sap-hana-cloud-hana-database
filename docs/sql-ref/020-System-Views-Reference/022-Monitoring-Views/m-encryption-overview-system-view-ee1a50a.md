<!-- loioee1a50a49a684124ba3cc4815ecc7189 -->

# M\_ENCRYPTION\_OVERVIEW System View

Reports the encryption status for all data at rest where encryption is supported.



<a name="loioee1a50a49a684124ba3cc4815ecc7189___m_e_n_c_r_y_p_t_i_o_n_o_v_e_r_v_i_e_w_1struct_M_ENCRYPTION_OVERVIEW"/>

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

SCOPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays whether the scope includes PERSISTENCE \(data volumes\), LOG \(redo log\), or BACKUP.

</td>
</tr>
<tr>
<td valign="top">

IS\_ENCRYPTION\_ACTIVE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates if the encryption for the scope is currently active: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

LAST\_CHANGE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the latest timestamp, in the server's local time, when the status was changed

</td>
</tr>
<tr>
<td valign="top">

CONFIGURATION\_CONTROL

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Indicates whether encryption configuration is controlled by the local database or the system database.

</td>
</tr>
<tr>
<td valign="top">

ENCRYPTION\_CONTROL\_LAST\_CHANGE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last time that the encryption control was changed.

</td>
</tr>
</table>

**Related Information**  


[ALTER SYSTEM APPLICATION ENCRYPTION Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-application-encryption-statement-system-management-f425959.md "Manages encryption keys for applications that use the internal data encryption service.")

[Data Storage Security](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/b30fda1483b34628802a8d62bd5d39df.html "Several mechanisms are used to protect security-relevant data used by the SAP HANA Cloud, SAP HANA database from unauthorized access.") :arrow_upper_right:

[SQLScript Encryption](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/afd729f2c11448a6a0cfb2b75fccc21b.html "") :arrow_upper_right:

