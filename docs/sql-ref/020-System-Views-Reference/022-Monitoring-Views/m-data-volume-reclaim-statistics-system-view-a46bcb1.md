<!-- loioa46bcb1203fa4c8691875a0b9e806b61 -->

# M\_DATA\_VOLUME\_RECLAIM\_STATISTICS System View

Displays statistical information on reclamation operations on a data volume.



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

DATABASE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the database.

</td>
</tr>
<tr>
<td valign="top">

HOST

</td>
<td valign="top">

VARCHAR\(64\)

</td>
<td valign="top">

Displays the name of the Host.

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

STATISTICS\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the statistics object unique ID.

</td>
</tr>
<tr>
<td valign="top">

RECLAIM\_STATUS

</td>
<td valign="top">

VARCHAR\(32\)

</td>
<td valign="top">

Displays the reclaim status.

</td>
</tr>
<tr>
<td valign="top">

START\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the start time of the reclaim.

</td>
</tr>
<tr>
<td valign="top">

END\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the end time of the reclaim.

</td>
</tr>
<tr>
<td valign="top">

DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the duration of the reclaim.

</td>
</tr>
<tr>
<td valign="top">

RECLAIM\_THRESHOLD

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Specifies the desired percentage of the payload to which the data volume should be reduced.

</td>
</tr>
<tr>
<td valign="top">

STEP\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of reclaimed steps already performed.

</td>
</tr>
<tr>
<td valign="top">

RECLAIMED\_PARTITION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of successfully reclaimed or currently reclaiming partitions.

</td>
</tr>
<tr>
<td valign="top">

FAILED\_RECLAIM\_PARTITION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of partitions on which reclaim operation failed.

</td>
</tr>
<tr>
<td valign="top">

PARTITION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of data volume partitions.

</td>
</tr>
<tr>
<td valign="top">

INITIAL\_USED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the used size in bytes before the reclaim.

</td>
</tr>
<tr>
<td valign="top">

INITIAL\_TOTAL\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size in bytes before the reclaim.

</td>
</tr>
<tr>
<td valign="top">

INITIAL\_FILE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the file's size in bytes before the reclaim.

</td>
</tr>
<tr>
<td valign="top">

INITIAL\_FILL\_RATIO

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the fill ratio before reclaim.

</td>
</tr>
<tr>
<td valign="top">

RECLAIM\_USED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the used size in bytes during the reclaim or right after it.

</td>
</tr>
<tr>
<td valign="top">

RECLAIM\_TOTAL\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size in bytes during the reclaim or right after it.

</td>
</tr>
<tr>
<td valign="top">

RECLAIM\_FILE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the file's size during reclaim or right after it

</td>
</tr>
<tr>
<td valign="top">

RECLAIM\_FILL\_RATIO

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the fill ratio during the reclaim or right after it.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_MOVED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size in bytes of moved data.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_MOVED\_PAGES

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of moved pages.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_MOVE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total time in seconds for moving pages.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_TRUNCATED\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size in bytes of truncated data.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_TRUNCATE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total time in seconds for truncating data.

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

USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the user.

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

Displays the application user name.

</td>
</tr>
</table>

