<!-- loio408255391bd043209a957830f8e87b65 -->

# UNSET PSE Statement \(System Management\)

Removes the purpose for a PSE.



## Syntax

```
UNSET PSE <pse_name> PURPOSE <purpose>
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

*<purpose\>*

</b></dt>
<dd>

Specifies the purpose of the PSE.

```
<purpose> ::= 
 JWT
 | SAML
 | LDAP
 | DATABASE REPLICATION
 | REMOTE SOURCE
```



</dd>
</dl>



## Description

Removes the assigned purpose for a PSE along with any assigned remote sources or providers.



<a name="loio408255391bd043209a957830f8e87b65__section_jtv_tj3_5rb"/>

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

ALTER object privilege on all assigned providers

</td>
</tr>
</table>



## Examples

Remove the REMOTE SOURCE purpose from the example\_pse PSE.

```
UNSET PSE example_pse PURPOSE REMOTE SOURCE;
```

**Related Information**  


[PSE\_PURPOSE\_OBJECTS System View](../../020-System-Views-Reference/021-System-Views/pse-purpose-objects-system-view-437cd32.md "Provides information about all PSEs and their assigned providers or hosts, referred to as purpose objects.")

[SET PSE Statement \(System Management\)](set-pse-statement-system-management-10fe807.md "Sets the purpose of a PSE.")

[Certificate Collections](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/75d0cfec8e4f44c3a649d26e9cefa314.html "A certificate collection is a secure location where the public-key certificates of trusted communication partners or root certificates from trusted Certification Authorities are stored. Certificate collections are created and managed as database objects directly in the SAP HANA database.") :arrow_upper_right:

[SQL Statements and Authorization for Certificate Management (Reference)](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/f32bcc9c4b734f24bedaf6253e7981d6.html "All administration tasks related to the management of public-key certificates (and public keys) can be performed using SQL.") :arrow_upper_right:

