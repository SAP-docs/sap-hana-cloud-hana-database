<!-- loio210347fc75191014a80dfe0a0af3c6bf -->

# X509\_USER\_MAPPINGS System View

Shows the X.509 certificates that are known for each user.



<a name="loio210347fc75191014a80dfe0a0af3c6bf___x509__u_s_e_r__m_a_p_p_i_n_g_s_1struct_X509_USER_MAPPINGS"/>

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

SUBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(512\)

</td>
<td valign="top">

Displays the subject name of the X.509 certificate of the user.If the user is mapped with a wildcard \(ANY\) for this subject, this value is NULL. 

</td>
</tr>
<tr>
<td valign="top">

ISSUER\_NAME

</td>
<td valign="top">

NVARCHAR\(512\)

</td>
<td valign="top">

Displays the issuer name of the X.509 certificate of the user.If the user is mapped using a provider, this column is NULL. 

</td>
</tr>
<tr>
<td valign="top">

X509\_PROVIDER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the X.509 provider.If the user is mapped without a provider, this column is NULL. 

</td>
</tr>
</table>



<a name="loio210347fc75191014a80dfe0a0af3c6bf__section_pck_lc1_fzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[CERTIFICATES System View](certificates-system-view-d076e2b.md "Provides information about certificates usable in PSEs.")

[SAML\_PROVIDERS System View](saml-providers-system-view-20cda7b.md "Shows available SAML providers.")

[PSE\_CERTIFICATES System View](pse-certificates-system-view-0184e53.md "Provides information about certificates used in PSEs.")

[CREATE SAML PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-saml-provider-statement-access-control-20d4cca.md "Defines a SAML provider in the SAP HANA database.")

[CREATE X509 PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-x509-provider-statement-access-control-3b3163d.md "Defines an X.509 provider in the SAP HANA database.")

[ALTER X509 PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-x509-provider-statement-access-control-4f7e59d.md "Alters an X.509 provider in the SAP HANA database.")

[DROP X509 PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-x509-provider-statement-access-control-f7a37e8.md "Drops an X.509 provider in the SAP HANA database.")

[X509\_PROVIDERS System View](x509-providers-system-view-07a3627.md "Lists all of the X.509 providers configured in the SAP HANA database.")

[X509\_PROVIDER\_RULES System View](x509-provider-rules-system-view-2457e71.md "Lists all of the matching rules for X.509 providers.")

[X.509 Certificate-Based User Authentication](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/2b335f7eec6a450095f110ea961d77cc.html "SAP HANA supports X.509 client certificates for user authentication in single sign-on environments. In particular, X.509 certificate-based authentication can be used for technical users to secure system-to-system integration.") :arrow_upper_right:

