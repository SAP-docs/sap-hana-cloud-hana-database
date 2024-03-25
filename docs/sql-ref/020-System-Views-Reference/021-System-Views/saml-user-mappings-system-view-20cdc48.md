<!-- loio20cdc48e75191014b2cc9d2872477297 -->

# SAML\_USER\_MAPPINGS System View

Shows the SAML provider information for each user.



<a name="loio20cdc48e75191014b2cc9d2872477297___s_a_m_l__u_s_e_r__m_a_p_p_i_n_g_s_1struct_SAML_USER_MAPPINGS"/>

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

Displays the user name.

</td>
</tr>
<tr>
<td valign="top">

SAML\_PROVIDER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the SAML provider.

</td>
</tr>
<tr>
<td valign="top">

EXTERNAL\_IDENTITY

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the user known to the provider.

</td>
</tr>
</table>



<a name="loio20cdc48e75191014b2cc9d2872477297__section_hm5_dsz_2zb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[SAML\_PROVIDERS System View](saml-providers-system-view-20cda7b.md "Shows available SAML providers.")

[CREATE SAML PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-saml-provider-statement-access-control-20d4cca.md "Defines a SAML provider in the SAP HANA database.")

[ALTER SAML PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-saml-provider-statement-access-control-20d04f7.md "Changes the properties of the specified SAML provider.")

[DROP SAML PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-saml-provider-statement-access-control-20d76c8.md "Drops the specified SAML provider.")

