<!-- loioaa94ca874c01458da5a275aac8883c23 -->

# ALTER USERGROUP Statement \(Access Control\)

Alters a usergroup.



<a name="loioaa94ca874c01458da5a275aac8883c23__section_vtw_rhm_nz"/>

## Syntax

```
ALTER USERGROUP <usergroup_name>
 [ SET PARAMETER <parameter_key_value_list> ]
 [ CLEAR PARAMETER <parameter_name_list> ]
 [ { ENABLE | DISABLE } PARAMETER SET <parameter_set_name> ]
 [ { ENABLE | DISABLE } CLIENT CONNECT
 [ { ENABLE | DISABLE } CONNECT RESTRICTION { <restriction_name>[, ...] | ALL } ]
 [ DROP CONNECT RESTRICTION { <restriction_name>[, ...] | ALL } ]
 [ { ADD | ALTER } CONNECT RESTRICTION <connect_restriction_list> ]
```



<a name="loioaa94ca874c01458da5a275aac8883c23__section_nrq_3hm_nz"/>

## Syntax Elements


<dl>
<dt><b>

*<usergroup\_name\>*

</b></dt>
<dd>

Specifies the name of the usergroup.



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

CLEAR PARAMETER *<parameter\_name\_list\>*

</b></dt>
<dd>

Resets the specified parameter\(s\) to the current system-wide setting.

```
<parameter_name_list> ::= <parameter_name> [, <parameter_name> [,..] ]
```



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

DISABLE PARAMETER SET *<parameter\_set\_name\>*

</b></dt>
<dd>

Disables the specified parameter set. Parameters that have been set remain stored for the usergroup but are not applied. The only supported parameter set name is 'password policy'.

```
<parameter_set_name> ::= 'password policy'
```



</dd><dt><b>

ENABLE / DISABLE CLIENT CONNECT

</b></dt>
<dd>

Allows or prevents users in the usergroup from connecting to the database. You cannot disable client connections to the usergroup you are a member of.



</dd><dt><b>

ENABLE / DISABLE CONNECT RESTRICTION

</b></dt>
<dd>

Enables or disables the named connect restrictions for the usergroup. If ALL is specified, then all connect restrictions of the usergroup are enabled or disabled. By default, a new connect restriction is disabled and must be enabled before it can be used.



</dd><dt><b>

DROP CONNECT RESTRICTION

</b></dt>
<dd>

Removes named connection restrictions for an existing usergroup.



</dd><dt><b>

ADD / ALTER CONNECT RESTRICTION

</b></dt>
<dd>

Adds a new or overrides an existing connect restriction definition for an existing usergroup.

For more information, see *CREATE USERGROUP* in *SAP HANA Cloud, SAP HANA Database SQL Reference Guide*.



</dd>
</dl>



<a name="loioaa94ca874c01458da5a275aac8883c23__section_ydr_jhm_nz"/>

## Description

To see the group-specific values of parameters, use the USERGROUP\_PARAMETERS system view. To see which values are currently in effect for a particular user, use the M\_EFFECTIVE\_PASSWORD\_POLICY system view.

You add users to a user group using the CREATE USER statement.

To see the current password policy settings for a user, use the M\_EFFECTIVE\_PASSWORD\_POLICY system view.

To see a list of connection restrictions by user group, see the USERGROUP\_CONNECT\_RESTRICTIONS system view.



<a name="loioaa94ca874c01458da5a275aac8883c23__section_v44_3b2_pbb"/>

## Permissions

You must have the OPERATOR object privilege on the user group.



<a name="loioaa94ca874c01458da5a275aac8883c23__section_kwk_mhm_nz"/>

## Examples

The following example disables the password policy parameter set for the MyUserGroup usergroup:

```
ALTER USERGROUP "MyUserGroup" DISABLE PARAMETER SET 'password policy';
```

This example enables an existing connect restriction IPS\_4 for USERGROUP:

```
ALTER USERGROUP usergroup ENABLE CONNECT RESTRICTION IPS_V4;
```

This example disables all connect restrictions for USERGROUP:

```
ALTER USERGROUP usergroup DISABLE CONNECT RESTRICTION ALL;
```

This example changes the IP/network addresses for the existing named connection restriction IPS\_V4 and IPS\_V6 for USERGROUP:

```
ALTER USERGROUP Usergroup1 ALTER CONNECT RESTRICTION (IPS_V4 IP ('1.2.3.4', '1.2.3.4/8'), IPS_V6 IP ('1:2:3:4:5:6:7:8/16'));
```

**Related Information**  


[User Groups](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/b9174d035f274ce481387700c13b7d2c.html "User groups support a separation of user management tasks, allowing you to manage related users together.") :arrow_upper_right:

[Password Policy Configuration Options](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/61662e3032ad4f8dbdb5063a21a7d706.html "The password policy of the database is defined by parameters in the password policy section of the indexserver.ini configuration file. The initial password policy of a user group is a copy of the database password policy.") :arrow_upper_right:

[Password Exclude List](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/fe3ffb3d7ac24fddb80e3322c671299f.html "A password exclude list is a list of words that are not allowed as passwords or parts of passwords. A password exclude list can be managed for every database individually.") :arrow_upper_right:

[CREATE USERGROUP Statement \(Access Control\)](create-usergroup-statement-access-control-9869125.md "Creates a usergroup.")

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

