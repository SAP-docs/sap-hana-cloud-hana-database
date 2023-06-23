<!-- loioe3caf68bb0b84b4cbcc0e3a7c022e92a -->

# DROP JWT PROVIDER Statement \(Access Control\)

Drops a JWT provider in the SAP HANA database.



## Syntax

```
DROP JWT PROVIDER <jwt_provider_name> [ CASCADE ]
```



## Syntax Elements


<dl>
<dt><b>

*<jwt\_provider\_name\>*

</b></dt>
<dd>

Specifies which JWT provider to drop.

```
<jwt_provider_name> ::= <simple_identifier>
```

*<jwt\_provider\_name\>* must be an existing JWT provider.



</dd>
</dl>


<dl>
<dt><b>

CASCADE

</b></dt>
<dd>

Required only when the JWT provider is referenced by a PSE's purpose object. The provider is removed from any PSE referencing it along with any user mappings for users authenticating with the provider. For PSEs where it is the only provider assigned, the purpose of that PSE is also removed.



</dd>
</dl>



## Description

If the JWT provider is in use by an SAP HANA database user, then the JWT provider cannot be dropped when the CASCADE parameter is specified.



<a name="loioe3caf68bb0b84b4cbcc0e3a7c022e92a__section_irq_1mh_qbb"/>

## Permissions

You must have the DROP object privilege on the JWT provider or be the object owner.



## Examples

Drops the JWT provider, my\_jwt\_provider1.

```
DROP JWT PROVIDER my_jwt_provider1;
```

Drops the JWT provider, my\_jwt\_provider2, which is referenced by the PSE mypse1.

```
DROP JWT PROVIDER my_jwt_provider2 CASCADE;
```

**Related Information**  


[CREATE JWT PROVIDER Statement \(Access Control\)](create-jwt-provider-statement-access-control-bfe3daf.md "Defines a JWT provider in the SAP HANA database.")

[ALTER JWT PROVIDER Statement \(Access Control\)](alter-jwt-provider-statement-access-control-61863f6.md "Alters a JWT provider in the SAP HANA database.")

[JWT\_PROVIDERS System View](../../020-System-Views-Reference/021-System-Views/jwt-providers-system-view-3df748d.md "Lists all of the JWT providers configured in the SAP HANA database.")

[JWT\_USER\_MAPPINGS System View](../../020-System-Views-Reference/021-System-Views/jwt-user-mappings-system-view-49f380b.md "Lists all of the user-JWT mappings configured in the SAP HANA database.")

