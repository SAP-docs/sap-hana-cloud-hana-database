<!-- loiod1e58889c4bb4f9e88411a0e5a5e3590 -->

# M\_CS\_TABLE\_LOCKS System View

Shows the locked tables threads waiting to lock tables.




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

Displays the schema name as used in SQL.



</td>
</tr>
<tr>
<td valign="top">

TABLE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the table name as used in SQL.



</td>
</tr>
<tr>
<td valign="top">

TABLE\_OID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the unique internal table ID, which remains unchanged during rename.



</td>
</tr>
<tr>
<td valign="top">

PART\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the logical partition number, 0 if the table is not partitioned, -1 if the logical partition number cannot be retrieved from metadata.



</td>
</tr>
<tr>
<td valign="top">

INTERNAL\_PART\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the internal partition number as used in internal IndexName objects.



</td>
</tr>
<tr>
<td valign="top">

ACQUIRED\_HANDLE\_COUNT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the number of handles acquired for the table.



</td>
</tr>
<tr>
<td valign="top">

WAITING\_HANDLE\_COUNT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the number of handles waiting for access to the table.



</td>
</tr>
<tr>
<td valign="top">

LOCK\_ID



</td>
<td valign="top">

VARCHAR\(20\)



</td>
<td valign="top">

Displays the unique identifier for the table at IndexMgr level, also found in dumps, trace output, etc.



</td>
</tr>
<tr>
<td valign="top">

IS\_COORDINATOR



</td>
<td valign="top">

VARCHAR\(5\)



</td>
<td valign="top">

Displays the internal flag used for asserting in IndexMgr code.



</td>
</tr>
<tr>
<td valign="top">

IS\_SHARED



</td>
<td valign="top">

VARCHAR\(5\)



</td>
<td valign="top">

Displays the internal flag used for asserting in IndexMgr code.



</td>
</tr>
<tr>
<td valign="top">

IS\_BLOCK\_MAIN



</td>
<td valign="top">

VARCHAR\(5\)



</td>
<td valign="top">

I Displays the iternal flag used for asserting in IndexMgr code.



</td>
</tr>
<tr>
<td valign="top">

IS\_TABLE



</td>
<td valign="top">

VARCHAR\(5\)



</td>
<td valign="top">

Displays the internal flag used for asserting in IndexMgr code.



</td>
</tr>
<tr>
<td valign="top">

IS\_MODE\_NO\_WAIT



</td>
<td valign="top">

VARCHAR\(5\)



</td>
<td valign="top">

Displays the IS\_MODE\_NO\_WAIT flag. Access to all current handles is granted without waiting in an optimized per thread structure since none of the active handles are in conflict. This internal flag is automatically set and reset during locking operations to trigger internal performance optimizations, it does not relate to the NOWAIT keyword of SQL.



</td>
</tr>
</table>

