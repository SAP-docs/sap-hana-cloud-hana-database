<!-- loio340e913ae1d044d993dec2a7eff941c4 -->

# DROP LDAP PROVIDER Statement \(Access Control\)

Drops an LDAP provider, and its associated credential, from the internal secure credential store.



## Syntax

```
DROP LDAP PROVIDER <ldap_provider_name>
```



## Syntax Elements


<dl>
<dt><b>

*<ldap\_provider\_name\>*

</b></dt>
<dd>

The identifier for a valid LDAP provider previously created using the CREATE LDAP PROVIDER statement.

```
<ldap_provider_name> ::= <unicode_name>
```



</dd>
</dl>



## Description

Drops an LDAP provider.

If the dropped LDAP provider is the default LDAP provider, subsequent connections for users configured for LDAP authorization are impacted as follows:

-   Any user connections created before the expiration of the value for the ldap\_authorization\_role\_reuse\_duration database property will succeed.

-   Any user connections created after the expiration of the value for the ldap\_authorization\_role\_reuse\_duration database property will fail.

-   Any first time user connections will fail.


With regards to LDAP authentication, if the default LDAP provider is dropped, subsequent user connections fail.



<a name="loio340e913ae1d044d993dec2a7eff941c4__section_cgk_hnh_qbb"/>

## Permissions

You must have the LDAP ADMIN system privilege to drop an LDAP provider.



## Examples

The following example drops an LDAP provider called ***my\_ldap\_provider***.

```
DROP LDAP PROVIDER my_ldap_provider;
```

**Related Information**  


[CREATE LDAP PROVIDER Statement \(Access Control\)](create-ldap-provider-statement-access-control-3b72203.md "Creates an LDAP provider for use with LDAP authorization and authentication.")

[ALTER LDAP PROVIDER Statement \(Access Control\)](alter-ldap-provider-statement-access-control-ae9ba28.md "Updates an LDAP provider for use with LDAP authorization and authentication.")

[VALIDATE LDAP PROVIDER Statement \(Access Control\)](validate-ldap-provider-statement-access-control-4181217.md "Validates an LDAP provider configuration and LDAP authentication and authorization for users of that LDAP provider.")

[LDAP\_PROVIDER\_URLS System View](../../020-System-Views-Reference/021-System-Views/ldap-provider-urls-system-view-7cf2869.md "Lists all LDAP provider URLs.")

[LDAP\_PROVIDERS System View](../../020-System-Views-Reference/021-System-Views/ldap-providers-system-view-5b54fe2.md "Lists all LDAP providers.")

[LDAP\_USERS System View](../../020-System-Views-Reference/021-System-Views/ldap-users-system-view-704e5b6.md "Shows information about the users using LDAP authorization.")

