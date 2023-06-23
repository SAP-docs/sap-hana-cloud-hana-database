<!-- loiobfe3daf744324bc390902251817a1fcc -->

# CREATE JWT PROVIDER Statement \(Access Control\)

Defines a JWT provider in the SAP HANA database.



<a name="loiobfe3daf744324bc390902251817a1fcc__section_rpm_5rd_rhb"/>

## Syntax

```
CREATE JWT PROVIDER <jwt_provider_name> 
   <issuer_clause> <claims_clause> 
   [ <case_clause> ]
   [ <priority_clause> ]
   [ <enable_user_creation_clause> ]
```



<a name="loiobfe3daf744324bc390902251817a1fcc__section_hqm_5rd_rhb"/>

## Syntax Elements


<dl>
<dt><b>

*<jwt\_provider\_name\>*

</b></dt>
<dd>

Specifies the identifier of a JWT provider to be created. The JWT provider name must not already be defined.

```
<jwt_provider_name> ::= <simple_identifier>
```



</dd><dt><b>

*<issuer\_clause\>*

</b></dt>
<dd>

Sets JWT provider information.

```
<issuer_clause> ::= WITH ISSUER <issuer_claim>
```

```
<issuer_claim> ::= <string_literal>
```

*<issuer\_claim\>* is the issuer name provided in the iss claim of the JWT issued by this JWT provider. The *<issuer\_claim\>* *<priority\_clause\>* combination must be unique across all JWT providers.



</dd><dt><b>

*<claims\_clause\>*

</b></dt>
<dd>

```
<claims_clause> ::= 
   <external_id_clause>
   [ <application_user_clause> ]
   [ <compare_claim_clause> ]
```


<dl>
<dt><b>

*<external\_id\_clause\>*

</b></dt>
<dd>

Specifies the claim provided in the JWT to use for mapping the HANA user to an external user name.

```
<external_id_clause> ::= CLAIM <string_literal> AS EXTERNAL IDENTITY
```



</dd><dt><b>

*<application\_user\_clause\>*

</b></dt>
<dd>

The value of this claim in the JWT is used to set the XS\_APPLICATIONUSER session variable during login.

```
<application_user_clause> ::= CLAIM <string_literal> AS APPLICATION USER

```



</dd><dt><b>

*<compare\_claim\_clause\>*

</b></dt>
<dd>

A claim can only be used for one compare operation, be it equal or has\_memeber.

```
<compare_claim_clause> ::= <compare_claim>[, <compare_claim>[,...] ]
```

```
<compare_claim> ::= { <claim_equals_clause> | <claim_has_member_clause> }
```


<dl>
<dt><b>

*<claim\_equals\_clause\>*

</b></dt>
<dd>

*<claim\_equals\_clause\>* expects the JWT claim value to be a string, number, Boolean, or array \(with a single string\) and the value must exactly match the configured value \(for example, 'origin' claim or 'zone\_uuid' claim\).

```
<claim_equals_clause> ::= CLAIM <string_literal> = <string_literal>

```



</dd><dt><b>

*<claim\_has\_member\_clause\>*

</b></dt>
<dd>

*<claim\_equals\_clause\>* expects the JWT claim to be an array of strings. If the JWT, which is used for authentication, contains a simple string instead of an array of strings, then the simple string is treated like an array with one entry. Thus, the effect would be like an equals comparison.

```
<claim_has_member_clause> ::= CLAIM <string_literal> HAS MEMBER <string_literal>
```



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<case\_clause\>*

</b></dt>
<dd>

Specifies whether the user mapping is checked case sensitive \(default\) or insensitive.

```
<case_clause> ::= CASE { SENSITIVE | INSENSITIVE } IDENTITY ]
```



</dd><dt><b>

*<priority\_clause\>*

</b></dt>
<dd>

Specifies the priority order in which the issuer is checked.

```
<priority_clause> ::= PRIORITY <number>
```

*<number\>* is a value between 1-255. The default is 100.

Providers with the same issuer must have different priorities. During authentication, the provider with the highest priority is checked first. If the claims match with the provided JWT, that provider is used for the authentication; otherwise, the provider with the next lower priority is tested until a match is found.



</dd><dt><b>

*<enable\_user\_creation\_clause\>*

</b></dt>
<dd>

Enables automatic user creation when using JWT authentication, and specifies type of the user to create - standard or restricted.

```
<enable_user_creation_clause> ::= 
   ENABLE USER CREATION [ USER TYPE { STANDARD | RESTRICTED } ] 
   USERGROUP <usergroup_name> 
   LDAP AUTHORIZATION
```

When enabling automatic user creation, optionally specify the type of the new users to be created. By default, new users are created as STANDARD users. The user is created in the specified user group. The RESTRICTED user created using this clause is not automatically granted the PUBLIC role.



</dd>
</dl>



<a name="loiobfe3daf744324bc390902251817a1fcc__section_iqm_5rd_rhb"/>

## Permissions

You must have the CREATE JWT PROVIDER system privilege to create a JWT provider.

To use the *<enable\_user\_creation\_clause\>* also requires the OPERATOR object privilege on the referenced USERGROUP.



<a name="loiobfe3daf744324bc390902251817a1fcc__section_jqm_5rd_rhb"/>

## Examples

Create a JWT provider with the name my\_jwt\_provider, using issuer name www/url/my\_url and claim user1. The identity checked by the provider is case sensitive.

```
CREATE JWT PROVIDER my_jwt_provider WITH ISSUER 'www/url/my_url' 
   CLAIM 'user1' AS EXTERNAL IDENTITY CASE SENSITIVE IDENTITY;
```

Create a JWT provider named prov\_a with an issuer named xsuaa and three compare claims: origin, aud, and sub.

```
CREATE JWT PROVIDER prov_a WITH ISSUER 'http://xsuaa' CLAIM 'origin' = 'http://customerA' CLAIM 'aud' HAS MEMBER 'app1' CLAIM 'sub' AS EXTERNAL IDENTITY;

```

Create a JWT provider named prov\_b with an issuer named xsuaa and two claims: sub and appuser.

```
CREATE JWT PROVIDER prov_b WITH ISSUER 'http://xsuaa' CLAIM 'sub' AS EXTERNAL IDENTITY CLAIM 'appuser' AS APPLICATION USER PRIORITY 110;

```

**Related Information**  


[ALTER JWT PROVIDER Statement \(Access Control\)](alter-jwt-provider-statement-access-control-61863f6.md "Alters a JWT provider in the SAP HANA database.")

[DROP JWT PROVIDER Statement \(Access Control\)](drop-jwt-provider-statement-access-control-e3caf68.md "Drops a JWT provider in the SAP HANA database.")

[JWT\_PROVIDERS System View](../../020-System-Views-Reference/021-System-Views/jwt-providers-system-view-3df748d.md "Lists all of the JWT providers configured in the SAP HANA database.")

[JWT\_USER\_MAPPINGS System View](../../020-System-Views-Reference/021-System-Views/jwt-user-mappings-system-view-49f380b.md "Lists all of the user-JWT mappings configured in the SAP HANA database.")

[Single Sign-On Using JSON Web Tokens](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/4b3dc4d4b5514dbd9d45cee7bc167c5a.html "SAP HANA supports JSON Web Tokens (JWT) for user authentication in single sign-on environments.") :arrow_upper_right:

