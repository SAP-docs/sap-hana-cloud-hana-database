<!-- loio49b31f5d92044d9786b5e8f4d40d60de -->

# M\_PLE\_SESSIONS System View

Lists all planning sessions on the system as well as their status and details.



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

SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name.

</td>
</tr>
<tr>
<td valign="top">

SESSION\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the session name.

</td>
</tr>
<tr>
<td valign="top">

IS\_VALID

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the session is valid: TRUE or FALSE.

</td>
</tr>
<tr>
<td valign="top">

LAST\_ERROR

</td>
<td valign="top">

NVARCHAR\(2000\)

</td>
<td valign="top">

Displays the last error.

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

Displays the host name.

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

Displays the internal port.

</td>
</tr>
<tr>
<td valign="top">

SITE\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the site ID of the secondary site. This value is -1 on a single instance.

</td>
</tr>
</table>

**Related Information**  


[M\_PLE\_RUNTIME\_OBJECTS System View](m-ple-runtime-objects-system-view-d2aeece.md "Lists all the internal cache objects created to support the planning sessions, with details about each one.")

