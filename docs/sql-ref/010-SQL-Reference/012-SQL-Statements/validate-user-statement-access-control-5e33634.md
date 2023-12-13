<!-- loio5e336347cb8444279b451c172ad00c75 -->

# VALIDATE USER Statement \(Access Control\)

Validates the credentials of a user in the current database.



<a name="loio5e336347cb8444279b451c172ad00c75__section_o2z_gt3_1z"/>

## Syntax

```
VALIDATE USER { <user_name> PASSWORD <password> | WITH ASSERTION <assertion> }
```



<a name="loio5e336347cb8444279b451c172ad00c75__section_p2z_gt3_1z"/>

## Syntax Elements


<dl>
<dt><b>

*<user\_name\>*

</b></dt>
<dd>

Specifies the identifier for the credentials being validated.



</dd><dt><b>

*<password\>*

</b></dt>
<dd>

Specifies the password for the credentials being validated.



</dd><dt><b>

assertion

</b></dt>
<dd>

Specifies a valid ticket for a single-sign on service such as SAML and JWT.



</dd>
</dl>



<a name="loio5e336347cb8444279b451c172ad00c75__section_q2z_gt3_1z"/>

## Description

VALIDATE USER can be used to validate the credentials for a user in the current database without causing a login using the credentials.

When validation fails, an error is returned indicating that authentication failed. The error does not indicate whether the failure is because *<user\_name\>* does not exist or because the specified *<password\>* does not match the current password for *<user\_name\>*.

After successful validation, the user name can be found in the session variable VALIDATE\_USER\_NAME.



<a name="loio5e336347cb8444279b451c172ad00c75__section_r2z_gt3_1z"/>

## Examples

The following example validates the credentials of user `JSmith` and returns a message indicating that the statement executed successfully \(`JSmith` is a valid user\):

```
CREATE USER JSmith PASSWORD shg8475ghh11;
VALIDATE USER JSmith PASSWORD shg8475ghh11;
```

The following example returns an error indicating that validation of user `T12345` failed. Although the error does not indicate whether it failed because the user name doesn't exist or whether the password is incorrect, you can see from the example that the reason is because the password specified in the VALIDATE USER statement doesn't match the user's password:

```
CREATE USER T12345 PASSWORD suelg75sjh;
VALIDATE USER T12345 PASSWORD shgi33shi;
```

The following example returns an error indicating that validation failed \(because the user `BJones` has not been created in this example\):

```
VALIDATE USER BJones PASSWORD 34875hgj75;
```

