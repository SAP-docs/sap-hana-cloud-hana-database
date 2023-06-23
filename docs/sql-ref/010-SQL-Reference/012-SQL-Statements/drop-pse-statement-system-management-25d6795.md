<!-- loio25d67950e6614770aa98aec23ab117ee -->

# DROP PSE Statement \(System Management\)

Drops a PSE.



## Syntax

```
DROP PSE <pse_name>
```



## Syntax Elements


<dl>
<dt><b>

*<pse\_name\>*

</b></dt>
<dd>

Specifies the name of the PSE to drop.

```
<pse_name> ::= <identifier>
```



</dd>
</dl>



## Description

Dropping of a PSE fails if the PSE is assigned a purpose. Certificates assigned to a PSE remain in the certificate store after the PSE is dropped.

When the owner of a PSE is dropped, the PSE is dropped as well, even if it is assigned a purpose. The deletion of a PSE that is assigned a purpose could render the database unusable. For example, if SAML is being used for user authentication and the PSE used for SAML is deleted, users can no longer log on.



<a name="loio25d67950e6614770aa98aec23ab117ee__section_kt1_zlm_wcb"/>

## Permissions

You must have the DROP object privilege on the PSE.



## Examples

Drop the PSE ***examplepse***.

```
DROP PSE examplepse;
```

**Related Information**  


[CREATE PSE Statement \(System Management\)](create-pse-statement-system-management-4d80bf6.md "Creates a personal security environment (PSE).")

[Certificate Collections](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/75d0cfec8e4f44c3a649d26e9cefa314.html "A certificate collection is a secure location where the public-key certificates of trusted communication partners or root certificates from trusted Certification Authorities are stored. Certificate collections are created and managed as database objects directly in the SAP HANA database.") :arrow_upper_right:

