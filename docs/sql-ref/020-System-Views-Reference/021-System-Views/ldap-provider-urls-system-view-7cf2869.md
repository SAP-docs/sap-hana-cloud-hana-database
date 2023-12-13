<!-- loio7cf28690884b4082ae9de7b7e5a07153 -->

# LDAP\_PROVIDER\_URLS System View

Lists all LDAP provider URLs.



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

LDAP\_PROVIDER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the LDAP provider.

</td>
</tr>
<tr>
<td valign="top">

URL TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the LDAP provider URL type.

</td>
</tr>
<tr>
<td valign="top">

URL

</td>
<td valign="top">

NVARCHAR\(4096\)

</td>
<td valign="top">

Displays the URL for the LDAP provider.

</td>
</tr>
</table>



<a name="loio7cf28690884b4082ae9de7b7e5a07153__section_hk1_wtb_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[CREATE LDAP PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-ldap-provider-statement-access-control-3b72203.md "Creates an LDAP provider for use with LDAP authorization and authentication.")

[ALTER LDAP PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-ldap-provider-statement-access-control-ae9ba28.md "Updates an LDAP provider for use with LDAP authorization and authentication.")

[DROP LDAP PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-ldap-provider-statement-access-control-340e913.md "Drops an LDAP provider, and its associated credential, from the internal secure credential store.")

[VALIDATE LDAP PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/validate-ldap-provider-statement-access-control-4181217.md "Validates an LDAP provider configuration and LDAP authentication and authorization for users of that LDAP provider.")

[LDAP\_PROVIDERS System View](ldap-providers-system-view-5b54fe2.md "Lists all LDAP providers.")

[LDAP\_USERS System View](ldap-users-system-view-704e5b6.md "Provides information about the users using LDAP authorization.")

[LDAP Provider Configuration (Reference)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/b8406c6e363747dea9098f00648d15b5.html "To set up a connection to an LDAP server, you must create an LDAP provider in the SAP HANA database. Depending on your requirements, you can use the LDAP server to authenticate and/or authorize users. For LDAP-authenticated users, you can also enable the automatic creation of users in SAP HANA.") :arrow_upper_right:

