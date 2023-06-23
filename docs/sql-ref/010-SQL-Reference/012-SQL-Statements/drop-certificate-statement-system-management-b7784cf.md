<!-- loiob7784cfa101942f4ae17a258d060998e -->

# DROP CERTIFICATE Statement \(System Management\)

Drops a specified certificate from the list of certificates.



## Syntax

```
DROP CERTIFICATE { <certificate_name> | <certificate_id> }
```



## Syntax Elements


<dl>
<dt><b>

*<certificate\_name\>*

</b></dt>
<dd>

Specifies the name of the certificate to be dropped.

```
<certificate_name> ::= <identifier>
```



</dd><dt><b>

*<certificate\_id\>*

</b></dt>
<dd>

Specifies the id of the certificate to be dropped.

```
<certificate_id> ::= <unsigned_integer>
```



</dd>
</dl>



## Description

The DROP CERTIFICATE statement drops this certificate from the list of certificates, which can be assigned to a PSE store. The statement succeeds only if the certificate is not assigned to a PSE store.

Information about certificates that are usable for assignment to PSE stores is stored in the CERTIFICATES system view.



<a name="loiob7784cfa101942f4ae17a258d060998e__section_ofg_qwx_vcb"/>

## Permissions

Only users with the CERTIFICATE ADMIN system privilege are allowed to drop certificates.



## Examples

Assuming the certificate name is SAP\_CERT, drop it.

```
DROP CERTIFICATE SAP_CERT;
```

**Related Information**  


[CERTIFICATES System View](../../020-System-Views-Reference/021-System-Views/certificates-system-view-d076e2b.md "Provides information about certificates useable in PSEs.")

