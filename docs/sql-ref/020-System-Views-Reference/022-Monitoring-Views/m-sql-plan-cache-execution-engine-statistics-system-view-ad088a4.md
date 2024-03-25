<!-- loioad088a4d0d254d1ba6d0a1fc58068eb9 -->

# M\_SQL\_PLAN\_CACHE\_EXECUTION\_ENGINE\_STATISTICS System View

Displays execution statistics information. For some plan IDs, two entries for a single query string are returned, one each for HEX and non-HEX.




<table>
<tr>
<th valign="top">

COLUMN\_NAME

</th>
<th valign="top">

DATA\_TYPE\_NAME

</th>
<th valign="top">

COMMENTS

</th>
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

PLAN\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the logical plan ID which is a non-negative value.

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

Displays the statement string.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_HASH

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the MD5 hash value for STATEMENT\_STRING.

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

Displays the user name who prepared the plan.

</td>
</tr>
<tr>
<td valign="top">

SESSION\_USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the SESSION\_USER name who prepared the plan. The same value with M\_CONNECTIONS.USER\_NAME

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

Displays the schema name that the SQL plan belongs to. SQL plans are generated in each schema even though the statement string is the same since the query optimizer statistics might be different.

</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_ENGINE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays a list of all involved execution frameworks.

</td>
</tr>
<tr>
<td valign="top">

PREPARATION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated count of plan preparation.

</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated count of plan execution.

</td>
</tr>
<tr>
<td valign="top">

AVG\_PREPARATION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time of plan preparation in milliseconds.

</td>
</tr>
<tr>
<td valign="top">

AVG\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average elapsed time of plan execution in milliseconds.

</td>
</tr>
<tr>
<td valign="top">

AVG\_EXECUTION\_CPU\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average CPU time of plan execution in milliseconds.

</td>
</tr>
<tr>
<td valign="top">

AVG\_EXECUTION\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average size of tracked actual memory consumption in bytes.

</td>
</tr>
<tr>
<td valign="top">

LAST\_EXECUTION\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last execution timestamp

</td>
</tr>
</table>

