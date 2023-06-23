<!-- loiod2aeece066a0430abafedcd155eec331 -->

# M\_PLE\_RUNTIME\_OBJECTS System View

Lists all the internal cache objects created to support the planning sessions, with details about each one.



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

OBJECT\_TYPE



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the object type:

-   LOOKUP DICTIONARY
-   TIMETABLE DICTIONARY
-   FISCPERTABLE DICTIONARY
-   CONVERSTION DICTIONARY
-   FOX REFERENCE DATA DICTIONARY



</td>
</tr>
<tr>
<td valign="top">

OBJECT\_SCOPE



</td>
<td valign="top">

NVARCHAR\(45\)



</td>
<td valign="top">

Displays the object scope: SESSION/GLOBAL.



</td>
</tr>
<tr>
<td valign="top">

OBJECT\_NAME



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

Displays the object name. This name is a generated, unique name for the runtime object, derived from the corresponding session name, planning command name, and source columns.



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

SOURCE\_COLUMNS



</td>
<td valign="top">

NVARCHAR\(2000\)



</td>
<td valign="top">

Displays the source columns.



</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the memory size, in bytes.



</td>
</tr>
<tr>
<td valign="top">

ENTRY\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of entries in the runtime object.



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


[M\_PLE\_SESSIONS System View](m-ple-sessions-system-view-49b31f5.md "Lists all planning sessions on the system as well as their status and details.")

[Session Variables](../../010-SQL-Reference/session-variables-a16678c.md " 		 		 		 		 		 		 	")

