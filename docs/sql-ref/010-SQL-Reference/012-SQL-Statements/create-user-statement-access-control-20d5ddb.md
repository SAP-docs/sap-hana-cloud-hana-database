<!-- loio20d5ddb075191014b594f7b11ff08ee2 -->

# CREATE USER Statement \(Access Control\)

Creates a new database user.



<a name="loio20d5ddb075191014b594f7b11ff08ee2__sql_create_user_1sql_create_user_syntax"/>

## Syntax

```
CREATE [ RESTRICTED ] USER <user_name>
 [ <authentication_options> ]
 [ <validity_specification> ] 
 [ <set_user_parameters> ] 
 [ <ldap_group_authorization> ] 
 [ SET USERGROUP <usergroup_name> ]
```



<a name="loio20d5ddb075191014b594f7b11ff08ee2__sql_create_user_1sql_create_user_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<user\_name\>*

</b></dt>
<dd>

Specifies the user name of the user to be created. The specified user name must not be identical to the name of an existing user, user group, role, role group or schema.

```
<user_name> ::= <unicode_name>
```



</dd><dt><b>

*<authentication\_options\>*

</b></dt>
<dd>

Specifies the authentication options for the user.

```
<authentication_options> ::=
 { <remote_identity_option> 
  | <password_option>  
  | <external_ident>  
  | <with_ident_opts> 
 }
```


<dl>
<dt><b>

*<remote\_identity\_option\>*

</b></dt>
<dd>

Specifies a database user in another database as the remote identity of the database user being created.

```
<remote_identity_option> ::= 
 <remote_database_identity> [ <remote_database_identity> […] ]

<remote_database_identity> ::= <remote_user_name> AT DATABASE <database_name>
<remote_user_name> ::= <simple_identifier>
<database_name> ::= <identifier>
```



</dd><dt><b>

*<password\_option\>*

</b></dt>
<dd>

Specifies the user password of the user being created.

```
<password_option> ::= PASSWORD <password> [ NO FORCE_FIRST_PASSWORD_CHANGE ]
```

The option NO FORCE\_FIRST\_PASSWORD\_CHANGE overrules the setting of the password policy parameter force\_first\_password\_change and allows the final password to be specified during user creation.

The password must follow the rules defined for the current SAP HANA instance. The password rules include a minimum password length and a definition of which character types \(lower, upper, digit, special characters\) must be part of the password.



</dd><dt><b>

*<external\_ident\>*

</b></dt>
<dd>

Specifies the external identity for the user. This clause is only for Kerberos authentication.

```
<external_ident> ::= IDENTIFIED EXTERNALLY AS <external_identity>
```


<dl>
<dt><b>

*<external\_identity\>*

</b></dt>
<dd>

Defines an external identity for user authentication.

```
<external_identity> ::= 
 <simple_identifier> 
 | <string_literal>
```



</dd>
</dl>



</dd><dt><b>

*<with\_ident\_opts\>*

</b></dt>
<dd>

Defines a method for user authentication.

```
<with_ident_opts> ::= WITH IDENTITY <provider_identity> [ <provider_identity> […] ]

<provider_identity> ::= 
<saml_provider_ident> 
 | <x509_provider_ident> 
 | <kerberos_provider_ident>
 | <jwt_provider_ident>
 | <ldap_provider_ident>
```


<dl>
<dt><b>

*<saml\_provider\_ident\>*

</b></dt>
<dd>

Defines a SAML provider.

```
<saml_provider_ident> ::= <mapped_user_name> FOR SAML PROVIDER <saml_provider_name>
<mapped_user_name> ::= { ANY | <string_literal> }
<saml_provider_name> ::= <simple_identifier>
```

*<mapped\_user\_name\>* specifies the mapped SAML user name to use. If the keyword ANY is used, then the SPProvidedID attribute of the SAML assertion contains the name of the database user that the assertion is valid for. For more information, see the section on single sign-on using SAML in the *SAP HANA Cloud, SAP HANA Database Security Guide*.

*<saml\_provider\_name\>* specifies the identifier of a SAML provider that already exists in the system.



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

*<mapped\_user\_name\>* specifies the mapped JWT user name to use. If the keyword ANY is used, then the JWT token will contain the name of the database user that the token is valid for.

*<jwt\_provider\_name\>* specifies the identifier of a JWT provider that already exists in the system.



</dd>
</dl>


<dl>
<dt><b>

*<ldap\_provider\_ident\>*

</b></dt>
<dd>

Creates a user enabled to use LDAP authentication.

```
<ldap_provider_ident> ::= FOR LDAP PROVIDER
```



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

*<validity\_specification\>*

</b></dt>
<dd>

Defines the validity specification with an optional user parameter option.

```
<validity_specification> ::= VALID <validity_opts>
```


<dl>
<dt><b>

*<validity\_opts\>*

</b></dt>
<dd>

Configures the user's temporal validity.

```
<validity_opts> ::= 
 <from_specification> [ <until_specification> ]  
 | <until_specification>
```

The specified user can only connect within the given date range. By using this feature, you can create users in advance or restrict the period when users can connect to the SAP HANA database.



</dd><dt><b>

*<from\_specification\>*

</b></dt>
<dd>

Sets when the user is valid from.

```
<from_specification> ::= FROM { <timestamp> | NOW }
```

Use the NOW keyword to configure the user account to be valid from the current time.

The default value is NOW.



</dd><dt><b>

*<until\_specification\>*

</b></dt>
<dd>

Sets when the user is valid until.

```
<until_specification> ::= UNTIL { <timestamp> | FOREVER }
```

Use the FOREVER keyword to configure the user account to never expire.

The default value is FOREVER.



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

*<set\_user\_parameters\>*

</b></dt>
<dd>

Sets parameters in the user parameter list.

```
<set_user_parameters> ::= SET PARAMETER <user_parameter_list>
```


<dl>
<dt><b>

*<user\_parameter\_list\>*

</b></dt>
<dd>

Specifies a list of user parameters.

```
<user_parameter_list> ::= 
 <user_parameter>  [, <user_parameter> [,…] ]
```



</dd><dt><b>

*<user\_parameter\>*

</b></dt>
<dd>

Defines user parameters.

```
<user_parameter> ::= 
 CLIENT = <string_literal>
 | LOCALE = <string_literal> 
 | TIME ZONE  = <string_literal>
 | EMAIL ADDRESS = <string_literal>
 | STATEMENT MEMORY LIMIT = '<integer>'
 | STATEMENT THREAD LIMIT = '<integer>'
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

When you define column store views, the user parameter CLIENT restricts the access of the user to the specified client.

This parameter is for internal use only.

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

Not used by the SAP HANA database, but can be read by external applications.

</td>
</tr>
<tr>
<td valign="top">

EMAIL ADDRESS

</td>
<td valign="top">

Not currently used by the SAP HANA database, but can be read by external applications. This value must be unique.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT MEMORY LIMIT

</td>
<td valign="top">

Sets a user specific statement memory limit in gigabytes.

-   If both a global and a user statement memory limit are set, then the user-specific limit takes precedence, regardless of whether it is higher or lower than the global statement memory limit.

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

Sets a user-specific concurrency limit on statements \(despite the name, STATEMENT THREAD LIMIT is not an actual thread limit\). Similar behaviors to STATEMENT MEMORY LIMIT apply to STATEMENT THREAD LIMIT.

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



</dd>
</dl>



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

When changing the LDAP authorization mode from LDAP to LOCAL for a user, roles that were granted using LDAP are revoked, and the DN value for the SAP HANA user is cleared.



</dd><dt><b>

LDAP

</b></dt>
<dd>

Specifies the use of LDAP authorization mode for the user.

Users with LDAP authorization mode cannot be granted permissions directly, and cannot have local roles granted to them.

When changing the LDAP authorization mode from LOCAL authorization to LDAP for a user, LDAP roles are evaluated and activated upon next login. Also, local roles and privileges granted to the user are revoked except for roles that are granted by SYS--for example, the PUBLIC role--and the CREATE ANY privilege on the user's own schema.



</dd>
</dl>



</dd><dt><b>

SET USERGROUP *<usergroup\_name\>*

</b></dt>
<dd>

Adds the user to the specified user group. For example, SET USERGROUP DEFAULT creates the user in the same user group as the cloud administrator \(DBADMIN\).

If the user creating the new user has the OPERATOR privilege on only one usergroup, this clause is optional. For example, if USER1 has the OPERATOR privilege on GROUP1 only, this clause is not required and USER1 will be created in GROUP1. If USER1 has the privilege on GROUP1 and GROUP2, this clause is required.

This clause is required, unless the user group for newly created users has been set for the session using the SET USERGROUP statement.



</dd>
</dl>



<a name="loio20d5ddb075191014b594f7b11ff08ee2__sql_create_user_1sql_create_user_description"/>

## Description

The specified user name must not be identical to the name of an existing user, user group, role, role group or schema.

There are some users that are delivered with the SAP HANA database: SYS, SYSTEM, and a number of users with the \_SYS\_ prefix.

Users in the database can be authenticated by varying mechanisms:

-   Internal authentication mechanism using a password.

-   External mechanisms such as Kerberos, SAML, or X.509.


A user can be authenticated by more than one mechanism at a time; however, only one password and one principal name for Kerberos can be valid at any one time.

Specify at least one authentication mechanism to allow the user to connect and work with the database instance. For backwards compatibility, the IDENTIFIED EXTERNALLY AS *<external\_identity\>* syntax is maintained. This syntax essentially performs the same function as the *<kerberos\_principal\_name\>* FOR KERBEROS syntax.

External users are authenticated by using an external system, for example a Kerberos system. For detailed information about external identities, contact your domain administrator.

A schema with the user's name is created for each database user: this schema cannot be explicitly dropped. The user's schema is automatically dropped when the user is deleted. The database user owns this schema and it is used as their default schema when they execute a command without explicitly specifying a schema name.

Users created without the RESTRICTED option can create any object in their own schema and they are granted the role PUBLIC allowing them to select any system view. Users created with the RESTRICTED option have no privileges, not even the ability to create objects in their own schema. These users are meant for using specific applications only. All privileges needed for the application have to be granted to such users, preferably using a role combined with the application.



<a name="loio20d5ddb075191014b594f7b11ff08ee2__section_qbb_g5c_pbb"/>

## Permissions

You must have the OPERATOR object privilege on the user group that the user is created in.



<a name="loio20d5ddb075191014b594f7b11ff08ee2__sql_create_user_1sql_create_user_configuration_parameter"/>

## Configuration Parameters

Configuration parameters concerning the user's password can be observed with the monitoring view M\_PASSWORD\_POLICY. These parameters are stored in the password policy section of the `indexserver.ini` file.

The description of the parameters concerned can be found in the Appendix of the *SAP HANA Cloud, SAP HANA Database Security Guide* under Password Policy Parameters.



<a name="loio20d5ddb075191014b594f7b11ff08ee2__sql_create_user_1sql_create_user_examples"/>

## Examples



<a name="loio20d5ddb075191014b594f7b11ff08ee2__sql_create_user_1sql_create_user_example_1"/>

## Example 1 - Create user with password

The following example shows you how to create a user `T12345` with a password `Password123`.

```
CREATE USER T12345 PASSWORD Password123;
```



<a name="loio20d5ddb075191014b594f7b11ff08ee2__sql_create_user_1sql_create_user_example_2"/>

## Example 2 - Create user that uses an external authentication mechanism

The following example creates an SAML provider named `ac_saml_provider` in the database, specifying a subject and issuer for `ACompany`.

```
CREATE SAML PROVIDER ac_saml_provider 
    WITH SUBJECT 'CN = wiki.detroit.ACompany.corp,OU = ACNet,O = ACompany,C = EN' 
    ISSUER 'E = John.Do@acompany.com,CN = ACNetCA,OU = ACNet,O = ACompany,C = EN';
```

The following example creates a new user called `new_user` with password `Password1`. The user can connect to the system by using the given password and with an assertion of the existing SAML provider `ac_saml_provider`. The *<mapped\_user\_name\>* is set to `ANY` as the assertion provides the database user name.

```
CREATE USER new_user PASSWORD Password1 WITH IDENTITY ANY FOR SAML PROVIDER ac_saml_provider;
```

The following example creates a user that is only allowed to log in using X509:

```
CREATE USER testuser WITH IDENTITY 'C=US, ST=VA, L=Fairfax, O=example.com, CN=testuser' ISSUER 'C=US, ST=VA, L=Fairfax, O=example.com, CN=Root CA' FOR X509;
```

The following example creates a user that is only allowed to log in using password or X509:

```
CREATE USER testuser PASSWORD BadPassword5 WITH IDENTITY 'C=US, ST=VA, L=Fairfax, O=example.com, CN=testuser' ISSUER 'C=US, ST=VA, L=Fairfax, O=example.com, CN=Root CA' FOR X509; 
```

The following example creates a user that is only allowed to log in using X509 and whose account is deactivated on Jan 1, 2028:

```
CREATE USER testuser WITH IDENTITY 'C=US, ST=VA, L=Fairfax, O=example.com, CN=testuser' ISSUER 'C=US, ST=VA, L=Fairfax, O=example.com, CN=Root CA' FOR X509 VALID UNTIL '2028-01-01';
```

The following example creates a user that is only allowed to log in using SAML \(this statement actually throws an error if the SAML provider does not exist\):

```
CREATE USER testuser WITH IDENTITY ANY FOR SAML PROVIDER nonexistandsamlprovider;
```



## Example 3 - Create user that is associated with a remote user

This example creates a new user called `USER1` associated with the user `USER2` at the remote database `DB2`.

```
CREATE USER USER1 WITH REMOTE IDENTITY USER2 AT DATABASE DB2;
```

**Related Information**  


[User Management](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/dea55d23bb571014bf25f6ed0d3b2b17.html "Every user who wants to work directly with the SAP HANA database must have a database user with the necessary privileges. Depending on the scenario, the user accessing SAP HANA may either be a technical system user or an individual end user.") :arrow_upper_right:

[Authentication and Single Sign-On](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/db60da90bb5710149e358d50a7361419.html "The identity of users accessing the SAP HANA database is verified through a process called authentication. SAP HANA supports several authentication mechanisms that can be used for the integration of SAP HANA into single sign-on environments (SSO). The mechanisms used to authenticate individual users are specified as part of the user definition.") :arrow_upper_right:

[Characters Not Permitted in User Names](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/55d3b5a01166494582cc12f70ccfa17f.html "User names can contain any Compatibility Encoding Scheme for UTF-16: 8-Bit (CESU-8) characters except for a small subset.") :arrow_upper_right:

[CREATE SAML PROVIDER Statement \(Access Control\)](create-saml-provider-statement-access-control-20d4cca.md "Defines a SAML provider in the SAP HANA database.")

[CREATE JWT PROVIDER Statement \(Access Control\)](create-jwt-provider-statement-access-control-bfe3daf.md "Defines a JWT provider in the SAP HANA database.")

[M\_PASSWORD\_POLICY System View](../../020-System-Views-Reference/022-Monitoring-Views/m-password-policy-system-view-20b6e99.md "Defines effective password policy settings.")

[USERS System View](../../020-System-Views-Reference/021-System-Views/users-system-view-2102609.md "Lists all users.")

[USER\_PARAMETERS System View](../../020-System-Views-Reference/021-System-Views/user-parameters-system-view-2102244.md "Lists all parameters and their values, which have been assigned to users in the system (using CREATE USER ... SET PARAMETER or ALTER USER ... SET PARAMETER).")

[INVALID\_CONNECT\_ATTEMPTS System View](../../020-System-Views-Reference/021-System-Views/invalid-connect-attempts-system-view-ea60f23.md "Provides the number of invalid connection attempts for a user between two successful connections.")

[SAML\_PROVIDERS System View](../../020-System-Views-Reference/021-System-Views/saml-providers-system-view-20cda7b.md "Shows available SAML providers.")

[SAML\_USER\_MAPPINGS System View](../../020-System-Views-Reference/021-System-Views/saml-user-mappings-system-view-20cdc48.md "Shows the SAML provider information for each user.")

[Password Policy Configuration Options](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/61662e3032ad4f8dbdb5063a21a7d706.html "The password policy of the database is defined by parameters in the password policy section of the indexserver.ini configuration file. The initial password policy of a user group is a copy of the database password policy.") :arrow_upper_right:

[SET USERGROUP Statement \(Session Management\)](set-usergroup-statement-session-management-1991853.md "Specify a user group to which every subsequently created user is automatically assigned.")

