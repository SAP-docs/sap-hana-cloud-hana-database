<!-- loio61863f687c3d40c5a7c76a4ab110ede5 -->

# ALTER JWT PROVIDER Statement \(Access Control\)

Alters a JWT provider in the SAP HANA database.



<a name="loio61863f687c3d40c5a7c76a4ab110ede5__section_g2s_yrd_rhb"/>

## Syntax

```
ALTER JWT PROVIDER <jwt_provider_name> 
 { SET { <issuer_clause>
         | <claims_clause>
         | <priority_clause>
       }
   | <case_clause> 
   | UNSET <unset_claims_clause>
   | <enable_disable_user_creation_clause>
 }
```



<a name="loio61863f687c3d40c5a7c76a4ab110ede5__section_h2s_yrd_rhb"/>

## Syntax Elements


<dl>
<dt><b>

*<jwt\_provider\_name\>*

</b></dt>
<dd>

Specifies the identifier of a JWT provider to be modified.

```
<jwt_provider_name> ::= <simple_identifier>
```



</dd><dt><b>

*<issuer\_clause\>*

</b></dt>
<dd>

Alters the issuer set for the provider.

```
<issuer_clause> ::= WITH ISSUER <issuer_claim>

<issuer_claim> ::= <string_literal>
```

The *<issuer\_claim\>* *<priority\_clause\>* combination must be unique across all JWT providers.



</dd><dt><b>

*<claims\_clause\>*

</b></dt>
<dd>

```
<claims_clause> ::= 
   { [ <external_id_clause> ]
   [ <application_user_clause> ]
   [ <compare_claim_clause> ] }
```


<dl>
<dt><b>

*<external\_id\_clause\>*

</b></dt>
<dd>

Alters the claim set in the JWTs to use for mapping the SAP HANA user to an external user name. Once set, the *<external\_id\_clause\>* cannot be unset.

```
<external_id_clause> ::= CLAIM <string_literal> AS EXTERNAL IDENTITY
```



</dd><dt><b>

*<application\_user\_clause\>*

</b></dt>
<dd>

The value is used to set the XS\_APPLICATIONUSER session variable during login.

```
<application_user_clause> ::= CLAIM <string_literal> AS APPLICATION USER

```



</dd><dt><b>

*<compare\_claim\_clause\>*

</b></dt>
<dd>

A claim can only be used for one compare operation, be it = or HAS MEMBER.

```
<compare_claim_clause> ::= { <claim_equals_clause>[, ...] | <claim_has_member_clause>[, ...] }
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

*<priority\_clause\>*

</b></dt>
<dd>

Alters the priority order set in which the issuer is checked.

```
<priority_clause> ::= PRIORITY <number>
```

*<number\>* is a value between 1-255.

Providers with the same issuer must have different priorities. During authentication, the provider with the highest priority is checked first. If the claims match with the provided JWT, that provider is used for the authentication; otherwise, the provider with the next lower priority is tested until a match is found.



</dd><dt><b>

*<case\_clause\>*

</b></dt>
<dd>

Alters whether the user mapping is checked case sensitive \(default\) or insensitive.

```
<case_clause> ::= CASE { SENSITIVE | INSENSITIVE } IDENTITY 
```



</dd><dt><b>

*<unset\_claims\_clause\>*

</b></dt>
<dd>

Removes the claims set.

```
<unset_claims_clause> ::= <unset_claim> [ <unset_claim>[…] ]
```

```
<unset_claim> ::= CLAIM <string_literal> 
```



</dd><dt><b>

*<enable\_disable\_user\_creation\_clause\>*

</b></dt>
<dd>

Enables or disables automatic user creation for JWT authentication.

```
<enable_disable_user_creation_clause> ::=
   { ENABLE USER CREATION [ USER TYPE { STANDARD | RESTRICTED } ] USERGROUP <usergroup_name> LDAP AUTHORIZATION
   | DISABLE USER CREATION } 
```

When enabling automatic user creation, optionally specify the type of the new users to be created. By default, new users are created as STANDARD users. The user is created in the specified user group. The RESTRICTED user created using this clause is not automatically granted the PUBLIC role.



</dd>
</dl>



<a name="loio61863f687c3d40c5a7c76a4ab110ede5__section_i2s_yrd_rhb"/>

## Description

For the SET clause, at least one of the two optional parameters must be specified.



<a name="loio61863f687c3d40c5a7c76a4ab110ede5__section_s21_1cg_qbb"/>

## Permissions

You must have the ALTER object privilege on the JWT provider or be the object owner.

To use the *<enable\_disable\_user\_creation\_clause\>* also requires the OPERATOR object privilege on the referenced USERGROUP.



<a name="loio61863f687c3d40c5a7c76a4ab110ede5__section_j2s_yrd_rhb"/>

## Examples

Change the issuer of the my\_jwt\_provider JWT provider to www/url/my\_new\_url.

```
ALTER JWT PROVIDER my_jwt_provider SET ISSUER 'www/url/my_new_url';
```

Change the external identify of the my\_jwt\_provider JWT provider to user2.

```
ALTER JWT PROVIDER my_jwt_provider SET CLAIM 'user2' AS EXTERNAL IDENTITY;
```

Change the my\_jwt\_provider JWT provider to be case insensitive.

```
ALTER JWT PROVIDER my_jwt_provider CASE INSENSITIVE IDENTITY;
```

**Related Information**  


[CREATE JWT PROVIDER Statement \(Access Control\)](create-jwt-provider-statement-access-control-bfe3daf.md "Defines a JWT provider in the SAP HANA database.")

[DROP JWT PROVIDER Statement \(Access Control\)](drop-jwt-provider-statement-access-control-e3caf68.md "Drops a JWT provider in the SAP HANA database.")

[JWT\_PROVIDERS System View](../../020-System-Views-Reference/021-System-Views/jwt-providers-system-view-3df748d.md "Lists all of the JWT providers configured in the SAP HANA database.")

[JWT\_USER\_MAPPINGS System View](../../020-System-Views-Reference/021-System-Views/jwt-user-mappings-system-view-49f380b.md "Lists all of the user-JWT mappings configured in the SAP HANA database.")

