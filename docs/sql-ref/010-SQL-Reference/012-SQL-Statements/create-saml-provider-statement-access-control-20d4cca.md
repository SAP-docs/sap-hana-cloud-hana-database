<!-- loio20d4cca075191014824eeda2cbba6445 -->

# CREATE SAML PROVIDER Statement \(Access Control\)

Defines a SAML provider in the SAP HANA database.



<a name="loio20d4cca075191014824eeda2cbba6445__sql_create_saml_provider_1sql_create_saml_provider_syntax"/>

## Syntax

```
CREATE SAML PROVIDER <saml_provider_name> <subject_issuer_clause>
   [ <entityid_clause> ]
   [ <case_clause> ] 
   [ <application_user_clause> ]
   [ <enable_user_creation_clause> ]
```



<a name="loio20d4cca075191014824eeda2cbba6445__sql_create_saml_provider_1sql_create_saml_provider_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<saml\_provider\_name\>*

</b></dt>
<dd>

Specifies the identifier of a SAML provider to be created.

```
<saml_provider_name> ::= <simple_identifier>
```

The SAML provider name must not already be defined.



</dd><dt><b>

*<subject\_issuer\_clause\>*

</b></dt>
<dd>

Sets SAML identity provider information.

```
<subject_issuer_clause> ::= 
   WITH SUBJECT <subject_distinguished_name> ISSUER <issuer_distinguished_name>
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

Specifies the entity ID of the SAML identity provider.

```
<entityid_clause> ::= ENTITY ID <string_literal>
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

Specifies a value to be used as XS\_APPLICATIONUSER during login.

```
<application_user_clause> ::=
   ATTRIBUTE <string_literal> AS APPLICATION USER ]
```



</dd><dt><b>

*<enable\_user\_creation\_clause\>*

</b></dt>
<dd>

Enables automatic user creation when using SAML authentication, and specifies type of the user to create - standard or restricted.

```
<enable_user_creation_clause> ::= 
   ENABLE USER CREATION [ USER TYPE { STANDARD | RESTRICTED } ] 
   USERGROUP <usergroup_name> 
   LDAP AUTHORIZATION
```

When enabling automatic user creation, optionally specify the type of the new users to be created. By default, new users are created as STANDARD users. The user is created in the specified user group. The RESTRICTED user created using this clause is not automatically granted the PUBLIC role.



</dd>
</dl>



<a name="loio20d4cca075191014824eeda2cbba6445__sql_create_saml_provider_1sql_create_saml_provider_description"/>

## Description

A SAML provider is required to provide a SAML connection facility for users.

The *<subject\_distinguished\_name\>* and the *<issuer\_distinguished\_name\>* correspond to the subject and issuer of the X.509 certificate used by the SAML identity provider to sign assertions. The syntax of these names can be found in ISO/IEC 9594-1.

A detailed description of the concepts of SAML can be found in Oasis SAML 2.0.



<a name="loio20d4cca075191014824eeda2cbba6445__section_zxd_hwx_vcb"/>

## Permissions

Only database users with the CREATE SAML PROVIDER system privilege can create a SAML provider.

To use the *<enable\_user\_creation\_clause\>* also requires the OPERATOR object privilege on the referenced USERGROUP.



<a name="loio20d4cca075191014824eeda2cbba6445__sql_create_saml_provider_1sql_create_saml_provider_examples"/>

## Example

Create a SAML provider with the name ac\_saml\_provider in the database specifying the subject and issuer to belong to ACompany. The entity ID is entity1. The identity checked by the provider is case sensitive.

```
CREATE SAML PROVIDER ac_saml_provider 
    WITH SUBJECT 'CN = wiki.detroit.ACompany.corp,OU = ACNet,O = ACompany,C = EN' 
    ISSUER 'E = John.Do@acompany.com,CN = ACNetCA,OU = ACNet,O = ACompany,C = EN'
    ENTITY ID 'entity1' CASE SENSITIVE IDENTITY
    ATTRIBUTE 'email' AS APPLICATION USER;
```

**Related Information**  


[SAML\_PROVIDERS System View](../../020-System-Views-Reference/021-System-Views/saml-providers-system-view-20cda7b.md "Shows available SAML providers.")

[Single Sign-On Using SAML 2.0](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/db6db355bb571014b56eb25057daec5f.html "SAP HANA supports the Security Assertion Markup Language (SAML) for user authentication in single sign-on environments. SAML is used for authentication purposes only and not for authorization.") :arrow_upper_right:

