<!-- loio2457e71d1a6a41c1a02d9668fdf3df8e -->

# X509\_PROVIDER\_RULES System View

Lists all of the matching rules for X.509 providers.



<a name="loio2457e71d1a6a41c1a02d9668fdf3df8e__section_y5v_3sd_rhb"/>

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

X509\_PROVIDER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the X.509 provider.

</td>
</tr>
<tr>
<td valign="top">

POSITION

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Displays the order of the rule.

</td>
</tr>
<tr>
<td valign="top">

MATCHING\_RULE

</td>
<td valign="top">

NVARCHAR\(512\)

</td>
<td valign="top">

Displays the matching rule for the subject distinguished name.

</td>
</tr>
</table>



<a name="loio2457e71d1a6a41c1a02d9668fdf3df8e__section_vbh_kc1_fzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[CREATE X509 PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-x509-provider-statement-access-control-3b3163d.md "Defines an X.509 provider in the SAP HANA database.")

[ALTER X509 PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-x509-provider-statement-access-control-4f7e59d.md "Alters an X.509 provider in the SAP HANA database.")

[DROP X509 PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-x509-provider-statement-access-control-f7a37e8.md "Drops an X.509 provider in the SAP HANA database.")

[X509\_PROVIDERS System View](x509-providers-system-view-07a3627.md "Lists all of the X.509 providers configured in the SAP HANA database.")

[X509\_USER\_MAPPINGS System View](x509-user-mappings-system-view-210347f.md "Shows the X.509 certificates that are known for each user.")

[X.509 Certificate-Based User Authentication](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/2b335f7eec6a450095f110ea961d77cc.html "SAP HANA supports X.509 client certificates for user authentication in single sign-on environments. In particular, X.509 certificate-based authentication can be used for technical users to secure system-to-system integration.") :arrow_upper_right:

