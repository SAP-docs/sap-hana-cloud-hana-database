<!-- loiod1fe1244d29510148f69be8b0e060dcc -->

# AUDIT\_LOG System View

Provides information about audit records, with the exception of XSA-auditing. You must have the AUDIT ADMIN, AUDIT OPERATOR, or AUDIT READ system privilege to access this view.



<a name="loiod1fe1244d29510148f69be8b0e060dcc___a_u_d_i_t__l_o_g_1struct_AUDIT_LOG"/>

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

TIMESTAMP



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the time that the event occurred.



</td>
</tr>
<tr>
<td valign="top">

HOST



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the name of the host where the event occurred.



</td>
</tr>
<tr>
<td valign="top">

PORT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the port number.



</td>
</tr>
<tr>
<td valign="top">

SERVICE\_NAME



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the name of the service.



</td>
</tr>
<tr>
<td valign="top">

CONNECTION\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the connection ID.



</td>
</tr>
<tr>
<td valign="top">

CLIENT\_HOST



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the IP of the client host.



</td>
</tr>
<tr>
<td valign="top">

CLIENT\_IP



</td>
<td valign="top">

NVARCHAR\(45\)



</td>
<td valign="top">

Displays the IP of the client application.



</td>
</tr>
<tr>
<td valign="top">

CLIENT\_PID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the PID of the client process.



</td>
</tr>
<tr>
<td valign="top">

CLIENT\_PORT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the port of the client process.



</td>
</tr>
<tr>
<td valign="top">

USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the user that is connected to the database.



</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the user who executed the statement.



</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the application.



</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the application user.



</td>
</tr>
<tr>
<td valign="top">

XS\_APPLICATION\_USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the XS application user.



</td>
</tr>
<tr>
<td valign="top">

AUDIT\_POLICY\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the Audit Policy hit.



</td>
</tr>
<tr>
<td valign="top">

AUTHENTICATION\_METHOD



</td>
<td valign="top">

VARCHAR\(48\)



</td>
<td valign="top">

Displays the name of the authentication method used to authenticate the audit log.



</td>
</tr>
<tr>
<td valign="top">

EVENT\_STATUS



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays whether the event was successful or not.



</td>
</tr>
<tr>
<td valign="top">

EVENT\_LEVEL



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the severity level of the event.



</td>
</tr>
<tr>
<td valign="top">

EVENT\_ACTION



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the action performed by the audit event.



</td>
</tr>
<tr>
<td valign="top">

SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of schema.



</td>
</tr>
<tr>
<td valign="top">

OBJECT\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of object.



</td>
</tr>
<tr>
<td valign="top">

PRIVILEGE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the granted privilege.



</td>
</tr>
<tr>
<td valign="top">

ROLE\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name of the granted role.



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

Displays the name of the granted role.



</td>
</tr>
<tr>
<td valign="top">

GRANTEE\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name of the grantee in GRANT/REVOKE statements.



</td>
</tr>
<tr>
<td valign="top">

GRANTEE



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the grantee in GRANT/REVOKE statements.



</td>
</tr>
<tr>
<td valign="top">

GRANTABLE



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays whether the privilege/role being granted is grantable or not.



</td>
</tr>
<tr>
<td valign="top">

FILE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the configuration file that was changed.



</td>
</tr>
<tr>
<td valign="top">

SECTION



</td>
<td valign="top">

NVARCHAR\(128\)



</td>
<td valign="top">

Displays the configuration that was changed.



</td>
</tr>
<tr>
<td valign="top">

KEY



</td>
<td valign="top">

NVARCHAR\(2000\)



</td>
<td valign="top">

Displays the attribute that was changed.



</td>
</tr>
<tr>
<td valign="top">

PREV\_VALUE



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

Displays the old value of the attribute.



</td>
</tr>
<tr>
<td valign="top">

VALUE



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

Displays the new value of the attribute.



</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_STRING



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays the SQL statement that caused the event.



</td>
</tr>
<tr>
<td valign="top">

COMMENT



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

Displays extra information about the event.



</td>
</tr>
<tr>
<td valign="top">

ORIGIN\_DATABASE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the original database name on cross-database queries.



</td>
</tr>
<tr>
<td valign="top">

ORIGIN\_USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the original user name on cross-database queries.



</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_ROOTCONTEXT\_ID



</td>
<td valign="top">

VARBINARY\(16\)



</td>
<td valign="top">

Displays the passport root context ID.



</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_TRANSACTION\_ID



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the passport transaction ID.



</td>
</tr>
<tr>
<td valign="top">

PASSPORT\_CONNECTION\_ID



</td>
<td valign="top">

VARBINARY\(16\)



</td>
<td valign="top">

Displays the passport connection ID.



</td>
</tr>
</table>



<a name="loiod1fe1244d29510148f69be8b0e060dcc__section_jxz_5fc_qhb"/>

## Additional Information

Database users with the AUDIT ADMIN, AUDIT OPERATOR, or AUDIT READ system privilege can view information in this system view. For all other database users, this view is empty.

**Related Information**  


[AUDIT\_ACTIONS System View](audit-actions-system-view-b856cdd.md "Provides information about all available audit actions.")

[AUDIT\_POLICIES System View](audit-policies-system-view-209e4d3.md "Provides information about audit policies.")

[GRANT Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/grant-statement-access-control-20f674e.md "Grants various types of privileges to users and roles.")

[REVOKE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/revoke-statement-access-control-20fc91c.md "Revokes roles or privileges for the specified objects from a user or role.")

[ALTER SYSTEM CLEAR AUDIT LOG Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-clear-audit-log-statement-system-management-d2231bd.md "Deletes old audit data from the SAP HANA database audit table.")

