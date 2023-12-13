<!-- loio3b3163d6ad0f4eb9bd73c7c060f49649 -->

# CREATE X509 PROVIDER Statement \(Access Control\)

Defines an X.509 provider in the SAP HANA database.



<a name="loio3b3163d6ad0f4eb9bd73c7c060f49649__section_rpm_5rd_rhb"/>

## Syntax

```
CREATE X509 PROVIDER <x509_provider_name> <issuer_clause> [ <matching_rules_clause> ]
```



<a name="loio3b3163d6ad0f4eb9bd73c7c060f49649__section_hqm_5rd_rhb"/>

## Syntax Elements


<dl>
<dt><b>

*<x509\_provider\_name\>*

</b></dt>
<dd>

Specifies the identifier of an X.509 provider to be created. The X.509 provider name must not already be defined.

```
<x509_provider_name> ::= <simple_identifier>
```



</dd><dt><b>

*<issuer\_clause\>*

</b></dt>
<dd>

Sets the issuer distinguished name for the X.509 provider.

```
<issuer_clause> ::= WITH ISSUER <issuer_distinguished_name>

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



</dd>
</dl>



<a name="loio3b3163d6ad0f4eb9bd73c7c060f49649__section_iqm_5rd_rhb"/>

## Permissions

Only database users that have the CREATE X509 PROVIDER system privilege can create an X.509 provider.



<a name="loio3b3163d6ad0f4eb9bd73c7c060f49649__section_jqm_5rd_rhb"/>

## Examples

Create an X.509 provider.

```
CREATE X509 PROVIDER MyProvider WITH ISSUER 'CN=DigiCert Global Root G2, OU=www.digicert.com, O=DigiCert Inc, C=US';
```

Create an X.509 provider with a matching rule.

```
CREATE X509 PROVIDER MyProvider WITH ISSUER 'CN=DigiCert Global Root G2, OU=www.digicert.com, O=DigiCert Inc, C=US'
   MATCHING RULES 'CN=*, OU=SAP SE, C=DE';
```

**Related Information**  


[X.509 Certificate-Based User Authentication](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2023_4_QRC/en-US/2b335f7eec6a450095f110ea961d77cc.html "SAP HANA supports X.509 client certificates for user authentication in single sign-on environments. In particular, X.509 certificate-based authentication can be used for technical users to secure system-to-system integration.") :arrow_upper_right:

[ALTER X509 PROVIDER Statement \(Access Control\)](alter-x509-provider-statement-access-control-4f7e59d.md "Alters an X.509 provider in the SAP HANA database.")

[DROP X509 PROVIDER Statement \(Access Control\)](drop-x509-provider-statement-access-control-f7a37e8.md "Drops an X.509 provider in the SAP HANA database.")

[X509\_PROVIDERS System View](../../020-System-Views-Reference/021-System-Views/x509-providers-system-view-07a3627.md "Lists all of the X.509 providers configured in the SAP HANA database.")

[X509\_PROVIDER\_RULES System View](../../020-System-Views-Reference/021-System-Views/x509-provider-rules-system-view-2457e71.md "Lists all of the matching rules for X.509 providers.")

[X509\_USER\_MAPPINGS System View](../../020-System-Views-Reference/021-System-Views/x509-user-mappings-system-view-210347f.md "Shows the X.509 certificates that are known for each user.")

