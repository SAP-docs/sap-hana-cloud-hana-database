<!-- loio20cfdad57519101482fcb19af478ec34 -->

# ALTER CREDENTIAL Statement \(Access Control\)

Modifies an existing component-specific or application-specific credential.



<a name="loio20cfdad57519101482fcb19af478ec34__sql_alter_credential_1sql_alter_credential_syntax"/>

## Syntax

```
ALTER CREDENTIAL FOR [USER <user_name>] COMPONENT <component_id>
   PURPOSE <purpose_def> TYPE <type_def> [USING <using_param>]
```



<a name="loio20cfdad57519101482fcb19af478ec34__sql_alter_credential_1sql_alter_credential_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<user\_name\>*

</b></dt>
<dd>

Specifies the user that owns the credential.

```
<user_name> ::= <unicode_name>
```

Only users with the CREDENTIAL ADMIN system privilege are allowed to alter credentials for other users.



</dd>
</dl>


<dl>
<dt><b>

*<component\_id\>*

</b></dt>
<dd>

Specifies an identifier for the component that uses the credential.

```
<component_id> ::= <string_literal>
```



</dd>
</dl>


<dl>
<dt><b>

*<purpose\_def\>*

</b></dt>
<dd>

Specifies the application-specific or component-specific purpose string.

```
<purpose_def> ::= <string_literal>
```



</dd>
</dl>


<dl>
<dt><b>

*<type\_def\>*

</b></dt>
<dd>

Specifies a connection mechanism. For data lake Files, *<type\_def\>* must be X509. For all other components, *<type\_def\>* must be 'PASSWORD' or 'KERBEROS'.

```
<type_def> ::= <string_literal>
```



</dd><dt><b>

*<using\_param\>*

</b></dt>
<dd>

Specifies the credentials for the connection parameter. The USING *<using\_param\>* parameter is only required when the component is SAPHANAIMPORTEXPORT and the *<type\_def\>* is PASSWORD.

```
<using_param> ::=
   { <azure_credentials>
   | <amazon_credentials>
   | <google_credentials>
   | <hdlfs_creadentials>
   | <string_literal> }
```


<dl>
<dt><b>

*<azure\_credentials\>*

</b></dt>
<dd>

```
<azure_credentials> ::= 
   'USER=<azure_storage_account_name>;PASSWORD=<SAS-token>'
```



</dd><dt><b>

*<amazon\_credentials\>*

</b></dt>
<dd>

```
<amazon_credentials> ::=
   'USER=<amazon_access_key>;PASSWORD=<amazon_secret_key>'
```



</dd><dt><b>

*<google\_credentials\>*

</b></dt>
<dd>

```
<google_credentials> ::=
   'USER=<google_service_account>;PASSWORD=<google_private_key>'
```



</dd><dt><b>

*<hdlfs\_creadentials\>*

</b></dt>
<dd>

```
<hdlfs_creadentials> ::= TYPE 'X509'
```



</dd>
</dl>



</dd>
</dl>



<a name="loio20cfdad57519101482fcb19af478ec34__sql_alter_credential_1sql_alter_credential_description"/>

## Description

Only the credentials can be changed using this command. Each user can alter their own credentials.



<a name="loio20cfdad57519101482fcb19af478ec34__section_opr_ddt_5cb"/>

## Permissions

You must have the CREDENTIAL ADMIN system privilege to modify a credential.



<a name="loio20cfdad57519101482fcb19af478ec34__sql_alter_credential_1sql_alter_credential_examples"/>

## Example

Create a credential for all users that is used by the component INTERNAL\_APP. This credential uses the password mechanism for the purpose COMPANY\_MASTER\_MACHINE.

```
CREATE CREDENTIAL FOR COMPONENT 'INTERNAL_APP' PURPOSE 'COMPANY_MASTER_MACHINE' TYPE 'PASSWORD' USING 'PASSWORD_9876';
```

Change the password of the credential created in the previous step.

```
ALTER CREDENTIAL FOR COMPONENT 'INTERNAL_APP' PURPOSE 'COMPANY_MASTER_MACHINE' TYPE 'PASSWORD' USING '1234_PASSWORD';
```

**Related Information**  


[CREDENTIALS System View](../../020-System-Views-Reference/021-System-Views/credentials-system-view-209fabf.md "Provides information about credentials for users and components.")

