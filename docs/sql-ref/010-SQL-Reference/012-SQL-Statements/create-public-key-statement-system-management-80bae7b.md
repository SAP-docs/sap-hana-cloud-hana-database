<!-- loio80bae7bd45b14516b334d649fdac6de2 -->

# CREATE PUBLIC KEY Statement \(System Management\)

Creates a public key for JWT validation.



<a name="loio80bae7bd45b14516b334d649fdac6de2__section_bq5_zk5_4pb"/>

## Syntax

```
CREATE PUBLIC KEY [ <public_key_name> ] FROM <pem> [ KEY ID HINT '<hint>'] [ COMMENT '<comment>' ]
```



<a name="loio80bae7bd45b14516b334d649fdac6de2__section_cq5_zk5_4pb"/>

## Syntax Elements


<dl>
<dt><b>

*<public\_key\_name\>*

</b></dt>
<dd>

Specifies a unique name, which can be used to add the key to a PSE. If not specified, the name is auto-generated using the schema: "\_SYS\_PUBLIC\_KEY\_" + *<id\>*



</dd><dt><b>

*<pem\>*

</b></dt>
<dd>

Specifies the key format.

```
<pem> ::= { <PKCS1> | <PKCS8> }

<PKCS1> ::= ('-----BEGIN RSA PUBLIC KEY-----...-----END RSA PUBLIC KEY-----')
<PKCS8> ::= ('-----BEGIN PUBLIC KEY-----...-----END PUBLIC KEY-----')
```

For the PKCS8 format, only RSA keys are supported. EC keys are not supported.



</dd><dt><b>

*<hint\>*

</b></dt>
<dd>

Used during the user authentication \(JWT validation\) to identify the key, if the JWT token contained a "kid" claim in its header.



</dd>
</dl>



<a name="loio80bae7bd45b14516b334d649fdac6de2__section_dq5_zk5_4pb"/>

## Description

Creates a public key for JWT validation.

The database does not check for duplicate public keys. To check if a public key already exists in the database, see the PUBLIC\_KEYS system view.



<a name="loio80bae7bd45b14516b334d649fdac6de2__section_bgz_yvx_vcb"/>

## Permissions

You must have the CERTIFICATE ADMIN system privilege to execute this statement.



<a name="loio80bae7bd45b14516b334d649fdac6de2__section_eq5_zk5_4pb"/>

## Examples

Create a public key with the name jwt\_pubkey.

```
CREATE PUBLIC KEY jwt_pubkey FROM '-----BEGIN PUBLIC KEY-----...-----END PUBLIC KEY-----' KEY ID HINT 'key1';
```

**Related Information**  


[PUBLIC\_KEYS System View](../../020-System-Views-Reference/021-System-Views/public-keys-system-view-4924523.md "Provides information about all public keys.")

[Certificate Management](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/1e6042c4402545f7a0574f7bc91fab25.html "SAP HANA uses public-key certificates as the basis for several user authentication mechanisms, and for securing internal and external communication channels. Certificates are stored and managed directly in the SAP HANA database.") :arrow_upper_right:

