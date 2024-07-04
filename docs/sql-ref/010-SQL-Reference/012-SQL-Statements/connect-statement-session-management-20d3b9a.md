<!-- loio20d3b9ad751910148cdccc8205563a87 -->

# CONNECT Statement \(Session Management\)

Connects to a database instance.



<a name="loio20d3b9ad751910148cdccc8205563a87__sql_connect_1sql_connect_syntax"/>

## Syntax

```
CONNECT { <user_name> PASSWORD <password>
 | WITH SAML ASSERTION <xml>
 | WITH JWT <token> }
```



<a name="loio20d3b9ad751910148cdccc8205563a87__sql_connect_1sql_connect_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<user\_name\>*

</b></dt>
<dd>

Specifies the user name for the connection.

```
<user_name> ::= <unicode_name>
```



</dd><dt><b>

WITH SAML ASSERTION *<xml\>*

</b></dt>
<dd>

Specifies a SAML assertion to use when connecting to the database.

```
WITH SAML ASSERTION <xml>
 <xml> ::= <string_literal>
```



</dd><dt><b>

WITH JWT *<token\>*

</b></dt>
<dd>

Specifies a JWT token to use when connecting to the database.

```
WITH JWT <token>
 <token> ::= <string_literal>
```



</dd>
</dl>



<a name="loio20d3b9ad751910148cdccc8205563a87__sql_connect_1sql_connect_description"/>

## Description

Connects to a database instance using either a user name and password pair, JWT token, or a SAML assertion for identification.

Automatic LDAP user creation is not supported with the CONNECT statement.



<a name="loio20d3b9ad751910148cdccc8205563a87__section_m1v_ncv_rsb"/>

## Permissions

You do not require any privileges to execute this statement. However, execution will only succeed if all logon checks are successful.



<a name="loio20d3b9ad751910148cdccc8205563a87__sql_connect_1sql_connect_examples"/>

## Example

Connect to the database with the user name new\_user and password Password1.

```
CONNECT new_user PASSWORD Password1;
```

**Related Information**  


[Logon Checks](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/5992fc5aa48d43259e4f605be64760fe.html "Before a user can connect to an SAP HANA instance, the system performs several checks as part of the logon process.") :arrow_upper_right:

