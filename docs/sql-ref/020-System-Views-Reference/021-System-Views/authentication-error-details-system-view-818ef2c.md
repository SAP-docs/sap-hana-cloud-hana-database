<!-- loio818ef2c9866842cf94a3adb36050b2a7 -->

# AUTHENTICATION\_ERROR\_DETAILS System View

Displays details of authentication errors occurring during connection using a client or SQL statement.



<a name="loio818ef2c9866842cf94a3adb36050b2a7___a_u_d_i_t__p_o_l_i_c_i_e_s_1struct_AUDIT_POLICIES"/>

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

CORRELATION\_ID

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the unique correlation ID for this authentication error.

</td>
</tr>
<tr>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time the authentication error occurred.

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

Displays the name of the host where the authentication error occurred.

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

AUTHENTICATION\_FOR

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays for which action the authentication failed. \[Client Connect, SQL Connect, SQL Validate ,HTTP Request\]

</td>
</tr>
<tr>
<td valign="top">

AUTHENTICATION\_METHOD

</td>
<td valign="top">

NVARCHAR\(48\)

</td>
<td valign="top">

Displays the name of the used authentication method.

</td>
</tr>
<tr>
<td valign="top">

INTERNAL\_ERROR\_CODE

</td>
<td valign="top">

NVARCHAR\(3\)

</td>
<td valign="top">

Displays the error type code why the authentication failed.

</td>
</tr>
<tr>
<td valign="top">

REASON

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the reason why the authentication failed.

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

Displays the name of the user that tried to authenticate.

</td>
</tr>
<tr>
<td valign="top">

EXTERNAL\_IDENTITY

</td>
<td valign="top">

NVARCHAR\(512\)

</td>
<td valign="top">

Displays the external identity of the user.

</td>
</tr>
<tr>
<td valign="top">

IDENTITY\_PROVIDER

</td>
<td valign="top">

NVARCHAR\(512\)

</td>
<td valign="top">

Displays the issuer of the identity provider.

</td>
</tr>
<tr>
<td valign="top">

PROVIDER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the JWT, SAML or X509 provider used to authenticate the user.

</td>
</tr>
<tr>
<td valign="top">

PSE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the PSE to validate the assertion or token.

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

Displays the host name of the client machine.

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

Displays the IP of the client machine.

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

Displays the client process ID.

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

CLIENT\_TYPE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the type of the used client.

</td>
</tr>
<tr>
<td valign="top">

CLIENT\_VERSION

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Display the version information of the used client.

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

APPLICATION\_SOURCE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays application source information.

</td>
</tr>
</table>



<a name="loio818ef2c9866842cf94a3adb36050b2a7__section_f2z_3tb_kxb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

This view also requires the SELECT object-level privilege. Users with the DELETE object-level privilege can remove rows from the view.

