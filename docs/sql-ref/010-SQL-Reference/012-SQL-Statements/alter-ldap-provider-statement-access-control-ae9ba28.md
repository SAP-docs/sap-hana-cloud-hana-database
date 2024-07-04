<!-- loioae9ba28ddefc4b29809d5b926d6ee02d -->

# ALTER LDAP PROVIDER Statement \(Access Control\)

Updates an LDAP provider for use with LDAP authorization and authentication.



## Syntax

```
ALTER LDAP PROVIDER <ldap_provider_name> 
 [ CREDENTIAL TYPE <credential_type_name> USING <credential_of_ldap_account> ]	
 [ USER LOOKUP URL <url_string_literal> ] 
 [ NESTED GROUP LOOKUP URL { <url_string_literal> | NULL } ]
 [ ATTRIBUTE DN <dn_string_literal> ]
 [ ATTRIBUTE MEMBER_OF { <member_of_string_literal> | NULL } ]
 [ SSL { ON | OFF } ]
 [ DEFAULT { ON | OFF } ]
 [ { ENABLE | DISABLE } PROVIDER ]
 [ <enable_disable_user_creation> ]
```



## Syntax Elements


<dl>
<dt><b>

*<ldap\_provider\_name\>*

</b></dt>
<dd>

Specifies the identifier of a valid LDAP provider.

```
<ldap_provider_name> ::= <unicode_name>
```



</dd><dt><b>

CREDENTIAL TYPE *<credential\_type\_name\>* USING *<credential\_of\_ldap\_account\>*

</b></dt>
<dd>

Specifies the credential type for the LDAP access account. Only one credential type can be configured for an LDAP provider and the only supported type is PASSWORD.

```
<credential_type_name> ::= 'PASSWORD'

<credential_of_ldap_account> ::= 'user=<user_dn_string_literal>;password=<passphrase>'
```

LDAP access account information includes the distinguished name \(DN\) and password of the user that is set up in LDAP server for use by SAP HANA server. This user must have permissions within the LDAP server to perform searches as specified by the USER LOOKUP URL and NESTED GROUP LOOKUP URL clauses.

PASSWORD specifies an LDAP access account for which you specify the credentials by using the USING clause.

*<credential\_of\_ldap\_account\>* specifies the credential of the LDAP access account that SAP HANA uses to log in to the LDAP server.

*<user\_dn\_string\_literal\>* specifies the distinguished name \(DN\) of the LDAP access account that HANA uses to log in to the LDAP server.

*<passphrase\>* specifies the password for the access account that SAP HANA uses to log in to the LDAP server.

An example CREDENTIAL clause might look like this: `'PASSWORD' USING 'user=cn=LookupAccount,o=largebank.com;password=secret'`.



</dd><dt><b>

USER LOOKUP URL *<url\_string\_literal\>*

</b></dt>
<dd>

Specifies an LDAP URL that locates a unique user entry in the LDAP server that corresponds to an SAP HANA user. The format of a USER LOOKUP URL is as follows:

```
ldap[s]://<hostname>:<port>/<base_dn>?<attributes>?<scope>?<filter>
```

A search filter *<filter\>* uses the USER\_NAME of the SAP HANA user to locate the user entry in the LDAP Server.*<filter\>* must include a condition of the form `'<attr>=*'` where `<attr>` is an LDAP attribute whose value is matched against the USER\_NAME of the SAP HANA user. SAP HANA replaces the `'*'` in the search filter with the USER\_NAME of the current SAP HANA user

For example, when the following statement is executed, `(&(objectClass=user)(sAMAccountName=*))` is replaced with <code>(&amp;(objectClass=user)(sAMAccountName=<b>&lt;USER_NAME of the current or specified SAP HANA user&gt;</b>))</code>:

```
USER LOOKUP URL 'ldap://myhostname:389/ou=Users,dc=largebank,dc=com??sub?(&(objectClass=user)(sAMAccountName=*))'
```

*<filter\>* must contain one and only one `'*'`; otherwise, an error is returned..

The *<attributes\>* specification lists LDAP attributes whose values are returned to the SAP HANA server for a given user entry. *<attributes\>* must be left empty for USER LOOKUP URL. SAP HANA constructs the *<attributes\>* internally based on the LDAP attributes specified with ATTRIBUTE clause.

The following is an example of a USER LOOKUP URL:



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

Specifies or removes \(NULL\) the LDAP attribute that provides a list of groups that a user is a member of. If NESTED GROUP LOOOKUP URL is specified, then the group information is obtained using NESTED GROUP LOOKUP URL \(that is, ATTRIBUTE MEMBER\_OF is not used\).

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

Connections to LDAP Server can also be secured by using Secure LDAP protocol. In this case, URL begins with “ldaps://”. SSL should be set to OFF when using Secure LDAP protocol.



</dd><dt><b>

DEFAULT \{ON | OFF\}

</b></dt>
<dd>

Designates the LDAP provider to use for LDAP authorization and authentication. The default is OFF.

If you create multiple named LDAP providers, then you can designate one as the default. Designating an LDAP provider as DEFAULT removes the default designation of the previous default LDAP provider, if any.



</dd><dt><b>

\{ENABLE | DISABLE \} PROVIDER

</b></dt>
<dd>

Enables or disables the use of an LDAP provider. The default is DISABLE PROVIDER.

If a default LDAP provider is disabled, then users cannot log in by using LDAP authorization. VALIDATE LDAP PROVIDER can still be used to verify the configuration of a disabled LDAP provider.



</dd><dt><b>

*<enable\_disable\_user\_creation\>*

</b></dt>
<dd>

Enables or disables automatic user creation for LDAP authentication.

```
<enable_user_creation_for_ldap> ::=
   { ENABLE USER CREATION FOR LDAP [ USER TYPE { STANDARD | RESTRICTED } ] USERGROUP <usergroup_name>
   | DISABLE USER CREATION FOR LDAP } 
```

When enabling automatic user creation, optionally specify the type of the new users to be created. By default, new users are created as STANDARD users. The user is created in the specified user group.



</dd>
</dl>



## Description

Use the ALTER LDAP PROVIDER statement to update the configuration of an LDAP provider:

If the LDAP provider is set to DEFAULT OFF and there is no other default provider that is enabled, or if the LDAP provider is set to DISABLE PROVIDER and there is no other default provider that is enabled, then:

-   Any user connections created before the expiration of the value for the ldap\_authorization\_role\_reuse\_duration database property succeed.

-   Any user connections created after the expiration of the value for the ldap\_authorization\_role\_reuse\_duration database property fail.

-   Any first time user connections will fail.


When a default and enabled LDAP provider is altered such that it is either no longer a default LDAP provider or it is no longer enabled, the following occurs with respect to authentication and authorization:

-   In case of authentication, the connection fails

-   In case of authorization, the user connections *may* succeed. This is because within the user's role reuse duration, SAP HANA does not contact the LDAP server to validate the user's role with LDAP server.




<a name="loioae9ba28ddefc4b29809d5b926d6ee02d__section_if2_5tc_pbb"/>

## Permissions

You must have the LDAP ADMIN system privilege to alter an LDAP provider. If automatic user creation is enabled, the OPERATOR object privilege on the user group in which automatically created users are created is also required.



## Examples

**Example 1:** Alter the USER LOOKUP URL for an LDAP provider called `my_ldap_provider`:

```
ALTER LDAP PROVIDER my_ldap_provider
  USER LOOKUP URL 'ldap://myhostname:389/ou=Users,dc=largebank,dc=com??sub? (&(objectClass=user)(sAMAccountName=*))';
```

**Example 2:** Make the LDAP provider `my_ldap_provider` the default and enable it:

```
ALTER LDAP PROVIDER my_ldap_provider DEFAULT ON ENABLE PROVIDER;
```

**Example 3:** Change the NESTED GROUP LOOKUP URL for the LDAP provider `my_ldap_provider`:

```
ALTER LDAP PROVIDER my_ldap_provider
 NESTED GROUP LOOKUP URL 'ldap://myhostname:389/ou=groupsOU,dc=x?sub?(member:1.2.840.113556.1.4.1941:=*)';
```

**Example 4:** Remove the NESTED GROUP LOOKUP URL setting for the LDAP provider`my_ldap_provider`, and add the ATTRIBUTE MEMBER\_OF setting instead:

```
ALTER LDAP PROVIDER my_ldap_provider
 NESTED GROUP LOOKUP URL NULL
 ATTRIBUTE MEMBER_OF 'memberOf';
```

**Example 5:** Enable automatic user creation for LDAP authentication:

```
ALTER LDAP PROVIDER my_ldap_provider ENABLE USER CREATION FOR LDAP;
```

**Example 6:** Change the user type for the new users to be auto-created with LDAP authentication to RESTRICTED:

```
ALTER LDAP PROVIDER my_ldap_provider
  ENABLE USER CREATION FOR LDAP USER TYPE RESTRICTED USERGROUP LDAP_USERS;
```

**Example 7:** Disable user creation for LDAP authentication:

```
ALTER LDAP PROVIDER my_ldap_provider DISABLE USER CREATION FOR LDAP;
```

**Related Information**  


[Certificate Management](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/1e6042c4402545f7a0574f7bc91fab25.html "SAP HANA uses public-key certificates as the basis for several user authentication mechanisms, and for securing internal and external communication channels. Certificates are stored and managed directly in the SAP HANA database.") :arrow_upper_right:

[CREATE LDAP PROVIDER Statement \(Access Control\)](create-ldap-provider-statement-access-control-3b72203.md "Creates an LDAP provider for use with LDAP authorization and authentication.")

[DROP LDAP PROVIDER Statement \(Access Control\)](drop-ldap-provider-statement-access-control-340e913.md "Drops an LDAP provider, and its associated credential, from the internal secure credential store.")

[VALIDATE LDAP PROVIDER Statement \(Access Control\)](validate-ldap-provider-statement-access-control-4181217.md "Validates an LDAP provider configuration and LDAP authentication and authorization for users of that LDAP provider.")

[LDAP\_PROVIDER\_URLS System View](../../020-System-Views-Reference/021-System-Views/ldap-provider-urls-system-view-7cf2869.md "Lists all LDAP provider URLs.")

[LDAP\_PROVIDERS System View](../../020-System-Views-Reference/021-System-Views/ldap-providers-system-view-5b54fe2.md "Lists all LDAP providers.")

[LDAP\_USERS System View](../../020-System-Views-Reference/021-System-Views/ldap-users-system-view-704e5b6.md "Provides information about the users using LDAP authorization.")

[LDAP User Authentication](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/868f8b988e2d42ccb89ccaf263cd9986.html "The Lightweight Directory Access Protocol (LDAP) is an application protocol for accessing directory services. If you use an LDAP-compliant directory server to manage users and their passwords, you can leverage LDAP-based authentication to access SAP HANA.") :arrow_upper_right:

[LDAP Group Authorization](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/f494db9664ba45af9bcdd88c7b342405.html "The Lightweight Directory Access Protocol (LDAP) is an application protocol for accessing directory services. If you use an LDAP-compliant directory server to manage users and their access to resources, you can leverage LDAP group membership to authorize SAP HANA database users.") :arrow_upper_right:

[Secure Communication Between SAP HANA and an LDAP Directory Server](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/b9086809b9bb466cbd15542430f2ebe6.html "Communication between the SAP HANA Cloud, SAP HANA database and an LDAP directory server must be secured.") :arrow_upper_right:

[Configuring LDAP Integration](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/03c98f3aade14b2c955a054833d90426.html "The Lightweight Directory Access Protocol (LDAP) is an application protocol for accessing directory services. If you use an LDAP-compliant directory server to manage users and their access to resources, you can leverage LDAP-based authentication to access SAP HANA and LDAP group membership to authorize users.") :arrow_upper_right:

