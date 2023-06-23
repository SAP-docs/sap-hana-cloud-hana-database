<!-- loio4d80bf63fc374a7f99be94d8ce70a07a -->

# CREATE PSE Statement \(System Management\)

Creates a personal security environment \(PSE\).



## Syntax

```
CREATE PSE <pse_name>
```



## Syntax Elements


<dl>
<dt><b>

*<pse\_name\>*

</b></dt>
<dd>

Specifies a unique name for the PSE.

```
<pse_name> ::= <identifier>
```



</dd>
</dl>



## Description

Creates a PSE as a database object. PSEs are used for trust validation in SAP HANA.

PSEs are referred to as certificate collections in front-end terminology.



<a name="loio4d80bf63fc374a7f99be94d8ce70a07a__section_bgz_yvx_vcb"/>

## Permissions

You must have the TRUST ADMIN system privilege to create a PSE.



## Examples

Create a PSE with the name ***examplepse***.

```
CREATE PSE examplepse;
```

**Related Information**  


[ALTER PSE Statement \(System Management\)](alter-pse-statement-system-management-9c22c6f.md "Modifies a PSE.")

[SET PSE Statement \(System Management\)](set-pse-statement-system-management-10fe807.md "Sets the purpose of a PSE.")

[UNSET PSE Statement \(System Management\)](unset-pse-statement-system-management-4082553.md "Removes the purpose for a PSE.")

[Certificate Collections](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/75d0cfec8e4f44c3a649d26e9cefa314.html "A certificate collection is a secure location where the public-key certificates of trusted communication partners or root certificates from trusted Certification Authorities are stored. Certificate collections are created and managed as database objects directly in the SAP HANA database.") :arrow_upper_right:

