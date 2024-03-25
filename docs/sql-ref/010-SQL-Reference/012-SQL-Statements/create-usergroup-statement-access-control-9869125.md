<!-- loio9869125ea93548009820702f5bd897d8 -->

# CREATE USERGROUP Statement \(Access Control\)

Creates a usergroup.



## Syntax

```
CREATE USERGROUP <usergroup_name>
 [ NO GRANT TO CREATOR ]
 [ SET PARAMETER <parameter_key_value_list> ]
 [ { ENABLE | DISABLE } PARAMETER SET <parameter_set_name> ]
 [ DISABLE CLIENT CONNECT ]
 [ CONNECT RESTRICTION <connect_restriction_list> ]
```



<a name="loio9869125ea93548009820702f5bd897d8__section_nrq_3hm_nz"/>

## Syntax Elements


<dl>
<dt><b>

*<usergroup\_name\>*

</b></dt>
<dd>

Specifies a name for the user group. *<usergroup\_name\>* cannot match the name of an existing user, user group, role, or role group.



</dd><dt><b>

NO GRANT TO CREATOR

</b></dt>
<dd>

Prevents the automatic granting of all object privileges of the usergroup to the user creating the usergroup. When you create a usergroup, you are not automatically granted the USERGROUP OPERATOR privilege on that user group if you use this clause. This clause makes the usergroup unmanageable. You would need to drop the usergroup and create it again without the NO GRANT TO CREATOR syntax.



</dd><dt><b>

SET PARAMETER *<parameter\_key\_value\_list\>*

</b></dt>
<dd>

Configures parameter options as a key-value list for a parameter set that can be enabled and disabled for the group. Specifically, use this clause to configure group-specific values for the individual options of the password policy set called 'password policy'.

```
<parameter_key_value_list> ::= <key_value_pair> [,<key_value_pair> [,…] ]

<key_value_pair> ::= '<parameter_name>'='<value>'
```

When the SET PARAMETER clause is used to specify password policy options, all policy option settings are stored for the usergroup. However, this does not mean you need to specify all of the password policy options. Password policy options that are not specified in the SET PARAMETER clause are copied from the current system-wide password policy settings and stored with the specified options for the usergroup. Subsequent changes to the system-wide settings do not impact any stored password policy options for the usergroup. Refer to the *SAP HANA Cloud, SAP HANA Database Security Guide* for the list of password policy configuration options and password exclude lists you can set.

Once you set the parameter set options, use a ALTER USERGROUP...SET PARAMETER statement to alter specific parameter settings without impacting other parameter settings that have been set.



</dd><dt><b>

\{ENABLE | DISABLE \} PARAMETER SET *<parameter\_set\_name\>*

</b></dt>
<dd>

Enables or disables the specified parameter set. If not specified, the default is ENABLED. The only supported parameter set name is 'password policy'.

```
<parameter_set_name> ::= 'password policy'
```

Enabling the password policy parameter causes any password policy options that have been defined to be applied. If disabled, any password policy options configured using the SET PARAMETER clause remain configured for the usergroup, but are not applied. If a parameter set is enabled before any parameters have been set, then all parameter values are identical to the current system wide settings.



</dd><dt><b>

DISABLE CLIENT CONNECT

</b></dt>
<dd>

Prevents users in the usergroup from connecting to the database. If DISABLE CLIENT CONNECT is set for a usergroup, no user of that group can connect, even if the connect is allowed by connect restrictions.



</dd><dt><b>

CONNECT RESTRICTION

</b></dt>
<dd>

Specifies the list of restrictions under which a connection is allowed. Members of the user group are only allowed to log in if the connection attempt satisfies at least one of the active connection restrictions.

By default, a new the connection restriction is disabled. Use the ALTER USERGROUP statement to enable the restriction. A single *<connect\_restriction\>* can contain both application and IP conditions.

```
<connect_restriction_list> ::
	<connect_restriction> | (<connect_restriction>, ...)
<connect_restriction> ::
	<restriction_name> [ <client_ip_restriction > ][ <application_restriction> ]
```

*<restriction\_name\>* is a unique name that identifies the set of restricted connections.

IP restrictions define which IP addresses or address ranges are allowed to connect. IP addresses/ranges can be specified as IPv4 or IPv6 addresses in CIDR notation.

```
<client_ip_restriction> ::
    IP  <ip_address> | ( <ip_address>, ... ) 
```

APPLICATION and APPLICATION ALLOW are equivalent. APPLICATION \[ALLOW\] and APPLICATION DENY conditions cannot be used in the same restriction.

> ### Note:  
> Application-based connect restrictions rely on the value of the APPLICATION session property which is set on the client side. This means a client could work around these restrictions by configuring the APPLICATION session property on the client. However, application-based connect restrictions can allow/exclude applications that self-manage the APPLICATION session property so that the user cannot influence it.

```
<application_restriction> ::= 
   APPLICATION  [ALLOW | DENY  <application_name_list> ]

<application_name_list> ::=
    <application_name> | ( <application_name>[, ...] ) 
```



</dd>
</dl>



<a name="loio9869125ea93548009820702f5bd897d8__section_ydr_jhm_nz"/>

## Description

You add users to a user group by using the CREATE USER and ALTER USER statements.

To see the current password policy settings for a user, use the M\_EFFECTIVE\_PASSWORD\_POLICY system view.

To see a list of connection restrictions by user group, see the USERGROUP\_CONNECT\_RESTRICTIONS system view.



<a name="loio9869125ea93548009820702f5bd897d8__section_u4g_lyc_pbb"/>

## Permissions

You must have the CREATE USERGROUP system privilege.



<a name="loio9869125ea93548009820702f5bd897d8__section_kwk_mhm_nz"/>

## Example

The following example creates a usergroup called MyUserGroup and sets several password policy options for the usergroup:

```
CREATE USERGROUP MyUserGroup SET PARAMETER 'password_layout' = 'A1a!', 'minimal_password_length' = '16' ENABLE PARAMETER SET 'password policy';
```

The following example creates a usergroup called MyUserGroup and disables connections to the database by its members:

```
CREATE USERGROUP MyUserGroup DISABLE CLIENT CONNECT;
```

The following example creates a usergroup called TechnicalUsers and defines two connect restrictions named 'internal\_network\_not\_interactive' on IP addresses and applications to only allow access from an internal network and deny typical interactive applications to connect. The second connect restriction 'jumphost' allows full access from a dedicated IP address:

```
CREATE USERGROUP "TechnicalUsers" CONNECT RESTRICTION ("internal_not_interactive" IP ('10.0.0.0/24', 'fd00::/8') APPLICATION DENY ('hdbsql', 'SAP_HANARuntimeTools_HRA')) 

ALTER USERGROUP "TechnicalUsers" ADD CONNECT RESTRICTION ("jumphost" IP ('1.2.3.4'))
```

The following example creates and defines the usergroup and connect restrictions in the above example in one statement:

```
CREATE USERGROUP "TechnicalUsers" CONNECT RESTRICTION ("internal_not_interactive" IP ('10.0.0.0/24', 'fd00::/8') APPLICATION DENY ('hdbsql', 'SAP_HANARuntimeTools_HRA'), "jumphost" IP ('1.2.3.4'))
```

Connect restrictions are by default disabled on creation and must be enabled:

```
ALTER USERGROUP "TechnicalUsers" ENABLE CONNECT RESTRICTION "internal_not_interactive", "jumphost" 
```

**Related Information**  


[User Groups](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/b9174d035f274ce481387700c13b7d2c.html "User groups support a separation of user management tasks, allowing you to manage related users together.") :arrow_upper_right:

[Password Policy Configuration Options](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/61662e3032ad4f8dbdb5063a21a7d706.html "The password policy of the database is defined by parameters in the password policy section of the indexserver.ini configuration file. The initial password policy of a user group is a copy of the database password policy.") :arrow_upper_right:

[Password Exclude List](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/fe3ffb3d7ac24fddb80e3322c671299f.html "A password exclude list is a list of words that are not allowed as passwords or parts of passwords. A password exclude list can be managed for every database individually.") :arrow_upper_right:

[ALTER USERGROUP Statement \(Access Control\)](alter-usergroup-statement-access-control-aa94ca8.md "Alters a usergroup.")

[DROP USERGROUP Statement \(Access Control\)](drop-usergroup-statement-access-control-6dc0ada.md "Removes a user group from the database.")

[GRANT Statement \(Access Control\)](grant-statement-access-control-20f674e.md "Grants various types of privileges to users and roles.")

[USERGROUPS System View](../../020-System-Views-Reference/021-System-Views/usergroups-system-view-ac342d0.md "Provides details on all user groups.")

[USERS System View](../../020-System-Views-Reference/021-System-Views/users-system-view-2102609.md "Lists all users.")

[CREATE USER Statement \(Access Control\)](create-user-statement-access-control-20d5ddb.md "Creates a new database user.")

[USERGROUP\_PARAMETERS System View](../../020-System-Views-Reference/021-System-Views/usergroup-parameters-system-view-365bd21.md "Provides the list of parameter sets defined for usergroups.")

[M\_EFFECTIVE\_PASSWORD\_POLICY System View](../../020-System-Views-Reference/022-Monitoring-Views/m-effective-password-policy-system-view-388378c.md "Provides information about password policy parameters for database users.")

[USERGROUP\_CONNECT\_RESTRICTIONS System View](../../020-System-Views-Reference/021-System-Views/usergroup-connect-restrictions-system-view-57d3364.md "Provides details on connection restrictions for all user groups.")

[VALIDATE\_USERGROUP\_CONNECT\_RESTRICTION Function \(Security\)](../011-SQL-Functions/validate-usergroup-connect-restriction-function-security-c7a96e0.md "Displays whether a connect attempt would be possible given the active connect restrictions of a user group.")

[VALIDATE\_USERGROUP\_CONNECT\_RESTRICTION\_DETAILS Function \(Security\)](../011-SQL-Functions/validate-usergroup-connect-restriction-details-function-security-508e173.md "Displays details of each connect restriction if a login were allowed for a specific condition.")

