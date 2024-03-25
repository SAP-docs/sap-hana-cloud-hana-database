<!-- loio20d64db0751910149535843182bf8d86 -->

# DROP CREDENTIAL Statement \(Access Control\)

Drops an existing component-specific or application-specific credential.



<a name="loio20d64db0751910149535843182bf8d86__sql_drop_credential_1sql_drop_credential_syntax"/>

## Syntax

```
DROP CREDENTIAL FOR [USER <user_name>] COMPONENT <component_id>
   PURPOSE <purpose_def> TYPE <type_def>
```



<a name="loio20d64db0751910149535843182bf8d86__sql_drop_credential_1sql_drop_credential_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<user\_name\>*

</b></dt>
<dd>

Specifies the owner of the credential to be dropped.

```
<user_name> ::= <unicode_name>
```

Only users with the CREDENTIAL ADMIN system privilege can drop credentials for other users.

> ### Note:  
> When dropping a credential, it is crucial to specify the user component \[USER *<user\_name\>*\] consistently with how the credential was initially created. Credentials created with a specified user are distinct from those created without. To drop a credential successfully:
> 
> -   If the credential was created with a specified user, you must include the \[USER *<user\_name\>*\] component in the DROP CREDENTIAL statement.
> -   If the credential was created without specifying a user, the DROP CREDENTIAL statement should not include the \[USER *<user\_name\>*\] component. Only the credential without a user will be dropped in this case. Attempting to drop a credential without specifying a user, when it was created with one, will result in an error.



</dd><dt><b>

*<component\_id\>*

</b></dt>
<dd>

Specifies an identifier for the component that uses the credential.

```
<component_id> ::= <string_literal>
```



</dd><dt><b>

*<purpose\_def\>*

</b></dt>
<dd>

Specifies the application-specific or component-specific purpose string.

```
<purpose_def> ::= <string_literal>
```



</dd><dt><b>

*<type\_def\>*

</b></dt>
<dd>

Specifies a connection mechanism; for example 'PASSWORD'.

```
<type_def> ::= <string_literal>
```



</dd>
</dl>



<a name="loio20d64db0751910149535843182bf8d86__sql_drop_credential_1sql_drop_credential_description"/>

## Description

Each user can drop credentials that they own.





<a name="loio20d64db0751910149535843182bf8d86__section_opr_ddt_5cb"/>

## Permissions

This statement requires the CREDENTIAL ADMIN system privilege.



<a name="loio20d64db0751910149535843182bf8d86__sql_drop_credential_1sql_drop_credential_examples"/>

## Example

Create a credential for user WORKER that is used by the component INTERNAL\_APP. This credential uses the password mechanism for the PURPOSE COMPANY\_MASTER\_MACHINE.

```
CREATE CREDENTIAL FOR USER WORKER COMPONENT 'INTERNAL_APP' PURPOSE 'COMPANY_MASTER_MACHINE' TYPE 'PASSWORD' USING 'PASSWORD_9876';
```

Drop the credential.

```
DROP CREDENTIAL FOR USER WORKER COMPONENT 'INTERNAL_APP' PURPOSE 'COMPANY_MASTER_MACHINE' TYPE 'PASSWORD';
```

**Related Information**  


[CREDENTIALS System View](../../020-System-Views-Reference/021-System-Views/credentials-system-view-209fabf.md "Provides information about credentials for users and components.")

