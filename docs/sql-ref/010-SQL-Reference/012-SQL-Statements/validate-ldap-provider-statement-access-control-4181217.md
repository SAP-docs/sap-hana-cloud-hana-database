<!-- loio4181217e3e104c57a5090431c1cd70b7 -->

# VALIDATE LDAP PROVIDER Statement \(Access Control\)

Validates an LDAP provider configuration and LDAP authentication and authorization for users of that LDAP provider.



## Syntax

```
VALIDATE LDAP PROVIDER <ldap_provider_name> [ <validate_clause> ]
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



</dd><dt><b>

*<validate\_clause\>*

</b></dt>
<dd>

Specifies the type of validation to perform.

```
<validate_clause> ::=
 CHECK USER <user_name> [ PASSWORD <password_string_literal> | NO AUTHORIZATION CHECK ]

```

If this clause is not specified, then the statement is successful if SAP HANA can connect and bind to the named LDAP server using the credential of the access lookup account as configured in the LDAP provider.


<dl>
<dt><b>

CHECK USER *<user\_name\>*

</b></dt>
<dd>

Checks LDAP authorization for the user.

SAP HANA connects and binds to the named LDAP server and then performs the LDAP search using the USER LOOKUP URL specified for the LDAP provider after replacing '\*' with the specified *<user\_name\>* and after replacing the *<attributes\>* element of the URL with the attributes specified by DN and MEMBER\_OF \(if NESTED GROUP LOOKUP URL is not defined\). If NESTED GROUP LOOKUP URL is defined, then to obtain the user's LDAP group information, SAP HANA performs another LDAP search using NESTED GROUP LOOKUP URL after replacing '\*' with the DN of the user obtained from the USER LOOKUP URL search. This statement is successful if the user has at least one role with a mapping to LDAP groups obtained from a USER LOOKUP URL or NESTED GROUP LOOKUP URL search.



</dd><dt><b>

CHECK USER *<user\_name\>* PASSWORD *<password\_string\_literal\>* 

</b></dt>
<dd>

Checks LDAP authentication for the user.

SAP HANA connects and binds to the named LDAP server and then performs the LDAP search using the USER LOOKUP URL specified for the LDAP provider after replacing '\*' with the specified *<user\_name\>* and after replacing the <attributes\> element of the URL with the attribute specified by DN. The search is performed and if no errors occur, then the result value for the DN and the value of password are used to again connect to the LDAP server. When the connection with DN and password is successful, this is successful authentication of the user.



</dd><dt><b>

CHECK USER *<username\>* NO AUTHORIZATION CHECK

</b></dt>
<dd>

Checks whether the user exists in LDAP; that is, neither an LDAP authorization nor an LDAP authentication check is done.

SAP HANA connects and binds to the named LDAP server and then performs the LDAP search using the USER LOOKUP URL specified for the LDAP provider after replacing '\*' with the specified *<user\_name\>* and after replacing the <attributes\> element of the URL with the attribute specified by DN. The search is performed and if no errors occur, then this successfully verifies that the user exists on the LDAP server. This is useful when authorization checking is not to be done or the user’s password is unknown, since it validates the user existence on the LDAP server and validates the values specified in the LDAP provider.



</dd>
</dl>



</dd>
</dl>



## Description

Validates an LDAP provider configuration and LDAP authentication and authorization for users of that LDAP provider.



<a name="loio4181217e3e104c57a5090431c1cd70b7__section_ffz_ftc_pbb"/>

## Permissions

Only users with the LDAP ADMIN system privilege can execute the VALIDATE LDAP PROVIDER statement.



## Examples

**EXAMPLE 1:** The following statement causes SAP HANA to perform the validation steps listed after the statement.

```
VALIDATE LDAP PROVIDER my_ldap_provider CHECK USER johnd;
```

1.  Check that USER LOOKUP URL is a valid URL, and that either ATTRIBUTE MEMBER\_OF is defined or NESTED GROUP LOOOKUP URL is defined and is a valid URL.

2.  Bind to the LDAP server specified in the USER LOOKUP URL using the access account credentials specified in the provider.

3.  Search for user 'johnd' using the USER LOOKUP URL to obtain the users's distinguished name from the LDAP server.

4.  Obtain the user's LDAP group membership from the LDAP server. Find matching roles based on the user's LDAP groups and mapping entries in the SAP HANA server between SAP HANA roles in LDAP groups.


A successful return validates the configuration of the LDAP provider for LDAP authorization, and that the user exists in LDAP server and that the user has at least one role in SAP HANA that can be granted to the user based on user's LDAP group membership in LDAP server and role to LDAP group mapping in SAP HANA.

**EXAMPLE 2:** The following statement causes SAP HANA to perform the validation steps listed after the statement.

```
VALIDATE LDAP PROVIDER my_ldap_provider CHECK USER testuser1 PASSWORD 'Sap123456';
```

1.  Check that the USER LOOKUP URL is a valid LDAP URL.

2.  Bind to the LDAP server specified in the USER LOOKUP URL using the access account credentials specified in the provider.

3.  Search for user 'testuser1' using the USER LOOKUP URL to obtain user's distinguished name from the LDAP server.

4.  Bind to the LDAP server specified in the USER LOOKUP URL using the user's distinguished name and the specified password.


A successful return validates the configuration of the LDAP provider for LDAP authentication and that the user exists in the LDAP server and can successfully bind to the LDAP server using the specified password.

**EXAMPLE 3:** The following statement causes SAP HANA to perform the validation steps listed after the statement.

```
VALIDATE LDAP PROVIDER my_ldap_provider CHECK USER testuser2 NO AUTHORIZATION CHECK;
```

1.  Check that the USER LOOKUP URL is a valid LDAP URL.

2.  Bind to the LDAP server specified in USER LOOKUP URL using the access account credentials specified in the provider.

3.  Search for user 'testuser2' using the USER LOOKUP URL to obtain user's distinguished name from the LDAP server.


A successful return validates the configuration of the LDAP provider and that the user exists in the LDAP server.

**Related Information**  


[CREATE LDAP PROVIDER Statement \(Access Control\)](create-ldap-provider-statement-access-control-3b72203.md "Creates an LDAP provider for use with LDAP authorization and authentication.")

[ALTER LDAP PROVIDER Statement \(Access Control\)](alter-ldap-provider-statement-access-control-ae9ba28.md "Updates an LDAP provider for use with LDAP authorization and authentication.")

[DROP LDAP PROVIDER Statement \(Access Control\)](drop-ldap-provider-statement-access-control-340e913.md "Drops an LDAP provider, and its associated credential, from the internal secure credential store.")

[LDAP\_PROVIDER\_URLS System View](../../020-System-Views-Reference/021-System-Views/ldap-provider-urls-system-view-7cf2869.md "Lists all LDAP provider URLs.")

[LDAP\_PROVIDERS System View](../../020-System-Views-Reference/021-System-Views/ldap-providers-system-view-5b54fe2.md "Lists all LDAP providers.")

[LDAP\_USERS System View](../../020-System-Views-Reference/021-System-Views/ldap-users-system-view-704e5b6.md "Provides information about the users using LDAP authorization.")

