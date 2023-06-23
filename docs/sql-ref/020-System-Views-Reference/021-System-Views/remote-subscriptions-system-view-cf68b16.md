<!-- loiocf68b16bdfce47edad38adef7a71fe64 -->

# REMOTE\_SUBSCRIPTIONS System View

Lists all the remote subscriptions created for a remote source.




<table>
<tr>
<th valign="top">

Column



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

SUBSCRIPTION\_OID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the remote subscription OID.



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

Displays the remote subscription schema name.



</td>
</tr>
<tr>
<td valign="top">

SUBSCRIPTION\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the remote subscription name.



</td>
</tr>
<tr>
<td valign="top">

OWNER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the owner's name.



</td>
</tr>
<tr>
<td valign="top">

REMOTE\_SOURCE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the remote source name.



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

Displays whether the remote subscription is valid or not: TRUE/FALSE. This value is FALSE when its source or target objects are changed or dropped.



</td>
</tr>
<tr>
<td valign="top">

SUBSCRIPTION\_TYPE



</td>
<td valign="top">

NVARCHAR\(13\)



</td>
<td valign="top">

Displays the remote subscription type.



</td>
</tr>
<tr>
<td valign="top">

VIRTUAL\_TABLE\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the virtual table schema name.



</td>
</tr>
<tr>
<td valign="top">

VIRTUAL\_TABLE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the virtual table name.



</td>
</tr>
<tr>
<td valign="top">

SUBSCRIPTION\_QUERY\_STRING



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays the SELECT statement specified in the subscription when subscription type is SQL.



</td>
</tr>
<tr>
<td valign="top">

TARGET\_OBJECT\_TYPE



</td>
<td valign="top">

NVARCHAR\(9\)



</td>
<td valign="top">

Displays the remote subscription target object type: TABLE, PROCEDURE, or TASK.



</td>
</tr>
<tr>
<td valign="top">

TARGET\_OBJECT\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the target object schema name.



</td>
</tr>
<tr>
<td valign="top">

TARGET\_OBJECT\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the target object name.



</td>
</tr>
<tr>
<td valign="top">

TARGET\_OTHER\_PARAM\_STRING



</td>
<td valign="top">

NVARCHAR\(4000\)



</td>
<td valign="top">

Displays the constant parameter string to pass during execution when the target object type is PROCEDURE or TASK.



</td>
</tr>
<tr>
<td valign="top">

CHANGE\_MODE



</td>
<td valign="top">

NVARCHAR\(6\)



</td>
<td valign="top">

Displays the remote subscription change mode: NULL, NORMAL, UPSERT, or INSERT.



</td>
</tr>
<tr>
<td valign="top">

CHANGE\_TYPE\_COLUMN\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the remote subscription change type column name in the target table: I \(INSERT\), D \(DELETE\), and so on.



</td>
</tr>
<tr>
<td valign="top">

CHANGE\_TIME\_COLUMN\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the remote subscription change time column name in the target table. Supported data types are TIMESTAMP, CHAR, and NVARCHAR with a minimum length of 27.



</td>
</tr>
<tr>
<td valign="top">

CHANGE\_SEQUENCE\_COLUMN\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the remote subscription change sequence column name in the target table.



</td>
</tr>
<tr>
<td valign="top">

SCHEMA\_CHANGES



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether or not the remote subscription propagates schema changes: TRUE/FALSE.



</td>
</tr>
<tr>
<td valign="top">

TASK\_PROCEDURE\_PARAMETERS



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

Displays the comma-separated list of task parameters.



</td>
</tr>
</table>

**Related Information**  


[REMOTE\_SUBSCRIPTION\_DATA\_CONTAINERS System View](remote-subscription-data-containers-system-view-9289305.md "Provides information regarding remote subscription data.")

[REMOTE\_USERS System View](remote-users-system-view-d8980f4.md "Provides information about user mappings for cross-database access.")

[REMOTE\_SOURCES System View](remote-sources-system-view-20ccdd3.md "Provides information about remote sources.")

[M\_REMOTE\_SUBSCRIPTIONS System View](../022-Monitoring-Views/m-remote-subscriptions-system-view-5bb5aec.md "Provides the status and run-time information of a remote subscription.")

[CREATE REMOTE SUBSCRIPTION Statement \[Smart Data Integration\]](https://help.sap.com/viewer/7952ef28a6914997abc01745fef1b607/latest/en-US/12d89b67c7994f80bc516e30dadd3c0a.html)

[ALTER REMOTE SUBSCRIPTION Statement \[Smart Data Integration\]](https://help.sap.com/viewer/7952ef28a6914997abc01745fef1b607/latest/en-US/f88b70b3170849b0a57d4ff618887dce.html)

[DROP REMOTE SUBSCRIPTION Statement \[Smart Data Integration\]](https://help.sap.com/viewer/7952ef28a6914997abc01745fef1b607/latest/en-US/af65fc25d26c4968ac1448cf13056432.html)

