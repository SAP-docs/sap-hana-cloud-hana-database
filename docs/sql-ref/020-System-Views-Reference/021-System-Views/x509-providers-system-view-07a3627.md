<!-- loio07a362793a194647957d86b521f086a9 -->

# X509\_PROVIDERS System View

Lists all of the X.509 providers configured in the SAP HANA database.



<a name="loio07a362793a194647957d86b521f086a9__section_y5v_3sd_rhb"/>

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

ISSUER\_NAME



</td>
<td valign="top">

NVARCHAR\(512\)



</td>
<td valign="top">

Displays the issuer distinguished name.



</td>
</tr>
<tr>
<td valign="top">

OWNER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the provider's owner.



</td>
</tr>
</table>

**Related Information**  


[CREATE X509 PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-x509-provider-statement-access-control-3b3163d.md "Defines an X.509 provider in the SAP HANA database.")

[ALTER X509 PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-x509-provider-statement-access-control-4f7e59d.md "Alters an X.509 provider in the SAP HANA database.")

[DROP X509 PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-x509-provider-statement-access-control-f7a37e8.md "Drops an X.509 provider in the SAP HANA database.")

[X509\_PROVIDER\_RULES System View](x509-provider-rules-system-view-2457e71.md "Lists all of the matching rules for X.509 providers.")

[X509\_USER\_MAPPINGS System View](x509-user-mappings-system-view-210347f.md "Shows the X.509 certificates that are known for each user.")

[X.509 Certificate-Based User Authentication](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/2b335f7eec6a450095f110ea961d77cc.html "SAP HANA supports X.509 client certificates for user authentication in single sign-on environments. In particular, X.509 certificate-based authentication can be used for technical users to secure system-to-system integration.") :arrow_upper_right:

