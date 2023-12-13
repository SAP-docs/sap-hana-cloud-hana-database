<!-- loiof7a37e81a9b64a2cb6a6092a38b06c60 -->

# DROP X509 PROVIDER Statement \(Access Control\)

Drops an X.509 provider in the SAP HANA database.



<a name="loiof7a37e81a9b64a2cb6a6092a38b06c60__section_e3b_fdj_5nb"/>

## Syntax

```
DROP X509 PROVIDER <x509_provider_name> [ CASCADE ]
```



<a name="loiof7a37e81a9b64a2cb6a6092a38b06c60__section_e5y_fdj_5nb"/>

## Syntax Elements


<dl>
<dt><b>

*<x509\_provider\_name\>*

</b></dt>
<dd>

Specifies which X.509 provider to drop.

```
<x509_provider_name> ::= <simple_identifier>
```

*<x509\_provider\_name\>* must be an existing X.509 provider.



</dd>
</dl>


<dl>
<dt><b>

CASCADE

</b></dt>
<dd>

Required only when the X.509 provider is referenced by a PSE's purpose object. The provider is removed from any PSE referencing it along with any user mappings for users authenticating with the provider. For PSEs where it is the only provider assigned, the purpose of that PSE is also removed.



</dd>
</dl>



<a name="loiof7a37e81a9b64a2cb6a6092a38b06c60__section_irq_1mh_qbb"/>

## Permissions

To execute this statement you must have the DROP object privilege on the specific X509 provider or be the object owner.



<a name="loiof7a37e81a9b64a2cb6a6092a38b06c60__section_djc_x2j_5nb"/>

## Examples

Drops the X.509 provider, my\_x509\_provider1.

```
DROP X509 PROVIDER my_x509_provider1;
```

**Related Information**  


[X.509 Certificate-Based User Authentication](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2023_4_QRC/en-US/2b335f7eec6a450095f110ea961d77cc.html "SAP HANA supports X.509 client certificates for user authentication in single sign-on environments. In particular, X.509 certificate-based authentication can be used for technical users to secure system-to-system integration.") :arrow_upper_right:

[CREATE X509 PROVIDER Statement \(Access Control\)](create-x509-provider-statement-access-control-3b3163d.md "Defines an X.509 provider in the SAP HANA database.")

[ALTER X509 PROVIDER Statement \(Access Control\)](alter-x509-provider-statement-access-control-4f7e59d.md "Alters an X.509 provider in the SAP HANA database.")

[X509\_PROVIDERS System View](../../020-System-Views-Reference/021-System-Views/x509-providers-system-view-07a3627.md "Lists all of the X.509 providers configured in the SAP HANA database.")

[X509\_PROVIDER\_RULES System View](../../020-System-Views-Reference/021-System-Views/x509-provider-rules-system-view-2457e71.md "Lists all of the matching rules for X.509 providers.")

[X509\_USER\_MAPPINGS System View](../../020-System-Views-Reference/021-System-Views/x509-user-mappings-system-view-210347f.md "Shows the X.509 certificates that are known for each user.")

