<!-- loio3b722036ba4941df8712508a3b231643 -->

# CREATE LDAP PROVIDER Statement \(Access Control\)

Creates an LDAP provider for use with LDAP authorization and authentication.



## Syntax

```
CREATE LDAP PROVIDER <ldap_provider_name>
 CREDENTIAL TYPE <credential_type_name> USING <credential_of_ldap_account> 	
 USER LOOKUP URL <url_string_literal>
 [ NESTED GROUP LOOKUP URL <url_string_literal> ]
 ATTRIBUTE DN <dn_string_literal>
 [ ATTRIBUTE MEMBER_OF <member_of_string_literal> ]
 [ SSL { ON | OFF } ]
 [ DEFAULT { ON | OFF } ]
 [ { ENABLE | DISABLE } PROVIDER ]
 [ <enable_user_creation>
```



## Syntax Elements


<dl>
<dt><b>

*<ldap\_provider\_name\>*

</b></dt>
<dd>

Specifies the name of the LDAP provider you want to create.

```
<ldap_provider_name> ::= <unicode_name>
```



</dd><dt><b>

CREDENTIAL TYPE *<credential\_type\_name\>* USING *<credential\_of\_ldap\_account\>*

</b></dt>
<dd>

Specifies the credential for the LDAP access account. Only one credential type can be configured for an LDAP provider and the only supported type is PASSWORD.

```
<credential_type_name> ::= 'PASSWORD'

<credential_of_ldap_account> ::= 'user=<user_dn_string_literal>;password=<passphrase>'
```

LDAP access account information includes the distinguished name \(DN\) and password of the user that is set up in LDAP server for use by SAP HANA server. This user must have permissions within the LDAP server to perform searches as specified by the USER LOOKUP URL and NESTED GROUP LOOKUP URL clauses.

For the credential type PASSWORD, specifies the credentials of an LDAP access account by using the USING clause.

*<credential\_of\_ldap\_account\>* specifies the credential of the LDAP access account that SAP HANA uses to log in to the LDAP server.

*<user\_dn\_string\_literal\>* specifies the distinguished name \(DN\) of the LDAP access account that HANA uses to log in to the LDAP server.

*<passphrase\>* specifies the password for the access account that SAP HANA uses to log in to the LDAP server.

An example CREDENTIAL clause might look like this: `CREDENTIAL TYPE 'PASSWORD' USING 'user=cn=LookupAccount,o=largebank.com;password=secret'`.



</dd><dt><b>

USER LOOKUP URL *<url\_string\_literal\>*

</b></dt>
<dd>

Specifies an LDAP URL that locates a unique user entry in the LDAP server that corresponds to an SAP HANA user. The format of a USER LOOKUP URL is as follows:

```
ldap[s]://<hostname>:<port>/<base_dn>?<attributes>?<scope>?<filter>
```

A search filter *<filter\>* uses the USER\_NAME of the SAP HANA user to locate the user entry in the LDAP Server.*<filter\>* must include a condition of the form `'<attr>=*'` where `<attr>` is an LDAP attribute whose value is matched against the USER\_NAME of the SAP HANA user. SAP HANA replaces the `'*'` in the search filter with the USER\_NAME of the current SAP HANA user

For example, when the following LDAP query is sent to the LDAP server, `(&(objectClass=user)(sAMAccountName=*))` is replaced with <code>(&amp;(objectClass=user)(sAMAccountName=<b>&lt;USER_NAME of the current or specified SAP HANA user&gt;</b>))</code>:

```
USER LOOKUP URL 'ldap://myhostname:389/ou=Users,dc=largebank,dc=com??sub?(&(objectClass=user)(sAMAccountName=*))'
```

*<filter\>* must contain one and only one `'*'`; otherwise, an error is returned..

The *<attributes\>* specification lists LDAP attributes whose values are returned to the SAP HANA server for a given user entry. *<attributes\>* must be left empty for USER LOOKUP URL. SAP HANA constructs the *<attributes\>* internally based on the LDAP attributes specified with ATTRIBUTE clause.



</dd><dt><b>

NESTED GROUP LOOKUP URL *<url\_string\_literal\>*

</b></dt>
<dd>

Specifies an LDAP URL for obtaining LDAP group membership information, including nested groups, for a user from the LDAP server. For example: `NESTED GROUP LOOKUP URL 'ldap://myhostname:389/ou=groupsOU,dc=x??sub?(member:1.2.840.113556.1.4.1941:=*)'`

The asterisk in *<url\_string\_literal\>* is replaced by the user DN, which is obtained by using the USER LOOKUP URL.

Depending upon the NESTED GROUP LOOKUP URL, one or more levels of LDAP groups may be returned. It is possible to specify a URL that returns only one level of groups with NESTED GROUP LOOKUP URL. SAP HANA sends this LDAP query to the LDAP server for execution. Before sending the query, SAP HANA replaces '\*' in the NESTED GROUP LOOKUP URL with the DN of the user obtained from execution of USER LOOKUP URL.

While ATTRIBUTE MEMBER\_OF and NESTED GROUP LOOKUP URL are both optional, if LDAP authorization is used and neither of these are defined, then an error is returned at run-time.

Support for nested LDAP groups is provided *only* when a single URL can be specified such that it returns a complete list of groups with the user’s membership \(including groups with indirect membership\). SAP HANA does not recursively fetch nested groups if they were not obtained by executing the search specified by NESTED GROUP LOOKUP URL.



</dd><dt><b>

ATTRIBUTE DN *<dn\_string\_literal\>*

</b></dt>
<dd>

Specifies the LDAP attribute that provides the DN \(distinguished name\) of the LDAP User entry. The DN of the user is stored in the SAP HANA catalog.



</dd><dt><b>

ATTRIBUTE MEMBER\_OF *<member\_of\_string\_literal\>*

</b></dt>
<dd>

Specifies the LDAP attribute that provides a list of groups that a user is a member of. If NESTED GROUP LOOOKUP URL is specified, then the group information is obtained using NESTED GROUP LOOKUP URL \(that is, ATTRIBUTE MEMBER\_OF is not used\).

While ATTRIBUTE MEMBER\_OF and NESTED GROUP LOOKUP URL are both optional, if LDAP authorization is used and neither of these are defined, then an error is returned at run-time.



</dd><dt><b>

SSL \{ON | OFF\}

</b></dt>
<dd>

Specifies whether SSL/TLS secures connections to the LDAP server, both for LDAP access account authentication and LDAP user and group searches. The default is OFF.

> ### Caution:  
> If using the LDAP server for user authorization and authentication, you must secure communication between SAP HANA and the LDAP server using the TLS/SSL protocol to protect the transmission of sensitive information such as user names, passwords, and group membership, which are otherwise sent in the clear between SAP HANA and the LDAP server.

When using SSL protocol, the trust store used to authenticate communication must be a certificate collection in the SAP HANA database with the purpose LDAP. The certificate of the Certificate Authority \(CA\) that signed the certificate used by the LDAP server must be available in this certificate collection. For more information, see the section on certificate management in the *SAP HANA Cloud, SAP HANA Database Security Guide*.

When set to ON, the SSL/TLS protocol is used and the URL begins with "ldap://".

Connections to LDAP server can also be secured by using Secure LDAP protocol. In this case, URL begins with “ldaps://”. SSL should be set to OFF when using secure LDAP protocol.



</dd><dt><b>

DEFAULT \{ON | OFF\}

</b></dt>
<dd>

Designates the LDAP provider to use for LDAP authorization and authentication. The default is OFF.

You can create multiple named LDAP providers, but you can only designate one as the default. Designating an LDAP provider as DEFAULT removes the default designation of the previous default LDAP provider, if any.



</dd><dt><b>

\{ENABLE | DISABLE \} PROVIDER

</b></dt>
<dd>

Creates the provider as enabled or disabled. The default is DISABLE PROVIDER.

If a default LDAP provider is disabled, then users cannot log in by using LDAP authorization. VALIDATE LDAP PROVIDER can still be used to verify the configuration of a disabled LDAP provider.



</dd><dt><b>

*<enable\_user\_creation\>*

</b></dt>
<dd>

Enables automatic user creation when using LDAP authentication, and specifies type of the user to create - standard or restricted.

```
<enable_user_creation> ::= 
   ENABLE USER CREATION FOR LDAP [ USER TYPE { STANDARD | RESTRICTED } ] USERGROUP <usergroup_name>
```

When enabling automatic user creation, optionally specify the type of the new users to be created. By default, new users are created as STANDARD users. The user is created in the specified user group.



</dd>
</dl>



## Description

To use LDAP group-based authorization or LDAP authentication, access to an LDAP Server is configured in SAP HANA using an LDAP provider.

LDAP authentication and LDAP authorization require a default LDAP provider that is in an enabled state.

Nested LDAP groups is only supported when there is a single URL that can be used to return the complete list of groups that the user is a member of \(including groups with indirect membership\). Nested LDAP groups is not supported on directory servers that do not provide this capability.



<a name="loio3b722036ba4941df8712508a3b231643__section_s4s_ytc_pbb"/>

## Permissions

You must have the LDAP ADMIN system privilege to create an LDAP provider.



## Examples

**Example 1:** Create an LDAP provider, `my_ldap_provider`, for obtaining LDAP group memberships for SAP HANA users and activating it as the default LDAP provider for authorization.

```
CREATE LDAP PROVIDER my_ldap_provider
   CREDENTIAL TYPE 'PASSWORD' USING 'user=cn=LookupAccount,o=largebank.com;password=secret'
   USER LOOKUP URL 'ldap://myhostname:389/ou=Users,dc=largebank,dc=com??sub?(&(objectClass=user)(sAMAccountName=*))'
   ATTRIBUTE DN 'distinguishedName'
   ATTRIBUTE MEMBER_OF 'memberOf'
   SSL ON
   DEFAULT ON
   ENABLE PROVIDER;
```

**Example 2:** Create an LDAP provider to use nested groups:

```
CREATE LDAP PROVIDER my_ldap_provider
 CREDENTIAL TYPE 'PASSWORD' USING 'user=cn=LookupAccount,o=largebank.com;password=secret'
 USER LOOKUP URL 'ldap://myhostname:389/ou=Users,dc=largebank,dc=com??sub?(&(objectClass=user)(sAMAccountName=*))'
 NESTED GROUP LOOKUP URL 'ldap://myhostname:389/ou=groupsOU,dc=x??sub?(member:1.2.840.113556.1.4.1941:=*)'
 ATTRIBUTE DN 'distinguishedName'
 SSL ON
 DEFAULT ON
 ENABLE PROVIDER;
```

**Example 3:** Create an LDAP provider configured for automatic creation of STANDARD users with LDAP authentication:

```
CREATE LDAP PROVIDER my_ldap_provider
 CREDENTIAL TYPE 'PASSWORD' USING 'user=cn=LookupAccount,o=largebank.com;password=secret'
 USER LOOKUP URL 'ldap://myhostname:389/ou=Users,dc=largebank,dc=com??sub?(&(objectClass=user)(sAMAccountName=*))'
 ATTRIBUTE DN 'distinguishedName'
 SSL ON
 DEFAULT ON
 ENABLE PROVIDER
 ENABLE USER CREATION FOR LDAP USERGROUP LDAP_USERS;
```

**Example 4:** Configure an LDAP Provider for automatic creation of RESTRICTED users with LDAP authentication:

```
CREATE LDAP PROVIDER my_ldap_provider
  CREDENTIAL TYPE 'PASSWORD' USING 'user=cn=LookupAccount,o=largebank.com;password=secret'
  USER LOOKUP URL 'ldap://myhostname:389/ou=Users,dc=largebank,dc=com??sub?(&(objectClass=user)(sAMAccountName=*))'
  ATTRIBUTE DN 'distinguishedName'
  SSL ON
  DEFAULT ON
  ENABLE PROVIDER
  ENABLE USER CREATION FOR LDAP USER TYPE RESTRICTED USERGROUP LDAP_USERS;
```

**Related Information**  


[Certificate Management](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2023_4_QRC/en-US/1e6042c4402545f7a0574f7bc91fab25.html "SAP HANA uses public-key certificates as the basis for several user authentication mechanisms, and for securing internal and external communication channels. Certificates are stored and managed directly in the SAP HANA database.") :arrow_upper_right:

[ALTER LDAP PROVIDER Statement \(Access Control\)](alter-ldap-provider-statement-access-control-ae9ba28.md "Updates an LDAP provider for use with LDAP authorization and authentication.")

[DROP LDAP PROVIDER Statement \(Access Control\)](drop-ldap-provider-statement-access-control-340e913.md "Drops an LDAP provider, and its associated credential, from the internal secure credential store.")

[VALIDATE LDAP PROVIDER Statement \(Access Control\)](validate-ldap-provider-statement-access-control-4181217.md "Validates an LDAP provider configuration and LDAP authentication and authorization for users of that LDAP provider.")

[LDAP\_PROVIDER\_URLS System View](../../020-System-Views-Reference/021-System-Views/ldap-provider-urls-system-view-7cf2869.md "Lists all LDAP provider URLs.")

[LDAP\_PROVIDERS System View](../../020-System-Views-Reference/021-System-Views/ldap-providers-system-view-5b54fe2.md "Lists all LDAP providers.")

[LDAP\_USERS System View](../../020-System-Views-Reference/021-System-Views/ldap-users-system-view-704e5b6.md "Provides information about the users using LDAP authorization.")

[LDAP User Authentication](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2023_4_QRC/en-US/868f8b988e2d42ccb89ccaf263cd9986.html "The Lightweight Directory Access Protocol (LDAP) is an application protocol for accessing directory services. If you use an LDAP-compliant directory server to manage users and their passwords, you can leverage LDAP-based authentication to access SAP HANA.") :arrow_upper_right:

[LDAP Group Authorization](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2023_4_QRC/en-US/f494db9664ba45af9bcdd88c7b342405.html "The Lightweight Directory Access Protocol (LDAP) is an application protocol for accessing directory services. If you use an LDAP-compliant directory server to manage users and their access to resources, you can leverage LDAP group membership to authorize SAP HANA database users.") :arrow_upper_right:

[Secure Communication Between SAP HANA and an LDAP Directory Server](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2023_4_QRC/en-US/b9086809b9bb466cbd15542430f2ebe6.html "Communication between the SAP HANA Cloud, SAP HANA database and an LDAP directory server must be secured.") :arrow_upper_right:

[Configuring LDAP Integration](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/03c98f3aade14b2c955a054833d90426.html "The Lightweight Directory Access Protocol (LDAP) is an application protocol for accessing directory services. If you use an LDAP-compliant directory server to manage users and their access to resources, you can leverage LDAP-based authentication to access SAP HANA and LDAP group membership to authorize users.") :arrow_upper_right:

