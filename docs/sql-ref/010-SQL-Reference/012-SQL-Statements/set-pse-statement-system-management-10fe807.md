<!-- loio10fe8070539649358c79955110311082 -->

# SET PSE Statement \(System Management\)

Sets the purpose of a PSE, which is the type of trust validation for the PSE to use.



## Syntax

```
SET PSE <pse_name> PURPOSE <purpose_list>
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

*<purpose\_list\>*

</b></dt>
<dd>

Specifies the purpose of the PSE.

```
<purpose_list> ::= 
   { LDAP
   | <purpose_JWT>
   | <purpose_SAML>
   | <purpose_X509>
   | <purpose_REMOTE_SOURCE>
   | <purpose_HTTPS> }
```


<dl>
<dt><b>

*<purpose\_JWT\>*

</b></dt>
<dd>

```
<purpose_JWT> ::= JWT FOR PROVIDER <provider_list>
```



</dd><dt><b>

*<purpose\_SAML\>*

</b></dt>
<dd>

```
<purpose_SAML> ::= SAML FOR PROVIDER <provider_list>
```



</dd><dt><b>

*<purpose\_X509\>*

</b></dt>
<dd>

```
<purpose_X509> ::= x509 FOR PROVIDER <provider_list>
```



</dd><dt><b>

*<purpose\_REMOTE\_SOURCE\>*

</b></dt>
<dd>

```
<purpose_REMOTE_SOURCE> ::= REMOTE SOURCE [FOR REMOTE SOURECE <remote_source_list> FOR PROVIDER <provider_list> ]
```



</dd><dt><b>

*<purpose\_HTTPS\>*

</b></dt>
<dd>

```
<purpose_HTTPS> ::= HTTPS FOR MANAGED PSE <managed_pse_list>
```



</dd>
</dl>



</dd><dt><b>

*<provider\_list\>*

</b></dt>
<dd>

A list of provider names. Providers of different types cannot be mixed in a single purpose.

```
<provider_list> ::= <provider>[, <provider>[,...] ]

<provider> ::= <simple_identifier>

```



</dd><dt><b>

*<remote\_source\_list\>*

</b></dt>
<dd>

A list of remote sourece names.

```
<remote_source_list> ::= <remote_source>[, <remote_source>[,...] ]

<remote_source> ::= <simple_identifier>
```



</dd><dt><b>

*<managed\_pse\_list\>*

</b></dt>
<dd>

A list of Managed PSE names.

```
<managed_pse_list> ::= <managed_pse>[, <managed_pse>[,...] ]

<managed_pse> ::= <simple_identifier>
```



</dd>
</dl>



## Description

For information about qualifying PSEs, see *Certificate Collections* in the *SAP HANA Cloud, SAP HANA Database Security Guide*.

Using SET PSE to set the purpose of a PSE removes any previous purpose assignments from the PSE. Use the ALTER PSE statement to add or remove purpose elements to a PSE. To change the purpose of an existing PSE, first execute the UNSET PSE statement to remove the existing purpose and any assigned objects from the PSE. Then use the SET PSE statement to assign a new purpose.

A PSE can only have one main purpose such as JWT or SAML assigned. Mixing different purposes is not allowed.

An object, such as a provider, remote source, etc., can only be assigned to one PSE. Assigning an object to a PSE removes a previous PSE assignment for that object.

If a PSE does not have any purpose objects assigned, the assignment of a purpose object must be done using the SET PSE statement.

Reassigning an object to another PSE may result in the original PSE losing its purpose assignment if the object was the only one assigned to the original PSE.

The purpose REMOTE SOURCE without any qualifying objects is used for all remote sources that do not have a specific PSE assigned.



<a name="loio10fe8070539649358c79955110311082__section_jtv_tj3_5rb"/>

## Permissions

Requires one of the following:

-   You own the object.
-   You have the REFERENCES object privilege on the PSE.

In addition, depending on the type of purpose, you also require one of the following:


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
<tr>
<td valign="top">

HTTPS

</td>
<td valign="top">

ALTER object privilege on the Managed PSE

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

This example sets the purpose for PSE pse1 to HTTPS.

```
SET PSE pse1 PURPOSE HTTPS FOR MANAGED PSE my_managed_pse;
```

**Related Information**  


[ALTER PSE Statement \(System Management\)](alter-pse-statement-system-management-9c22c6f.md "Modifies a PSE.")

[PSE\_PURPOSE\_OBJECTS System View](../../020-System-Views-Reference/021-System-Views/pse-purpose-objects-system-view-437cd32.md "Provides information about all PSEs and their assigned providers or hosts, referred to as purpose objects.")

[UNSET PSE Statement \(System Management\)](unset-pse-statement-system-management-4082553.md "Remove the assigned purpose for a PSE along with any assigned objects.")

[CREATE JWT PROVIDER Statement \(Access Control\)](create-jwt-provider-statement-access-control-bfe3daf.md "Defines a JWT provider in the SAP HANA database.")

[CREATE SAML PROVIDER Statement \(Access Control\)](create-saml-provider-statement-access-control-20d4cca.md "Defines a SAML provider in the SAP HANA database.")

[CREATE X509 PROVIDER Statement \(Access Control\)](create-x509-provider-statement-access-control-3b3163d.md "Defines an X.509 provider in the SAP HANA database.")

[CREATE REMOTE SOURCE Statement \(Access Control\)](create-remote-source-statement-access-control-20d4834.md "Defines an external data source that can connect to the SAP HANA database.")

[Certificate Collections](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/75d0cfec8e4f44c3a649d26e9cefa314.html "A certificate collection is a secure location where the public-key certificates of trusted communication partners or root certificates from trusted Certification Authorities are stored. Certificate collections are created and managed as database objects directly in the SAP HANA database.") :arrow_upper_right:

[SQL Statements and Authorization for Certificate Management (Reference)](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/f32bcc9c4b734f24bedaf6253e7981d6.html "All administration tasks related to the management of public-key certificates (and public keys) can be performed using SQL.") :arrow_upper_right:

