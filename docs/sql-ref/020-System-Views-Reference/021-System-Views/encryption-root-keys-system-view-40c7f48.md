<!-- loio40c7f484a9ab49d5b3dbcb305ac91fcd -->

# ENCRYPTION\_ROOT\_KEYS System View

Provides information about root keys.



<a name="loio40c7f484a9ab49d5b3dbcb305ac91fcd___e_n_c_r_y_p_t_i_o_n__r_o_o_t__k_e_y_s_1struct_ENCRYPTION_ROOT_KEYS"/>

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

ROOT\_KEY\_TYPE



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the usage type of the root key: PERSISTENCE, DPAPI, LOG, BACKUP.



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

Displays the creation time of the root key \(UTC\).



</td>
</tr>
<tr>
<td valign="top">

IS\_CONSISTENT



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the key is consistent between persistence and the SSFS file: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

RESET\_COUNT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the number of consistency resets.



</td>
</tr>
<tr>
<td valign="top">

IS\_USED



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether key version is the version used for encryption: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

ROOT\_KEY\_STATUS



</td>
<td valign="top">

NVARCHAR\(11\)



</td>
<td valign="top">

Displays the state of the root key: ACTIVE, PREACTIVE, or DEACTIVATED.



</td>
</tr>
<tr>
<td valign="top">

ROOT\_KEY\_HASH



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the root key hash value.



</td>
</tr>
<tr>
<td valign="top">

IN\_BACKUP



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether root key has been previously backed up: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

ENCRYPTION\_ALGORITHM



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the algorithm associated with this key.



</td>
</tr>
<tr>
<td valign="top">

TENANT\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the tenant name if the configuration is tenant-specific.



</td>
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
</table>

**Related Information**  


[ALTER SYSTEM APPLICATION ENCRYPTION Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-application-encryption-statement-system-management-f425959.md "Manages encryption keys for applications that use the internal data encryption service.")

[M\_ENCRYPTION\_OVERVIEW System View](../022-Monitoring-Views/m-encryption-overview-system-view-ee1a50a.md "Reports the encryption status for all data at rest where encryption is supported.")

[M\_PERSISTENCE\_ENCRYPTION\_STATUS System View](../022-Monitoring-Views/m-persistence-encryption-status-system-view-20b7570.md "Provides information about persistence encryption.")

[Data Encryption](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/8b39eaf4af7a422e9ffd48a62c2558ce.html "The SAP HANA Cloud, SAP HANA database uses a number of encryption services to protect data at rest.") :arrow_upper_right:

[SQLScript Encryption](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/afd729f2c11448a6a0cfb2b75fccc21b.html "") :arrow_upper_right:

