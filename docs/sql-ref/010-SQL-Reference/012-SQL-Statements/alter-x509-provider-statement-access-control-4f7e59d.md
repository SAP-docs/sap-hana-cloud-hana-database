<!-- loio4f7e59d60616461cbfaa00bda366b9f2 -->

# ALTER X509 PROVIDER Statement \(Access Control\)

Alters an X.509 provider in the SAP HANA database.



<a name="loio4f7e59d60616461cbfaa00bda366b9f2__section_rpm_5rd_rhb"/>

## Syntax

```
ALTER X509 PROVIDER <x509_provider_name> 
   { SET { [ <issuer_clause> ] [ <matching_rules_clause> ] }
   | UNSET MATCHING RULES
```



<a name="loio4f7e59d60616461cbfaa00bda366b9f2__section_hqm_5rd_rhb"/>

## Syntax Elements


<dl>
<dt><b>

*<x509\_provider\_name\>*

</b></dt>
<dd>

Specifies the identifier of an X.509 provider to be modified.

```
<x509_provider_name> ::= <simple_identifier>
```



</dd><dt><b>

*<issuer\_clause\>*

</b></dt>
<dd>

Sets the issuer distinguished name for the X.509 provider.

```
<issuer_clause> ::= ISSUER <issuer_distinguished_name>

<issuer_distinguished_name> ::= <string_literal>
```



</dd><dt><b>

*<matching\_rules\_clause\>*

</b></dt>
<dd>

Specifies one or more rules for matching external identities to database users. A matching rule is a distinguished name where one attribute has a value of ‘\*’. This attribute contains the user name that needs to be matched during logon. All other attributes must match and be in the same order.

Matching rules are tried in the same order they are defined in the provider, and the first one that matches is used.

```
<matching_rules_clause> ::= MATCHING RULES '<subject_distinguished_name_mapping>'
   [, '<subject_distinguished_name_mapping>' ... ]

<subject_distinguished_name_mapping> ::= <string_literal>
```

Setting new matching rules replaces existing rules for the provider.



</dd><dt><b>

UNSET MATCHING RULES

</b></dt>
<dd>

Removes matching rules for the provider. If a user is mapped to the provider using a wildcard \(ANY\) subject, you cannot unset the matching rules.



</dd>
</dl>



<a name="loio4f7e59d60616461cbfaa00bda366b9f2__section_i2s_yrd_rhb"/>

## Description

For the SET clause, at least one of the two optional parameters must be specified.



<a name="loio4f7e59d60616461cbfaa00bda366b9f2__section_s21_1cg_qbb"/>

## Permissions

You must have the ALTER object privilege on the X.509 provider.



<a name="loio4f7e59d60616461cbfaa00bda366b9f2__section_j2s_yrd_rhb"/>

## Examples

Change the issuer of the MyProvider X.509 provider.

```
ALTER X509 PROVIDER MyProvider SET ISSUER 'CN=DigiCert Global Root G2, OU=www.digicert.com, O=DigiCert Inc, C=US'
```

Remove the matching rules of the MyProvider X.509 provider.

```
ALTER X509 PROVIDER MyProvider UNSET MATCHING RULES
```

**Related Information**  


[X.509 Certificate-Based User Authentication](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/2b335f7eec6a450095f110ea961d77cc.html "SAP HANA supports X.509 client certificates for user authentication in single sign-on environments. In particular, X.509 certificate-based authentication can be used for technical users to secure system-to-system integration.") :arrow_upper_right:

[CREATE X509 PROVIDER Statement \(Access Control\)](create-x509-provider-statement-access-control-3b3163d.md "Defines an X.509 provider in the SAP HANA database.")

[DROP X509 PROVIDER Statement \(Access Control\)](drop-x509-provider-statement-access-control-f7a37e8.md "Drops an X.509 provider in the SAP HANA database.")

[X509\_PROVIDERS System View](../../020-System-Views-Reference/021-System-Views/x509-providers-system-view-07a3627.md "Lists all of the X.509 providers configured in the SAP HANA database.")

[X509\_PROVIDER\_RULES System View](../../020-System-Views-Reference/021-System-Views/x509-provider-rules-system-view-2457e71.md "Lists all of the matching rules for X.509 providers.")

[X509\_USER\_MAPPINGS System View](../../020-System-Views-Reference/021-System-Views/x509-user-mappings-system-view-210347f.md "Shows the X.509 certificates that are known for each user.")

