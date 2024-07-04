<!-- loio4d80bf63fc374a7f99be94d8ce70a07a -->

# CREATE PSE Statement \(System Management\)

Creates a personal security environment \(PSE\).



## Syntax

```
CREATE PSE <pse_name> [ MANAGED BY JWKS URL <url_string_literal> ]
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


<dl>
<dt><b>

<url\_string\_literal\>

</b></dt>
<dd>

Specifies the URL to the content of the Managed PSE. For a Managed PSE, you also need an additional PSE with purpose HTTPS to establish the trust for the secure connection to the URL.



</dd>
</dl>



## Description

Creates a PSE as a database object. PSEs are used for trust validation in SAP HANA. They are referred to as certificate collections in front-end terminology.

The content of a managed PSE is automatically refreshed every 24 hours or during a system restart.

If you create a Managed PSE, you need an additional PSE with purpose HTTPS to establish the trust for the secure connection to the URL.



<a name="loio4d80bf63fc374a7f99be94d8ce70a07a__section_bgz_yvx_vcb"/>

## Permissions

To create a PSE requires the TRUST ADMIN system privileges. To create a Managed PSE, you also require the CERTIFICATE ADMIN system privilege.



## Examples

Create a PSE with the name example\_pse.

```
CREATE PSE example_pse;
```

Creates a managed PSE.

```
CREATE PSE example2_pse MANAGED BY JWKS URL 'https://XXXXX.sap.com/.well-known/xxxxx/jwks';
```

**Related Information**  


[ALTER PSE Statement \(System Management\)](alter-pse-statement-system-management-9c22c6f.md "Modifies a PSE.")

[SET PSE Statement \(System Management\)](set-pse-statement-system-management-10fe807.md "Sets the purpose of a PSE, which is the type of trust validation for the PSE to use.")

[UNSET PSE Statement \(System Management\)](unset-pse-statement-system-management-4082553.md "Remove the assigned purpose for a PSE along with any assigned objects.")

[Certificate Collections](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/75d0cfec8e4f44c3a649d26e9cefa314.html "A certificate collection is a secure location where the public-key certificates of trusted communication partners or root certificates from trusted Certification Authorities are stored. Certificate collections are created and managed as database objects directly in the SAP HANA database.") :arrow_upper_right:

[REFRESH PSE Statement \(System Management\)](refresh-pse-statement-system-management-c2f1007.md "Refreshes a managed PSE.")

[M\_MANAGED\_PSES System View](../../020-System-Views-Reference/022-Monitoring-Views/m-managed-pses-system-view-5c745ca.md "Provides information about managed personal security environments (managed PSEs).")

