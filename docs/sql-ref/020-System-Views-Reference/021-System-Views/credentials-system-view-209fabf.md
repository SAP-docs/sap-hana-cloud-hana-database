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

Displays the purpose the credential is valid for, for example, remote machine.

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



<a name="loio209fabf875191014b8f2a4731c564884__section_twx_41q_bzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[CREATE CREDENTIAL Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-credential-statement-access-control-20d3f46.md "Creates a component-specific or application-specific credential.")

[ALTER CREDENTIAL Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-credential-statement-access-control-20cfdad.md "Modifies an existing component-specific or application-specific credential.")

[DROP CREDENTIAL Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-credential-statement-access-control-20d64db.md "Drops an existing component-specific or application-specific credential.")

[Managing Credentials for Remote Sources](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/2ba7db1c676f4f838979b6f33ad207f7.html "The following credential types (or credential modes) are supported for accessing a remote source: technical user, secondary credentials, single sign-on with JSON Web Tokens, and mutual authentication with X.509 certificates.") :arrow_upper_right:

[Managing Secondary Credentials](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/93159ac691654784898d2f6e700f821f.html "Secondary credentials let you assign different credentials to different users when using a remote source.") :arrow_upper_right:

