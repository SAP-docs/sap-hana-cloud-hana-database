<!-- loio20d3459f75191014a7bbeb670bad8850 -->

# ALTER USER Statement \(Access Control\)

Modifies the database user.



<a name="loio20d3459f75191014a7bbeb670bad8850__sql_alter_user_1sql_alter_user_syntax"/>

## Syntax

```
ALTER USER <user_name> { 
   <remote_identity_option> 
   | <password_validation_option> [ <validity_specification> ] [ <user_parameter_option> ] 
   | <usergroup_membership_option>   
   | <validity_specification> [ <user_parameter_option> ]
   | <user_parameter_option>  
   | <external_ident> [ <validity_specification> ] [ <user_parameter_option> ] 
   | <reset_connect_attempts> 
   | <drop_connect_attempts>  
   | <password_lifetime>   
   | <force_pass_change> 
   | <user_activation_opts> 
   | <authent_mech_opts>   
   | <add_ident_opts> 
   | <drop_ident_opts> 
   | <add_remote_database_identity>  
   | <drop_remote_database_identity> 
   | <client_connect_option>
   | <special_privilege_handling>
   | <ldap_group_authorization>
  }
```



<a name="loio20d3459f75191014a7bbeb670bad8850__sql_alter_user_1sql_alter_user_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<user\_name\>*

</b></dt>
<dd>

Specifies the username of the user to be modified.

```
<user_name> ::= <unicode_name>
```



</dd><dt><b>

*<remote\_identity\_option\>*

</b></dt>
<dd>

Defines a remote database identification mechanism.

```
ADD REMOTE IDENTITY <remote_user_name> AT DATABASE <database_name>
```


<dl>
<dt><b>

*<remote\_user\_name\>*

</b></dt>
<dd>

Specifies the remote user name.

```
<remote_user_name> ::= <unicode_name>
```



</dd><dt><b>

*<database\_name\>*

</b></dt>
<dd>

Specifies the remote database name.

```
<database_name> ::= <identifier>
```



</dd>
</dl>



</dd><dt><b>

*<password\_validation\_option\>*

</b></dt>
<dd>

Specifies the user password.

```
<password_validation_option> ::= PASSWORD <password> [ NO FORCE_FIRST_PASSWORD_CHANGE ]
```

The password must follow the rules defined for the current SAP HANA instance. The password rules include a minimal password length and a definition of which character types \(lower, upper, digit, special characters\) must be part of the password.

NO FORCE\_FIRST\_PASSWORD\_CHANGE overrules the setting of the password policy parameter FORCE\_FIRST\_PASSWORD\_CHANGE and allows the final password to be specified during user creation.



</dd><dt><b>

*<validity\_specification\>*

</b></dt>
<dd>

Specifies the validity specification with an optional user parameter option.

```
<validity_specification> ::= VALID <validity_opts>
```


<dl>
<dt><b>

*<validity\_opts\>*

</b></dt>
<dd>

Configures the user's temporal validity. The specified user is only allowed to connect within the given date range. Using this feature you can create users in advance or restrict the period when users can connect to the SAP HANA database.

```
<validity_opts> ::= 
 <from_specification> [ <until_specification> ] 
 | <until_specification>
```



</dd><dt><b>

*<from\_specification\>*

</b></dt>
<dd>

Sets when the user is valid from.

```
<from_specification> ::= FROM { <timestamp> | NOW }
```

Use the NOW keyword to configure the user account to be valid from the current time.

The default is NOW.



</dd><dt><b>

*<until\_specification\>*

</b></dt>
<dd>

Specifies when the user is valid until.

```
<until_specification> ::= UNTIL { <timestamp> | FOREVER }
```

Use the FOREVER keyword to configure the user account to never expire.

The default is FOREVER.



</dd><dt><b>

*<timestamp\>*

</b></dt>
<dd>

Specifies a timestamp.

```
<timestamp> ::= <string_literal>
```



</dd>
</dl>



</dd><dt><b>

*<user\_parameter\_option\>*

</b></dt>
<dd>

Sets or clears user parameters.

In the case of competing settings between user parameter options and workload class settings, a workload class setting takes precedence over a user parameter option. Workload class settings and user parameter options always take precedence over `.ini` file settings.

```
<user_parameter_option> ::= 
 <set_user_parameters> [ <clear_user_parameter_option> ]
 | <clear_user_parameter_option>
```


<dl>
<dt><b>

*<set\_user\_parameters\>*

</b></dt>
<dd>

Sets parameters in the user parameter list.

```
<set_user_parameters> ::= SET PARAMETER <user_parameter_list>
```



</dd><dt><b>

*<user\_parameter\_list\>*

</b></dt>
<dd>

Specifies a list of user parameters.

```
<user_parameter_list> ::= 
 <user_parameter> [, <user_parameter> [,…] ]
```

```
<user_parameter> ::= CLIENT = <string_literal>
 | LOCALE = <string_literal>  
 | TIME ZONE  = <string_literal> 
 | EMAIL ADDRESS = <string_literal>
 | STATEMENT MEMORY LIMIT = '<integer>'
 | STATEMENT THREAD LIMIT = '<integer>'
```


<table>
<tr>
<th valign="top">

User Parameter

</th>
<th valign="top">

Purpose

</th>
</tr>
<tr>
<td valign="top">

CLIENT

</td>
<td valign="top">

When you define column store views, this parameter restricts the user's access to the specified client.

This parameter cannot be specified by users themselves.

</td>
</tr>
<tr>
<td valign="top">

LOCALE

</td>
<td valign="top">

When you define column store views, the user parameter LOCALE translates information according to the user's locale.

</td>
</tr>
<tr>
<td valign="top">

TIME ZONE

</td>
<td valign="top">

This parameter is not used by the SAP HANA database, but it can be read by external applications.

</td>
</tr>
<tr>
<td valign="top">

EMAIL ADDRESS

</td>
<td valign="top">

This parameter is not used by the SAP HANA database, but can be read by external applications. This value must be unique.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT MEMORY LIMIT

</td>
<td valign="top">

Sets a user-specific statement memory limit in gigabytes.

-   If both a global and a user statement memory limit are set, then the user specific limit takes precedence, regardless of whether it is higher or lower than the global statement memory limit.

-   If the user-specific statement memory limit is removed, then the global limit takes effect for the user.

-   Setting the statement memory limit to 0 disables any statement memory limit for the user.

-   For STATEMENT MEMORY LIMIT to take effect, resource\_tracking and memory\_tracking must be active.




</td>
</tr>
<tr>
<td valign="top">

STATEMENT THREAD LIMIT

</td>
<td valign="top">

Sets a user specific concurrency limit on statements \(despite the name, STATEMENT THREAD LIMIT is not an actual thread limit\). Similar behaviors to STATEMENT MEMORY LIMIT apply for STATEMENT THREAD LIMIT.

</td>
</tr>
<tr>
<td valign="top">

PARAMETER PRIORITY

</td>
<td valign="top">

Sets a user-level priority value for all statements in the current connection; the range of possible values is from 0 to 9 \(the default is 5\).

</td>
</tr>
</table>



</dd><dt><b>

*<clear\_user\_parameter\_option\>*

</b></dt>
<dd>

Clears one or more user parameters.

```
<clear_user_parameter_option> ::= 
 CLEAR PARAMETER <clear_user_parameter_list>
 | CLEAR ALL PARAMETERS

<clear_user_parameter_list> ::= 
 <clear_user_parameter> [, <clear_user_parameter> [,…] ]
```

For the list of parameters you can clear, refer to the list you can set in the *<user\_parameter\_list\>* in the previous clause.



</dd>
</dl>



</dd><dt><b>

*<usergroup\_membership\_option\>*

</b></dt>
<dd>

Adds or removes a user from a user group. A user can only be a member of one user group at a time.

```
<usergroup_membership_option> ::= 
 SET USERGROUP <usergroup_name>
```


<dl>
<dt><b>

SET USERGROUP *<usergroup\_name\>*

</b></dt>
<dd>

Adds the user to the specified user group.



</dd>
</dl>



</dd><dt><b>

*<external\_ident\>*

</b></dt>
<dd>

Specifies the external identity for the user. This clause is only for Kerberos authentication.

```
IDENTIFIED EXTERNALLY AS <external_identity> [ VALID <validity_specification> ]
```


<dl>
<dt><b>

*<external\_identity\>*

</b></dt>
<dd>

Defines an external identity that authenticates the user.

```
<external_identity> ::= 
 <simple_identifier> 
 | <string_literal>
```



</dd>
</dl>



</dd><dt><b>

*<reset\_connect\_attempts\>*

</b></dt>
<dd>

Resets the number of invalid connection attempts to zero so the user can connect immediately.

```
<reset_connect_attempts> ::= RESET CONNECT ATTEMPTS
```

For the maximum number of allowed invalid connection attempts before a user is locked, see the M\_PASSWORD\_POLICY system view.



</dd><dt><b>

*<drop\_connect\_attempts\>*

</b></dt>
<dd>

Drops old information about invalid connect attempts recorded for the specified user.

```
<drop_connect_attempts> ::= DROP CONNECT ATTEMPTS
```

It does not reset the current count of invalid connect attempts and therefore does not allow the user to connect immediately.

To view the count of invalid connection attempts that have occurred, see the INVALID\_CONNECT\_ATTEMPTS system view.



</dd><dt><b>

*<password\_lifetime\>*

</b></dt>
<dd>

Enables or disables password lifetime checks.

```
<password_lifetime> ::= { ENABLE | DISABLE } PASSWORD LIFETIME
```



</dd><dt><b>

*<force\_pass\_change\>*

</b></dt>
<dd>

Forces the user to change their password immediately after the next connection to the SAP HANA database.

```
<force_pass_change> ::= FORCE PASSWORD CHANGE
```



</dd><dt><b>

*<user\_activation\_opts\>*

</b></dt>
<dd>

Activates or deactivates a user's account.

```
<user_activation_opts> ::= { ACTIVATE | DEACTIVATE } [ USER NOW ]
```

Users cannot connect to the SAP HANA database once their account is deactivated. However, it may appear as though deactivated users are still active in the system \(for example when a procedure that was created by the user with DEFINER MODE is called\). Reactivate a deactivated user with the ACTIVATE keyword.



</dd><dt><b>

*<authent\_mech\_opts\>*

</b></dt>
<dd>

Enables or disables the selected authentication mechanism.

```
<authent_mech_opts> ::= { ENABLE | DISABLE } <authentication_mechanism>
```


<dl>
<dt><b>

*<authentication\_mechanism\>*

</b></dt>
<dd>

Specifies the type of the authentication mechanism to enable or disable.

```
<authentication_mechanism> ::= 
 PASSWORD 
 | KERBEROS 
 | SAML 
 | X509 
 | JWT
 | LDAP
```



</dd>
</dl>



</dd><dt><b>

*<add\_ident\_opts\>*

</b></dt>
<dd>

Defines a method for authenticating the user.

```
<add_ident_opts> ::= 
 ADD IDENTITY { <add_provider_identity> [ <add_provider_identity> […] ] 
 | { <external_identity> FOR KERBEROS } }

<add_provider_identity> ::= 
 <saml_provider_ident> 
 | <x509_provider_ident>
 | <kerberos_provider_ident>
 | <jwt_provider_ident>
```


<dl>
<dt><b>

*<saml\_provider\_ident\>*

</b></dt>
<dd>

Defines a SAML provider.

```
<saml_provider_ident> = <mapped_user_name> FOR SAML PROVIDER <saml_provider_name>
<mapped_user_name> ::= ANY | <string_literal>
<saml_provider_name> ::= <simple_identifier>
```

*<mapped\_user\_name\>* specifies the mapped SAML user name to use. If the keyword ANY is used, then the SAML assertion contains the name of the database user that the assertion is valid for.

*<saml\_provider\_name\>* specifies the identifier of a SAML provider that already exists in the system.

For more information on SAML providers, see the CREATE SAML PROVIDER statement.



</dd><dt><b>

*<x509\_provider\_ident\>*

</b></dt>
<dd>

Defines an X.509 certificate issuer or X.509 provider.

```
<x509_provider_ident> ::= 
   <subject_distinguished_name> ISSUER <issuer_distinguished_name> FOR X509
   | { '<subject_distinguished_name>' | ANY } FOR X509 PROVIDER <x509_provider_name>

<subject_distinguished_name> ::= <string_literal>
<issuer_distinguished_name> ::= <string_literal>
<x509_provider_name> ::= <simple_identifier>
```

*<subject\_distinguished\_name\>* specifies the subject name provided in the certificate of the X.509 identity provider.

*<issuer\_distinguished\_name\>* specifies the issuer name provided in the certificate of the X.509 identity provider.

You can specify a wildcard \(ANY\) for the subject name only for an X.509 provider with matching rules.

*<x509\_provider\_name\>* specifies the identifier of an X.509 provider that already exists in the system.



</dd><dt><b>

*<kerberos\_provider\_ident\>*

</b></dt>
<dd>

Defines a KERBEROS identity.

```
<kerberos_provider_ident> ::= <kerberos_principal_name> FOR KERBEROS
<kerberos_principal_name> ::= <string_literal>
```

*<kerberos\_principal\_name\>* specifies an identity within an external authentication system.



</dd><dt><b>

*<jwt\_provider\_ident\>*

</b></dt>
<dd>

Defines a JWT provider-user-mapping.

```
<jwt_provider_ident> ::= <mapped_user_name> FOR JWT PROVIDER <jwt_provider_name>                          
<mapped_user_name> ::= { ANY | <string_literal> }
<jwt_provider_name> ::= <simple_identifier>
```

*<mapped\_user\_name\>* specifies the mapped JWT user name to use. If the keyword ANY is used, then the JWT token contains the name of the database user that the token is valid for.

*<jwt\_provider\_name\>* specifies the identifier of a JWT provider already existing in the system.



</dd>
</dl>



</dd><dt><b>

*<drop\_ident\_opts\>*

</b></dt>
<dd>

Drops the defined identity provider.

```
<drop_ident_opts> = 
 DROP IDENTITY { <provider_info> [ <provider_info> […] ] | FOR KERBEROS }
```


<dl>
<dt><b>

*<provider\_info\>*

</b></dt>
<dd>

Specifies the provider info to be dropped.

```
<provider_info> ::= 
 [ <mapped_user_name> ] FOR SAML PROVIDER <saml_provider_name>
 | <subject_distinguished_name> ISSUER <issuer_distinguished_name> FOR X509
 | [ '<subject_distinguished_name>' | ANY ] FOR X509 PROVIDER <x509_provider_name>
 | [ <mapped_user_name> ] FOR JWT PROVIDER <jwt_provider_name>

<mapped_user_name> ::= { ANY | <string_literal> }
```

Specifying a subject and issuer for an X.509 provider removes only that mapping. Specifying ANY removes the wildcard mapping. If you don't specify a subject and issuer or ANY, all mappings between the user and provider are removed.

Specifying a mapped user name or ANY for a JWT or SAML provider removes only that mapping. If you don't specify a mapped user name, all mappings between the user and provider are removed.



</dd>
</dl>



</dd><dt><b>

*<add\_remote\_database\_identity\>*

</b></dt>
<dd>

Adds a remote database identity.

```
ADD REMOTE IDENTITY <remote_user_name> AT DATABASE <database_name>
```



</dd><dt><b>

*<drop\_remote\_database\_identity\>*

</b></dt>
<dd>

Drops a remote database identity.

```
DROP REMOTE IDENTITY <remote_user_name> AT DATABASE <database_name>
```



</dd><dt><b>

*<client\_connect\_option\>*

</b></dt>
<dd>

Enables or disables the client from connecting at all. In case of disabled client connect, only connecting via an XS application is allowed.

```
<client_connect_option> ::= { ENABLE | DISABLE } CLIENT CONNECT
```



</dd><dt><b>

*<special\_privilege\_handling\>*

</b></dt>
<dd>

Allows a user to control whether another user can create objects in their own schema, and whether the user has the PUBLIC role.

When a user is created, they are automatically granted PUBLIC and CREATE ANY for objects in their schema, and these are granted by user SYS. *<special\_privilege\_handling\>* allows users to remove \(or re-grant\) CREATE ANY and PUBLIC. Users that do not have the PUBLIC role and do not have the CREATE ANY ON OWN SCHEMA privilege are indicated in the USERS system view as restricted users.

```
<special_privilege_handling> ::=
 { GRANT | REVOKE } CREATE ANY ON OWN SCHEMA
 | { GRANT | REVOKE } ROLE PUBLIC
```

Use the GRANT | REVOKE CREATE ANY ON OWN SCHEMA clause to grant or revoke, respectively, a user's ability to create objects in their own schema.

Use the GRANT | REVOKE ROLE PUBLIC clause to grant or revoke, respectively, PUBLIC role from a user.



</dd><dt><b>

*<ldap\_group\_authorization\>*

</b></dt>
<dd>

Specifies the LDAP group authorization mode for the user.

```
<ldap_group_authorization> ::= AUTHORIZATION { LOCAL | LDAP }
```


<dl>
<dt><b>

LOCAL

</b></dt>
<dd>

Specifies the use of local authorization mode for the user. This is the default.



</dd><dt><b>

LDAP

</b></dt>
<dd>

Specifies the use of LDAP authorization mode for the user.

Users with LDAP authorization mode cannot be granted permissions directly and cannot have local roles granted to them.

When changing the LDAP authorization mode from LOCAL authorization to LDAP for a user, LDAP roles are evaluated and activated upon next login. Also, local roles and privileges granted to the user are revoked except for roles that are granted by SYS--for example, the PUBLIC role--and the CREATE ANY privilege on the user's own schema.



</dd>
</dl>



</dd>
</dl>



<a name="loio20d3459f75191014a7bbeb670bad8850__sql_alter_user_1sql_alter_user_description"/>

## Description

External users are authenticated by using an external system, for example a Kerberos system. For detailed information about external identities, contact your domain administrator.

Users configured for LDAP authentication cannot simultaneously be configured for local password authentication. Local password authentication must be disabled before a user can be configured for LDAP authentication, for example, using ALTER USER...DISABLE PASSWORD.



<a name="loio20d3459f75191014a7bbeb670bad8850__section_mxv_fyc_pbb"/>

## Permissions

You must have the OPERATOR object privilege on the user group that the user is in. For JWT, SAML or X.509 authentication, you must have the REFERENCES object privilege on the specified providers.



<a name="loio20d3459f75191014a7bbeb670bad8850__sql_alter_user_1sql_alter_user_configuration_parameter"/>

## Configuration Parameters

Configuration parameters concerning the user's password can be observed with the M\_PASSWORD\_POLICY system view. These parameters are stored in `indexserver.ini`, in the password policy section.

The description of the parameters concerned can be found in the Appendix of the *SAP HANA Cloud, SAP HANA Database Security Guide* under Password Policy Parameters.



<a name="loio20d3459f75191014a7bbeb670bad8850__sql_alter_user_1sql_alter_user_examples"/>

## Examples

Create a SAML provider named ac\_saml\_provider in the database specifying a subject and issuer for ACompany.

```
CREATE SAML PROVIDER ac_saml_provider 
   WITH SUBJECT 'CN = wiki.detroit.ACompany.corp,OU = ACNet,O = ACompany,C = EN'
   ISSUER 'E = John.Do@acompany.com,CN = ACNetCA,OU = ACNet,O = ACompany,C = EN';
```

Create a new user named new\_user that can connect by using a password or with an assertion of the SAML provider ac\_saml\_provider. The *<mapped\_user\_name\>* was set to ANY as the assertion provides the database user name.

```
CREATE USER new_user PASSWORD Password1 WITH IDENTITY ANY FOR SAML PROVIDER ac_saml_provider;
```

Force the user to change their password.

```
ALTER USER new_user FORCE PASSWORD CHANGE;
```

Disable SAML authentication for the user.

```
ALTER USER new_user DISABLE SAML;
```

Reset the number of invalid connection attempts to zero for new\_user.

```
ALTER USER new_user RESET CONNECT ATTEMPTS;
```

Define the external identity for KERBEROS and enable KERBEROS for this user. Adding an external identification mechanism to a user does not automatically enable it. You must do this as a separate step as shown in this example.

```
ALTER USER new_user ADD IDENTITY 'testkerberosName' FOR KERBEROS;
ALTER USER new_user ENABLE KERBEROS;
```

Remove the ac\_saml\_provider SAML provider identity from new\_user.

```
ALTER USER new_user DROP IDENTITY FOR SAML PROVIDER ac_saml_provider;
```

Disable the account.

```
ALTER USER new_user DEACTIVATE;
```

**Related Information**  


[CREATE USER Statement \(Access Control\)](create-user-statement-access-control-20d5ddb.md "Creates a new database user.")

[USERGROUPS System View](../../020-System-Views-Reference/021-System-Views/usergroups-system-view-ac342d0.md "Provides details on all user groups.")

[USERS System View](../../020-System-Views-Reference/021-System-Views/users-system-view-2102609.md "Lists all users.")

[SQL Notation Conventions](../sql-notation-conventions-209e0cd.md "SQL syntax notation conventions used in this guide.")

[Data Types](../data-types-20a1569.md "A data type defines the characteristics of a data value. A special value of NULL is included in every data type to indicate the absence of a value.")

[M\_PASSWORD\_POLICY System View](../../020-System-Views-Reference/022-Monitoring-Views/m-password-policy-system-view-20b6e99.md "Defines effective password policy settings.")

[INVALID\_CONNECT\_ATTEMPTS System View](../../020-System-Views-Reference/021-System-Views/invalid-connect-attempts-system-view-ea60f23.md "Provides the number of invalid connection attempts for a user between two successful connections.")

[CREATE SAML PROVIDER Statement \(Access Control\)](create-saml-provider-statement-access-control-20d4cca.md "Defines a SAML provider in the SAP HANA database.")

[USER\_PARAMETERS System View](../../020-System-Views-Reference/021-System-Views/user-parameters-system-view-2102244.md "Lists all parameters and their values, which have been assigned to users in the system (using CREATE USER ... SET PARAMETER or ALTER USER ... SET PARAMETER).")

[SAML\_PROVIDERS System View](../../020-System-Views-Reference/021-System-Views/saml-providers-system-view-20cda7b.md "Shows available SAML providers.")

[SAML\_USER\_MAPPINGS System View](../../020-System-Views-Reference/021-System-Views/saml-user-mappings-system-view-20cdc48.md "Shows the SAML providers known for each user.")

