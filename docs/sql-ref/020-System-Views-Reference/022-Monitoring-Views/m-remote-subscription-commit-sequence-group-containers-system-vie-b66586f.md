<!-- loiob66586f385e54207966f8036eedff85a -->

# M\_REMOTE\_SUBSCRIPTION\_COMMIT\_SEQUENCE\_GROUP\_CONTAINERS System View

Lists all CommitSequece virtual files for a remote source, and the number of entries stored in each virtual file.




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

REMOTE\_SOURCE\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the remote source OID.

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

SUBSCRIPTION\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the subscription OID

</td>
</tr>
<tr>
<td valign="top">

SUBSCRIPTION\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the subscription schema name.

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

Displays the subscription name.

</td>
</tr>
<tr>
<td valign="top">

CONTAINER\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the ID of the container of the virtual file.

</td>
</tr>
<tr>
<td valign="top">

COMMIT\_SEQUENCE\_CONTAINER\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the container ID of the CommitSequence virtual file.

</td>
</tr>
<tr>
<td valign="top">

MIN\_SEQUENCE\_ID

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the minimum sequence ID of the CommitSequence virtual file.

</td>
</tr>
<tr>
<td valign="top">

MAX\_SEQUENCE\_ID

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the maximum sequence ID of the CommitSequence virtual file.

</td>
</tr>
<tr>
<td valign="top">

ENTRY\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of CommitSequence entries in the virtual file.

</td>
</tr>
<tr>
<td valign="top">

IS\_DELETED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates if the container identified by COMMIT\_SEQUENCE\_CONTAINER\_ID is deleted. Values are TRUE or FALSE.

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

Displays the internal port number.

</td>
</tr>
</table>

**Related Information**  


[M\_REMOTE\_SUBSCRIPTIONS System View](m-remote-subscriptions-system-view-5bb5aec.md "Provides the status and run-time information of a remote subscription.")

[M\_REMOTE\_SUBSCRIPTION\_COMMIT\_SEQUENCE\_CONTAINERS System View](m-remote-subscription-commit-sequence-containers-system-view-ce09386.md "Lists all real time data elements such as markers and commit / rollback rows in the remote subscription commit sequence container.")

[M\_REMOTE\_SUBSCRIPTION\_COMPONENTS System View](m-remote-subscription-components-system-view-8a707f0.md "Provides remote subscription component information.")

[M\_REMOTE\_SUBSCRIPTION\_DISTRIBUTOR\_QUEUE\_DATA\_CONTAINERS System View](m-remote-subscription-distributor-queue-data-containers-system-vi-0cf80ab.md "Lists all real time data elements between begin-marker and end-marker for the remote subscription.")

[M\_REMOTE\_SUBSCRIPTION\_LOB\_CONTAINERS System View](m-remote-subscription-lob-containers-system-view-13e3ccb.md "Lists all lob container IDs for each remote subscription transaction.")

[M\_REMOTE\_SUBSCRIPTION\_ROLLBACK\_SAVEPOINT\_CONTAINERS System View](m-remote-subscription-rollback-savepoint-containers-system-view-0217719.md "Lists all rollback save points for each remote subscription transaction.")

[M\_REMOTE\_SUBSCRIPTION\_STATISTICS System View](m-remote-subscription-statistics-system-view-859e5eb.md "Provides remote subscription statistic information.")

[M\_REMOTE\_SUBSCRIPTION\_TRANSACTION\_CONTAINERS System View](m-remote-subscription-transaction-containers-system-view-6134e02.md "Lists all real time data rowsets in the remote subscription transaction container.")

[REMOTE\_SUBSCRIPTIONS System View](../021-System-Views/remote-subscriptions-system-view-cf68b16.md "Lists all the remote subscriptions created for a remote source.")

[REMOTE\_SUBSCRIPTION\_DATA\_CONTAINERS System View](../021-System-Views/remote-subscription-data-containers-system-view-9289305.md "Provides information regarding remote subscription data.")

[REMOTE\_SUBSCRIPTION\_EXCEPTIONS System View](../021-System-Views/remote-subscription-exceptions-system-view-6a5ada4.md "Provides remote subscription exception information.")

