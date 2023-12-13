<!-- loio21026099751910148e0cdbddc75652b8 -->

# USERS System View

Lists all users.



<a name="loio21026099751910148e0cdbddc75652b8___u_s_e_r_s_1struct_USERS"/>

## Structure


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the user.

</td>
</tr>
<tr>
<td valign="top">

USER\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the ID of the user.

</td>
</tr>
<tr>
<td valign="top">

USERGROUP\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the user group that the user belongs to; otherwise, NULL.

</td>
</tr>
<tr>
<td valign="top">

USER\_MODE

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays the mode of the user: LOCAL/EXTERNAL.

</td>
</tr>
<tr>
<td valign="top">

EXTERNAL\_IDENTITY

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the external identity of the user.

</td>
</tr>
<tr>
<td valign="top">

CREATOR

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the creator of the user, SYSTEM, or the ID of a user with the privilege.

</td>
</tr>
<tr>
<td valign="top">

CREATE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the creation time.

</td>
</tr>
<tr>
<td valign="top">

VALID\_FROM

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the start time of the user's validity.

</td>
</tr>
<tr>
<td valign="top">

VALID\_UNTIL

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the end time of the user's validity.

</td>
</tr>
<tr>
<td valign="top">

LAST\_SUCCESSFUL\_CONNECT

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time of the last successful connection of the user.

</td>
</tr>
<tr>
<td valign="top">

LAST\_INVALID\_CONNECT\_ATTEMPT

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time of the last invalid connection attempt.

</td>
</tr>
<tr>
<td valign="top">

INVALID\_CONNECT\_ATTEMPTS

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of invalid connection attempts since the last successful connection.

</td>
</tr>
<tr>
<td valign="top">

ADMIN\_GIVEN\_PASSWORD

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the password was provided by the administrator or by the user: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

LAST\_PASSWORD\_CHANGE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time of the last password change.

</td>
</tr>
<tr>
<td valign="top">

PASSWORD\_CHANGE\_NEEDED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the user is forced to change their own password: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_PASSWORD\_LIFETIME\_CHECK\_ENABLED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the password-lifetime will be checked for the user: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

USER\_DEACTIVATED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the user is deactivated: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

DEACTIVATION\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time given with an explicit deactivation command for the specified user.

</td>
</tr>
<tr>
<td valign="top">

IS\_PASSWORD\_ENABLED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether authentication using a password is enabled: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_KERBEROS\_ENABLED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether authentication using KERBEROS is enabled: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_SAML\_ENABLED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether authentication using SAML is enabled: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_X509\_ENABLED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether authentication using an X.509 certificate is enabled: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_RESTRICTED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates whether the user is missing the PUBLIC role and privilege on their own schema: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_RESTRICTED\_DETAILS

</td>
<td valign="top">

NVARCHAR\(40\)

</td>
<td valign="top">

Displays the missing privilege\(s\): ROLE PUBLIC/CREATE ANY ON OWN SCHEMA.

</td>
</tr>
<tr>
<td valign="top">

IS\_CLIENT\_CONNECT\_ENABLED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the user is allowed to connect outside of applications: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

HAS\_REMOTE\_USERS

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the user has a remote identity mapping: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

AUTHORIZATION\_MODE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays the Authorization mode of the user: LOCAL/LDAP.

</td>
</tr>
<tr>
<td valign="top">

IS\_JWT\_ENABLED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether authentication using JWT is enabled: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_LDAP\_ENABLED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether authentication using LDAP is enabled:TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

CREATE\_PROVIDER\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

If the user was created by a provider using automatic user provisioning, then value indicates the type of provider: LDAP PROVIDER/SAML PROVIDER. If the user was created by another user \(using a CREATE USER statement\), then the value is NULL.

</td>
</tr>
<tr>
<td valign="top">

CREATE\_PROVIDER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the provider that created the user, or NULL if the user was created by a user \(using a CREATE USER statement\).

</td>
</tr>
</table>



<a name="loio21026099751910148e0cdbddc75652b8__section_cs2_cdb_x2b"/>

## Additional Information

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

Users see different values in this view depending on their privileges, as follows:

-   Users with on of the following privileges can see everything for all users: CATALOG READ, USERGROUP OPERATOR

-   All other users see only information specific to themselves.


**Related Information**  


[CREATE USER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-user-statement-access-control-20d5ddb.md "Creates a new database user.")

[ALTER USER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-user-statement-access-control-20d3459.md "Modifies the database user.")

[VALIDATE USER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/validate-user-statement-access-control-5e33634.md "Validates the credentials of a user in the current database.")

[DROP USER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-user-statement-access-control-20d8d33.md "Deletes a database user.")

[USERGROUPS System View](usergroups-system-view-ac342d0.md "Provides details on all user groups.")

[Managing SAP HANA Users](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/ed7af17e5ae14de694d9bee5f35098f4.html "Every user who wants to work with the SAP HANA database must have a database user who can log on and is authorized to perform their individual tasks.") :arrow_upper_right:

[User Provisioning](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/bebc1c98bb571014a119aa7e6763c7e1.html "Depending on your organization and its user provisioning strategy, people with different job functions may be involved in the process of provisioning users. If you use an LDAP-compliant directory server to manage users and their access to resources, you can leverage this infrastructure for user provisioning.") :arrow_upper_right:

[User Authorization](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/bd592d78bb57101499eabd0e17606802.html "After successful logon, the user's authorization to perform the requested operations on the requested objects is verified.") :arrow_upper_right:

