<!-- loio5f1dffe49b484f9c88ba57c0340d6020 -->

# ROLE\_LDAP\_GROUPS System View

Shows the mapping between SAP HANA roles and LDAP groups.



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

ROLE\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name of the role.



</td>
</tr>
<tr>
<td valign="top">

ROLE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the role.



</td>
</tr>
<tr>
<td valign="top">

LDAP\_GROUP\_NAME



</td>
<td valign="top">

NVARCHAR\(1024\)



</td>
<td valign="top">

Displays the name of the LDAP group.



</td>
</tr>
</table>

**Related Information**  


[CREATE LDAP PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-ldap-provider-statement-access-control-3b72203.md "Creates an LDAP provider for use with LDAP authorization and authentication.")

[ALTER LDAP PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-ldap-provider-statement-access-control-ae9ba28.md "Updates an LDAP provider for use with LDAP authorization and authentication.")

[VALIDATE LDAP PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/validate-ldap-provider-statement-access-control-4181217.md "Validates an LDAP provider configuration and LDAP authentication and authorization for users of that LDAP provider.")

[DROP LDAP PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-ldap-provider-statement-access-control-340e913.md "Drops an LDAP provider, and its associated credential, from the internal secure credential store.")

[LDAP\_USERS System View](ldap-users-system-view-704e5b6.md "Shows information about the users using LDAP authorization.")

[LDAP\_PROVIDERS System View](ldap-providers-system-view-5b54fe2.md "Lists all LDAP providers.")

[CREATE ROLE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-role-statement-access-control-20d4a23.md "Creates a new role.")

[ALTER ROLE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-role-statement-access-control-c16ff34.md "Sets or unsets the role group of a role, and adds or drops the mapping of LDAP groups to a role.")

[DROP ROLE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-role-statement-access-control-20d74f7.md "Drops a role.")

