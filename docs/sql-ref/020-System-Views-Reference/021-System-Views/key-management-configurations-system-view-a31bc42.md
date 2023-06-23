<!-- loioa31bc428fef04c02a3cd911fd06a0be9 -->

# KEY\_MANAGEMENT\_CONFIGURATIONS System View

Displays information about the existing key management configurations.



<a name="loioa31bc428fef04c02a3cd911fd06a0be9__section_ysw_bkb_xlb"/>

## Structure


<table>
<tr>
<th valign="top">

Column



</th>
<th valign="top">

Data Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

DATABASE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the database name.



</td>
</tr>
<tr>
<td valign="top">

CONFIGURATION\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the key management configuration.



</td>
</tr>
<tr>
<td valign="top">

IS\_ACTIVE



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Indicates whether this configuration is used by LSS to define access to SAP HANA's sensitive information.



</td>
</tr>
<tr>
<td valign="top">

TYPE



</td>
<td valign="top">

NVARCHAR\(20\)



</td>
<td valign="top">

Displays the type of external key management.



</td>
</tr>
<tr>
<td valign="top">

CLIENT\_VERSION



</td>
<td valign="top">

NVARCHAR\(12\)



</td>
<td valign="top">

Displays the version of the driver software.



</td>
</tr>
<tr>
<td valign="top">

PROPERTIES



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays a reduced version of the properties section of the *<settings\>* JSON \(the "credentials" object is omitted\).



</td>
</tr>
<tr>
<td valign="top">

TENANT\_NAME



</td>
<td valign="top">

NVARCHAR\(256



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

