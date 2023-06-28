<!-- loio209fabf875191014b8f2a4731c564884 -->

# CREDENTIALS System View

Provides information about credentials for users and components.



<a name="loio209fabf875191014b8f2a4731c564884___c_r_e_d_e_n_t_i_a_l_s_1struct_CREDENTIALS"/>

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

Displays the name of the user the credential belongs to.



</td>
</tr>
<tr>
<td valign="top">

COMPONENT



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the component the credential is valid for.



</td>
</tr>
<tr>
<td valign="top">

PURPOSE



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the purpose, for example remote machine, that the credential is valid for.



</td>
</tr>
<tr>
<td valign="top">

CREDENTIAL\_TYPE



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the type of the credential, for example, password or X509.



</td>
</tr>
</table>

**Related Information**  


[CREATE CREDENTIAL Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-credential-statement-access-control-20d3f46.md "Creates a component-specific or application-specific credential.")

[ALTER CREDENTIAL Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-credential-statement-access-control-20cfdad.md "Modifies an existing component-specific or application-specific credential.")

[DROP CREDENTIAL Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-credential-statement-access-control-20d64db.md "Drops an existing component-specific or application-specific credential.")

[Managing Credentials for Remote Sources](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/2ba7db1c676f4f838979b6f33ad207f7.html "The following credential types (or credential modes) are supported for accessing a remote source: technical user, secondary credentials, single sign-on with JSON Web Tokens, and mutual authentication with X.509 certificates.") :arrow_upper_right:

[Managing Secondary Credentials](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/93159ac691654784898d2f6e700f821f.html "Secondary credentials let you assign different credentials to different users when using a remote source.") :arrow_upper_right:
