<!-- loio20d8d33275191014adce9c099eeed35c -->

# DROP USER Statement \(Access Control\)

Deletes a database user.



<a name="loio20d8d33275191014adce9c099eeed35c__sql_drop_user_1sql_drop_user_syntax"/>

## Syntax

```
DROP USER <user_name> [<drop_option>]
```



<a name="loio20d8d33275191014adce9c099eeed35c__sql_drop_user_1sql_drop_user_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<user\_name\>*

</b></dt>
<dd>

Drops the specified user.

```
<user_name> ::= <unicode_name>
```

*<user\_name\>* must specify an existing database user.



</dd><dt><b>

*<drop\_option\>*

</b></dt>
<dd>

Specifies the drop option to use.

```
<drop_option> ::= CASCADE | RESTRICT
```

CASCADE drops the user and performs the following actions:

-   Drops the user's home schema and other schemas belonging to the user, together with all objects stored in them regardless of which user created them.

-   Drops all objects owned by the user, even if they are part of another schema.

-   Drops objects that are dependent on deleted objects and that are owned by the user being dropped.

-   Invalidates objects that are dependent on deleted objects and that are owned by a different user in a schema not belonging to the user being dropped.

-   Drops public synonyms that are owned by the user being dropped.

-   Revokes privileges on deleted objects.

-   Revokes privileges granted by the deleted user. Revoked privileges may cause further revokes if the privileges have been granted further.


RESTRICT drops the user only if they don’t own any schemas or objects other than their home schema. If RESTRICT is specified while the user owns any objects, then an error is returned.

When *<drop\_option\>* is not specified, RESTRICT is used by default.



</dd>
</dl>



<a name="loio20d8d33275191014adce9c099eeed35c__sql_drop_user_1sql_drop_user_description"/>

## Description

Do not attempt to delete internal users such as DBADMIN, as unintended side effects can occur.

Users created by the deleted user and roles created by them are not deleted.

Audit policies created by the deleted user are not deleted.

It is possible to delete a user even if an open session for this user exists.

The deleted user is deleted in the following views: USERS, USER\_PARAMETERS, INVALID\_CONNECT\_ATTEMPTS

The deletion of objects influence all of the system views describing objects: TABLES, VIEWS, PROCEDURES, and so on.

The deletion of objects influence the view describing privileges like GRANTED\_PRIVILEGES and all of the monitoring views like M\_RS\_TABLES, M\_TABLE\_LOCATIONS, and so on.



<a name="loio20d8d33275191014adce9c099eeed35c__section_pbd_b3h_qbb"/>

## Permissions

You must have the OPERATOR object privilege for the user group that the user is in.



<a name="loio20d8d33275191014adce9c099eeed35c__sql_drop_user_1sql_drop_user_examples"/>

## Example

Create a new user called new\_user.

```
CREATE USER new_user PASSWORD Password1;
```

Drop the user new\_user you created in the previous step. As the CASCADE option is used, the user is dropped together with all of the objects belonging to that user.

```
DROP USER new_user CASCADE;
```

**Related Information**  


[USERS System View](../../020-System-Views-Reference/021-System-Views/users-system-view-2102609.md "Lists all users.")

[USER\_PARAMETERS System View](../../020-System-Views-Reference/021-System-Views/user-parameters-system-view-2102244.md "Lists all parameters and their values, which have been assigned to users in the system (using CREATE USER ... SET PARAMETER or ALTER USER ... SET PARAMETER).")

[INVALID\_CONNECT\_ATTEMPTS System View](../../020-System-Views-Reference/021-System-Views/invalid-connect-attempts-system-view-ea60f23.md "Provides the number of invalid connection attempts for a user between two successful connections.")

[M\_RS\_TABLES System View](../../020-System-Views-Reference/022-Monitoring-Views/m-rs-tables-system-view-20bbc60.md "Provides information about row tables, including detailed table sizes and record count.")

[M\_TABLE\_LOCATIONS System View](../../020-System-Views-Reference/022-Monitoring-Views/m-table-locations-system-view-20c65d5.md "Provides information about tables and their logical location. Physical locations are shown in M_TABLE_PERSISTENCE_LOCATIONS.")

[User Groups](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/b9174d035f274ce481387700c13b7d2c.html "User groups support a separation of user management tasks, allowing you to manage related users together.") :arrow_upper_right:

