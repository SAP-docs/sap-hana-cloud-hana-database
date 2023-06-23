<!-- loio20d04f7b751910148a98f145797d3482 -->

# ALTER SAML PROVIDER Statement \(Access Control\)

Changes the properties of the specified SAML provider.



<a name="loio20d04f7b751910148a98f145797d3482__sql_alter_saml_provider_1sql_alter_saml_provider_syntax"/>

## Syntax

```
ALTER SAML PROVIDER <saml_provider_name> 
 { <subject_issuer_clause> 
   | <entityid_clause>
   | <case_clause>
   | <application_user_clause>
   | <enable_disable_user_creation_clause>
 }
```



<a name="loio20d04f7b751910148a98f145797d3482__sql_alter_saml_provider_1sql_alter_saml_provider_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<saml\_provider\_name\>*

</b></dt>
<dd>

Specifies the SAML provider to alter.

```
<saml_provider_name> ::= <simple_identifier>
```



</dd>
</dl>


<dl>
<dt><b>

*<subject\_issuer\_clause\>*

</b></dt>
<dd>

Sets the SAML identity provider information.

```
<subject_issuer_clause> ::= 
   SET SUBJECT <subject_distinguished_name> ISSUER <issuer_distinguished_name>
```


<dl>
<dt><b>

*<subject\_distinguished\_name\>*

</b></dt>
<dd>

Specifies the subject name provided in the certificate of the SAML identity provider.

```
<subject_distinguished_name> ::= <string_literal>
```



</dd><dt><b>

*<issuer\_distinguished\_name\>*

</b></dt>
<dd>

Specifies the issuer name provided in the certificate of the SAML identity provider.

```
<issuer_distinguished_name> ::= <string_literal>
```



</dd>
</dl>



</dd><dt><b>

*<entityid\_clause\>*

</b></dt>
<dd>

Sets or unsets the entity ID of the SAML identity provider.

```
<entityid_clause> ::= [ UNSET ] ENTITY ID <string_literal>
```



</dd><dt><b>

*<case\_clause\>*

</b></dt>
<dd>

Specifies whether the user mapping is checked case sensitive \(default\) or insensitive.

```
<case_clause> ::= CASE { SENSITIVE | INSENSITIVE } IDENTITY 
```



</dd><dt><b>

*<application\_user\_clause\>*

</b></dt>
<dd>

Sets or unsets a value to be used as XS\_APPLICATIONUSER during login.

```
<application_user_clause> ::=
   { SET ATTRIBUTE <string_literal> AS APPLICATION USER 
     | UNSET APPLICATION USER ATTRIBUTE }
```



</dd><dt><b>

*<enable\_disable\_user\_creation\_clause\>*

</b></dt>
<dd>

Enables or disables automatic user creation for SAML authentication.

```
<enable_disable_user_creation_clause> ::=
 { ENABLE USER CREATION [ USER TYPE { STANDARD | RESTRICTED } ] 
       USERGROUP <usergroup_name> LDAP AUTHORIZATION
   | DISABLE USER CREATION 
 } 
```

When enabling automatic user creation, optionally specify the type of the new users to be created. By default, new users are created as STANDARD users. The user is created in the specified user group. The RESTRICTED user created using this clause is not automatically granted the PUBLIC role.



</dd>
</dl>



<a name="loio20d04f7b751910148a98f145797d3482__sql_alter_saml_provider_1sql_alter_saml_provider_description"/>

## Description

The SAML provider must already exist in the SAP HANA database.



<a name="loio20d04f7b751910148a98f145797d3482__section_wmn_r5x_vcb"/>

## Permissions

Requires the ALTER object privilege on the specific SAML provider.

To use the *<enable\_disable\_user\_creation\_clause\>* also requires the OPERATOR object privilege on the referenced USERGROUP.



<a name="loio20d04f7b751910148a98f145797d3482__sql_alter_saml_provider_1sql_alter_saml_provider_examples"/>

## Example

Create the ac\_saml\_provider SAML provider.

```
CREATE SAML PROVIDER ac_saml_provider
    WITH SUBJECT 'CN = wiki.detroit.ACompany.corp,OU = ACNet,O = ACompany,C = EN'
    ISSUER 'E = John.Do@acompany.com,CN = ACNetCA,OU = ACNet,O = ACompany,C = EN'
    ENTITY ID 'entity1';
```

View the currently defined SAML providers in the SAP HANA database.

```
SELECT * FROM sys.SAML_PROVIDERS;
```

Alter the ac\_saml\_provider.

```
ALTER SAML PROVIDER ac_saml_provider
        SET SUBJECT 'CN = wiki.detroit.BCompany.corp,OU = BCNet,O = BCompany,C = EN'
        ISSUER 'E = John.Do@acompany.com,CN = BCNetCA,OU = BCNet,O = BCompany,C = EN';
```

Make the case identity insensitive.

```
ALTER SAML PROVIDER ac_saml_provider CASE INSENSITIVE IDENTITY;
```

Remove the entity ID defined for the ac\_saml\_provider SAML provider.

```
ALTER SAML PROVIDER ac_saml_provider UNSET ENTITY ID;
```

Review the changes made to the ac\_saml\_provider SAML provider.

```
SELECT * FROM SYS.SAML_PROVIDERS;
```

**Related Information**  


[SAML\_PROVIDERS System View](../../020-System-Views-Reference/021-System-Views/saml-providers-system-view-20cda7b.md "Shows available SAML providers.")

[CREATE SAML PROVIDER Statement \(Access Control\)](create-saml-provider-statement-access-control-20d4cca.md "Defines a SAML provider in the SAP HANA database.")

