<!-- loioba87935fc4a84f4eb805d5eba9a7b480 -->

# CREATE CERTIFICATE Statement \(System Management\)

Adds the specified certificate to the list of certificates.



## Syntax

```
CREATE CERTIFICATE [ <certificate_name> ] FROM <certificate> [ COMMENT <comment> ]
```



## Syntax Elements


<dl>
<dt><b>

*<certificate\_name\>*

</b></dt>
<dd>

If a *<certificate\_name\>* is not specified, a name is automatically generated from its ID in the format \_SYS\_CERTIFICATE\_*<id\>*. If migrating from an earlier release of SAP HANA database, a certificate name for existing certificates is automatically generated using the same format. The CERTIFICATE\_NAME column has been added to the CERTIFICATES and PSE\_CERTIFICATES system views.

```
<certificate_name> ::= <identifier>
```



</dd><dt><b>

*<certificate\>*

</b></dt>
<dd>

Specifies the certificate in PEM-representation, which should be stored in the database.

```
<certificate> ::= <string literal>
```



</dd><dt><b>

*<comment\>*

</b></dt>
<dd>

Adds a description for the certificate.

```
<comment> ::= <string_literal>
```

Use this value to help you find a specific certificate in the list of certificates.



</dd>
</dl>



## Description

The CREATE CERTIFICATE statement adds this certificate to the list of certificates, which can be assigned to a PSE store.

Information about certificates that are usable for assignment to PSE stores is stored in the CERTIFICATES system view.

Duplicate certificates are allowed as long as a certificate name is specified and unique.



<a name="loioba87935fc4a84f4eb805d5eba9a7b480__section_zt3_ytx_vcb"/>

## Permissions

Only users with the system privilege CERTIFICATE ADMIN can create certificates.



## Examples

Create a certificate with subject and issuer SAP AG and a validity between 2011 and 2285. The certificate is shortened and the missing 21 lines mentioned as '...'.

```
 CREATE CERTIFICATE FROM '-----BEGIN CERTIFICATE-----
MIIEVjCCAz6gAwIBAgIJAKZmSWxYxVmGMA0GCSqGSIb3DQEBBQUAMHkxCzAJBgNV
...
zn2Q+T5Og6ozD1WgUYsegJl3W2gNznEj66Ku1SDDzR0POjCnfK5xLt1WE5KBAIav
1SSbSTsw6rCRdg==
-----END CERTIFICATE-----' COMMENT 'Subject SAP AG Valid until 2285'
```

Create a certificate named SAP\_CERT. The certificate is shortened and the missing 21 lines mentioned as '...'.

```
 CREATE CERTIFICATE SAP_CERT FROM '-----BEGIN CERTIFICATE-----
MIIEVjCCAz6gAwIBAgIJAKZmSWxYxVmGMA0GCSqGSIb3DQEBBQUAMHkxCzAJBgNV
...
zn2Q+T5Og6ozD1WgUYsegJl3W2gNznEj66Ku1SDDzR0POjCnfK5xLt1WE5KBAIav
1SSbSTsw6rCRdg==
-----END CERTIFICATE-----'
```

**Related Information**  


[CERTIFICATES System View](../../020-System-Views-Reference/021-System-Views/certificates-system-view-d076e2b.md "Provides information about certificates useable in PSEs.")

[CREATE PUBLIC KEY Statement \(System Management\)](create-public-key-statement-system-management-80bae7b.md "Creates a public key for JWT validation.")

[Certificate Management](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/1e6042c4402545f7a0574f7bc91fab25.html "SAP HANA uses public-key certificates as the basis for several user authentication mechanisms, and for securing internal and external communication channels. Certificates are stored and managed directly in the SAP HANA database.") :arrow_upper_right:

