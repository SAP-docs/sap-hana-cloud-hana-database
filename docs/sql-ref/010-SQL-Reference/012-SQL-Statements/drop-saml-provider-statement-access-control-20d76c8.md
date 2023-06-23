<!-- loio20d76c8675191014b9acc9697a367773 -->

# DROP SAML PROVIDER Statement \(Access Control\)

Drops the specified SAML provider.



<a name="loio20d76c8675191014b9acc9697a367773__sql_drop_saml_provider_1sql_drop_saml_provider_syntax"/>

## Syntax

```
DROP SAML PROVIDER <saml_provider_name> CASCADE
```



<a name="loio20d76c8675191014b9acc9697a367773__sql_drop_saml_provider_1sql_drop_saml_provider_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<saml\_provider\_name\>*

</b></dt>
<dd>

Specifies the name of the SAML provider to drop.

```
<saml_provider_name> ::= <simple_identifier>
```

*<saml\_provider\_name\>* must be an existing SAML provider.



</dd>
</dl>


<dl>
<dt><b>

CASCADE

</b></dt>
<dd>

Required only when the SAML purpose is referenced by a PSE's purpose object. The provider is removed from any PSE referencing it along with any user mappings for users authenticating with the provider. For PSEs where it is the only provider assigned, the purpose of that PSE is also removed.



</dd>
</dl>



<a name="loio20d76c8675191014b9acc9697a367773__sql_drop_saml_provider_1sql_drop_saml_provider_description"/>

## Description

If the SAML provider is currently used by an SAP HANA database user, then the SAML provider cannot be dropped when the CASCADE parameter is specified.



<a name="loio20d76c8675191014b9acc9697a367773__section_rwy_vwx_vcb"/>

## Permissions

To execute this statement you must have the DROP object privilege on the specific SAML provider or be the object owner.



<a name="loio20d76c8675191014b9acc9697a367773__sql_drop_saml_provider_1sql_drop_saml_provider_examples"/>

## Example

Drop the SAML provider named ac\_saml\_provider1.

```
DROP SAML PROVIDER ac_saml_provider1;
```

Drops the SAML provider, ac\_saml\_provider2, which is referenced by the PSE mypse1.

```
DROP SAML PROVIDER ac_saml_provider2 CASCADE;
```

**Related Information**  


[PSE\_PURPOSE\_OBJECTS System View](../../020-System-Views-Reference/021-System-Views/pse-purpose-objects-system-view-437cd32.md "Provides information about all PSEs and their assigned providers or hosts, referred to as purpose objects.")

[SAML\_PROVIDERS System View](../../020-System-Views-Reference/021-System-Views/saml-providers-system-view-20cda7b.md "Shows available SAML providers.")

