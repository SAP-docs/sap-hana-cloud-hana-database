<!-- loio10fe8070539649358c79955110311082 -->

# SET PSE Statement \(System Management\)

Sets the purpose of a PSE.



## Syntax

```
SET PSE <pse_name> PURPOSE <purpose> [ FOR <purpose_object_list> ]
```



## Syntax Elements


<dl>
<dt><b>

*<pse\_name\>*

</b></dt>
<dd>

Specifies the name of the PSE.

```
<pse_name> ::= <identifier>
```



</dd><dt><b>

PURPOSE *<purpose\>*

</b></dt>
<dd>

Specifies the purpose of the PSE.

```
<purpose> ::= 
 JWT
 | SAML
 | X509
 | LDAP
 | REMOTE SOURCE
```



</dd><dt><b>

*<purpose\_object\_list\>*

</b></dt>
<dd>

Specifies the remote sources or identity providers to assign to a PSE that has no purpose objects assigned.

```
<purpose_object_list> ::= 
{ PROVIDER <provider_list> | REMOTE SOURCE <remote_source_list> }

<provider_list> ::= <provider> [ , <provider>[ ,...] ]
<provider> ::= <simple_identifier>
<remote_source_list> ::= <remote_source> [, <remote_source> [,...] ]
<remote_source> ::= <simple_identifier>
```

Use the ALTER PSE statement with the *<add\_purpose\_object\_clause\>* clause, not the SET PSE statement with the *<purpose\_object\_list\>* clause, to add or reassign providers or remote sources to an existing PSE with providers or remote sources already assigned.

No objects can be assigned to a PSE with purpose LDAP.

PROVIDER can only be specified for a PSE with purpose SAML, JWT, or X509. A PSE with purpose SAML, JWT, or X509 must specify a provider.

REMOTE SOURCE can only be specified for a PSE with purpose REMOTE SOURCE. Specifying REMOTE SOURCE is optional.

For JWT, SAML, and X509, the provider must exist before it can be added. See *CREATE JWT PROVIDER Statement*, *CREATE SAML PROVIDER Statement*, and *CREATE X509 PROVIDER Statement*. For REMOTE SOURCE, the remote source must exist before it can be added. See *CREATE REMOTE SOURCE* Statement.

Duplicates defined in *<provider\_list\>* or *<remote\_source\_list\>* are ignored.

Multiple providers or remote sources can be assigned to a single PSE, but a provider or remote source can only be assigned to one PSE.

Assigning a provider or remote source that has already been assigned to another PSE results in a reassignment. If such a reassignment results in the other PSE having no objects, then its purpose is cleared.

For a PSE with purpose REMOTE SOURCE, to remove all remote sources but keep the purpose, execute the SET PSE statement without the FOR *<remote\_source\_list\>* clauses. The purpose of the PSE becomes unqualified.

To remove a provider or remote source from a PSE, use ALTER PSE with the *<drop\_purpose\_object\_clause\>* clause.



</dd>
</dl>



## Description

Sets the purpose of the PSE, that is which type of trust validation the PSE will be used for. For information about qualifying PSEs, see *Certificate Collections* in the *SAP HANA Cloud, SAP HANA Database Security Guide*.

To change the purpose of an existing PSE, you must first execute the UNSET PSE statement to remove the existing purpose and any assigned objects from the PSE and then use the SET PSE statement to assign a new purpose.



<a name="loio10fe8070539649358c79955110311082__section_jtv_tj3_5rb"/>

## Permissions

You must have the REFERENCES object privilege on the PSE or be the owner and the following purpose-specific privileges:


<table>
<tr>
<th valign="top">

Purpose

</th>
<th valign="top">

Privileges

</th>
</tr>
<tr>
<td valign="top">

LDAP

</td>
<td valign="top">

LDAP ADMIN system privilege

</td>
</tr>
<tr>
<td valign="top">

REMOTE SOURCE

</td>
<td valign="top">

CREATE REMOTE SOURCE system privilege

</td>
</tr>
<tr>
<td valign="top">

SAML, JWT, or X509

</td>
<td valign="top">

ALTER object privilege on the providers

</td>
</tr>
</table>



## Examples

Set the REMOTE SOURCE purpose for the HDD\_PSE PSE using remote source HDB\_SYS.

```
SET PSE HDB_PSE PURPOSE REMOTE SOURCE FOR REMOTE SOURCE HDB_SYS;
```

Set the REMOTE SOURCE purpose for the HDD1\_PSE store using remote sources HDB\_SYS1 and HDB\_SYS2.

```
SET PSE HDB1_PSE PURPOSE REMOTE SOURCE FOR REMOTE SOURCE HDB_SYS1, HDB_SYS2;
```

This example creates the JWT PSE JWT\_PSE for the provider MY\_JWT\_PROVIDER.

```
SET PSE JWT_PSE PURPOSE JWT FOR PROVIDER MY_JWT_PROVIDER;
```

This example creates the SAML PSE SAML\_PSE for the provider MY\_SAML\_PROVIDER.

```
SET PSE SAML_PSE PURPOSE SAML FOR PROVIDER MY_SAML_PROVIDER;
```

**Related Information**  


[ALTER PSE Statement \(System Management\)](alter-pse-statement-system-management-9c22c6f.md "Modifies a PSE.")

[PSE\_PURPOSE\_OBJECTS System View](../../020-System-Views-Reference/021-System-Views/pse-purpose-objects-system-view-437cd32.md "Provides information about all PSEs and their assigned providers or hosts, referred to as purpose objects.")

[UNSET PSE Statement \(System Management\)](unset-pse-statement-system-management-4082553.md "Removes the purpose for a PSE.")

[CREATE JWT PROVIDER Statement \(Access Control\)](create-jwt-provider-statement-access-control-bfe3daf.md "Defines a JWT provider in the SAP HANA database.")

[CREATE SAML PROVIDER Statement \(Access Control\)](create-saml-provider-statement-access-control-20d4cca.md "Defines a SAML provider in the SAP HANA database.")

[CREATE X509 PROVIDER Statement \(Access Control\)](create-x509-provider-statement-access-control-3b3163d.md "Defines an X.509 provider in the SAP HANA database.")

[CREATE REMOTE SOURCE Statement \(Access Control\)](create-remote-source-statement-access-control-20d4834.md "Defines an external data source that can connect to the SAP HANA database.")

[Certificate Collections](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2023_4_QRC/en-US/75d0cfec8e4f44c3a649d26e9cefa314.html "A certificate collection is a secure location where the public-key certificates of trusted communication partners or root certificates from trusted Certification Authorities are stored. Certificate collections are created and managed as database objects directly in the SAP HANA database.") :arrow_upper_right:

[SQL Statements and Authorization for Certificate Management (Reference)](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2023_4_QRC/en-US/f32bcc9c4b734f24bedaf6253e7981d6.html "All administration tasks related to the management of public-key certificates (and public keys) can be performed using SQL.") :arrow_upper_right:

