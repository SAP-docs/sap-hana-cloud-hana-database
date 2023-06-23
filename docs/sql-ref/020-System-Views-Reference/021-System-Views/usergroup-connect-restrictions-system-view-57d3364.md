<!-- loio57d3364557d140c291e6cc5fb09eef7c -->

# USERGROUP\_CONNECT\_RESTRICTIONS System View

Provides details on connection restrictions for all user groups.



<a name="loio57d3364557d140c291e6cc5fb09eef7c__section_izj_b4s_3xb"/>

## Structure

****


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

USERGROUP\_NAME



</td>
<td valign="top">

NVARCHAR\(256\) NOT NULL



</td>
<td valign="top">

Displays the name of the user group.



</td>
</tr>
<tr>
<td valign="top">

RESTRICTION\_NAME



</td>
<td valign="top">

NVARCHAR\(256\) NOT NULL



</td>
<td valign="top">

Displays the name of the connect restriction.



</td>
</tr>
<tr>
<td valign="top">

IS\_ENABLED



</td>
<td valign="top">

NVARCHAR\(5\) NOT NULL



</td>
<td valign="top">

Displays whether the connect restriction is enabled or not. Possible values are: TRUE / FALSE.



</td>
</tr>
<tr>
<td valign="top">

RESTRICTION\_TYPE



</td>
<td valign="top">

VARCHAR\(14\)



</td>
<td valign="top">

Displays the type of the restriction. Possible values are: IP.



</td>
</tr>
<tr>
<td valign="top">

VALUE



</td>
<td valign="top">

VARCHAR\(50\)



</td>
<td valign="top">

Displays a network address.



</td>
</tr>
<tr>
<td valign="top">

TIME\_FROM



</td>
<td valign="top">

TIME



</td>
<td valign="top">

For internal use.



</td>
</tr>
<tr>
<td valign="top">

TIME\_UNTIL



</td>
<td valign="top">

TIME



</td>
<td valign="top">

For internal use.



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

For internal use.



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

For internal use.



</td>
</tr>
</table>



<a name="loio57d3364557d140c291e6cc5fb09eef7c__section_oly_g3s_3xb"/>

## Additional Information

Users see different values in this view depending on their privileges, as follows:

-   Users with one of the following object privileges can see all connection restrictions for that user group:
    -   OPERATOR object privilege
    -   DROP object privilege
    -   GRANTOR object privilege

-   Users with one of the following system privileges can see all connections restrictions for all user groups:
-   -   CATALOG READ system privilege
-   CREATE USERGROUP system privilege

-   Members of a user group can see connection restrictions only for that user group.

