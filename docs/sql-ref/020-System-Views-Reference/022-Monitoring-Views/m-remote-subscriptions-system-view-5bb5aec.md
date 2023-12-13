<!-- loio5bb5aec934e143bdabac0d05736cbeb5 -->

# M\_REMOTE\_SUBSCRIPTIONS System View

Provides the status and run-time information of a remote subscription.




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

STATE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the event state:

-   CREATED
-   MAT\_START\_BEG\_MARKER - Materialization started. Waiting for BEGIN MARKER
-   MAT\_START\_END\_MARKER - Materialization started. Waiting for end marker
-   MAT\_COMP\_BEG\_MARKER - Materialization completed. Waiting for begin marker
-   MAT\_COMP\_END\_MARKER - Materialization completed. Waiting for end marker
-   AUTO\_CORRECT\_CHANGE\_DATA
-   APPLY\_CHANGE\_DATA



</td>
</tr>
<tr>
<td valign="top">

OPTIMIZED\_QUERY\_STRING

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the optimized query string. If there are multiple subscriptions interested in the same query result, with the same internal distribution ID, each subscription can use the same result.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZED\_QUERY\_HASH

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the hash of the optimized query string.

</td>
</tr>
<tr>
<td valign="top">

INTERNAL\_DISTRIBUTION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the generated integer that identifies if multiple target tables are interested in the changes from the same source SQL or virtual table.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZED\_QUERY\_RESULTSET\_TYPE

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Displays the query result set type:

0 - REGULAR

1 - CLUSTER

2 - POOL

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_SUBSCRIPTION

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays an optional subscription name registered by the adapter in the remote source system.

</td>
</tr>
<tr>
<td valign="top">

VOLUME\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the persistence volume ID.

</td>
</tr>
<tr>
<td valign="top">

BEGIN\_MARKER

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the generated begin marker when the QUEUE command is called. The begin marker must use the format: B*<remote\_source\_oid\>*\_*<remote\_subscription\_oid\>*\_*<YYYYMMDDHH24MMSSFF7\>*.

</td>
</tr>
<tr>
<td valign="top">

END\_MARKER

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the generated end marker when the DISTRIBUTE command is called. The end marker must use the format: E*<remote\_source\_oid\>*\_*<remote\_subscription\_oid\>*\_*<YYYYMMDDHH24MMSSFF7\>*.

</td>
</tr>
<tr>
<td valign="top">

BEGIN\_MARKER\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the timestamp when the QUEUE request is received.

</td>
</tr>
<tr>
<td valign="top">

END\_MARKER\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the timestamp when the DISTRIBUTE command is called.

</td>
</tr>
<tr>
<td valign="top">

LAST\_PROCESSED\_TRANSACTION\_ID

</td>
<td valign="top">

VARBINARY\(128\)

</td>
<td valign="top">

Displays the transaction ID of the last processed transaction.

</td>
</tr>
<tr>
<td valign="top">

LAST\_PROCESSED\_TRANSACTION\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time when the last transaction was applied.

</td>
</tr>
<tr>
<td valign="top">

LAST\_PROCESSED\_BEGIN\_SEQUENCE\_ID

</td>
<td valign="top">

VARBINARY\(68\)

</td>
<td valign="top">

Displays the begin record sequence ID of the last processed transaction.

</td>
</tr>
<tr>
<td valign="top">

LAST\_PROCESSED\_COMMIT\_SEQUENCE\_ID

</td>
<td valign="top">

VARBINARY\(68\)

</td>
<td valign="top">

Displays the commit record sequence ID of the last processed transaction.

</td>
</tr>
<tr>
<td valign="top">

LAST\_RECEIVED\_SEQUENCE\_ID

</td>
<td valign="top">

VARBINARY\(68\)

</td>
<td valign="top">

Displays the last received sequence ID.

</td>
</tr>
<tr>
<td valign="top">

LAST\_RECEIVED\_CUSTOM\_ID

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the last received custom ID. Custom IDs may be used by adapters with every changed-data row of a transaction.

</td>
</tr>
<tr>
<td valign="top">

LAST\_PROCESSED\_CUSTOM\_ID

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the last processed custom ID. Custom IDs may be used by adapters with every changed-data row of a transaction.

</td>
</tr>
</table>

**Related Information**  


[M\_REMOTE\_SUBSCRIPTION\_COMMIT\_SEQUENCE\_CONTAINERS System View](m-remote-subscription-commit-sequence-containers-system-view-ce09386.md "Lists all real time data elements such as markers and commit / rollback rows in the remote subscription commit sequence container.")

[M\_REMOTE\_SUBSCRIPTION\_COMMIT\_SEQUENCE\_GROUP\_CONTAINERS System View](m-remote-subscription-commit-sequence-group-containers-system-vie-b66586f.md "Lists all CommitSequece virtual files for a remote source, and the number of entries stored in each virtual file.")

[M\_REMOTE\_SUBSCRIPTION\_COMPONENTS System View](m-remote-subscription-components-system-view-8a707f0.md "Provides remote subscription component information.")

[M\_REMOTE\_SUBSCRIPTION\_DISTRIBUTOR\_QUEUE\_DATA\_CONTAINERS System View](m-remote-subscription-distributor-queue-data-containers-system-vi-0cf80ab.md "Lists all real time data elements between begin-marker and end-marker for the remote subscription.")

[M\_REMOTE\_SUBSCRIPTION\_LOB\_CONTAINERS System View](m-remote-subscription-lob-containers-system-view-13e3ccb.md "Lists all lob container IDs for each remote subscription transaction.")

[M\_REMOTE\_SUBSCRIPTION\_ROLLBACK\_SAVEPOINT\_CONTAINERS System View](m-remote-subscription-rollback-savepoint-containers-system-view-0217719.md "Lists all rollback save points for each remote subscription transaction.")

[M\_REMOTE\_SUBSCRIPTION\_STATISTICS System View](m-remote-subscription-statistics-system-view-859e5eb.md "Provides remote subscription statistic information.")

[M\_REMOTE\_SUBSCRIPTION\_TRANSACTION\_CONTAINERS System View](m-remote-subscription-transaction-containers-system-view-6134e02.md "Lists all real time data rowsets in the remote subscription transaction container.")

[REMOTE\_SUBSCRIPTIONS System View](../021-System-Views/remote-subscriptions-system-view-cf68b16.md "Lists all the remote subscriptions created for a remote source.")

[REMOTE\_SUBSCRIPTION\_DATA\_CONTAINERS System View](../021-System-Views/remote-subscription-data-containers-system-view-9289305.md "Provides information regarding remote subscription data.")

[REMOTE\_SUBSCRIPTION\_EXCEPTIONS System View](../021-System-Views/remote-subscription-exceptions-system-view-6a5ada4.md "Provides remote subscription exception information.")

