<!-- loio859e5eb043b6493a93d5f66abd320ffd -->

# M\_REMOTE\_SUBSCRIPTION\_STATISTICS System View

Provides remote subscription statistic information.



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

RECEIVED\_MESSAGE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the received message count.

</td>
</tr>
<tr>
<td valign="top">

RECEIVED\_MESSAGE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the received message size in bytes.

</td>
</tr>
<tr>
<td valign="top">

APPLIED\_MESSAGE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the received message count.

</td>
</tr>
<tr>
<td valign="top">

APPLIED\_MESSAGE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the applied message size in bytes.

</td>
</tr>
<tr>
<td valign="top">

REJECTED\_MESSAGE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the rejected message count.

</td>
</tr>
<tr>
<td valign="top">

LAST\_MESSAGE\_RECEIVED

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last received message.

</td>
</tr>
<tr>
<td valign="top">

LAST\_MESSAGE\_APPLIED

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last applied message.

</td>
</tr>
<tr>
<td valign="top">

RECEIVER\_LATENCY

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the receiver latency.

</td>
</tr>
<tr>
<td valign="top">

APPLIER\_LATENCY

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the applier latency.

</td>
</tr>
</table>

