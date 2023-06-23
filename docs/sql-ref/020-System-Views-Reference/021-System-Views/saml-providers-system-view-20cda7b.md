<!-- loio20cda7b5751910149d0ef5e67ff1a947 -->

# SAML\_PROVIDERS System View

Shows available SAML providers.



<a name="loio20cda7b5751910149d0ef5e67ff1a947__section_ml1_hsd_rhb"/>

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

SAML\_PROVIDER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the provider name.



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

Displays the subject of the X.509 certificate of the SAML provider.



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

Displays the issuer of the X.509 certificate of the SAML provider.



</td>
</tr>
<tr>
<td valign="top">

ENTITY\_ID



</td>
<td valign="top">

NVARCHAR\(1024\)



</td>
<td valign="top">

Displays the entity name of the SAML provider \(optional\).



</td>
</tr>
<tr>
<td valign="top">

IS\_CASE\_SENSITIVE



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the user mapping is checked case sensitive: TRUE/FALSE.



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

Displays the name of the owner of the provider.



</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_USER\_ATTRIBUTE



</td>
<td valign="top">

NVARCHAR\(512\)



</td>
<td valign="top">

Displays the attribute from where the application user is extracted.



</td>
</tr>
<tr>
<td valign="top">

IS\_USER\_CREATION\_ENABLED



</td>
<td valign="top">

VARCHAR\(5\)



</td>
<td valign="top">

Displays whether the provider is allowed to create a user implicitly: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

USER\_CREATION\_USER\_TYPE



</td>
<td valign="top">

VARCHAR\(10\)



</td>
<td valign="top">

Displays the type of user to create when user creation is enabled: STANDARD, RESTRICTED



</td>
</tr>
<tr>
<td valign="top">

USER\_CREATION\_USERGROUP



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the user group a created user will be a member of.



</td>
</tr>
</table>

**Related Information**  


[CREATE SAML PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-saml-provider-statement-access-control-20d4cca.md "Defines a SAML provider in the SAP HANA database.")

[ALTER SAML PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-saml-provider-statement-access-control-20d04f7.md "Changes the properties of the specified SAML provider.")

[DROP SAML PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-saml-provider-statement-access-control-20d76c8.md "Drops the specified SAML provider.")

