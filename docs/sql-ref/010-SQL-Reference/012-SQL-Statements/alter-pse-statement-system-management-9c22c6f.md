<!-- loio9c22c6f22df64bc6881d1ed61be18b8d -->

# ALTER PSE Statement \(System Management\)

Modifies a PSE.



## Syntax

```
ALTER PSE <pse_name> { <certificate_clause>
   | <set_own_certificate_clause>
   | <unset_own_certificate_clause>
   | <add_purpose_object_clause>
   | <drop_purpose_object_clause>
   | <public_key_clause> 
   | <set_url_clause> } 
```



## Syntax Elements


<dl>
<dt><b>

*<pse\_name\>*

</b></dt>
<dd>

Specifies the name of the PSE to be altered.

```
<pse_name> ::= <identifier>
```



</dd><dt><b>

*<certificate\_clause\>*

</b></dt>
<dd>

Add or drop the certificate\(s\) to the PSE.

```
<certificate_clause> ::= 
   { ADD | DROP } CERTIFICATE ( 
   { <certificate_name> [ , <certificate_name> ]...
   | <certificate_id> [ , <certificate_id> ]...} )

<certificate_id> ::= <unsigned_integer>
<certificate_name> ::= <identifier>
```



</dd><dt><b>

*<set\_own\_certificate\_clause\>*

</b></dt>
<dd>

Sets an own certificate and private key.

```
<set_own_certificate_clause> ::= SET OWN CERTIFICATE <certificate_content>

<certificate_content> ::= <string_literal>
```

The string *<certificate\_content\>* may contain one or several certificates in the PEM format and the private key of the own certificate. One of the certificates is the own certificate and the other certificate\(s\) are intermediate chain certificates completing the trust chain from the own certificate to the root certificate which the peer trusts. The own certificate and the order of the certificates forming a chain can be identified by the issuer or subject relationship. In case the PSE already has an own certificate assigned, it is replaced.



</dd><dt><b>

*<unset\_own\_certificate\_clause\>*

</b></dt>
<dd>

Removes an own certificate and private key.

```
<unset_own_certificate_clause> ::= UNSET OWN CERTIFICATE
```



</dd><dt><b>

*<add\_purpose\_object\_clause\>*

</b></dt>
<dd>

Specifies the remote source or identity provider to add to the PSE.

```
<add_purpose_object_clause> ::= 
ADD { PROVIDER <provider_list>
    | REMOTE SOURCE <remote_source_list> 
    | MANAGED PSE <managed_pse_list> }

<provider_list> ::= <provider>[, <provider> [,...] ]
<provider> ::= <simple_identifier>
<remote_source_list> ::= <remote_source> [, <remote_source> [,...] ]
<remote_source> ::= <simple_identifier>
<managed_pse_list> ::= <managed_pse>[, <managed_pse> [,...] ]
<managed_pse> ::= <string_identifier>
```

Use the SET PSE statement with the *<purpose\_object\_list\>* clause, not the ALTER PSE statement with the *<add\_purpose\_object\_clause\>* clause, to add a provider or remote source to an existing PSE that does not have at least one provider or remote source assigned.

PROVIDER can only be specified for a PSE with purpose SAML, JWT, or X509. A PSE with purpose SAML, JWT, or X509 must specify a provider.

REMOTE SOURCE can only be specified for a PSE with purpose REMOTE SOURCE. Specifying REMOTE SOURCE is optional.

Duplicates objects in the object lists are ignored.

Multiple providers or remote sources can be assigned to a single PSE, but a provider or remote source can only be assigned to one PSE.

An object, such as a provider, remote source, etc., can only be assigned to one PSE. Assigning an object to a PSE removes a previous PSE assignment for that object.

Reassigning an object to another PSE may result in the original PSE losing its purpose assignment if the object was the only one assigned to the original PSE.



</dd>
</dl>


<dl>
<dt><b>

*<drop\_purpose\_object\_clause\>*

</b></dt>
<dd>

Specifies the objects to remove from the PSE.

```
<drop_purpose_object_clause> ::= 
   { DROP { PROVIDER <provider_list>
   | REMOTE SOURCE <remote_source_list> }
   | MANAGED PSE <managed_pse_list> }

<provider_list> ::= <provider>[, <provider> [,...] ]
<provider> ::= <simple_identifier>
<remote_source_list> ::= <remote_source> [, <remote_source> [,...] ]
<remote_source> ::= <simple_identifier>
<managed_pse_list> ::= <managed_pse>[, <managed_pse> [,...] ]
<managed_pse> ::= <string_identifier>
```

Use the UNSET PSE statement with the *<purpose\_object\_list\>* clause, not the ALTER PSE statement with the *<drop\_purpose\_object\_clause\>* clause, to remove a provider or remote source from a PSE that does not have any other provider or remote source assigned.



</dd><dt><b>

*<public\_key\_clause\>*

</b></dt>
<dd>

Add or drop a public key to or from the PSE.

```
<public_key_clause> ::= 
   { ADD | DROP } PUBLIC KEY ( <public_key_name> [ , <public_key_name> ]...)

<public_key_name> ::= <unsigned_integer>
```



</dd><dt><b>

*<set\_url\_clause\>*

</b></dt>
<dd>

Defines the URL for the managed PSE.

```
<set_url_clause> ::= 
   SET URL <url_string_literal>
```



</dd>
</dl>



## Description

Modifies a PSE.

Use the SET PURPOSE and UNSET PURPOSE statements to change the purpose of a PSE.



<a name="loio9c22c6f22df64bc6881d1ed61be18b8d__section_uxr_f5x_vcb"/>

## Permissions

The privilege required depends on the action performed.


<table>
<tr>
<th valign="top">

Action

</th>
<th valign="top" colspan="2">

Privilege

</th>
</tr>
<tr>
<td valign="top">

Alter a PSE with no purpose assigned.

</td>
<td valign="top" colspan="2">

Requires one of the following:

-   You own the PSE object.
-   ALTER object privilege on the PSE object.



</td>
</tr>
<tr>
<td valign="top">

Alter a PSE that has a purpose assigned.

</td>
<td valign="top" colspan="2">

Requires the REVERENCES object-level privilege on the PSE along with purpose-specific permissions to add or drop a purpose object:

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

**Purpose**

</td>
<td valign="top">

**Privilege**

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

Remote source,

</td>
<td valign="top">

CREATE REMOTE SOURCE system privilege

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

SAML, JWT, X509 identity provider, or a Managed PSE

</td>
<td valign="top">

ALTER object privilege on the provider

</td>
</tr>
</table>



## Examples

The following example adds another remote source to a PSE that has the purpose REMOTE SOURCE.

```
ALTER PSE HDB_PSE ADD REMOTE SOURCE HDB_ADM;
```

The following example adds the public key jwt\_pubkey to the PSE jwt\_pse.

```
ALTER PSE jwt_pse ADD PUBLIC KEY jwt_pubkey;
```

The following example adds the certificate saml\_cert to the PSE saml\_pse.

```
ALTER PSE saml_pse ADD CERTIFICATE saml_cert;
```

The following example sets the managed PSE URL for pse1.

```
ALTER PSE pse1 SET URL 'https://XXXXX.sap.com/.well-known/xxxxx/jwks';
```

The following example adds two managed PSEs to pse1.

```
ALTER PSE pse1 ADD MANAGED PSE my_managed_pse1, my_managed_pse2;
```

The following example drops a managed PSE my\_managed\_pse1 from pse1.

```
ALTER PSE pse1 DROP MANAGED PSE my_managed_pse1;
```

**Related Information**  


[SET PSE Statement \(System Management\)](set-pse-statement-system-management-10fe807.md "Sets the purpose of a PSE, which is the type of trust validation for the PSE to use.")

[PSE\_PURPOSE\_OBJECTS System View](../../020-System-Views-Reference/021-System-Views/pse-purpose-objects-system-view-437cd32.md "Provides information about all PSEs and their assigned providers or hosts, referred to as purpose objects.")

[UNSET PSE Statement \(System Management\)](unset-pse-statement-system-management-4082553.md "Remove the assigned purpose for a PSE along with any assigned objects.")

[CREATE REMOTE SOURCE Statement \(Access Control\)](create-remote-source-statement-access-control-20d4834.md "Defines an external data source that can connect to the SAP HANA database.")

[CREATE JWT PROVIDER Statement \(Access Control\)](create-jwt-provider-statement-access-control-bfe3daf.md "Defines a JWT provider in the SAP HANA database.")

[CREATE SAML PROVIDER Statement \(Access Control\)](create-saml-provider-statement-access-control-20d4cca.md "Defines a SAML provider in the SAP HANA database.")

[CREATE X509 PROVIDER Statement \(Access Control\)](create-x509-provider-statement-access-control-3b3163d.md "Defines an X.509 provider in the SAP HANA database.")

[Certificate Collections](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/75d0cfec8e4f44c3a649d26e9cefa314.html "A certificate collection is a secure location where the public-key certificates of trusted communication partners or root certificates from trusted Certification Authorities are stored. Certificate collections are created and managed as database objects directly in the SAP HANA database.") :arrow_upper_right:

[SQL Statements and Authorization for Certificate Management (Reference)](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/f32bcc9c4b734f24bedaf6253e7981d6.html "All administration tasks related to the management of public-key certificates (and public keys) can be performed using SQL.") :arrow_upper_right:

