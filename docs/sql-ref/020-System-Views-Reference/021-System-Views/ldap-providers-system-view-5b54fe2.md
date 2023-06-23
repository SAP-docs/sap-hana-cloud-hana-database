<!-- loio5b54fe223a8045bfbc6b51cb66c64967 -->

# LDAP\_PROVIDERS System View

Lists all LDAP providers.



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

LDAP\_PROVIDER\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the ID of the LDAP provider.



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

IS\_DEFAULT



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the the LDAP provider is the default provider: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

IS\_SSL\_USED



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the connection to the configured LDAP Server uses SSL: TRUE/FALSE. If SSL ON is specified for the provider, or if USER LOOKUP URL or NESTED GROUP LOOKUP URL use 'ldaps://', the value is TRUE. Otherwise, the value is FALSE.



</td>
</tr>
<tr>
<td valign="top">

IS\_PROVIDER\_ENABLED



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the LDAP provider is enabled for use: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

ATTRIBUTE\_DN



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the LDAP attribute to provide the LDAP distinguished name of a user.



</td>
</tr>
<tr>
<td valign="top">

ATTRIBUTE\_MEMBER\_OF



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the LDAP attribute that provides the list of LDAP groups that the user is a member of.



</td>
</tr>
<tr>
<td valign="top">

IS\_USER\_CREATION\_ENABLED



</td>
<td valign="top">

VARCHAR\(5\)



</td>
<td valign="top">

Displays whether the LDAP provider is allowed to create a user implicitly: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

USER\_CREATION\_USER\_TYPE



</td>
<td valign="top">

NVARCHAR\(10\)



</td>
<td valign="top">

Displays the type of user to create when LDAP user creation is enabled. NULL if LDAP user creation is not enabled: STANDARD, RESTRICTED, NULL



</td>
</tr>
<tr>
<td valign="top">

USER\_CREATION\_USERGROUP



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the usergroup a newly created user will be a member of.



</td>
</tr>
</table>

**Related Information**  


[CREATE LDAP PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-ldap-provider-statement-access-control-3b72203.md "Creates an LDAP provider for use with LDAP authorization and authentication.")

[ALTER LDAP PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-ldap-provider-statement-access-control-ae9ba28.md "Updates an LDAP provider for use with LDAP authorization and authentication.")

[DROP LDAP PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-ldap-provider-statement-access-control-340e913.md "Drops an LDAP provider, and its associated credential, from the internal secure credential store.")

[VALIDATE LDAP PROVIDER Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/validate-ldap-provider-statement-access-control-4181217.md "Validates an LDAP provider configuration and LDAP authentication and authorization for users of that LDAP provider.")

[LDAP\_PROVIDER\_URLS System View](ldap-provider-urls-system-view-7cf2869.md "Lists all LDAP provider URLs.")

[LDAP\_USERS System View](ldap-users-system-view-704e5b6.md "Shows information about the users using LDAP authorization.")

[LDAP Provider Configuration (Reference)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/b8406c6e363747dea9098f00648d15b5.html "To set up a connection to an LDAP server, you must create an LDAP provider in the SAP HANA database. Depending on your requirements, you can use the LDAP server to authenticate and/or authorize users. For LDAP-authenticated users, you can also enable the automatic creation of users in SAP HANA.") :arrow_upper_right:

